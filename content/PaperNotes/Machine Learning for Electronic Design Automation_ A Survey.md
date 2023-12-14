---
zotero-key: PJAF3C8N
zt-attachments:
  - "38"
title: "Machine Learning for Electronic Design Automation: A Survey"
citekey: huangMachineLearningElectronic2021
---
# Machine Learning for Electronic Design Automation: A Survey

[Zotero](zotero://select/library/items/PJAF3C8N) [attachment](<file:///D:/my_files/studying_stuffs/zotero_paper_vault/storage/AUMCCBTI/2021_Machine%20Learning%20for%20Electronic%20Design%20Automation_Huang%20et%20al.pdf>)
### interesting insights

> @[Page 2](zotero://open-pdf/library/items/AUMCCBTI?page=2&annotation=8H6RI7RQ)
> <span style="background:rgba(248, 255, 0, 0.28)">ML model is trained to select among available tool chains, algorithms, or hyper-parameters, to replace empirical choice or brute-force search</span>

> @[Page 2](zotero://open-pdf/library/items/AUMCCBTI?page=2&annotation=XKV593FR)
> <span style="background:rgba(248, 255, 0, 0.28)">predict the quality of new designs</span>

> @[Page 3](zotero://open-pdf/library/items/AUMCCBTI?page=3&annotation=F2KTITQH)
> <span style="background:rgba(248, 255, 0, 0.28)">Fig. 1. Modern chip design flow</span>

> @[Page 3](zotero://open-pdf/library/items/AUMCCBTI?page=3&annotation=H5B64VTL)
> <span style="background:rgba(248, 255, 0, 0.28)">Logic synthesis is a complicated process that usually cannot be solved optimally</span>

> @[Page 3](zotero://open-pdf/library/items/AUMCCBTI?page=3&annotation=V8J8WU52)
> <span style="background:rgba(248, 255, 0, 0.28)">ML-based routing-aware methods are proposed to improve the performance of physical design</span>

> @[Page 3](zotero://open-pdf/library/items/AUMCCBTI?page=3&annotation=84VHFQVW)
> <span style="background:rgba(248, 255, 0, 0.28)">ML-based methods are applied in the lithography simulation and mask synthesis</span>

> @[Page 3](zotero://open-pdf/library/items/AUMCCBTI?page=3&annotation=N83RDZMD)
> <span style="background:rgba(248, 255, 0, 0.28)">apply ML methods to optimize test set generation for verification</span>

> @[Page 4](zotero://open-pdf/library/items/AUMCCBTI?page=4&annotation=X63WR559)
> <span style="background:rgba(248, 255, 0, 0.28)">applying ML techniques for test set optimization [100, 120, 140, 141] and test complexity reduction</span>

> @[Page 4](zotero://open-pdf/library/items/AUMCCBTI?page=4&annotation=UPJ4GSV7)
> <span style="background:rgba(248, 255, 0, 0.28)">conventional machine learning models have been extensively studied for the EDA problems, especially for physical design</span>

> @[Page 5](zotero://open-pdf/library/items/AUMCCBTI?page=5&annotation=9E6QRDWN)
> <span style="background:rgba(248, 255, 0, 0.28)">fast and accurate result estimation [30, 37, 108, 109, 143, 164, 172], refining conventional DSE algorithms [74, 107, 149], and reforming DSE as an active-learning problem</span>

> @[Page 5](zotero://open-pdf/library/items/AUMCCBTI?page=5&annotation=6LULDE6J)
> <span style="background:rgba(248, 255, 0, 0.28)">train an ML model that takes HLS reports as input and outputs a more accurate implementation report without conducting the time-consuming post-implementation</span>

> @[Page 6](zotero://open-pdf/library/items/AUMCCBTI?page=6&annotation=RNR3YRZC)
> <span style="background:rgba(248, 255, 0, 0.28)">ML techniques have been applied recently to reduce the HLS tool’s prediction error of the operation delay</span>

> @[Page 7](zotero://open-pdf/library/items/AUMCCBTI?page=7&annotation=9AUQZBU2)
> <span style="background:rgba(248, 255, 0, 0.28)">key functionality of XPPE is using the resource utilization of an application on one specific FPGA to estimate its performance on other FPGAs.</span>

> @[Page 7](zotero://open-pdf/library/items/AUMCCBTI?page=7&annotation=L2VPXFGL)
> <span style="background:rgba(248, 255, 0, 0.28)">Overall workflow of XPPE</span>

> @[Page 8](zotero://open-pdf/library/items/AUMCCBTI?page=8&annotation=93A4XFQN)
> <span style="background:rgba(248, 255, 0, 0.28)">The iterative-refinement DSE framework</span>

### definitions

> @[Page 1](zotero://open-pdf/library/items/AUMCCBTI?page=1&annotation=4T9XCWVH)
> <span style="background:rgba(92, 92, 92, 0.2)">NP-complete (NPC) problems</span>

> @[Page 2](zotero://open-pdf/library/items/AUMCCBTI?page=2&annotation=6F7CBPQJ)
> <span style="background:rgba(92, 92, 92, 0.2)">decision making in traditional methods, performance prediction, black-box optimization, and automated design</span>
- **Notes**: 4 types applications

> @[Page 2](zotero://open-pdf/library/items/AUMCCBTI?page=2&annotation=5MJZZYNE)
> <span style="background:rgba(92, 92, 92, 0.2)">design space exploration (DSE)</span>

> @[Page 2](zotero://open-pdf/library/items/AUMCCBTI?page=2&annotation=EWLVLWFS)
> <span style="background:rgba(92, 92, 92, 0.2)">High-level synthesis (HLS) provides automatic conversion from C/C++/SystemC-based specifications to hardware description languages (HDL)</span>

> @[Page 2](zotero://open-pdf/library/items/AUMCCBTI?page=2&annotation=N8EHX7XD)
> <span style="background:rgba(92, 92, 92, 0.2)">Logic synthesis converts the behavioral level description to the gate level description</span>

> @[Page 3](zotero://open-pdf/library/items/AUMCCBTI?page=3&annotation=VFU39LND)
> <span style="background:rgba(92, 92, 92, 0.2)">Routing assigns the wires to connect the components on the chip. At the same time, routing needs to satisfy the requirements of timing performance and total wirelength without violating the design rules.</span>

> @[Page 3](zotero://open-pdf/library/items/AUMCCBTI?page=3&annotation=TRG8U7HT)
> <span style="background:rgba(92, 92, 92, 0.2)">Mask synthesis is one of the main steps in the fabrication process, where lithography simulation is leveraged to reduce the probability of fabrication failure</span>

> @[Page 4](zotero://open-pdf/library/items/AUMCCBTI?page=4&annotation=532NGWZR)
> <span style="background:rgba(92, 92, 92, 0.2)">tests to verify their functionality and reliability</span>

> @[Page 4](zotero://open-pdf/library/items/AUMCCBTI?page=4&annotation=264HLD5A)
> <span style="background:rgba(92, 92, 92, 0.2)">coverage and the efficiency are two main optimization goals</span>

> @[Page 4](zotero://open-pdf/library/items/AUMCCBTI?page=4&annotation=UWU6BHKM)
> <span style="background:rgba(92, 92, 92, 0.2)">Machine learning is a class of algorithms that automatically extract information from datasets or prior knowledge.</span>

> @[Page 4](zotero://open-pdf/library/items/AUMCCBTI?page=4&annotation=W9XLPFVX)
> <span style="background:rgba(92, 92, 92, 0.2)">CNN is suitable for feature extraction</span>

> @[Page 4](zotero://open-pdf/library/items/AUMCCBTI?page=4&annotation=XQFM9CRY)
> <span style="background:rgba(92, 92, 92, 0.2)">RNN is good at processing sequential data</span>

> @[Page 4](zotero://open-pdf/library/items/AUMCCBTI?page=4&annotation=PTNVMMS4)
> <span style="background:rgba(92, 92, 92, 0.2)">DRL has achieved great success in complicated tasks with large decision space</span>

> @[Page 5](zotero://open-pdf/library/items/AUMCCBTI?page=5&annotation=IYZA46ZY)
> <span style="background:rgba(92, 92, 92, 0.2)">High-level synthesis (HLS) tools provide automatic conversion from C/C++/SystemC-based specification to hardware description languages like Verilog or VHDL.</span>

### 蓝色

> @[Page 6](zotero://open-pdf/library/items/AUMCCBTI?page=6&annotation=A56ISWLB)
> <span style="background:rgba(0, 125, 255, 0.28)">[143].</span>
