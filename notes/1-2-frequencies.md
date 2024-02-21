# Stylistics for One

In “Conrad in the Computer: Examples of Quantitative Stylistic Methods,” Michael Stubbs walks readers through various ways to approach a single text using quantitative methods. He notes that *Heart of Darkness* is well-known for its narrative frames—the whole novel is actually one mane telling a story to his friends aboard a ship anchored on the Thames, and thus the role of telling plays in the novel as well as the novels consistent use of imagery involving smoke, fog, darkness, and jungle underlining how difficult it is to see things and, more importantly, to know things. That is, the novel seems to hang on the question of “what can we know?” especially with regard to the intentions of others. (The novel is available as a plain text file in the `data` directory as [Conrad-HoD](../data/Conrad-HoD.txt).)

As Stubbs notes, when working with a single text that you have already read or otherwise know, it is difficult not to begin with what you know. For example, if you were to go looking for words that emphasize the difficulty of seeing in *Heard of Darkness*, you would find that at the very least of the text’s 38,000 words, at least 150 are in the lexical field of *obscure*:

```
blurred 2, dark/ly/ness 52, dusk 7, fog 9, gloom/y 14, haze 2, mist/misty 7, murky 2, shadow/s/y 21, shade 8, shape/s/d 13, smoke 10, vapour 1
```

As Stubbs notes: “Marlow is frequently looking into a fog, uncertain of what he is seeing. Things are constantly *in a muddle* and *chaos* Unexplained things happen: a man hangs himself for no apparent reason” (9). The words listed above are just a sample of a much broader swathe of words one could turn to: the indeterminate *some* makes, Stubbs points out, over 200 appearances as both the word itself as well as part of compound words like *something*, *somebody*, *sometimes*, *somewhere*, *somehow*. 

Attending to such inventories begins to reveal how the text achieves the effects on the reader it does, why readers are frustrated by how nothing is clear; no one seems to want to say anything; everything is just so, so, so *obscure*. (For many of you, this may be how you feel about literary texts in general.) On the other hand, it is pretty impressive that a simple sequence of words can both show us things but in the process of showing make it clear that there is much that cannot be seen nor shown. 

*Heart of Darkness* isn’t a long novel at 38,000 words, and like any novel (or short story or play or screen play or essay or speech or manual or report), it is limited by the fact that one word comes after another. It’s just a string, but out of that string humans extract (unpack if you like) a story world within which a series of events take place within which people-like entities we call *characters* act. Again, just words. You could even argue that texts are nothing more than machines made of words, with clearly discernible parts gathered into sub-assemblies gathered into larger and larger assemblies until the entirety of the thing is a novel or play or whatever.

## Simple Frequency Data

One place to begin is with with frequencies, and we’ve already seen the utility of simply scanning a frequency list as a way to discover what words seem to have the largest role in determining the meaning of a text. If we assume that most texts will have a fair number of *function words* in the upper bounds of their frequencies, then it’s that middle range of words, the *lexical words*, that most often shape how we understand a text — though we should never rule out the power of the word with only a single, or otherwise limited use, to affect our understanding of a text.

### Working with a reference corpus

Okay, but just because a word occurs often, frequently, in a text does not mean it’s important. After all, as we already discussed there are a lot of words that occur most frequently and they have very little impact on what we think a text is about. A frequency list, however, is easily produced and sometimes just scanning the results of such list-making can provoke interesting questions. 

The good folks at Lancaster University have made word frequency lists available for British English:

* [LancsLex](https://lancslex.lancs.ac.uk/) has three lists: word, lemma, and lexeme.
* [Words, words, words: A new Frequency Dictionary of British English](https://cass.lancs.ac.uk/words-words-words-a-new-frequency-dictionary-of-british-english/)

## Frequency Distributions

Compiling a list of words and their frequencies is interesting, and we will use such lists many times over this course, but such a list renders a text into what is commonly called a “bag of words”. This term is in fact so common that you will usually see the acronym, *BoW*. In some cases you may come across such word frequency lists stored as files with a `bow` extension. Some sources of texts, like JSTOR, make those texts available only as BoWs, which does suggest how powerful co-occurrence of words in a text can be. (We will talk more about co-occurrence later in this course.) Just to be clear, a BoW (and thus also a BoW file) will simply be a list of words and their counts:

```
word1, 25
word2, 12
word3, 5
```

But in examining only one text, word frequencies will only get us so far, unless we begin to think about ways to relate them back to the text as a text and not as a bag of words. That is, the interesting words we find in the middle of such lists are not typically distributed evenly across a text: they typically occur in one or more clusters and usually reveal something about a text’s structure. Returning to our example text, Stubbs notes that the word Buddha occurs only at the beginning and end of the novel: they mark the opening and closing of the narrative frame in which the unnamed narrator describes Marlow. (Ben Schmidt does something similar in noting how the word distributions, seen through key word clusters of topics, reveal the plot structure of a show like *Law and Order*, in which the police investigate a crime in the first part of an episode and the attorneys prosecute the crime in the second part.)

For our purposes, the frequency distribution functionality that comes with the NLTK is quite useful.

## References

Bird, Steven, Edward Loper and Ewan Klein. 2009. *Natural Language Processing with Python*. O’Reilly Media Inc.

Stubbs, Michael. 2005. Conrad in the computer: examples of quantitative stylistic methods. *Language and Literature* 14(1): 5-24. 10.1177/0963947005048873. 
