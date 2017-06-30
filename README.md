# Exploring the evolution of technologies over the last decade in an attempt to visualize our recent tech history

We live in a very interesting time. Due to advances in technology, our world is constantly changing. For my final project at Metis, I went on an adventure to visualize our recent tech history to spot existing trends and to, hopefully, identify emerging ones. 
I also was curious to see whether I would be able to find any patterns in how varous technologies develop and to answer the questions on why some technologies develop rapidly while others take their time.

To collect data, I scaped TechCrunch and Venturebeat, the two leading tech news outlets. At that, I followed a mothodology outlined in a blog post by [MonkeyLearn](https://monkeylearn.com/blog/filtering-startup-news-machine-learning/). The only adjustment I've made is I've added a field "Author" to the list of fields being scraped by the spiders because I plan to use this information in one of my future project.

Altogether, my data contain 260K+ articles and cover 12 years. 

My particular challenge with this project was to extract the names of specific technologies that may not necessarily be the most common words. What eventually worked was the following approach to information retrieval:
  1. Simplified the original articles to leave only nouns;
  2. Applied LDA and NMF, two topic modeling algorithms, to the noun-only texts varying the number of topics from 5 to 10. The resulting table contained 10-word lines where each line desribed a topic. Altogether, there were 1,080 lines (45 topics multiplied by 2 methods multiplied by 12 years).
  3. Exctracted the most common words from the above table of topic description.
  4. Manually cleaned the resulting list from words that don't represent technologies such as companies' names and common words.
  5. Counted the relative number of times each word occured to use it in visualizations.

### Tools I used:
  * Scrapy, Python, Pandas - to collect, clean, and expplore the data
  * NLTK, Scikit-Learn, and TextBlob - to build a list of words that represent the technologies and their relative amount of usage
  * D3 and Dimple - to build visualizations

### Presentation and Slides
Here are my final slides and presentation (sorry for the bottle of beer in the middle of the screen. It was not planned :))

### Visualizations
Here is a lanscape of technologies that have been mentioned in the tech news.
Here is how our recent tech history looks like. 
