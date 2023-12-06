Thank you for your useful comments and suggestions on our manuscript. They are very valuable and helpful for revising and improving the paper. We have studied the comments carefully and made revision accordingly. The detailed responds are listed as follows:

**【Q1】** your real-world mobile networks application deployments' result is missing, try to add at least one or two.

**【A1】** Thanks for your advice. Magnifier has been effectively deployed in real-world scenarios. Specifically, it is employed for the detection of network access by mobile devices in both campus network and production network. The implementation and results are outlined as follows:

1. Before deployment, the initialization of Magnifier involves the meticulous construction and distillation of fingerprints, as elaborated in Section 4. This process ensures the creation of well-defined fingerprints that form the basis for Magnifier's functionality.
2. Magnifier is strategically deployed on both the gateway of our campus network and the enterprise network gateway. The implementation utilizes the KAFKA and Protobuf framework, supported by the DPDK backend.
3. Initially, a probe, developed using DPDK, is employed to capture passing traffic at the gateway. Upon capturing DNS traffic, the subsequent network traffic within a 15-second timeframe from the identified IP is collected and stored in the cache. 
4. Subsequently, a feature extractor is utilized to consistently extract domain features from the cached traffic fragments. These extracted features are represented as "Dn-freq" pairs (e.g., {dn_1: n_1, dn_2: n_2,..., dn_k: n_k }) and encapsulated within a protobuf message. The KAFKA producer then pushes this message to a predefined topic. It's important to note that the processed traffic is promptly flushed from the cache.
5. The real-time detection algorithm is integrated into a Docker environment, allowing for efficient resource allocation by adjusting the number of detector instances. These instances continually retrieve protobuf messages from the subscribed topic. The algorithm utilizes well-designed fingerprints to detect behaviors and outputs results, including the determination of network access and identification of the device's brand/model.
6. **Results on real-world deployments:** Magnifier was initially deployed on the gateway of our laboratory network. To assess the False Alarm Rate (FAR), we conducted an audit of the background network for 2 hours, during which no attempts of network access were made by mobile devices. Among the 20 thousand audited fragments, Magnifier triggered 37 alarms, resulting in a FAR of approximately 0.19%. Subsequently, we evaluated the Detection Rate (DR) by simulating repeated connections of mobile devices to an internal WIFI. Magnifier achieved an impressive DR of 96.86%, demonstrating performance consistent with our experimental results. Extending our deployment to an industrial enterprise, characterized by a high level of confidentiality, Magnifier maintained robust performance. In this context, it achieved a DR of 97.15% and an exceptionally low FAR of 0.097%.

**【Q2】** the number of data points or scale in your experiments needs to be enlarged.

**【A2】** Thanks for you advice. We have augmented the number of events in ScenarioA, B, and C of NetCess2023. The revised dataset is detailed as follows.

|            | Evts (S_A) | Evts (S_B) | Evts (S_C) |
| ---------- | ---------- | ---------- | ---------- |
| iPhone13U  | 72 -> 130  | 35 -> 120  | 73 -> 130  |
| iPhoneXR   | 90 -> 142  | 60 -> 130  | 126 -> 126 |
| iPhone7    | 91 -> 130  | 41 -> 136  | 92 -> 135  |
| iPhone6s   | 90 -> 121  | 26 -> 128  | 32 -> 130  |
| iPhone6    | 90 -> 130  | 59 -> 130  | 75 -> 130  |
| Mate50     | 90 -> 130  | 54 -> 130  | 60 -> 130  |
| Mate40P    | 90 -> 130  | 59 -> 130  | 79 -> 130  |
| Mate30     | 89 -> 130  | 37 -> 138  | 107 -> 107 |
| P30        | 90 -> 130  | 56 -> 130  | 15 -> 130  |
| P9         | 97 -> 147  | 65 -> 130  | 115 -> 115 |
| VivoX30    | 90 -> 130  | 42 -> 129  | 108 -> 108 |
| VivoX27    | 73 -> 130  | 41 -> 130  | 87 -> 129  |
| VivoX23    | 133 -> 133 | 86 -> 136  | 213 -> 213 |
| VivoY66i   | 85 -> 135  | 44 -> 115  | 134 -> 134 |
| Vivo93     | 90 -> 130  | 60 -> 130  | 45 -> 130  |
| OppoR15    | 135 -> 135 | 75 -> 135  | 166 -> 166 |
| OppoR9m    | 90 -> 130  | 58 -> 130  | 136 -> 136 |
| OppoA5     | 89 -> 130  | 59 -> 130  | 135 -> 135 |
| Xiaomi13U  | 79 -> 129  | 53 -> 128  | 29 -> 130  |
| Xiaomi6x   | 90 -> 130  | 60 -> 130  | 150 -> 150 |
| XiaomiMix2 | 88 -> 130  | 46 -> 130  | 28 -> 128  |
| Xiaomi3    | 151 -> 151 | 73 -> 156  | 141 -> 141 |
| Xiaomi2s   | 90 -> 130  | 56 -> 130  | 132 -> 132 |
| SamsungS10 | 113 -> 158 | 47 -> 130  | 121 -> 121 |
| SamsungC5  | 214 -> 214 | 104 -> 168 | 24 -> 130  |
| Dazen      | 86 -> 130  | 45 -> 130  | 69 -> 126  |

