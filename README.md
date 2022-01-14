<p align='center'>
  <img width="600" src='https://github.com/jenningst/olympic-tweet-sentiment-analysis/blob/main/images/shinnosuke-ando-VUsicdRLMFQ-unsplash.jpg' alt='Olympic Logo'>
</p>
<p align='center'>
  Photo by <a href="https://unsplash.com/@andy4822?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Shinnosuke Ando</a> on <a href="https://unsplash.com/s/photos/olympics?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
</p>

# Olympic Tweet Sentiment Analysis

Every four years (five years sometimes) something special happens. No, it is not the world’s greatest athletes coming together to showcase elite human athleticism in the Summer Olympics. Rather, it is the millions of people that come together to tweet about these athletes. In a showcase of exceptional human thumbs, these people tell you all you need to know about the Olympics; with 100% accuracy of course.

So what does the twitter-sphere have to say about the Olympics? Are there sports that are being talked about in a better light than others? How does the sentiment of the Olympics change over the course of the event? In this project, we will be investigating tweet sentiment involving Olympic sports to see how they evolve. In the end, the sentiment of specific sports will be analyzed and any trends should be discovered.

## Motivation

A particular interest of the authors is the ongoing Summer Olympic games. We enjoy watching the top athletes in the world compete in sports that are not on television very often; sports like gymnastics, swimming, and track. A natural curiosity was to see how other people view the Olympics.

As social media has grown Twitter has been the go-to platform for the world to express their views. Twitter allows people to express their feelings on just about any subject they desire (for better or for worst). It would make sense then to look at Twitter data to model the sentiment around the Olympics. Luckily, Twitter provides an API for us to query historical tweet data.

## Method and Results 

To provide sentiment analysis for tweet data, we utilize two packages: (1) TextBlob and (2) VADER from the NLTK toolkit. TextBlob provides a simple interface for processing text-based data and allows for the calculation of the subjectivity and polarity for a given text, which will aid in sentiment analysis using a set of additional text features. The VADER model is a pre-trained model that uses rule-based values which are especially attuned to sentiments from social media, making it a great choice for overall sentiment analysis.

From the output of TextBlob, we generate two additional features for use in our analysis:
- Polarity: a measure ([-1, 1]) of the sentiment of a text; higher polarity means the text contains more positive sentiment.
- Subjectivity: a measure ([0, 1]) of the opinion and factual information contained in a text; higher subjectivity means the text contains more personal opinion.

From the output of VADER, we generate three additional features for use in our analysis:
- Neg, Neu, and Pos are scores for the ratios for proportions of text that fall into a negative, neutral, and positive sentiment.
- Compound: a score computed by summing the valence scores of each word in the VADER lexicon and normalized to create a composite sentiment score.
- Sentiment: a categorical column that standardizes/generalizes the compound score into positive, neutral, and negative sentiment values.

With all of our tweets scored for sentiment and polarity, we can get an idea of the popular sports in the Olympics. A simple bar chart goes a along way in drawing our conclusions.

<p align='center'>
  <img width='600' src='https://github.com/jenningst/olympic-tweet-sentiment-analysis/blob/main/plots/barplot-sentiment-by-sport.png'>
</p>

We can also compare sentiment as well as the score differences betweet Vader and Textblob by a scatter plot. If Vader and Textblob agree completely we should get a diagonal line from the lower left to the upper right of each scatter plot.

<p align='center'>
  <img width='800' src='https://github.com/jenningst/olympic-tweet-sentiment-analysis/blob/main/plots/scatterplot-sentiment-by-sport.png'>
</p>

It appears that all of the sports were talked about in mostly a positive light. The traditional Summer Olympic sports of gymnastics and track were overwhelmingly positive with about 70% of their tweets interpreted as positive. Of the two new sports, skateboarding and surfing, both had slightly positive reactions. Interestingly, out of all of the sports investigated, surfing was talked about least negatively. Biking was the most indifferent sport with just over 40% of tweets interpreted as neutral tweets.

There does seem to be general agreement between TextBlob and Vader, although it is far from perfect. Both classified more tweets as positive than either neutral or negative. Most points are in the upper right quandrant of their respective scatter plots. This goes back to the two methods generally agreeing. It is clear that not as many tweets for skateboarding or surfing were collected. There were some tweets that the methods completly disagreed on (one said strongly positive and the other said strongly negative). Looking at the two methods combined it would appear that basketball, track, and volleyball had the most positive tweets. Biking and diving look as if they have the most neutral tweets.

The fact that most sports were talked about positively was not surprising to us. When the Olympics are on there is generally a positive feel around them. We believe this to be for a few reasons; they are not every year, other thnn basketball the sports are more niche and not considered to be American major sports, the country vs. country format actually helps breed comradery. We were surprised about the small sample size we were able to collect regarding the two newer sports. While skateboarding and surfing did not seem like they were on mush we anticipated a lot more tweets regarding them.

## Future Work
- Exploration and comparison between originating tweet sentiment and tweet reply sentiment to analyze differences
- Time-series analysis of sentiment over time for given sport(s)

## Project Members

- Cory Vorsanger
- Carl Ausmees
- Troy Jennings (https://github.com/jenningst)
