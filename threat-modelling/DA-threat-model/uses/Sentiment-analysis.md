# Sentiment analysis

Sentiment analysis is a technique to analyse opinions, sentiments, appraisals, and emotions and can for example, predict presidential election results by collecting and converting social media data and analysing the converted data.

## Methods
Sentiment analysis uses NLP, statistics, or machine learning methods to extract, identify, or characterise the sentiment content of a text. It can be used to determine associated emotions with a keyword or to predict emotions, for information extraction (discarding subjective information), question answering (and recognising opinion-oriented questions), summarization (accounting for multiple viewpoints), “flame” detection, identifying the suitability of videos for children based on comments, identification of bias in news sources and of (in)appropriate content of a text for a particular context. It has found application in politics/political science, law/policy making, sociology and psychology.

Common examples of questions asked are “how are people responding to this campaign/release/news item?” or “How have bloggers' attitudes about the president changed since the election?”. With content analysis tools, unstructured text from social media posts like Tweets and Facebook posts can be analysed to determine the macro level user sentiment related to a particular keyword.

## Example: Constructing political profiles

### Data collection and conversion

People discus and express their opinion by commenting, posting or sharing status (or tweets). Such social media status expressions can be collected according to the most frequently used keywords that contain for example, words related to election, parties and candidates. It involves content disclosure, and in some cases also link disclosure. Then the data set is cleaned up. For example, status expressions containing insults are removed. Status expressions written in different languages can either be handled manually, or by tools that have the needed language (machine learning) components.
Classification and evaluation

After this preprocessing, a text is classified by machine learning, by a lexicon, or by a hybrid of the two, and then evaluated. In its most simple form, classification is done using two steps: training and prediction. The classifier will use the training data to learn to make predictions. The better the dataset, the better the accuracy of the classifier.

Sentiment classification can be a positive/negative/neutral (where the neutral class is not a state between positive and negative but a separate class that denotes lack of sentiment) or a multi-class problem.

* Python offers several packages for natural language processing. Simple examples of sentiment analysis in python can be found here. In real life, the algorithms are more complex.
* With the opinionFinder tool it is easy to extract automatically subjective sentences and sentiment expressions. Based on SentiStrength which estimates the strength of positive and negative sentiment in texts and emoticons in various languages, words are classified into categories.
* Evaluation metrics like Precision, Recall, F-score, and Accuracy can be used. The end results are visualised through graphs, histograms, and confusion matrices.

This sentiment analysis can then be used as a base for targeted voter profiles. Conclusions can now be drawn for example, whether a given voter is with or against a particular party or candidate.

### Applications of sentiment analysis

* Sociological: Diffusion of innovations is a theory that seeks to explain how, why, and at what rate new ideas and technology spread. Opinions and reactions to ideas are relevant to adoption of new ideas. Analysing sentiment reactions on blogs can give insights into this process.
* Psychological: Sentiment analysis has the potential to augment psychological investigations/experiments with data extracted from natural language text.
* Political: In politics, sentiment analysis has found numerous applications and possibilities: for analysing trends, identifying ideological bias, targeting messages, gauging reactions, evaluation of public/voters' opinions and views/discussions of policy. And is used by some data brokers, to serve politicians. The Cambridge Analytica case being an example.

### Identifying political preferences and tendencies

Political preferences and tendency of the population can be assessed using classification and opinion mining (read sentiment analysis) techniques. Both patterns affected by socio-economic variables and voter sentiment analysis can be used. Some known strategies and patterns that have been studied are:

* Organisational affiliation strategies
* Electoral affiliation strategies
* Patterns of party systems transformation
* Organisational affiliation patterns of politicians
* Electoral affiliation patterns of voters

Those are the usual suspects, but other things in relation to elections have been studied as well.

For example, Akarca and Tansel studied voter behaviour in Turkey in 2007 and found that Turkish voters took economic performances into account and exhibited a tendency to vote against parties holding power. Voters distinguished between major and minor parties and held parties in power accountable for economic growth (or losses). Surprisingly, only the growth rate of the year preceding the election affected its outcome.

In 2010 Henderson and McEwen conducted a comparative analysis of voter turnout in regional elections in nine states between 2003 and 2006. According to that research, variations in strength of political autonomy and strength of attachment to the region among the electorate have a strong and positive impact on the level of turnout in regional elections. Their hypothesis of voter turnout in regional election being higher in regions with a high degree of regional distinctiveness was considered proven.

### Notes on sentiment analysis

* Humans are subjective creatures and opinions are important. Being able to interact with people on that level has many advantages for information systems.
* Sentiment analysis uses comparatively few categories compared to text categorisation.
* It crosses domains, topics, and users.
* The categories are not independent.
* Characteristics of answers to opinion-based questions are different from fact-based questions.
* In opinion texts, lexical content alone can be misleading.
* People express opinions in complex ways: rhetorical devices/modes such as sarcasm, irony, implication, intra-textual and sub-sentential reversals, negation, and topic changes can be a challenge for sentiment analysis.


