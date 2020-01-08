# Can Data Science help us find what makes a hit television show? 

![sitcoms](images/sitcoms.png)

This content is from the talk I gave at the Data Science Salon conference in Las Vegas on 11/07/2019.
[![Watch the video](https://www.youtube.com/watch?time_continue=519&v=SKviFcvDibA&feature=emb_logo)

<!--[![Watch the video](https://img.youtube.com/vi/T-D1KVIuvjA/maxresdefault.jpg)](https://www.youtube.com/watch?time_continue=519&v=SKviFcvDibA&feature=emb_logo)>

## What constitutes a hit television show like few of these? 
### Questions I asked and investigated through Data Science.

* Is it the consistency in the way individual Characters speak and behave?
* Is it the repeat shots at locations thereby making your audience feel like they know the place over time?
* Is it the similarity/difference in the way different Characters speak and behave?
* Is it the balanced distribution of emotions like joy, sadness, fear, anger, disgust etc. which makes a show interesting?
* Is it the similar/different personality of Characters that keeps the audience connected?
* Is it the interesting flashbacks which binds the audience? 

## Data Availability

* Are datasets available to do this analysis? No

What I got after extensively searching the internet, was the html transcripts from the following URLs.

* Friends - https://fangj.github.io/friends/ - 10 seasons
* The Big Bang Theory – https://bigbangtrans.wordpress.com/ - 10/12 seasons
* Breaking Bad - https://en.wikiquote.org/wiki/Breaking_Bad – 5 seasons (with missing data)

Following is a sample of what these transcripts look like.

![dataset_sample](images/dataset_sample.png)

Following is a brief illustration of how I prepared dataset for modeling from raw html transcripts.

![dataset_sample](images/data_prep_steps.png)

After I run the above steps, I get my dataset for each sitcom ready to be used for modeling. It took some significant effort on my part to generate these datasets. So, I uploaded them on Kaggle so that they can be used by the interested parties.

![dataset_sample](images/friends_dataset_kaggle.png)
https://www.kaggle.com/shilpibhattacharyya/friends-sitcom-dataset

![dataset_sample](images/big_bang_theory_dataset_kaggle.png)
https://www.kaggle.com/shilpibhattacharyya/the-big-bang-theory-dataset

![dataset_sample](images/breaking_bad_dataset_kaggle.png)
https://www.kaggle.com/shilpibhattacharyya/breaking-bad-sitcom-dataset

I am using **Watson Natural Language Understanding (NLU)** for emotion detection of the characters. Natural Language Understanding is a collection of APIs that offer text analysis through natural language processing. This set of APIs can analyze text to help you understand its concepts, entities, keywords, sentiment, and more. 

![nlu](images/nlu.png) 

## Emotion distribution of the Characters on F.R.I.E.N.D.S.
![nlu](images/emo_friends.png) 
## Emotion distribution of the Characters on The Big Bang Theory
![nlu](images/emo_bigbang.png) 
## Emotion distribution of the Characters on Breaking Bad
![nlu](images/emo_breakingbad.png) 

I have introduced a variable 'emotion qotient' to understand which emotion is most prominent with respect to other emotions on the show. I have defined it as follows:

```
Individual_Emotion_Quotient = Individual_Emotion_Score/Total_Emotion_Score
```

Following are the scattered plot results.
## Emotion Quotient of the Characters on F.R.I.E.N.D.S. 
![nlu](images/emo_quotient_friends.png)
```Happiness and Sadness are the key emotions of the Characters```

## Emotion Quotient of the Characters on The Big Bang Theory
![nlu](images/emo_quotient_bigbang.png)
```Happiness is most dominant emotion of the Characters in the show```

## Emotion Quotient of the Characters on Breaking Bad
![nlu](images/emo_quotient_breakingbad.png)
```Sadness and Anger are the key emotions of the Characters```

## Sentiment Density of Characters on F.R.I.E.N.D.S.
![nlu](images/sentiment_density_friends.png)
```All the Characters are biased towards joy and sadness```

## Sentiment Density of Characters on The Big Bang Theory
![nlu](images/sentiment_density_bigbang.png)
```All the Characters are biased towards sadness```

## Sentiment Density of Characters on Breaking Bad
![nlu](images/sentiment_density_breakingbad.png)
```All the Characters are biased towards sadness and anger```

I am using **Watson Personality Insights** to investigate the personality of each of the lead characters on the show.
![wpi](images/WPI.png)
We would go for the big 5 traits from WPI defined as below here.

1. **Agreeableness**  compassionate and cooperative toward others.
2. **Conscientiousness**  act in an organized or thoughtful way.
3. **Extraversion**  seek stimulation in the company of others.
4. **Emotional range**  the extent to which a person's emotions are sensitive to the person's environment.
5. **Openness** the extent to which a person is open to experiencing different activities.

The IBM Watson Personality Insights service uses linguistic analytics to extract a spectrum of cognitive and social characteristics from the text data that a person generates through blogs, tweets, forum posts, and more. Watson found Trump "boisterous."

## Personality Insights for the Characters on F.R.I.E.N.D.S.
![nlu](images/personality_friends.png)
The personalities of all the characters on the show are similar
## Personality Insights for the Characters on The Big Bang Theory
![nlu](images/personality_bigbang.png)
The personalities of all the characters on the show are nearly similar
## Personality Insights for the Characters on Breaking Bad
![nlu](images/personality_breakingbad.png)
The personalities of all the characters are not quite similar

## Personality Density of the Characters on F.R.I.E.N.D.S.
![nlu](images/personality_density_friends.png)
The personalities of all the characters have a similar distribution of attributes
## Personality Density of the Characters on The Big Bang Theory
![nlu](images/personality_density_bigbang.png)
The personalities of all the characters have a similar distribution of attributes
## Personality of the Characters on Breaking Bad
![nlu](images/personality_density_breakingbad.png)
The personalities of all the characters have a similar distribution of attributes

## What are the top 5 locations F.R.I.E.N.D.S. was shot?
![nlu](images/loc_friends.png)
The show did not have much variation in the places it happened. That succeeded in binding its audience to to the show.
## What are the top 5 locations The Big Bang Theory was shot?
![nlu](images/loc_bigbang.png)
The show did not have much variation in the places it happened. That succeeded in binding its audience to to the show.
## What are the top 5 locations The Breaking Bad was shot?
I did not have data for the Breaking Bad to plot the top 5 locations at this time.

Now to find out how different are each charcaters from each other, I am using a LSTM model on the dataset consisting of all the dialogues from every cahracter on the shows.

## Can we distinguish the lead Characters on F.R.I.E.N.D.S. from each other (LSTM model)?
![nlu](images/lstm_friends.png)
The Characters are quite different and identifiable from each other

## Can we distinguish the lead Characters on F.R.I.E.N.D.S. from each other (LSTM model)?
![nlu](images/lstm_bigbang.png)
The Characters are quite similar and non-identifiable from each other except Sheldon

## Can we distinguish the lead Characters on F.R.I.E.N.D.S. from each other (LSTM model)?
![nlu](images/lstm_breakingbad.png)
The Characters are quite similar and non-identifiable from each other except Walter

## Do the Characters on F.R.I.E.N.D.S. maintain consistency in the way they communicate?
![nlu](images/consistency_friends.png)
Yup! They mostly do

## Do the Characters on The Big Bang Theory maintain consistency in the way they communicate?
![nlu](images/consistency_bigbang.png)

Yup! They do

## Do the Characters on Breaking Bad maintain consistency in the way they communicate?
![nlu](images/consistency_breakingbad.png)

Mostly,  they do. Walter shows inconsistency because of his other Character - Heisenberg

## Do we have the answer to what makes a sitcom popular?

* Is it the consistency in the way individual Characters speak and behave?
We can infer this, as all the three popular shows reflects this in their analysis.

* Is it the repeat shots at locations thereby making your audience feel like they know the place?
Yes, both the shows ‘F.R.I.E.N.D.S.’ and ‘The Big Bang Theory’ confirm to this.  Unfortunately, I could not find location data for ‘Breaking Bad’.

* Is it the similarity/difference in the way different Characters speak and behave?
A.   They can be quite similar, as well as different. We did not get a solid evidence here on this from the confusion matrix we observed for the three shows.

* Is it the balanced distribution of emotions like joy, sadness, fear, anger, disgust which makes a show interesting?
A.  Yes, the results from Watson NLU on the input from three shows confirm this.

* Is it the similar/different personality of Characters that keeps the audience connected?
The results reveal that it’s obviously the similarity in personality which wins here.

* Is it the interesting flashbacks which binds the audience? 
A.   Unfortunately, the ‘flashback’ word does not appear in transcripts, so could not analyze this.

## A word to the show makers from this analysis

* If you are fortunate to have a show running long, try to establish consistency in the speech and behavior of individual Characters over the episodes.

* There should be minimal variance in the set of shooting locations. This would instill a sense of belonging to the environment and culture of the sitcom in the audience.

* The personality of the Characters on the sitcom should be similar and blend together, as the Personality Insights results highlight.

* The distribution of emotions are  leaning towards a particular emotion. F.R.I.E.N.D.S. is a show of primarily joy and sadness; The Big Bang Theory is leaning towards joy and sadness as well. Breaking Bad is a show mostly made of anger and sadness. The takeaway is keep the emotion quotient of the show coherent over a period of time.

* The Characters can be different or similar to each other as long as the above criteria are met. 

## Comparing the number of dialogues spoken by the lead Characters

![nlu](images/dialogues.png)

## Most Popular Characters
![nlu](images/pop_chars.png)



















