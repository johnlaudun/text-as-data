## Tokenizing & Counting Tokens

### Loading a File & Understanding What It Is

We need to load a text in order to start examining it. In the case of reading one file, as we are doing here, we open the file in **read** mode -- that's all the `r` is doing inside the parenthesis --and then we literally `read` the file into a variable. Two steps in two lines of code:


```python
# First we open the file:
opened_file = open('../data/mdg.txt', 'r')

# Then we read the file:
text_as_read = opened_file.read()
```

If we try to work with the first object we created, `opened_file`, let's say by printing it, Python is goint to tell us it's a file object and not really printable. Python recognizes that it is  a text file, but it hasn't been told specifically to take the stream of bytes, as Python understands them, and convert them into a string, which is how computers handle things humans call "texts."


```python
# What happens when we try to print the opened file?
print(opened_file)
```

    <_io.TextIOWrapper name='../data/hod.txt' mode='r' encoding='UTF-8'>


---
**NOTE**: In the code cells above and below you will also notice the presence of lines that are simply descriptions of what the code does and not themselves code: that is, they do not do anything but communicate to humans, yourself or others, what is happening in the code. These are called comments, and it's good to get in the habit of including them. Comments start with a hash mark, `#`, and are typically hand-wrapped if more than one line, with each line beginning with a hash mark. In Jupyter Notebook, you can simply select the lines you want to make comments and then `CMD + /` on your keyboard. This is a toggle-able action, so you can uncomment code this way too.

---


```python
# The work of the two lines above can also be achieved in one line.
mdg = open('mdg.txt', 'r').read()
```

You've just created your first "object" in Python, and it's a text! Or, rather, it's a string, one of the kinds of objects you can work with. If you ever wonder what kind of object you have, you can ask it its `type`:


```python
type(mdg)
```

You can ask it other kinds of things: how big, or long, it is with the length function: 


```python
len(mdg)
```

