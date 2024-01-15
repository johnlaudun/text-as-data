# X


#### 1.1 Texts as Vector Spaces

Every single act of text mining or analytics begins with a decision
about what to quantify and how to quantify it, sometimes known as the
vector space model. We begin with the simplest form of vectorization,
bag of words (BoW) and explore how much can be gleaned by simply
understanding which words co-occur in various ways.

Methods explored: TF-IDF, LDA. NMF

Task(s).

**Method(s)**:

**Action(s)**:

Every unit should have a task and every segment of the course (or maybe
its segments and units?) should have a task. The big tasks are: build a
corpus, do something with it, communicate the results and make the
corpus available. (I should really focus this on fan fiction and web
forums.)

#### 1.2 Understanding Dimensions

PCA, tSNE, KNN, ...

#### 1.3 Distributed Representations of Words

Most vector space representations of texts consider them to be bags of
words with the only importance attached to the co-occurrence of words
within the larger bag. But words have meanings and those meanings are
revealed through collocations: words accompany other words with
regularity.

**Method(s)**: word2vec

**Action(s)**:

**Consideration(s)**: cosine similarity.

#### 1.4 Sequences of Words

Not only do words go with other words, they usually go with those words
in a particular order. That is, words occur in regular sequences, and
those sequences either constitute strings we recognize as texts or
pieces of texts.

**Method(s)**: text reuse, part-of-speech tagging, named entity
recognition.

**Action(s)**:

**Consideration(s)**: information extraction.

### Unit 2 \| getting data

#### 2.1 Getting Data / Building a Corpus

We can't do much without data, but data just doesn't appear out of
nowhere: we have to go out and get it, which means we have to make
decisions about what drives us: a question or a phenomenon. How we
answer that questions determines what data we collect. (Most data
scientists estimate that at least 25% of their work involves collecting
and munging data.)

#### 2.2 Parsing and Manipulating Semi-Structured Data

Once we have data, or even in the process of accumulating data, we need
to decide how we are going to store it and how we are going to recall,
or load, it. Some of our responses here will be based on the
computational and storage resources available to us.

### UNIT 3 \| getting to work

#### 3.1 Designing a Project

Our project has already begun with data collection but now we need to
explore the scope of our work and what our outcomes might be. This is an
iterative process, and so the sketching we do here will be just that, a
sketch, a draft subject to revision.

#### 3.2 Working through the Dimensions

An important aspect of any analytical project is documentation: whether
you are working in a research or in an applied environment, others are
going to want to know how you got your results. That is, your results
are only as good as their replicability.

#### 3.3 Visualizations

Throughout this process, we have engaged in various forms of
visualization, and we will continue to do so, but it is important to
consider what visualizations can, and cannot do.

### UNIT 4 \| getting chatgpt

A number of sources would have you believe that SkyNet lurks around the
corner from ChatGPT. Others suggest that GPT is little more than a
souped-up neural network with some word vectors mixed in. The truth is
complicated and relies a great deal on the shear amount of data that
lies behind GPT and BERT. In this unit we explore the basics of
transformers and build our own to see if the models they produce tell us
anything interesting about the corpora we have built.
