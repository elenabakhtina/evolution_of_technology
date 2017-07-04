# Exploring the evolution of technologies over the last decade in an attempt to visualize our recent tech history

We live in a very interesting time. Due to advances in technology, our world is constantly changing. For my final project at Metis, I decided to visualize our recent tech history to spot existing trends and to, hopefully, identify emerging ones. 

I also was curious to see whether it would be possible to find any patterns in how varous technologies develop or understand why some technologies develop very fast while others seem to take their time.

To collect data, I scraped TechCrunch and Venturebeat, the two leading tech news outlets. To do that, I followed a methodology outlined in a blog post by [MonkeyLearn](https://monkeylearn.com/blog/filtering-startup-news-machine-learning/). The only adjustment I've made is I've added a field "Author" to the list of scraped by the spiders fields because I plan to use these data in one of my future projects.

Altogether, my data contain 260K+ articles and cover 12 years. 

My particular challenge with this project was to retrieve specific information, i.e. names of technologies, which may not necessarily be the most common words. What eventually worked was the following approach:  
  1. Applied LDA and NMF, two topic modeling algorithms, to the prepocessed texts selecting 10 top words to describe each topic and varying the number of topics from 5 to 10. The resulting table contains a list of 10-word documents, each of which desribes a topic. Altogether, the table contains 1,080 topics (45 topics created by each method multiplied by 2 methods multiplied by 12 years).
  2. Exctracted the most frequent words.
  3. Manually cleaned the resulting list of most frequent words to remove the ones that don't represent technologies such as companies' names and common words.
  4. Counted the relative number of times each word occured in topic descriptions and used the final numbers to build visualizations.

### Tools I used:
  * Scrapy, Python, Pandas - to collect, clean, and expplore the data
  * NLTK, Scikit-Learn, and TextBlob - to build a list of words that represent the technologies and calculate their relative usage
  * D3 and Dimple - to build visualizations

### Presentation and Slides
Here are my final [slides](https://github.com/elenabakhtina/evolution_of_technology/blob/master/presentation/ElenaBakhtina_TechEvolution_Final.pdf) and [the presentation (4:19)](https://youtu.be/nt4-IWo9noc) at the Metis Career Day.

### Visualizations
Here is a [lanscape of technologies](http://0.0.0.0:8000/BubbleChart_D3.html) that have been mentioned in the tech news. Different colors correspond to different years.
And here is how our recent [tech history](http://0.0.0.0:8000/TechInnovations2_.html) looks as shown by my analysis. 
