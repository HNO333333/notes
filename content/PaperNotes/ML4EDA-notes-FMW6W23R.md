---
tags: []
title: 'ML4EDA notes'
parent: ""
collections:
    - ML4EDA
version: 0
libraryID: 1
itemKey: FMW6W23R

---
# ML4EDA notes

## [@wuAIassistedSynthesisNext2022]

### HLS PERFORMANCE PREDICTIONS WITH GNNS

> [!note] [@Page 208](zotero://open-pdf/library/items/QJBKAC2H?page=2\&annotation=FCKBI9XK)
>
> Off-the-shelf approach. The first approach directly predicts post-implementation performance metrics based on IR graphs. ^FCKBI9XKaQJBKAC2Hp2

> [!note] [@Page 208](zotero://open-pdf/library/items/QJBKAC2H?page=2\&annotation=DLR89E97)
>
> Knowledge-infused approach. The third approach is a hierarchical GNN-based prediction strategy that reaps advantages of the previous two approaches: not only does it make the earliest prediction but also benefits from domain knowledge with almost zero overhead during inference. ^DLR89E97aQJBKAC2Hp2

> [!note] [@Page 209](zotero://open-pdf/library/items/QJBKAC2H?page=3\&annotation=6D586RNT) ![[imgs/2F6D586RNT.png]]^6D586RNTaQJBKAC2Hp3

For Fig 2 (b): model

> [!note] [@Page 208](zotero://open-pdf/library/items/QJBKAC2H?page=2\&annotation=73GK9ZFB)
>
> first step is node-level classification for resource types, in which the domain knowledge is infused during the training phase; the second step is graphlevel regression that estimates the numerical resource usage and timing on top of the self-inferred domain knowledge. ^73GK9ZFBaQJBKAC2Hp2

### LOGIC SYNTHESIS QORPREDICTIONS WITH MULTI-MODAL GRAPH LEARNING

#### challenges

* need **design specific** flow
* **transformation order** is critical
* **generalization**: across different designs and flow lengths is a necessity

...

> [!note] [@Page 211](zotero://open-pdf/library/items/QJBKAC2H?page=5\&annotation=H5RTY768) ![img](imgs/2FH5RTY768.png) ^H5RTY768aQJBKAC2Hp5

### prospects

* data collection
    * out-of-distribution data
    * simulation generates imperfect data
    * data scarcity (how to do data augmentation)

* model employment
    * multi-level design & optimization
    * interpretability

* deployment
    * online or offline or mixed
    * model maintenance (frequency? measurement of performance?)
