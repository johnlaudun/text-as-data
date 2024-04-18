# BERT

## Overview

### The Problem

> **Griezmann’s** announcement comes as a bit of a shock. After enduring the drama surrounding **his** potential last summer, many thought **he** was committed to Atletico for more than a year, but the **Frenchman** seems to have changed **his** mind.

### The Big Idea

- Capturing such **relationships & sequences** of words in sentences has been a roadblock for a number of text analytics / generation applications.
- Most of the data in our world is in the form of **sequences**: it can be a number sequence, text sequence, a video frame sequence or an audio sequence.
- The sequences can be quite complex: hierarchical, dynamic, etc.

## Background/Buildup

### seq2seq

- **seq2seq** models [in NLP] are used to convert sequences of Type A to sequences of Type B.
- A **seq2seq model** is composed of an **encoder** and a **decoder** typically implemented as **RNN**s. The encoder captures the context of the input sequence and sends it to the decoder, which then produces the final output sequence.
- **Attention mechanisms** were the final piece of the puzzle.
- **Applications**: machine translation, text summarization, speech recognition, question-answering system.

![image-20240416074142487](/Users/jl/Developer/text-as-data/assets/rnn.png)

- Both **encoder** and **decoder** are RNNs
- At every time step in the encoder, the RNN takes a word vector (xi) from the input sequence and a hidden state (Hi) from the previous time step
- The hidden state is updated at each time step
- The hidden state from the last unit is known as the context vector. This contains information about the input sequence
- This context vector is then passed to the decoder and it is then used to generate the target sequence.
- If we use the attention mechanism, then the weighted sum of the hidden states are passed as the context vector to the decoder

### Challenges

- Dealing with long-range dependencies is still challenging
- The sequential nature of the model architecture prevents parallelization.

## What is a language model?

One of the biggest challenges in NLP is the lack of enough training data. While there is an enormous amount of text data available, if we want to create task-specific datasets, we need to split that pile into a lot of smaller domains. And when we do this, we end up with only a few thousand or a few hundred thousand human-labeled training examples. 

Unfortunately, in order to perform well, deep learning based NLP models require much larger amounts of data — they see major improvements when trained on millions, or billions, of annotated training examples. To help bridge this gap in data, researchers have developed various techniques for training general purpose language representation models using the enormous piles of unannotated text on the web (this is known as **pre-training**). These general purpose pre-trained models can then be **fine-tuned** on smaller task-specific datasets. 

This approach results in great accuracy improvements compared to training on the smaller task-specific datasets from scratch.

## Why Bidirectional?

Pre-trained language representations can either be **context-free** or **context-based**. Context-based representations can then be **unidirectional** or **bidirectional**. Context-free models like word2vec generate a single representation (a vector of numbers) for each word in the vocabulary. 

For example, the word “*bank*” would have the same context-free representation in “*bank account*” and “*bank of the river.*” On the other hand, context-based models generate a representation of each word that is based on the other words in the sentence. For example, in the sentence “*I accessed the bank account*,” a unidirectional contextual model would represent “*bank*” based on “*I accessed the*” but not “*account*.” However, BERT represents “*bank*” using both its previous and next context — “*I accessed the* … *account*” — starting from the very bottom of a deep neural network, making it deeply bidirectional.

## The Many Flavors of BERT

- [**ALBERT**](https://arxiv.org/abs/1909.11942) by Google and more — This paper describes parameter reduction techniques to lower memory reduction and increase the training speed of BERT models.

- [**RoBERTa**](https://arxiv.org/abs/1907.11692) by Facebook — This paper for FAIR believes the original BERT models were under-trained and shows with more training/tuning it can outperform the initial results.

- [**ERNIE**](https://arxiv.org/abs/1904.09223): Enhanced Representation through Knowledge Integration by Baidu — It is inspired by the masking strategy of BERT and learns language representation enhanced by knowledge masking strategies, which includes entity-level masking and phrase-level masking.

- [**DistilBERT**](https://arxiv.org/abs/1910.01108) — Smaller BERT using model distillation from Huggingface.


## Histories & Primers

- TDS has a good run-down of BERT. While it’s dated, it still covers a lot of the necessary ground:[2019 — Year of BERT and Transformer](https://towardsdatascience.com/2019-year-of-bert-and-transformer-f200b53d05b9). 
- Jay Alammar’s illustrated guide is also a few years old, but it is outstanding: [The Illustrated BERT, ELMo, and Co.](http://jalammar.github.io/illustrated-bert/).
- [GLUE Benchmark board](https://gluebenchmark.com/leaderboard/).



## References

I read a lot of web pages and repository notes, some of which are logged below. 

* [jalammar.github.io/notebooks/bert/A\_Visual\_Notebook\_to\_Using\_BERT\_for\_the\_First\_Time.ipynb at master · jalammar/jalammar.github.io](https://github.com/jalammar/jalammar.github.io/blob/master/notebooks/bert/A\_Visual\_Notebook\_to\_Using\_BERT\_for\_the\_First\_Time.ipynb)
* [Distill-BERT: Using BERT for Smarter Text Generation | by Rohit Pillai | The Startup | Medium](https://medium.com/swlh/distill-bert-using-bert-for-smarter-text-generation-aa65ba6facf0)
* [ChenRocks/Distill-BERT-Textgen: Research code for ACL 2020 paper: "Distilling Knowledge Learned in BERT for Text Generation".](https://github.com/ChenRocks/Distill-BERT-Textgen)
* [sleepingcat4/bert-textgeneration: A complete guide in generating text using bert and fine-tune](https://github.com/sleepingcat4/bert-textgeneration)
* [Natural Language Generation using BERT | by Prakhar Mishra | Intel Student Ambassadors | Medium](https://medium.com/intel-student-ambassadors/natural-language-generation-using-bert-df6d863c3f52)
* [Writing-with-BERT/NLP\_LM\_Finetuning.ipynb at master · prakhar21/Writing-with-BERT](https://github.com/prakhar21/Writing-with-BERT/blob/master/NLP\_LM\_Finetuning.ipynb)