Combinged with `print()`, `type()` and `len()` are great ways to check your work. (I confess that I sometimes lose track of what kind of data I'm working with -- was that a tuple or a list I created?)

Try printing our `mdg` variable:


print(mdg)


When you run **`print(mdg)`**, you see all of the text in what appears to be "human readable" form. One of the problems you now face is understanding that when you hit `print` and see the text, the computer just sees a `string` of characters -- remember what `type` told you? Python doesn't natively understand human languages: they are nothing more than a series of things, characters made up of letters, numbers, punctuation marks, and spaces.

When you asked Python to tell you the length of the object, it just counted all those things and told you the total. Our version of "The Most Dangerous Game" is 44,000+ characters long. But characters isn't a very useful way to measure texts, is it? Letters are not meaningful. Words are. That's how we think of texts, isn't it? In order to count the words, we have to tell Python how to break the string into words, er, substrings.

 Rather, we need to convert our original string into a list of substrings which as humans we will call words. To do that, we need to figure out how to tell the computer to find words among the sequence of characters. The term for words, and all the other bits that make up written language (like punctuation) as they occur in discourse is **tokens**, and what we need to do is **tokenize**.

### Tokenizing

If only **tokenization** was straightforward. While your first essays into text analytics will probably rely upon relatively well-known methods, you will probably find yourself regularly re-visiting what you use and fine-tuning to fit the needs of your project. (That kind of iterative understanding and refinement based on the work at hand is part of what makes work in the digital humanities so rewarding.) In other words, it's important to remember that, first, tokenization refers "the process of breaking a stream of text up into words, phrases, symbols, or other meaningful elements called tokens" ([Wikipedia](https://en.wikipedia.org/wiki/Lexical_analysis#Tokenization)) and that "meaningful" is in the eye of the beholder.


One of the first places to start tokenizing is with the `split()` method available to use on strings, turning them into lists. If you supply no value inside the parentheses, the default  for `split()` is to split a string into a list wherever there is a white space. 

In the cell below, we first create a string object called `text` -- in this case, the first paragraph from _Heart of Darkness_ -- and then we `split()` it and print the list to see the results.


```python
text = """
The Nellie, a cruising yawl, swung to her anchor without a flutter of
the sails, and was at rest. The flood had made, the wind was nearly
calm, and being bound down the river, the only thing for it was to come
to and wait for the turn of the tide.
"""

split_text = text.split()

print(split_text)
```

**>>>**: Why not copy and paste a block of text from your own work to see what happens?

You can actually specify other values on which to split a string, which can be useful in some cases. (Please note that `split()` and `split(' ')` are the same thing, but do note that there is a space between the two quotation marks.)

In the next cell, we split the paragraph by comma -- the `\n`s you see are newline characters normally hidden from human eyes, but always there. They care considered part of white space by Python, which is why they are not part of the list above.


```python
comma_text = text.split(",")
print(comma_text)
```

As you can see, Python's built-in string method `split()` has plenty of power and may very well do everything you need for quick surveying of results. For more nuanced results, you may find yourself wanting to build a custom setup with regex or to use one of the tokenizers included with the NLTK. Both of those are discussed next.

[For more on tokenization in Python.](http://jeffreyfossett.com/2014/04/25/tokenizing-raw-text-in-python.html)

#### A Quick Note about Normalization

In the first sentence from the opening of _Heart of Darkness_ there are two instances of the definite article *the*:

> The Nellie, a cruising yawl, swung to her anchor without a flutter of the sails, and was at rest.

If we break the sentence into tokens as above and then ask Python to compose a set of words based on the sentence we get the following:


```python
# Whenever you have extra long text in a code example that breaks across lines,
# you enclose it within three quotation marks to let Python know that. 
# (This is one reason to load text from a file.)

sentence = """The Nellie, a cruising yawl, swung to her anchor without a flutter of 
the sails, and was at rest."""

split = sentence.split()
print(split)
# print("This set has {} items:".format(len(set(split))), set(split))
```

    ['The', 'Nellie,', 'a', 'cruising', 'yawl,', 'swung', 'to', 'her', 'anchor', 'without', 'a', 'flutter', 'of', 'the', 'sails,', 'and', 'was', 'at', 'rest.']


Python counts 18 keys, or unique words, out of 19 word tokens -- since we are splitting on white space, the punctuation is part of whatever word it comes after. From Pythons point of view *a* == *a*. (We will discuss `==` versus `=` some other time.) Since those two are the same and we are asking Python to count unique tokens, it only counts *a* once. 

But what about *The* and *the*? Aren't they the same? If we ask Python if *The* and *the* are the same, it tells us no:


```python
'The' == 'the'
```

The way most scholars and scientists avoid this particular semantic difficulty is to make all the text in a string lowercase with `lower()`. This too is a string method, and so you can append it just as you do `split()`. (FTR, there is also `upper()` that makes everything uppercase.)

Watch what happens when we normalize our text to lowercase and ask Python to count the set of words:


```python
sentence = """The Nellie, a cruising yawl, swung to her anchor without a flutter of
the sails, and was at rest."""

split = sentence.lower().split()

print("This set has {} items:".format(len(set(split))), set(split))
```

The two *the*s are now considered to be the same!

#### Using Regex to Tokenize

As you are already beginning to sense, there are a lot of ways to approach breaking a string of characters into a string of words. The first method presented above is the most basic and should be used when first starting out, especially when you pair lowercasing with it -- `.lower().split()` are your new best friends. But at some point you may find that you want a little bit more flexibility in how you handle your text. 

This next approach still depends upon `.lower().split()`, but before we pass our text to it, we do a bit of cleanup. It's one I have used quite often when making first passes through texts. After a while, you'll find that some bits of regex become part of your toolset, and reveal, as this one does mine, your own interests and concerns. In this case, the regex reveals a particular obsession of mine: I like to keep contractions together. (This reveals my own non-standard training: corpus linguists just take for granted that **`can't`** becomes **`ca`** and **`n't`**, or something else equally weird.


```python
# We need the regular expression library
import re

mdg_words = re.sub("[^a-zA-Z']"," ", mdg).lower().split()
```

A quick walkthrough might help a little:

* **`import re`** tells the script to import the regular expression module which comes bundled with every Python installation but doesn't get loaded into our workspace unless we tell it to do so.
* **`mdg_words`** is the object we are creating: everything to the right is the process by which we create the object.
* We aren't going to discuss the regular expression substitution, **`re.sub()`** that gets done here, except to note that you should read the stuff inside the parentheses like this: `(find this pattern, substitute this, in this text)` -- in this case I am telling it to find things that are **not** (`[^ ]` is called a *negated set*) letters (big and small) or apostrophes and replace them with spaces. 
* **`.lower()`** is a method you can apply to strings that makes everything lower case -- otherwise "The" and "the" are two different keys. 
* **`.split()`** is the string method discussed above and we're using its default setting of splitting on white spaces, of which we have plenty, since we have replaced everything except for letters and apostrophes with white space.

The **`split()`** method turns our string into a **list**. In this case, a list of words that are in the same order as they are in the original text. (The computer has no reason to disturb this order.)

If we ask how long the list is, we should come back with a reasonably close count of the words -- don't forget we kept apostrophes, and while most are buried inside contractions, there may be some loose apostrophes. 


```python
print('Words in text: {}.'.format(len(mdg_words)))
```

As you will discover, or have discovered, a list is a different kind of object than a string, and it has some useful properties. One of the things we can do is **slice** a list. In the command below we are saying we want the first 50 words in the list of words: start at the 0th element and go up to the 50th element. Note how the apostrophe, here as a single quotation mark inside Whitney's response about "'ship trap island'", is part of our tokens:


```python
print(mdg_words[0:50])
```

#### Using NLTK Tokenizers

Whether you develop your own tokenizer somewhere along the way or not is entirely up to you and the nature of the projects which you undertake. You may never find yourself doing so. There are certainly a lot of already available options, a number of which are packaged with the Natural Language Toolkit, more often called by its acronym "NLTK", which, by the way, is the same way we call it in Python: 

```python
import nltk
```

As you saw above, the way we tell Python we want some additional functionality is to tell it to **import** a particular library. Previously, we imported the regular expression library, which is called **`re`**. 

If we were to run the line above, we would probably wait a few seconds as the NLTK library loaded -- it's quite large. Because it is a large library, and we really don't need all its functionality, most people don't load all of it -- and isn't it cool that we can load only the parts we need! This is handy as you begin to work with larger scripts and larger data sets: keeping your workspace as tidy, and as small, becomes a necessity. And, in some cases, it's actually easier to use certain tools singly and with a particular name.

#### NLTK's WhitespaceTokenizer 


```python
# import the WhiteSpaceTokenizer directly
from nltk.tokenize import WhitespaceTokenizer
```

You can think of the NLTK as having the same kind of file and folder structure as you do on your computer. Just as you, perhaps, keep all your files for a given project together within a folder bearing some name, Python libraries do as well. All the command above is telling the computer is to go to the nltk library, look in the folder labeled "tokenize" and load this particular 

NLTK's `WhitespaceTokenizer` is about as basic as it comes -- in fact, in the NLTK documentation, they actually note you might as well use `split()`. Its output, so far as I can tell, is the same as `.lower().split()` while also keeping contractions together. However, do note that punctuation is kept with words. You might still prefer to use the `WhitespaceTokenizer` as part of a larger NLTK toolchain.


```python
mdg_tokens = WhitespaceTokenizer().tokenize(mdg.lower())
```

Please note that we now have two versions of "The Most Dangerous Game" rendered as a list in Python: **`mdg_words`** and **`mdg_tokens`**. We created the former using regex and the latter with the NLTK WhitespaceTokenizer. We could have re-used the former name, and that would have, in effect, replaced the older list with the newer one. Please keep this in mind as you work, and also remember to use sensible names for the objects you create. (The more self-explanatory things are, the better as your code grows.)

Now, let's take a look at what kind of object this is, how big it is, and then let's print the first 50 items -- I use 50 as a convenient, quick look, but you can adjust the number down to 25 or up to 100 or some other number that you find more useful. I often change the numbers several times, contracting and expanding as I feel the need.


```python
print(mdg_tokens[0:50])
```

#### NLTK's Word_Tokenize


To be clear, splitting contractions is actually a feature from the point of view of natural language processing. To follow that form of processing, you can use NLTK's **`word_tokenize()`**. As always, you can import the entire `nltk` and then simply use it in your code by writing `tokens = tokenize.word_tokenize(your_text)` or by importing it specifically as below:


```python
from nltk.tokenize import word_tokenize

tokens = word_tokenize(mdg.lower())
print(tokens[0:25])
```

As you can see, the contraction *it's* has been split into *it* and *'s*. 

Finally, we should note that the preferred practice when working with the Penn Treebank word_tokenizer is to use it in combination with the sentence tokenizer. What's that you say? There's a function in the NLTK that will break my text into sentences? Yes, there is, and in a subsequent notebook, working again with "The Most Dangerous Game," we will explore its utility. For now, let's just make sure we know how to use it, and, anticipating some control structures, how to use it in combination with the word tokenizer.

First, let's import the sentence tokenizer, create a list of sentences, and have a look at the first five sentences it creates:


```python
from nltk.tokenize import sent_tokenize

sentences = sent_tokenize(mdg.lower())
print(sentences[0:5])
```

That's a little hard to read, what if we write a `for` loop to make the printout a bit more readable? There's three ways to add a line break after a bit of text in Python, one is to let the algorithm do itself. This often works: `print(whatever)` The other is a weird bit of code-lore that always works: add a comma after the item you are printing -- `print(whatever,)`. Another way is to add a newline character to whatever you are printing: `print(whatever + "\n")`. I'm lazy, so I used the mysterious comma technique below:


```python
for sentence in sentences[0:5]:
    print(sentence,)
```

As you can see from even this limited example, the sentence tokenizer is not perfect: note how  it splits the sentence with a quoted question into two. Yikes. If things like this matter to you, you are going to need to write your own tokenizer -- which is not as hard as it sounds right now to you, but it is additional work when maybe you want to be examining your text.

Now, let's see if we can't combine the two tokenizers so that we get the preferred context for the word tokenizer, which is a single sentence, and yet all of our text is tokenized...

If we first try to pass the output of one, the sentence tokenizer, as input to the other, the word tokenizer, we will get a `TypeError`, revealing that because both tokenizers expect strings as input and we are feeding the output of the sentence tokenizer, which is a list, into the word tokenizer, something's gonna break:

```python
sentences = sent_tokenize(mdg)
tokens = word_tokenize(sentences)
print(tokens[0:20])
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-34-b0aa2f5e281c> in <module>
      1 sentences = sent_tokenize(mdg)
----> 2 tokens = word_tokenize(sentences)
      3 print(tokens[0:20])
```

See how Python not only tells you the kind of error but where the error occurs? (Sometimes it will actually point out the exact spot in a line!)

What we need to do is embed one of the tokenizers inside the other, stacking them as it were, in order to get the results we want:


```python
tokens = []
for sentence in sent_tokenize(mdg):
    for word in word_tokenize(sentence):
        tokens.append(word)
print(tokens[0:50])
```

It is a bit unfair that your second sight of a `for` loop should be one wrapped inside another, but this bit of code is not as complicated as it might look. Let's examine it more closely:

**`tokens = []`** creates an empty list, like first putting a bucket under a spigot before turning it on. (If you think about it, the idea that you can create the bucket as you pour the water is both weird and cool, but here's the old-fashioned way of doing things. Hmm, it feels solid.)

**`for sentence in sent_tokenize(mdg):`** grabs a sentence at a time using the power of the sentence tokenizer to do the work.

**`for word in word_tokenize(sentence):`** tells Python, "Hey, bud, while you've got that sentence in your hand, would you go ahead and tokenize it?"

**`tokens.append(word)`** drops each word, or punctuation!, into the `tokens` bucket. 

** **`print(tokens[0:50])`** just helps us check out work.

**Nota bene**: about this constant `print` thing I do to check my work, feel free to drop it anywhere, especially in the middle of things like `for` loops: it's a great way to see what the program is doing and helps you learn how to code more quickly. (This is something my collaborator, Katherine Kinnaird, taught me.)

Okay, that's enough for one workbook. We will return to this combination, or stack, of sentence and word tokenizers in the next workbook when we turn to the matter of counting words and creating dictionaries.

### Word Frequencies

Once we've established how we are going to tokenize our strings into words, we can start counting those words, er, tokens! In the remaining part of this notebook, we are going to explore three ways to compile word frequencies for a text:

- The Built-In Way
- The NLTK Way
- The Pandas way


```python
import re

# First we load our file into a string
mdg = open('mdg.txt', 'r').read()

# Then we turn that string into a list of words
mdg_words = re.sub("[^a-zA-Z']"," ", mdg).lower().split()
```


```python
import pandas as pd

mdg_series = pd.Series(mdg_words)

print(mdg_series[0:5])
```

    0      off
    1    there
    2       to
    3      the
    4    right
    dtype: object



```python
mdg_counts = mdg_series.value_counts()
print(mdg_counts[0:5])
```

    the    512
    a      258
    he     248
    of     172
    and    164
    Name: count, dtype: int64



```python
mdg_counts.to_csv('mdg.csv')
```
