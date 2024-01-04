---
title: CS224S Notes
date: 2024-01-03
draft: false
author: HNO3
---
[course syllabus](https://web.stanford.edu/class/cs224s/syllabus/)

>[!info]- why this course:
>of course final year project :(

## Lecture 2 Phonetics

### Acoustic Phonetics

#### observation from waveform of voice
- Each <font color="#00b050">peak</font> corresponds to an <font color="#00b050">opening</font> of the vocal folds
- low frequency of the complex wave is called the <font color="#00b050">fundamental frequency</font> of the wave or F0

#### Source-filter model of speech production
![[CS224S Notes-20231219-1.png|500]]
- Source and filter are independent, so
	- Different vowels can have same pitch
	- The same vowel can have different pitch

#### intonation
- use of suprasegmental phonetic features
	- F0
	- intensity
	- duration

#### pitch & F0
- Pitch is the mental sensation or perceptual correlated of F0
- Relationship between pitch and F0 is <font color="#00b050">not linear</font>
- Mel scale is one model of this F0-pitch mapping

#### prosody (韵律)
3 aspects
- *Prominence*: some syllables/words are more prominent than others
- *Structure*/boundaries: sentences have prosodic structure. Some words group naturally together, while others have a noticeable <font color="#00b050">break</font> or disjuncture between them
- *Tune*: the intonational melody of an utterance



## Lecture 5 Deep Learning Preliminaries

### recurrent NNs

- *input*: sequence of tokens $(x_1,x_2,...,x_T)$
- *output*: sequence of tokens $(y_1,y_2,...,y_T)$
- *goal*: map $x_t$ to a hidden state $h_t$ (a linear summary of input), then use $h_{t-1}$ and $x_t$ to predict $y_t$
- ![[CS224S Notes-20240103-1.png|500]]<br>(stacked RNNs)
- $\theta$ are shared overall all time steps
- application: speech denoising

RNN encoder
- *input*: sequence of tokens $(x_1,x_2,...,x_T)$
- *goal*: summarize into a single vector
- ![[CS224S Notes-20240103-2.png|500]]
- model should learn $p(x_t|x_1,...,x_{t-1})$

Seq2Seq
- *input* (given): input and output sequence $(x_1,...,x_T),(y_1,...,y_{T-1})$
- *goal*: predict output $y_T$ by $p(y_T|y_1,...,y_{T-1},x_1,...,x_T)$
- ![[CS224S Notes-20240103-3.png|500]]

limitation of RNNs
- long range dependency
- vanishing gradient ➡ $x_i$ has less impact on $y_{i+s}$ as $s$ goes to $\infty$

### attention

$\mathrm{q}\in\mathbb{R}^d$: query; $k_1,...k_T\in R^d$: key; $v_1,...,v_T\in R^d$: values
1. define a similarity function: $sim(q,k_t)$
2. compute attention weight: $a_t=\dfrac{exp\{sim(q,k_t)\}}{\sum_{s=1}^{T}exp\{sim(q,k_s)\}}$
3. attend to values vectors: $c = \sum_{t=1}{T}$

how to pay attention at the same time: multi-head attention
- pick $H$ heads
- for h in range(H): $$ \begin{array}{l}\mathbf{q^{(h)}=MLP_h(q)}\\\mathbf{k^{(h)}_t=MLP_h(k_t)for\:all\:t}\\\mathbf{v^{(h)}_t=MLP_h(v_t)for\:all\:t}\end{array}$$$$ \begin{aligned}&\mathbf{a^{\color{red}{(h)}}}_\mathbf{t}=\frac{\exp\{\mathbf{q^{\color{red}{(h)}T}k_t^{\color{red}{(h)}}/sqrt(d)}\}}{\sum_{s=1}^{\mathsf{T}}\exp\{\mathbf{q^{\color{red}{(h)}T}k_s^{\color{red}{(h)}}/sqrt(d)}\}}\\&\mathbf{c^{\color{red}{(h)}}=\sum_{t=1}^{\mathsf{T}}\mathbf{a^{\color{red}{(h)}}}_t\mathbf{v^{\color{red}{(h)}}}_t {aligned}}\end{aligned}$$$$c_{all}=concat(C^{(1)},...,C^{(H)})$$ $c=linear(c_{all})$ to project to a smaller dimension
- main idea: for a sequence $(x_1,...,x_T)$, for every $x_t$, build $q_t=MLP(x_t), k_t=MLP(x_t),q_t=MLP(x_t)$, then $c_t=\sum_{t=1}^{T}a_tv_t$ so we can get $c=(c_1,...,c_T)$

### transformers: stacking attention
- composed of *encoder* and *decoder*
- *encoder*: input $(x_1,...,x_T)$ and output $(h_1,...,h_T)$
- *decoder*: sees $(x_1,...,x_{T-1})$, output prediction for $(x_2,...,x_T)$


