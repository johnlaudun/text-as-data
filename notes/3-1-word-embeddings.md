# 3-1 Word Embeddings

### What We’ve Already Done

- tokenized
- filtered stop words
- counted words
- examined words co-occurrence
- created a corpus
- built custom stop word lists
- explored topic modeling (and k-means clustering)

### What We Are Going to Do Today

- concordance to understand similarity
- part-of-speech tagging
- chunking
- 

### Words in Context

So far we have approached text analytics as a matter of comparing one text to another, where every text is represented by a (usually weighted) collection of the words which make it up. Since we often take those weightings and place them in a matrix, we have tended to call the collections vectors, with our texts then being represented by n-dimensional vectors. (Typically those vectors have been in the thousands.)[^1]

One byproduct of this is that words are assumed to have distinct meanings so that if one text has a river in it and another a bayou, the texts are not related. (Chances are that texts that discuss rivers and bayous have other words in common, but you get the idea.) In the real world, however, we know that many words have similar meanings. Some of this happens when we lemmatize or stem words: if we convert writer and writers (and maybe even writing) all to write, we are arguing that, for the sake or our analysis, these words are *close enough* in meaning to be considered the same.

But what about *writer* and *author*? How do we establish statistically that these two words occupy similar semantic spaces? We establish that words that appear in similar locations in discourse often have the same meaning. The term *word embedding* comes from the fact that the techniques involved embed words in a common low-dimensional space (relative to the size of the vocabulary). We can glimpse this using the NLTK similar function.

## The Dimensionality Problem

Bag of words representations implicitly treat every word as having a distinct of unique meaning. It maximizes the information value of the word, and, if we have lots of data and processing power, we can learn a lot about the words involved. 

The problem is that most moderate-sized corpora, as each of you has developed, there are tens or hundreds of thousands of unique words in your vocabularies. Most documents do not contain most words, resulting in most rows in a DTM being made up of zeros. This means that middle-sized corpora have DTMs with more columns than rows, and the rows are mostly full of zeros. 

Embeddings solve this problem through what is known as the distributional hypothesis of language which most of you encountered in your primary and secondary education when you came across a new word and your teacher suggested that you could puzzle out what it meant by the context in which it occurred. 

> The machine tools required for this programme are really a **bagatelle** compared with our capacity to produce.

> We have proposed a reduction of £100, which of course is a mere **bagatelle** to him.

What word embeddings do is to represent a word as dense vector in a low-dimensional space learned from unlabeled data. In most cases, the representation is gleaned from a large corpus of text data to discover a text representation of each word from which we as analysts can then estimate which words are used in similar ways:

> The hope is that the embeddings from a large, general-purpose corpus will capture information about the meanings of words that will be helpful in performing a context-specific task where there is only limited available labeled data. This idea of using information from a large corpus of texts to help in a different setting is called *transfer learning* and rests on the idea that the meaning of words is relatively stable across different corpora.

### All the Pieces

Today we are going to tackle a number of pieces that will help us understand word embeddings. We are going to move back and forth between working with your larger corpus and working small-scale, and localized to your corpus, and so I am going to ask each of you to choose roughly 50-100 words from one of your texts, or if you are working with small texts like Conner, enough texts to make up that amount of words. 

What we will be doing today:

- Exploring context through similarity and concordance
- Lemmatizing
- n-grams
- Part-of-speech tagging
- 

| Part of speech | Role                                                         | Examples                   |
| -------------- | ------------------------------------------------------------ | -------------------------- |
| Noun           | Is a person, place, or thing                                 | mountain, bagel, Poland    |
| Pronoun        | Replaces a noun                                              | you, she, we               |
| Adjective      | Gives information about what a noun is like                  | efficient, windy, colorful |
| Verb           | Is an action or a state of being                             | learn, is, go              |
| Adverb         | Gives information about a verb, an adjective, or another adverb | efficiently, always, very  |
| Preposition    | Gives information about how a noun or pronoun is connected to another word | from, about, at            |
| Conjunction    | Connects two other words or phrases                          | so, because, and           |
| Interjection   | Is an exclamation                                            | yay, ow, wow               |

[^1]: It’s important to remember that anything you can do with a matrix in linear algebra, you can do with a document-term matrix. 
