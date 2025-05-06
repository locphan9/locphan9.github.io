---
layout: post
tags: Foundational NLP
author: Loc
---

Keywords: hypernyms, One-hot encoder, word meaning by context

Bob: What's the first thing that comes to your mind when I say the word "orange". This is not a trick question

Alice: Well, it's a fruit, it's also a color.

Bob: Very well, then what will a machine think about the word "orange" ?

Alice: 0 and 1?

Bob: That's a good start. Well we will study how machine understand meaning of words. We will begin with some rudimentary technique such as WordNet which contains list of hypernyms, encoding method like one-hot encoding, and representing words by context by looking the words surrounding it. 

## WordNet

Since we are going to study meaning. Here is the definition of the word "meaning": https://www.merriam-webster.com/dictionary/meaning

The word "good" can be equivalent to "fair", "proficient", "nice", which is not suitable for every context

## Represent words as discrete symbols

Below are just example of one-hot encoder not the actual encoded value
hotel = $$\begin{pmatrix} 0\\ 0 \\ 0 \\ 0 \\ 1 \\ 0 \end{pmatrix}$$
motel = $$\begin{pmatrix} 0\\ 0 \\ 1 \\ 0 \\ 0 \\ 0 \end{pmatrix}$$

Hotel and motel are very similar but the two one-hot vectors are orthogonal. Therefore, we need better encoding method

## Represent words as meaning of surrounding (context) words

The objective is to represent each word as a vector. And we will use numerical method to determine the optimate vector for each word based on "context" words.

$$L(\theta)=\prod_{w<t>} \prod_{i<m} P(u_{w_center}|v_{i_context})$$

where $$t$$ are the number of example sentence and $$2*i$$ is the number of context words for each sentences, and 

$$P(u_{w_center}|v_{i_context}) = \frac{exp(u*v)}{\sum_{w=1}^{t}exp(u_{w}v)}$$. 

The function we will minimize is 

$$J(\theta) = \sum_{}^{}\sum_{}^{}-\frac{}{}log(P(u_{w_center}|v_{i_context}))$$

Numerical method used for solving the objective function will be gradient descent or adaptive search 