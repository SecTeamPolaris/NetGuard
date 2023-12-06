Thank you for your useful comments and suggestions on our manuscript. They are very valuable and helpful for revising and improving the paper. We have studied the comments carefully and made revision accordingly. The detailed responds are listed as follows:

**【Q1】** The advantage of Magnifier over existing approach is not such significant.

**【A1】** Magnifier achieves the best performance compared with the existing methods, not only in terms of higher Detection Rate (DR), but also significantly lower False Alarm Rate (FAR) and better throughput.

1. Reduced FAR (False Alarm Rate): Under the parameter configuration  \tau = 15s, incorporating S_A/(S_C+S_D) and Model-Level classification, Magnifier demonstrates a 96.83% Detection Rate (DR), marking a 3.69% improvement over FlowPrint. Notably, Magnifier boasts a substantially lower FAR at 0.25%, in stark contrast to FlowPrint's 6.95%. This represents a noteworthy advancement for a real-time detector, particularly given the practical deployment requirement on high-throughput backbone gateways. For example, one of the campus gateways where Magnifier is practically deployed achieves a throughput of 100 bps. In this context, Magnifier may potentially misclassify only 0.25% of background traffic lacking any network access. In comparison, FlowPrint may yield false alarms at a rate of 6.95 bps, which is 27.8 times higher than Magnifier. This is deemed unacceptable for a real-time system, especially considering that a significant portion of real-world Internet traffic constitutes background traffic.
1. Increased Throughput: The efficiency of Magnifier is further assessed in Section 6.4, depicted in Figure 6. Notably, when subjected to testing with S_B + S_D on the model level, Magnifier demonstrates a testing duration of 2.6 seconds, a substantial improvement over FlowPrint's 19.8 seconds. We contend that this substantial increase in throughput, amounting to a 7.62 times improvement, constitutes another noteworthy advantage over the baseline methods.

​	Appreciating your insightful suggestion, we have incorporated additional details into the experimental section to enhance the presentation of Magnifier's performance.

**【Q2】** The relevance to the Web is not clearly described in the first page of the paper.

**【A2】** Thanks for your advice. We have made more discussion on the Web literature. Our research falls within the domain of network traffic analysis, a pivotal aspect of both network and web management, as evidenced by previous works discussed at WebConf [1] [2] [3]. Specifically, Magnifier is introduced to identify access to internal networks or the web, with a particular focus on instances where devices exploit web authentication evasion through authorized hotspots. Additionally, the concepts of website fingerprinting and network access fingerprinting share a common thread. Both aim to identify potential security risks, including malicious websites and unauthorized access, thereby contributing to more effective network and web management strategies.

[1] Zheng, Wenbo, et al. "Learning to classify: A flow-based relation network for encrypted traffic classification." *WWW2020*. 2020.

[2] Lin, Xinjie, et al. "Et-bert: A contextualized datagram representation with pre-training transformers for encrypted traffic classification." *WWW2022*. 2022.

[3] Zhang, Haozhen, et al. "TFE-GNN: A Temporal Fusion Encoder Using Graph Neural Networks for Fine-grained Encrypted Traffic Classification." *WWW2023*. 2023.

**【Q3】** Minor issues.

**【A3】** Thanks. We have revised the issues accordingly. 
