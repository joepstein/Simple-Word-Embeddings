# Data Science Blog Scraping

## File Structure

- |- data-science-blog-word-embeddings-1.ipynb
- |- data-science-blog-word-embeddings-2.ipynb
- |- data-science-blog-word-embeddings-3.ipynb
- |- data-science-blog-word-embeddings-final.ipynb
- |- data-science-blog-word-embeddings-final.html

## Introduction
I wanted to share with people a very straightforward implementation of Word2Vec, to achieve not so straightforward insights. It's safe to say, there's an overwhelming amount of data in this world, and, even if there wasn't, data naturally multiplies with context and multiple perspectives.

## Project Overview
Let's use word embeddings (with Word2Vec) to create a model of the topic space through PCA and T-SNE. With word embeddings, we can take a look at topic clusters, and at a glance start to understand how people are using these words. For instance, the word "vector" could be in a cluster with "word" and "embedding" for someone in Data Science, but that same word used by a designer would probably be near "support" and "graphic" (SVG).

### Preparing the Text Data
Data comes in many forms, and not all sources provide data in the same way. For our text data, I limited the scope to blog websites related to Data Science, that had a "next page" button (in contrast to the more modern "load more" button). From here, I implemented some simple data cleaning rules, removing punctuation, removing stop words, and removing words less than 3 letters in length (in general this is fine to do, but not a perfect approach).

### Creating the Model
Here, we simply leverage Word2Vec. When the motivation is to take a glance at the topic space, it's appropriate not to go too wild with the model. Although, there are many other techniques out there, that are certainly worth trying out! Note: Word2Vec accepts an array of arrays, with each item in the sub array being a word... [['word1', 'word2', 'word3', ...], [<words>], [<words>], ...].

### Plotting the Model
I'd love to plot the model in the ideal embedding space (as though this data was entering a neural net), but, alas, humans can only have useful visualizations in 2 and 3 dimensions. The plotting function leverages either PCA or TSNE, depending on the parameters, and I believe for the purpose of visualization, both are equally useful. Lastly, I limit the plotting to the most frequently used words, though this does not mean those are the most important (consider long-tail keywords!). Other metrics are certainly very useful (like TF-IDF), but there had to be some sort of cutoff in order to have actionable insights.
