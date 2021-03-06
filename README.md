# Exploring 12 years of tech news in an attempt to visualize our recent tech history.

We live in a very interesting time. Due to advances in technology, our world is constantly changing. For my final project at [Metis](https://www.thisismetis.com/), a 12-week full-time Data Science Bootcamp, I decided to visualize our recent tech history in an attempt to spot existing and emerging trends. 

I was also curious to see whether it would be possible to find any patterns in how varous technologies develop or understand why some technologies develop very fast while others seem to take their time.

To collect data, I scraped TechCrunch and Venturebeat, the two leading tech news outlets. At that, I followed a methodology outlined in a blog post by [MonkeyLearn](https://monkeylearn.com/blog/filtering-startup-news-machine-learning/) with some adjustments to adreess my specific needs.

Altogether, my data contain 260K+ articles and cover 12 years. 

My particular challenge with this project was to retrieve a particular information, specifically names of technologies, which may not necessarily be the most common words. What eventually worked was the following approach:  
  1. Applying LDA and NMF, two topic modeling algorithms, to the prepocessed texts selecting 10 top words to describe each topic and varying the number of topics from 5 to 10. The resulting table contains a list of 10-word documents, each of which desribes a topic. Altogether, the table contains 1,080 topics (45 topics created by each method multiplied by 2 methods multiplied by 12 years).
  2. Creating a list of the most frequent words from the topic descriptions.
  3. Manually cleaning the resulting list to remove words that don't represent technologies such as companies' names and common words.
  4. Counting a relative number of times each word occured among topic descriptions and using the final numbers to build visualizations.

### Tools:
  * Scrapy, Python, Pandas - to collect, clean, and expplore the data
  * NLTK, Scikit-Learn, and TextBlob - to build a list of words that represent the technologies and calculate their relative usage
  * D3 and Dimple - to build visualizations

### Presentation and Slides
Here are my final [slides](https://github.com/elenabakhtina/evolution_of_technology/blob/master/presentation/ElenaBakhtina_TechEvolution_Final.pdf) and [the presentation (4:19)](https://youtu.be/nt4-IWo9noc) at the Metis Career Day.

### Visualizations
Here is a [lanscape of technologies](https://bl.ocks.org/elenabakhtina/raw/7259f2aeda689b9887a741eebfddcfff/) that have been mentioned in the tech news in the last 12 years. Different colors show different years. 
Here is a [static visualization](https://github.com/elenabakhtina/evolution_of_technology/blob/master/visualization/TechnologyEvolution.png) that shows how various technologies have been developing over the time with identified large trends: Games, Applications, Mobile, Data, Social, and Virtual Reality as an emerging trend.
And here is an [interactive map of our recent tech history](http://bl.ocks.org/elenabakhtina/raw/f6b16fe968b675caccf9b19280103e49/) as constructed by my analysis.  
For those who are curious, here is a [map of companies](http://bl.ocks.org/elenabakhtina/raw/ba311bce4785bac48cc97f9e20aed747/) that considered newsworthy in the last 12 years by tech news sites.

### Interesting observation
As it can be observed on my tech history map, some technologies, for example "Mobile", appear to be slow burns, they start rather small and are slow to grow. Some other technologies, on the other hand, seem to break into our life in a big and sudden way as if being fully developed. “Driverless cars” ("car" on the map) and “Virtual Reality” ("vr" on the map) are good illustrations. 
The reason for that is that technologies, of course, don’t arrive out of nowhere, they evolve from existing technologies. If all the components are already in presence by the time a new technology has arriveed than this tech newcomer is bursting into growth. It's what is happening right now with driverless cars. But, if an infrastructure that would otherwise support a new tech innovation is not here, than the innovation is restrained in its development. That was the case with mobile technologies that heavily depended on hardware that was not here yet in 2006.

### Additional Research
Another approach to textmining, in addition to topic modelng, is clustering. I wanted to compare how both approaches would work for my problem, namely, how the resulting list of technolgies would look when generated by the methods of topic modeling and by the methods of clustering. The resulting visualization of technolgoes generated by clustering (KMeans) is [here](http://bl.ocks.org/elenabakhtina/raw/71f2b7912b2156580bf1141ea984e999/). In general, my conclusion was that topic modeling performed better, its resulting list turned out to be cleaner and more comprehensive. Additionally, for clustering, I used only nouns in hope to perform more granular analysis on them and identify technologies that might be missed by topic modeling that used the entire texts. It didn't happen. On the contrary, I lost some of the important trends such as "Mobile" and "Social". 
