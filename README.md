# Exploring 12 years of tech news in an attempt to visualize our recent tech history.

We live in a very interesting time. Due to advances in technology, our world is constantly changing. For my final project at [Metis](https://www.thisismetis.com/), I wanted to visualize our recent tech history to spot existing trends and to, hopefully, identify emerging ones. 

I was also curious to see whether it would be possible to find any patterns in how varous technologies develop or understand why some technologies develop very fast while others seem to take their time.

To collect data, I scraped TechCrunch and Venturebeat, the two leading tech news outlets. To do that, I followed a methodology outlined in a blog post by [MonkeyLearn](https://monkeylearn.com/blog/filtering-startup-news-machine-learning/). The only adjustment I've made is I've added a field "Author" to the list of scraped by the spiders fields because I plan to use these data in one of my future projects.

Altogether, my data contain 260K+ articles and cover 12 years. 

My particular challenge with this project was to retrieve specific information, i.e. names of technologies, which may not necessarily be the most common words. What eventually worked was the following approach:  
  1. Applied LDA and NMF, two topic modeling algorithms, to the prepocessed texts selecting 10 top words to describe each topic and varying the number of topics from 5 to 10. The resulting table contains a list of 10-word documents, each of which desribes a topic. Altogether, the table contains 1,080 topics (45 topics created by each method multiplied by 2 methods multiplied by 12 years).
  2. Exctracted the most frequent words.
  3. Manually cleaned the resulting list of most frequent words to remove the ones that don't represent technologies such as companies' names and common words.
  4. Counted the relative number of times each word occured in topic descriptions and used the final numbers to build visualizations.

### Tools:
  * Scrapy, Python, Pandas - to collect, clean, and expplore the data
  * NLTK, Scikit-Learn, and TextBlob - to build a list of words that represent the technologies and calculate their relative usage
  * D3 and Dimple - to build visualizations

### Presentation and Slides
Here are my final [slides](https://github.com/elenabakhtina/evolution_of_technology/blob/master/presentation/ElenaBakhtina_TechEvolution_Final.pdf) and [the presentation (4:19)](https://youtu.be/nt4-IWo9noc) at the Metis Career Day.

### Visualizations
Here is a [lanscape of technologies](http://0.0.0.0:8000/BubbleChart_D3.html) that have been mentioned in the tech news in the last 12 years. Different colors show different years. 
Here is a [static visualization](https://github.com/elenabakhtina/evolution_of_technology/blob/master/visualization/TechnologyEvolution.png) that shows how various technologies have been developing over time with identified large trends: Games, Applications, Mobile, Data, Social, and Virtual Reality as an emerging trend.
And here is an [interactive map of our recent tech history](https://bl.ocks.org/elenabakhtina/raw/f6b16fe968b675caccf9b19280103e49/) as constructed by my analysis.  
For those who are curious, here is a [map of companies](http://bl.ocks.org/elenabakhtina/raw/ba311bce4785bac48cc97f9e20aed747/) that appeared newsworthy as considered by tech news sites.  
[test](http://bl.ocks.org/elenabakhtina/ba311bce4785bac48cc97f9e20aed747/)

### Additional Research
Another approach to textmining, in addition to topic modelng, is clustering. I wanted to compare how both approaches would work for my problem, namely, how the resulting list of technolgies would look when generated by the methods of topic modeling and by the methods of clustering. The resulting visualization is [here](http://0.0.0.0:8000/KMeansTechInnovations2_%20.html). In general, my conclusion was that topic modeling performed better, the resulting list turned out to be cleaner and more comprehensive. For clustering, I used nouns only in hope to identify technologies that might be missed by topic modeling that used the entire texts. It didn't happen. On the contrary, I lost some of the important trends such as "Mobile" and "Social". 
