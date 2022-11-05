# How to present data for visualisation

*This post was originally published on codeandnumbers.co.uk on 19th September 2021*

This one goes in the box marked 'I should have thought about this a long time ago'. 

I've been creating charts and reports for a long time and never really stepped considered why I tend to gravitate towards presenting data in an 'aggregate by all useful dimensions' format. Having spent some time thinking about this and discussing my thoughts with [Alastair McKinley](https://twitter.com/dsl4life), I feel I can present this in a meaningful manner. I feel almost certain that this has been covered in great detail elsewhere but spent a lot time searching and finding nothing.

I tend to think about a dataset as a collection of:

* metrics: something that has been measured; often a number such as 'amount of money spent' or 'number of items' but may also be a non-numerical value such as a positive or negative test result
* dimensions: data that adds detail to the metrics, for example the age of the person tested, the type of the items or the location the money was spent in

Most visualisations show data that has been aggregated in some way; the data is summarised before being displayed. There are an infinite number of ways that data can be aggregated, from simple counts of records over a dimension to running complex machine learning models over all records in a dimension.

As with many things, there's a sliding scale between flexibility and performance in how we present this data - more flexible approaches are less efficient, more efficient approaches are less flexible. The three key approaches for presenting data for visualisation are to present:

1. All records (most flexible/least efficient)
2. Multiple combinations of dimensions aka Cube
3. One combination of all dimensions aka Grouped (least flexible/most efficient)

## All records

Presenting all records is the most flexible, as the person or process receiving that data can perform whatever aggregation they wish on the data. However, there are many situations where this is not preferable, e.g.:

* The dataset is large, and will take a long time to transfer
* Reaggregating the dataset every time it is used will unnecessarily consume resources and time
* You do not have all the records, you may be working with pre-aggregated data
* The records cannot be shared e.g. they contain personal or proprietary information

Note that aggregating your data does not ensure that personal/proprietary data cannot be extracted from your dataset - you may still need to apply [statistical disclosure control](https://en.wikipedia.org/wiki/Statistical_disclosure_control) to reduce this risk.

In SQL this looks like:

```sql
SELECT 
    dim1, 
    dim2, 
    metric 
FROM mytable;
```

## Cube

The Cube approach is necessary when you need to show non-aggregatable metrics, such as the distinct number of records for a combination of dimensions. It requires additional effort within the visualisations to filter the data so that only the relevant parts of your Cube are shown - otherwise your metrics may be counted many times over. The benefit is that it is likely still more efficient than presenting all the records.

In SQL this looks like:

```sql
SELECT 
    dim1, 
    dim2, 
    agg_function(metric) 
FROM mytable
GROUP BY GROUPING SETS ((dim1, dim2), (dim1), (dim2), ());
```

Which would produce four views of the dataset, each grouped by one of the dimensions specified.

## Grouped

The Grouped approach is most performant as it only calculates and transfers the data that is needed. It is the most performant but not usable where non aggregatable measurements are used - such as counts of distinct items, or median values. It requires some extra effort in visualisations to further aggregate the data  where not all dimensions are used.

In SQL this looks like:

```sql
SELECT 
    dim1, 
    dim2, 
    agg_function(metric) 
FROM mytable 
GROUP BY dim1, dim2;
```

## Very big data

Sometimes datasets are so large that even with Cubes or Grouped views they need to be filtered or sampled before they can effectively be visualised due to the sheer volume of data.  The challenge then becomes how to create a good user experience when not all data is available at the same time. Possible solutions include query or drill-down type visualisations where the user controls how they explore the data.