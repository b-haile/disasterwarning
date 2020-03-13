# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Capstone Project: Using Social Media to Create Disaster Alerts
#### by Benjamin Haile

## Problem Statement

While traditional methods for alerting on events such as hurricanes and tornadoes rely on information derived from official sources (e.g. USGS), this project aims to utilize Twitter activity to identify such an event. In practice, once the event is predicted, an alert can then be sent out across social media. The outcome of this project will be a binary classification model that can analyze tweets and use them to predict whether a disaster is present and a warning must be sent. As a proof of concept, this project will use archived tweets collected during the most dangerous days of Hurricane Sandy in 2012. The project's terminology will center around that of hurricanes specifically. In this situation, predicting no emergency while a hurricane approaches (false negative) is a much more dangerous outcome than predicting a hurricane when there is none (false positive). Models will therefore be evaluated on recall as well as accuracy.


## Executive Summary

### Data Acquisition

I initially atttempted to use Twitter's API to collect live data. I also tried to use tweet IDs from archived datasets to obtain exact data on the location and datetime of each tweet. This only yielded a small amount of data, not enough to for prediciton. For the scope of this project, I needed a time-efficient solution. I decided to take CrisisLex's dataset of archived tweets during Hurricane Sandy and use them to predict the presence of a hurricane. CrisisLex is a repository of social media data on various crises and natural disasters. This dataset consists of tweets taken from late October 2012, posted by users in coastal New York and New Jersey, and based on 4 keywords: hurricane, hurricane sandy, frankenstorm, and #sandy. One columns lists tweets as "on-topic" or "off-topic", meaning their relevance or irrelevance to the subject of the hurricane. This column is the basis of my binary classification.

### Data Cleaning and EDA

In this dataset, duplicated rows in the "tweets" column would refer to retweets. These rows are dropped so that tweets are not counted more than once, which would give some predictive words too much weight, leading to potential bias in the model. The positive class is the presence of a hurricane, so I set "on-topic" to 1 and "off-topic" to 0. I vectorized the corpus of tweets, and observed the most common words across the entire corpus and between the two classes. Irrelevant words from the positive class were added to the list of stop words to ensure that it was distinct from the negative class. I then used a clustering model to view the overlap between the two classes.

### Modeling

I started with logistic regression models to see if a simpler model would suffice. Following that, I used random forest models to determine if more complexity would lead to more accurate predictions, but these models underperformed. I also experimented with two different methods of vectorizing the tweets. As I conducted EDA, I added words to the list of stop words and re-examined the four models with various versions of the list. This did not have a marked effect on the models' performance. I selected the logistic regression model with CountVectorizer for its accuracy and low variance compared to the random forest models. The recall score of this model is high, meaning that false negatives are kept to a minimum. The strongest feature coefficients of this model correspond with words that are highly relevant to a hurricane. This includes direct references to the event and also to safety precautions taken during a disaster.


## Dataset

[Tweets During Hurricane Sandy](https://crisislex.org/data-collections.html#CrisisLexT6)

Tweets were provided by Twitter's partner Topsy, or by Twitirs v3 with Twitter's partner GNIP. They were labeled by crowdsourcing workers to determine their relevance to the disaster.

A. Olteanu, C. Castillo, F. Diaz, S. Vieweg. 2014. CrisisLex: A Lexicon for Collecting and Filtering Microblogged Communications in Crises. In Proceedings of the AAAI Conference on Weblogs and Social Media (ICWSM'14). AAAI Press, Ann Arbor, MI, USA.

## Data Dictionary

|Feature|Type|Description|
|---|---|---|
|tweet id|int64|Coded ID associated with the tweet|
|tweet|object|Text of the tweet|
|label|object|Lists whether or not the tweet is relevant to the event|


## Conclusion and Next Steps
This model accurately predicts whether or not a hurricane is present. A positive prediction could be used as the catalyst to send a storm warning across social media. 

Moving forward, it may be useful to consider if a retweet could add to a word's use in the model, rather than bias. I would like to look at Twitter handles and hashtags to see if any should be followed for more precise knowledge of approaching storms. This model can be applied to various types of natural disaster. The tweets would simply need to be searched using different keywords. It is possible to use the Twitter API to collect live data, which would fulfill the ultimate goal of a realtime alert system. This system could also be set up to be on higher alert during certain season. The National Hurricane Center reports that the height of hurricane season is mid-August to late October. If predicting hurrianes, for example, this warning system could be programmed to pull data and predict hurricanes throughout the season.

## References

[Study on creating a crisis lexicon for Twitter emergency warnings](https://crisislex.org/papers/icwsm2014_crisislex.pdf)

[National Hurricane Center](https://www.nhc.noaa.gov/climo/)