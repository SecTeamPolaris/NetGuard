Thank you for your useful comments and suggestions on our manuscript. They are very valuable and helpful for revising and improving the paper. We have studied the comments carefully and made revision accordingly. The detailed responds are listed as follows:

**【Q1】** The problem definition wasn't clear enough.

**【A1】** Apologies for any confusion in the problem definition. This paper focuses on detecting the network access behavior of mobile devices through the analysis of network traffic. Our objective is to identify when a mobile device connects to the network, distinguish the brand at a broad level, and identify its specific model with fine granularity.

​	To accomplish this goal, Magnifier, denoted as the detector function (f), takes network traffic fragments as input and produces output indicating the presence of network access behaviors in those fragments. If such behaviors are detected, Magnifier is then tasked with distinguishing the brands and models of the devices involved.

​	We have thoroughly revised this section to provide a clearer explanation of our objectives and the role of Magnifier in achieving them.

**【Q2】** At a high level, the motivation makes sense, but the connection to the approach wasn't as clear to me.  Why is it important to detect the  brand, specifically?  And if this is important, why wasn't it done  before?  The basic idea of looking at brand-specific traffic seems very  straightforward-- why would some variation of this not have been  attempted already?  

**【A2】** 

1. Magnifier exhibits the capability to differentiate between device brands by leveraging fingerprints; a match with any fingerprint from the same brand is considered successful. This approach, operating at a coarse-grained level, typically ensures higher detection precision. In contrast, discerning the specific models of devices can be more challenging. While it promises more detailed information, achieving precision at this level necessitates an exact match with the model fingerprints. Magnifier, therefore, provides two detection levels, allowing users to strike a balance between precision and the level of detail desired.
1. As discussed in Section 1, there are two primary methods for detecting network access in mobile devices. Endpoint-based approaches, extensively explored in both industry and academia, suffer from poor universality and limited coverage. Notably, the practical deployment of these methods is hindered by the underestimation of costs associated with their development and maintenance, posing challenges. In contrast, our approach relies on network traffic analysis and proves effective in detecting network access while also discerning device models. This alternative offers improved universality and coverage compared to endpoint-based methods, addressing some of the limitations associated with the latter.

**【Q3】** The detail provided for the baselines was insufficient.  

**【A3】** Some details of the implementation are outlined in the appendix. However, we acknowledge that the information provided is insufficient. Consequently, we have expanded the description of the implementation for a more comprehensive understanding of the baselines.

1. Firstly, all baselines undergo training and testing using the same sets. The training or initialization of baselines is conducted with ScenarioA from NetCess2023. Subsequently, the baselines are subjected to testing scenarios, namely ScenarioB and ScenarioC, to obtain the Detection Rate (DR). The False Alarm Rate (FAR) is assessed using ScenarioD. It's worth noting that most baselines necessitate the pre-definition of the number of classes. Consequently, the training and testing phases for brand-level and model-level classifications are independent. In other words, for a given baseline, a classifier with eight classes is trained for brand-level classification, while another classifier with 27 classes is trained for model-level classification.
2. Secondly, in our methodology, each training or testing sample corresponds to a network traffic fragment of a specified time duration (5s, 10s, or 15s). Diverse baselines implement feature engineering, extracting different features from these fragments. For instance, statistical feature-based methods such as RF, C4.5, and XGBoost extract packet-related parameters like packet number, average packet size, and average arrival time. Temporal feature-based methods like FS-Net and MBTree focus on extracting sequences of packet lengths or packet arrival intervals from the fragments. We re-design the graph initialization of ProGraph since clustering with IP features can hardly result in a legitimate graph. Specifically, each event is considered as a node during initialization so that features and labels can be aggregated and disseminated as expected. 
3. Thirdly, the classifiers of the baselines adhere to the procedures outlined in their respective proposals for initialization and detection. It is noteworthy that the majority of these baselines have made their source code publicly available.

 

