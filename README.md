# Exploring the evolution of technologies over the last decade in an attempt to visualize our recent tech history

We live in a very interesting time. Due to advances in technology, our world is constantly changing. For my final project at Metis, I went on an adventure to visualize our recent tech history to spot existing trends and to, hopefully, identify emerging ones. 
I also was curious to see whether I would be able to find any patterns in how varous technologies develop and to answer the questions on why some technologies develop rapidly while others take their time.

To collect data, I scaped TechCrunch and Venturebeat, the two leading tech news outlets. At that, I followed a mothodology outlined in a blog post by [MonkeyLearn](https://monkeylearn.com/blog/filtering-startup-news-machine-learning/). The only adjustment I've made is I've added a field "Author" to the list of fields being scraped by the spiders because I plan to use this information in one of my future project.

Altogether, my data contain 260K+ articles and cover 12 years. 

My particular challenge with this project was to extract the names of specific technologies that may not necessarily be the most common words. What eventually worked was the following combination of data-mining:
  1. Strip the original articles from all words but nouns
  2. Apply LDA and NMF, the two topic modeling algorithms, to the noun-only texts with number of topics ranging from 5 to 10. The result is a table with 10-word lines, each of which desribes a topic. Altogether, there are 1,080 lines.
  3. Exctract the most common words from this table of topic description.
  4. Clean the resulting list from words that don't represent technologies such as companies' names and common words.
  5. Count the relative number of times each word occurs.

### Tools I used:
  * Scrapy, Python, Pandas - to collect, clean, and expplore the data
  * NLTK, Scikit-Learn, and TextBlob - to build a list of words that represent the technologies and their relative amount of usage
  * D3 and Dimple - to build visualizations