​	The event counts for each device in all scenarios have been increased to approximately 130. Subsequently, Magnifier was re-evaluated using this enhanced dataset, and it yielded results comparable to those obtained with the original dataset. For instance, under the setting of \tau = 15s and model-level classification, Magnifier achieved a Detection Rate (DR) of 96.54% with the enhanced dataset, closely aligning with the original DR of 96.83%. The False Alarm Rate (FAR) for Magnifier remains at 0.25%, consistent with the original results, as ScenarioD remains unmodified. We intend to update NetCess2023 and make it publicly available for the community.

**【Q3】** try to introduce some production data from telecom companies, etc, to better demonstrate the usability of the proposed approach.

**【A3】** Given that the fingerprinting module of Magnifier is pluggable and customizable to suit the objects targeted for detection, Magnifier can effectively be employed to discern the network access patterns of Internet of Things (IoT) devices by monitoring the gateway traffic of a company. Similar to mobile devices, IoT devices establish connections with remote services, resulting in distinct traffic patterns. Deployed in a industry network, Magnifier successfully fingerprinted the network traffic of approximately 20 types of IoT devices, spanning various models of cameras, smart speakers, watches, and more, utilizing the algorithms proposed in this paper. Subsequently, Magnifier demonstrated its proficiency in effectively detecting the network access behaviors of these IoT devices. Notably, Magnifier showcased its ability to generalize for the detection of devices exhibiting similar communication patterns, illustrating its versatility in IoT device identification.

​	Thanks for your advice. We have added to the discussion section to to better demonstrate the usability of our work.

**【Q4】** there are related state-of-the-art you may want to compare: Online Optimization Methods for the Quantification Problem, Fast Distributed Bandits for Online Recommendation Systems.

**【A4】** Thanks for the provided baselines. After an in-depth examination of the two papers, I have encountered challenges in fine-tuning the proposed methods. The difficulty stems from the fact that these methods are designed as general solutions for online optimization and recommendation systems, lacking specificity for network traffic analysis. This absence of specialization complicates the process of crafting tailored feature engineering and fine-tuning algorithm parameters to suit the nuances of network traffic data.

​	Nevertheless, we have identified the potential to enhance current methods in traffic network analysis. Consequently, we have incorporated the following discussion on these methods in the related work section.

​	"Purushottam et al. [1] proposes a family of algorithms, NEMSIS, CAN, SCAN, and their  non-surrogate versions, for addressing the online quantification problem in machine learning and data mining, optimizing quantification-specific performance measures in an online stochastic setting, which can be  applied to network traffic analysis for improving the efficiency and  accuracy of traffic prediction and classification. Besides,  Kanak et al. [2] presents DistCLUB, a distributed bandit-based algorithm for  online recommendation systems that scales effectively and achieves  higher accuracy than state-of-the-art methods like DCCB by intelligently mixing user-based and cluster-based recommendations, which is  particularly useful for analyzing network traffic and providing  personalized content recommendations in large-scale dynamic systems."

[1] Kar, Purushottam, et al. "Online optimization methods for the quantification problem." *Proceedings of the 22nd ACM SIGKDD international conference on knowledge discovery and data mining*. 2016.

[2] Mahadik, Kanak, et al. "Fast distributed bandits for online recommendation systems." *Proceedings of the 34th ACM international conference on supercomputing*. 2020.

​	Furthermore, we have expanded our experiments by incorporating additional baselines, with a specific focus on IoT device recognition and encrypted traffic classification.

​	Sivanathan et al. [3] introduced a machine learning framework for the classification of IoT devices. This classification method involved analyzing various traffic features, including activity cycles, signaling patterns, communication protocols, and cipher suites.

