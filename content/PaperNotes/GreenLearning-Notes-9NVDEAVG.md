---
tags: []
title: 'GreenLearning Notes'
parent: ""
collections:
    - GreenML
version: 0
libraryID: 1
itemKey: 9NVDEAVG

---
# GreenLearning Notes

## [@kuoGreenLearningIntroduction2022]

characteristic of GL:

> [!note] [@Page 1](zotero://open-pdf/library/items/N3YHUJRF?page=1\&annotation=QUXZBF3S)
>
> low carbon footprints, small model sizes, low computational complexity, and logical transparency ^QUXZBF3SaN3YHUJRFp1

GL aimed for Edge or cloud

### intro

* DL: architecture + loss function
	* trending: pre-trained, transformer
	* problem: heavy supervision (try to solve by self/semi-supervised learning), high computational demand, large dataset, trustworthiness

First step of GL: understand building blocks

> [!note] [@Page 2](zotero://open-pdf/library/items/N3YHUJRF?page=2\&annotation=2LG9EQVT)
>
> clear and logical description of the decision-making process is emphasized in the development of GL. GL adopts a modularized design. Each module is statistically rooted with local optimization. ^2LG9EQVTaN3YHUJRFp2

avoid global optimization for transparency & efficiency

> [!note] [@Page 2](zotero://open-pdf/library/items/N3YHUJRF?page=2\&annotation=XU5E7MU3)
>
> GL attempts to address the following problems to make the learning process efficient and effective: 1. How to remove redundancy among source image pixels for concise representations? 2. How to generate more expressive representations? 3. How to select discriminant/relevant features based on labels? 4. How to achieve feature and decision combinations in the design of powerful classifiers/regressors? 5. How to design an architecture that enables rich ensembles for performance boosting? ^XU5E7MU3aN3YHUJRFp2

### Genesis of Green Learning

conventional neuron: vector ➡ linear mapping to a scalar ➡ *non-linear activation (not efficient)*.

conventional network pipeline: inputs ➡ embeddings (or features) ➡ predict based on embedding

> [!note] [@Page 4](zotero://open-pdf/library/items/N3YHUJRF?page=4\&annotation=7UQT384G)
>
> Dimension reduction is essential to the simplification of a decision pipeline ^7UQT384GaN3YHUJRFp4

#### what do features do:

1.  dimension reduction
2.  find discriminant dimensions

#### what does decision subnet do?

* ability of MLP: approximation arbitrary function
* essence: mapping n dim input to 1D function, activation decides the shape of 1D function
* observation: ML decision making based on space partitioning, no activation function required

#### weight determination

* DL: backpropagation
* implication of backpropagation for different subnet
	* feature subnet: find best expressive embeddiing
	* decision subnet: find best space partitioning

> [!note] [@Page 5](zotero://open-pdf/library/items/N3YHUJRF?page=5\&annotation=I6VSZ232)
>
> Filter weights in the convolutional layers of FF-CNN are determined by the Saab transform without supervision
>
> * **Notes**: 不用backpropagation来提高效率和规避supervise learning
>     ^I6VSZ232aN3YHUJRFp5

> [!note] [@Page 5](zotero://open-pdf/library/items/N3YHUJRF?page=5\&annotation=XFPZ9LC9)
>
> in FF-CNN training, one clusters training samples of the same class into multiple sub-clusters and create a pseudo-label for each sub-cluster. ^XFPZ9LC9aN3YHUJRFp5

### High-Level Sketch of GL

### GL methodologies

> [!note] [@Page 7](zotero://open-pdf/library/items/N3YHUJRF?page=7\&annotation=FWXPFNSH)
>
> a generic GL system consists of three learning modules in cascade: 1) unsupervised representation learning, 2) supervised feature learning and 3) supervised decision learning. ^FWXPFNSHaN3YHUJRFp7

> [!note] [@Page 7](zotero://open-pdf/library/items/N3YHUJRF?page=7\&annotation=D4J2HZ8K)
>
> The entire system is characterized by three traits: feedforward design, individually optimized module, and statistical ensembles ^D4J2HZ8KaN3YHUJRFp7
