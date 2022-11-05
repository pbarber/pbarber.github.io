# Asking the right questions

In the last few weeks I've worked on datasets across several different domains and had to quickly understand the data with the help of domain experts. This is very interesting, as I love learning about what other people do, and also difficult as I need to quickly learn about a new domain from someone who has a limited amount of time. I have found that the key is to **understand the context in which the data is used** rather than the data itself. Any work with that I will do using the data is most effective when I have a good grasp of the context.

To help me do this I've put together a list of questions that I typically ask when approaching new data for the first time. I usually approach this from the angle of a metric, rather than a dataset. Domain **experts are typically very comfortable talking about metrics that they use** but may not be comfortable talking about 'data' and may not recognise their metrics as data . As I said in a [previous post](how-to-present-data-for-visualisation.md) I class a metric as:

> something that has been measured; often a number such as ‘amount of money spent’ or ‘number of items’ but may also be a non-numerical value such as a positive or negative test result

The five questions I always ask are:

## What does it describe?

I like to think of data as an **attempt to measure the real world**. This question tries to elicit a summary of the real-world process that is being measured, making sure I understand any domain-specific language. I'm always trying to extract as much detail as I can through asking additional questions, although most of the time the additional question is either 'what do you mean by ...?' or 'why is ... important?'.

I always check my interpretations of the answers to these questions to the expert, which invariably finds errors in my understanding.

## What does it look like?

The key here is to get a feel for the data itself:

* Is it a percentage, a test result, a financial value, a time of day?
What is the range of possible values?
How often is it measured and updated?
Can it be broken down into sub-metrics or by different groups?
How do you prove to yourself that the data is correct?

## What do you compare it to?

This question helps me to understand what other data needs to be gathered in order to make the metric valuable, as well as how to present informative comparisons.

Users of the metric might be comparing it to itself at earlier points in time, their own targets, other organisations' data or completely different metrics:

* If they are comparing to older data, what comparisons make sense? Should we compare to the most recent data or last month's/year's data for the same date? This gives a good feel for seasonality of the data.
* Which other organisations are they comparing against?
* If we are comparing to other metrics, are we comparing values or rates of change? Why do these comparisons make sense?

## What actions will it inform?

This question helps to clarify the key uses of the metric, and the people who are using it to make decisions. Understanding what  decisions can be made helps to tease out the best way to present the data. Remember that **'do nothing' is still a decision**. My aim is always to provide the information that an end-user needs to be able to make informed decisions.

If I don't understand who all the users of the metric are, then now is the time to clarify this.

## Where does it come from?

Usually this question provides the name of the next person I need to talk to, but if the answer is 'my team aggregates it from seven different sources' then there is likely some scope for time-saving automation of the process.