​	ProfilIoT [4] represents a machine learning-driven approach designed for the identification of IoT devices within a network. The primary goal is to discern whether a given traffic flow originates from a PC, a smartphone, or a specific IoT device. The methodology involves the deployment of a set of classifiers, utilizing machine learning algorithms in a multi-stage process. This process enables the classification of traffic flows generated by a particular device based on their respective IP addresses.

​	ET-BERT  [5] is one of the state-of-the-art solutions on encrypted traffic classification. It considers the raw byte of the traffic sessions as the input of the pre-trained BERT. ET-BERT designs two novel pre-training tasks for traffic classification.

​	TFE-GNN [6] is one of the state-of-the-art solutions on encrypted traffic classification. It proposes a byte-level traffic graph construction approach based on point-wise mutual information (PMI).

​	We assessed the supplementary baselines under the identical settings outlined in the paper, specifically conducting the classification within the established detection duration of 15s. The experimental results are as follows: 

|                | DR (Brand-Level) | FAR (Brand-Level) | DR (Model-Level) | FAR (Model-Level) |
| -------------- | ---------------- | ----------------- | ---------------- | ----------------- |
| Sivanathan [3] | 82.73%           | 15.85%            | 74.15%           | 18.89%            |
| ProfilIoT [4]  | 86.33%           | 9.80%             | 82.17%           | 11.63%            |
| ET-BERT  [5]   | 92.21%           | 8.92%             | 87.64%           | 12.76%            |
| TFE-GNN [6]    | 84.59%           | 6.78%             | 79.02%           | 8.81%             |
| **Magnifier**  | **97.54%**       | **0.25%**         | **96.83%**       | **0.25%**         |

[3] Sivanathan, Arunan, et al. "Classifying IoT devices in smart environments using network traffic characteristics." TMC 18.8 (2018): 1745-1759.

[4] Meidan, Yair, et al. "ProfilIoT: A machine learning approach for IoT device identification based on network traffic analysis." *SAC*. 2017.

[5] Lin, Xinjie, et al. "Et-bert: A contextualized datagram representation with pre-training transformers for encrypted traffic classification." *WWW2022*. 2022.

[6] Zhang, Haozhen, et al. "TFE-GNN: A Temporal Fusion Encoder Using Graph Neural Networks for Fine-grained Encrypted Traffic Classification." *WWW2023*. 2023.

**【Q5】** last but not least, try to add some theoretical analysis would be also beneficial to enhance the quality of this submission.

**【A5】** Thanks for your advice. We have delved deeper into the efficiency of the distillation algorithm by providing a theoretical analysis of confidence scores.

​	The initial dnForest captures fingerprints from all traffic generated when devices connect to the network, encompassing both specific and background traffic. The presence of background traffic can result in significant false alarms during classification, given that these applications are commonly found on various devices. Moreover, background traffic constitutes a substantial portion of the captured data, causing an imbalance among dnTrees within a dnForest. 

​	To address this challenge, we introduce a two-stage distillation algorithm designed to emphasize proprietary fingerprints while diminishing the importance of background ones. To further validate the efficiency of the algorithm, we conduct a comparison of confidence score distributions before and after fingerprint distillation. Specifically, for each test sample, we compute the confidence score alongside its corresponding fingerprint:

$$
Score^c_i = f(x_i^y,dnTree^y)
$$

​	In the context of Magnifier, where f() represents the detector function, $x_i^y$ denotes a test sample from class y, and $dnTree^y$ represents the fingerprint of class y. By averaging the scores of all test samples, we derive confidence scores that facilitate correct classification. Simultaneously, we compute the confidence score with respect to other fingerprints:

$$
Score^w_i = \frac{\sum\limits_{k\in Y,k \neq y} f(x_i^y,dnTree^k)}{|Y|}
$$

where |Y| is the number of the generated fingerprints. By averaging the scores of all test samples, we can obtain confidence scores indicative of incorrect classifications.

​	Before fingerprint distillation, the average $Score^c$ and $Score^w$ is 0.678 and 0.461, respectively. After the two-stage distillation, the average $Score^c$ and $Score^w$ is 0.883 (30.2% improvement) and 0.167 (63.8% decline), respectively. The enhanced divergence of the two scores theoretically explain the experimental results in Section 6.5. 

​	Prior to fingerprint distillation, the average $Score^c$ and $Score^w$ are 0.678 and 0.461, respectively. Following the two-stage distillation, the averages for $Score^c$ and $Score^w$ become 0.883 (reflecting a 30.2% improvement) and 0.167 (representing a 63.8% decline), respectively. The amplified divergence between these two scores theoretically explains the experimental results outlined in Section 6.5.

​	Thanks for your advice. We have added the analysis to the ablation study (Section 6.5).
