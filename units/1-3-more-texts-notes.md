## 1-3 Texts and Words

In the previous lab we explored various functions within the NLTK using the text of “The Most Dangerous Game,” but the text of _Heart of Darkness_ is also available for comparison. Having a larger (longer) text is important for some of the functions offered in the first chapter: a number of them work better with more data. The paucity of data in an 8000-word text becomes apparent quickly!



### Lexical Diversity

We also wrote our own function to calculate lexical diversity, using simple functions like `len()` and `set()`. Using that function we have one way to compare texts: “The Most Dangerous Game” has a lexical diversity of 0.195, and _Heart of Darkness_, 0.124.

Those are interesting numbers. Perhaps we need to explore this idea of lexical diversity among texts a bit more. One place to begin is a small collection of short stories published roughly during the same period as “The Most Dangerous Game.” We can expand our `lex_div` function a bit, and when we do we get these results:

```python
A: 0.326
B: 0.308
C: 0.233
D: 0.283
E: 0.237
F: 0.284
G: 0.259
H: 0.246
```

What if we compare those numbers to something like a Shakespeare play, who is famed for his large vocabulary: one study in 1976 estimated that Shakespeare used at least 31,564 words and that he probably knew at least another 35,000 (Efron and Thisted 1976:435). It turns out the lexical diversity of _Hamlet_ is 0.138. That’s closer to Conrad than to Connell.

### Comparing Texts and Words

Lexical diversity is one measure. It tells us about the vocabulary of a text but not anything about what it’s about? How do we get at *aboutness*? 

A better measure would be relative frequencies of words, which we stack up like a fingerprint when it comes to function words.

Frequencies (tf)

Relative frequencies

inverse document frequencies (tf-idf)

topics (lexical words)

signature (function words): is punctuation part of a signature?
