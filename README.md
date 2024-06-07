# Sentiment Analysis of Tweets using LSTM (Long Short-Term Memory)

## Project Introduction

Twitter produces a huge amount of data from its users globally among which portion of it 
is feedback or re-tweet. As such, there is a need to automate the process of identifying sentiments 
on these tweets to benefit the users of the platform. Consequently, this project attempts to 
produce a model that can identify a sentiment of a tweet. The objective of this project is to explore 
the Natural Language Processing (NLP) landscape through the eye of text mining by producing a model that
can automate the categorization of sentences as positive, negative, or neutral sentiments. 

To answer the problem statement tweet data is required. For this, the project utilizes
Twitter API (Application Program Interface) for obtaining the tweets. Once the data is acquired, 
Python libraries will be used for prepossessing, model building, testing, and evaluating. 
This project uses Pandas, Sklearn, Tweepy, Natural Language ToolKit (NLTK), and 
Keras python libraries. The reason behind using different libraries is the fact that some libraries 
have good functions over others on specific tasks, for example, tokenization, stemming, etc. In 
addition, some of these libraries have functions for producing charts and diagrams that ease the 
text mining process. Some other libraries also provide model accuracy measurements, like 
precision, recall, f1-measure that can easily be used to determine the efficiency of the produced 
model. Also, other libraries contain functions to extract tweets, such as the ‘Tweepy’ library, 
from Twitter API directly.

## Data Acquisition
A data set is obtained from Kaggle - Sentiment140 data set. This data set contains approximately 1,600,000 tweets 
extracted from Twitter using the Twitter API and are labeled into 2 categories - positive and negative. But since 
this project also involves identifying neutral sentiments over tweets, another data set is also 
acquired from Kaggle that contains labeled tweets in those three categories. Then the data sets are 
merged and taken with a sample size of approximately 40,000 classified tweets to train the 
model. This helps to balance the training data across the 3 categories and limit the computation 
resource and time needed to produce a model. Figure 1 shows a sample of extracted data from the 
data set.
Next, for extracting live tweets for testing, I created a developer account on 
Twitter. This account allows developers to access recent tweet data. For this, Python’s ‘Tweepy’ 
library is used as it can directly connect to Twitter API to fetch data

## Data Cleaning and Pre-Processing
The data is already cleaned for duplicates and missing values. In addition, all the entries contain either 
of the sentiment class labels, i.e., positive, negative, orneutral. Besides, there are no concerns regarding 
data sensitivity and security as it is a publicly available data set. Figure 2 shows the distribution of the training data 
set in the 3 class labels. The data contains tweet texts in their original format. Hence, for the machine learning 
models to understand them, these texts need to be converted into numerical sequences. As such, a sanity check i.e., dropping 
any rows that have missing or null values is performed first. Yet, this yielded no result as the data was clean.

Once the data is confirmed to be cleaned, the text data is passed through a conversion function that applies a series of 
conversions in an order. First, the function converts an entire text to a lowercase. After that, it removes 
usernames, hyperlinks, and non-letters from the texts and tokenizes. Next, the function removes stop words from the texts. 
Stop words are words that occur frequently and do not contribute to the overall content of the text. These words are usually 
auxiliary verbs, conjunctions, articles and words that occur periodically. As a result, this project used stop word lists 
provided by the NLTK (Natural Language Tool Kit) library.

Then, a stemming algorithm is applied to shorten a given word into its root form. For the stemming of words, a Porter’s stemmer 
algorithm is used. Porter stemmer is the most popular stemming technique for the English language and contains a series of rules 
that are applied to a word. Lastly, a tokenizer padding function is applied to the data set to level up the separated individualized 
words into the same word length. This is done through Keras library’s Tokenizer class which produces machine understandable numeric results.
The function produces a sequence of integers associated with the text in which empty values are padded by 0 values to level up missing columns 
at the end. This project selected a maximum length of 50 as a column size as most tweets do not go beyond this threshold value.

## Data Modelling
For performing sentiment analysis, tweets are needed to be classified as either positive, neutral, or negative. Hence, a classification
model with an acceptable accuracy rate is needed. There are plenty of algorithms available that can be used to produce classification models. The 
model that this project selected is a type of Recurrent Neural Network (RNN) called Long Short Term Memory (LSTM). An RNN is a supervised deep learning 
algorithm that is an extension of ANN. These networks re–member the previous neuron’s information and hence they can remember what information was passed 
to themselves in the past which can be used for further analysis. In other words, if there was some information at a specific time say T1, it is used as 
an input for the next time instance T2.

Despite its advantage, however, RNN suffers from the problem called the Vanishing Gradient problem, where if the sequence of input data is too long, 
it makes it difficult to propagate data from one specific time instance to the next. That is where its variant LSTM becomes useful. LSTM is a version 
of RNN that comes into the picture for tackling the vanishing problem. LSTM has a memory cell for efficiently carrying data from one time instance to another
The model this project implements is a bidirectional LSTM which allows neurons to share data both ways. However, there are a few drawbacks to this model as well. 
As already mentioned above, LSTM has an additional memory component and takes up more time to train the model compared to other classification models.

## Data Analysis
Present the analysis performed on the data. This might include statistical analysis, exploratory data analysis (EDA), and other techniques used to extract insights from the data.

## Visualizing Outcomes
Detail the visualizations created to represent the outcomes of your analysis. Include examples of key charts, graphs, or other visual representations that highlight the results.
