# Improving trust in COVID-19 modelling

*This post was originally published on codeandnumbers.co.uk on 6th June 2021*

This quote from the CEO of NHS Providers is very illuminating in terms of the current level of respect for COVID-19 modelling in the NHS:

> For the record, trust leaders are sceptical of value of predictive statistical models here given their performance over last 15 months. Leaders point to the crude assumptions that have to be made and the huge shifts in outcome if small changes are made to those assumptions.
> https://twitter.com/ChrisCEOHopson/status/1401403343667347458

This isn't a flaw in modelling itself, but in the way models are used and created. There are three approaches that can dramatically improve this situation:

1. Standardisation
2. Open sourcing
3. Automation

## Standardisation

Another tweet, from an academic infection doctor in Bristol, gives a good insight on why standardisation can help:

> I'm sympathetic to his view that at a local level our models have not been good. E.g. our trust predictions in Bristol were miles off cases. We had estimates of 300/day at one point!
> https://twitter.com/gushamilton/status/1401430171647983616

If there was an 'official' set of models available to analyse and predict key metrics at local levels, this would ensure that all NHS Trusts have the option of looking at their area through the same lens. This would operate in the same way as the excellent Public Health England COVID dashboard, providing the same experience for all local areas, allowing comparison, and rolling up the predictions to a national level.

If the Trusts found the predictions difficult to consume or hard to interpret, they would be able to compare notes with colleagues from other trusts (who would be looking at the same outputs for their areas) and hopefully find ways to overcome these problems.

## Open sourcing

If the trusts were to find the models inaccurate, they could choose to continue developing their own. Developing a model isn't as simple as creating the model itself, it needs scaffolding: software or manual steps to load/transform the required input data and to create charts and reports.

If the official models were open sourced, then the surrounding scaffolding from that open sourced software would immediately give a significant start to any new modelling exercises. It is likely that all trust-level models will require case and test data, so why create your own software to load it from the PHE API?

Once the official models were open sourced, this would allow another option: for trusts to adapt the existing models to use different approaches or to add new input data sources. These could provide a lot of value to the wider community, and would lead to improvements to the official model.

Open sourcing allows both professional and spare-time developers and data scientists to use and examine the software, identifying small improvements and bug fixes that will again improve the official and local models over time.

## Automation

I expect that most COVID-19 models in the UK are run by hand - for each model there is a small number of expert users who need to do the analysis, either in a very manual fashion by copy and pasting data, or by starting an R script and sharing the outputs with colleagues. Automation removes this, allowing predictions to be (almost) as up to date as the data they operate on - if someone needs to look at the latest predictions on a Saturday evening, they don't need to phone someone to run the analysis for them.

Automating, open sourcing and standardising models will undoubtedly help at local levels, but also at national levels. The R number for a nation is typically estimated by a group of experts, such as [SAGE](https://www.gov.uk/government/organisations/scientific-advisory-group-for-emergencies) and the [NI expert modelling group](https://www.health-ni.gov.uk/r-number), running their own models and meeting in committee to agree a range for R. If this approach was also taken for R, I feel we would have higher quality, more accurate and more open estimates.

