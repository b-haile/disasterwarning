# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Capstone Project: Using Social Media to Create Disaster Alerts
#### by Benjamin Haile

## Problem Statement

While traditional methods for alerting on events such as hurricanes and tornadoes rely on information derived from official sources (e.g. USGS), this project aims to utilize Twitter activity to identify such an event. In practice, once the event is predicted, an alert can then be sent out across social media. The outcome of this project will be a binary classification model that can analyze tweets and use them to predict whether a disaster is present and a warning must be sent. As a proof of concept, this project will use archived tweets collected during the most dangerous days of Hurricane Sandy in 2012. The project's terminology will center around that of hurricanes specifically. In this situation, predicting no emergency while a hurricane approaches (false negative) is a much more dangerous outcome than predicting a hurricane when there is none (false positive). Models will therefore be evaluated on recall as well as accuracy.


## Executive Summary

### Data Acquisition

I initially atttempted to use Twitter's API to collect live data. 


## Datasets

The data has been pulled from the relevant subreddits using the Pushshift API.

[Tweets During Hurricane Sandy](https://crisislex.org/data-collections.html#CrisisLexT6)

Contents: ~60K tweets posted during 6 crisis events in 2012 and 2013.
Sampling method: ~10 million tweets in total sampled by keywords and geographical regions or coordinates. Tweets were provided by Twitter's partner Topsy (4 geo-based), or as lists of tweet ids by Twitris v3 (5 keyword-based datasets, thanks to Hemant Purohit) and Twitter's partner GNIP (1 keyword-based, 2 geo-based, thanks to Aron Culotta) .
Labels: ~60,000 tweets (10,000 in each collection) were labeled by crowdsourcing workers according to relatedness (as "on-topic", or "off-topic").
Data format: comma-separated values (.csv) files containing the text of the tweets and labels for the labeled ones.

2012 Sandy Hurricane	2012-10-28 / 3 days	4: hurricane, hurricane sandy, frankenstorm, #sandy	2,775,812	NY City; Bergen, Ocean, Union, Atlantic, Essex, Cape May, Hudson, Middlesex; Monmouth County, NJ, US	279,454

A. Olteanu, C. Castillo, F. Diaz, S. Vieweg. 2014. CrisisLex: A Lexicon for Collecting and Filtering Microblogged Communications in Crises. In Proceedings of the AAAI Conference on Weblogs and Social Media (ICWSM'14). AAAI Press, Ann Arbor, MI, USA.

### Data Dictionary

|Feature|Type|Description|
|---|---|---|---|
|title|object|The title of the subreddit post|
|subreddit|int|0: Rooster Teeth, 1: Castle Super Beast|

## Conclusion
Maybe weight the RTs? Consider @s and hashtags.

## References

[Study on creating a crisis lexicon for Twitter emergency warnings](https://crisislex.org/papers/icwsm2014_crisislex.pdf)