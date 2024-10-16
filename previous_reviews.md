REVIEW da Computer Methods and Programs in Biomedicine Update 


 This paper investigates the use of LLM-based chatbots for patient self-management. To alleviate concerns of privacy leakage, the paper proposes two solutions: an intent classification module in conjunction with a LLM service and the use of local open-source LLMs. The authors identified four categories of user intent and compared the data extraction and semantics of the two proposed solutions.
Strengths:
* The two proposed solutions are straightforward and reasonable.
Weaknesses:
* The topic presented in this paper is not focused. The paper provides too many details about the underlying implementations of the chatbot. Considering the title highlights privacy-preserving, the experiments also lack privacy evaluations. Therefore, I believe the paper needs to be revised to better highlight the topic of privacy-preserving and chronic disease self-management.




REVIEW da Computer Methods and Programs in Biomedicine


1. Are the objectives and the rationale of the study clearly stated?

Please provide suggestions to the author(s) on how to improve the clarity of the objectives and rationale of the study. Please number each suggestion so that author(s) can more easily respond.

Reviewer #1: The motivation for this paper is not very clear. The challenges described in this paper are overly broad, making the paper seem more like a technical report than a research paper.

Reviewer #2: Yes, the objectives are well-articulated.

Reviewer #3: This work aims to address an critical issue in medical robots: data safety and privacy. It explores the integration of cutting-edge LLMs into medial informatics. However, the objectives and the rationale need further clarification.

1. Focus on Chronic Diseases: The title indicates a focus on chronic diseases, but the manuscript does not discuss what makes the data safety and privacy needs of chronic diseases distinct from other diseases. Data safety and privacy are general concerns for all medical conditions. This distinction should be clarified to better justify the focus on chronic diseases.

2. Methodology and Objectives: The approach involves using a parser to extract information from user input and send it to LLMs with sensitive information masked or removed. However, this step is applied only to the "insertion" category, which is designed to include all the sensitive data. This motivates the category prediction step in the study. Given the critical importance of patient privacy and the non-guaranteed accuracy of machine learning models, it would be more realistic to mask or remove sensitive information across all categories. Consequently, the objectives for the classification phase appear unclear. The study would benefit from a more detailed explanation of why the current approach was chosen and how it effectively addresses data safety and privacy concerns across all categories.

2. If applicable, is the application/theory/method/study reported in sufficient detail to allow for its replicability and/or reproducibility?

Please provide suggestions to the author(s) on how to improve the replicability/reproducibility of their study. Please number each suggestion so that the author(s) can more easily respond.

Reviewer #1: Mark as appropriate with an X:
Yes [] No [X] N/A []
Provide further comments here:
The purpose of the 'information filtering' step is unclear to me. Utilizing an online LLM like GPT-3.5 inherently compromises privacy as sensitive data is exposed to the online server during user interactions. This risk extends beyond just OpenAI potentially accessing user data—it also includes the possibility of data interception by third parties. Moreover, in scenarios where user queries cause the chatbot to summarize and generalize data from its database, the risk of information leakage could actually increase. If the system were based on offline LLMs, such as Llama2, it could directly perform operations like insertion and retrieval based on user needs without the need for further classification and data transmission, thus reducing system redundancy. This approach should be considered as a baseline in experimental setups.

1. Missing Evaluation Prompts: The evaluation prompts are not provided. Table 1 presents the classification results for all messages, with each LLM tested given a message to predict its category. Given that LLMs are sensitive to the specific inquiry prompts used, the absence of these prompts in the manuscript is a significant omission. Including the prompts is essential for understanding the context in which the models were evaluated and for ensuring the validity of the results.

2. Missing Hyperparameters for Local LLMs: The hyperparameters for the local LLMs, such as temperature, are not specified. These parameters are crucial as they influence the consistency and quality of the model's output. Providing detailed hyperparameters is vital for the reproducibility of the study. Without this information, it is challenging for other researchers to replicate the experiments and verify the results.

1. The manuscript lacks a detailed description of the data used for evaluation, making it difficult to assess the validity and effectiveness of the evaluation results.

2. There is no explanation provided on how the data was labeled as ground truth, which undermines the credibility of the evaluation results.

4. Could the manuscript benefit from additional tables or figures, or from improving or removing (some of the) existing ones?

Please provide specific suggestions for improvements, removals, or additions of figures or tables. Please number each suggestion so that author(s) can more easily respond.

Reviewer #1: The usage of tables and figures in this paper is satisfactory.

Reviewer #2: See extended review below

Reviewer #3: 1. data statistics

5. If applicable, are the interpretation of results and study conclusions supported by the data?


The comparison between zero-shot inference of offline LLMs and well-trained L-BFGS logistic regression may be unfair due to the potential significant impact of the prompt on model performance. However, the paper did not provide the prompt used for the classification scenario, nor for the semantic analysis scenario.


Again, the results are hard to interpreted without more details of the dataset and the model.

6. Have the authors clearly emphasized the strengths of their study/theory/methods/argument?

Please provide suggestions to the author(s) on how to better emphasize the strengths of their study. Please number each suggestion so that the author(s) can more easily respond.

Reviewer #1: No. The paper does not clearly emphasize the strengths of the proposed approach. Additionally, the paper lacks baseline methods, and the comparison only focuses on different variants.

Reviewer #2: A broader analysis of their methods is necessary.

Reviewer #3: Yes. Authors have emphasized the strengths of their study.

7. Have the authors clearly stated the limitations of their study/theory/methods/argument?

Please list the limitations that the author(s) need to add or emphasize. Please number each limitation so that author(s) can more easily respond.

Reviewer #1: Yes, the Discussion section of the paper is satisfactory.

Reviewer #2: To some extent

Reviewer #3: I did not find limitations stated by the authors in the paper. Here are some limitations in my mind:
1. response time: response time could be a problem given different database and LLM implementations. It is critical to the performance of the system. The discussion of response time is missing in this paper.
2. sensitive data in other categories. The proposed approach assumes all the sentences with sensitive data are captured and put in the "insertion" category. How to handle the false negative cases?

8. Does the manuscript structure, flow or writing need improving (e.g., the addition of subheadings, shortening of text, reorganization of sections, or moving details from one section to another)?

Please provide suggestions to the author(s) on how to improve the manuscript structure and flow. Please number each suggestion so that author(s) can more easily respond.

Reviewer #1: Yes. The paper's structure is somewhat disorganized, failing to clearly differentiate between the functionalities of the chatbot and the NLP/NLG modules. Additionally, it lacks detailed information on the hyperparameters used for the offline LLMs and the chatbot configuration.

Reviewer #2: No

Reviewer #3: There is just one subsection in the background section, making labeling it as a subsection unnecessary. Some context is missing in the background. For example, what makes the LLM-based chatbot for chronic diseases different than those for other diseases?

9. Could the manuscript benefit from language editing?

Reviewer #1: Yes

Reviewer #2: No

Reviewer #3: Yes

 


Reviewer #1: This study explores integrating Large Language Models (LLMs) into medical chatbots for managing chronic diseases, focusing on reliability, clinical trials, and privacy issues. It proposes a dual approach: using an online LLM (GPT-3.5 Turbo) for enhanced interaction and fully local open-source LLMs to protect privacy. While GPT-3.5 Turbo performs better in various tasks, the two local models also show promising reliability and accuracy. The findings suggest that open-source LLMs could be viable, privacy-preserving alternatives for medical chatbots, emphasizing the need for ongoing refinement.
The paper introduces a detailed architectural design that includes local filtering mechanisms and offers capabilities for tracking or visualizing based on users' historical data. Additionally, it carefully considers the use of specific prompt engineering in interactions with users, demonstrating a detailed and thoughtful approach in medical contexts.
The primary concerns I have with the paper are as follows:
1. The purpose of the 'information filtering' step is unclear to me. Utilizing an online LLM like GPT-3.5 inherently compromises privacy as sensitive data is exposed to the online server during user interactions. This risk extends beyond just OpenAI potentially accessing user data—it also includes the possibility of data interception by third parties. Moreover, in scenarios where user queries cause the chatbot to summarize and generalize data from its database, the risk of information leakage could actually increase. If the system were based on offline LLMs, such as Llama2, it could directly perform operations like insertion and retrieval based on user needs without the need for further classification and data transmission, thus reducing system redundancy. This approach should be considered as a baseline in experimental setups.
2. The comparison between zero-shot inference of offline LLMs and well-trained L-BFGS logistic regression may be unfair due to the potential significant impact of the prompt on model performance. However, the paper did not provide the prompt used for the classification scenario, nor for the semantic analysis scenario.
3. The paper's structure is somewhat disorganized, failing to clearly differentiate between the functionalities of the chatbot and the NLP/NLG modules. Additionally, it lacks detailed information on the hyperparameters used for the offline LLMs and the chatbot configuration.


Reviewer #2: Strengths: Clear objective, well-articulated points, and reasonable methods used here. Authors include multiple metrics and domain expert evaluation to evaluate models which is a core strength of this study.

Weakness:
1. No citation for ChatGPT included - more citations of relevant research work backing the claims in the background section should be added as well - non exhaustive list of missing citations - Telegram, MongoDB, MNET (only git link provided).
2. In the result section - there is incorrect referencing for Table 1 and 2. It is quite confusing as the tables are not explained in the text. It would be ideal to include description of the table results in the text.
3. Figure 2 label is repeated thrice - one on Page 9 then on Page 14 and 15
4. Ollama based models are quantized that could lead to depreciation in quality of response and certain tasks. The authors should provide details about which level of quantization is selected for the models.
5. It is prudent to include the prompts for GPT 3.5 and other Models for clarity (mentioned in sec 4.2 pg 15). Additionally, the setting for 'temperature' parameter should be included as it could lead to variations if not optimized properly. Please check "A reliable knowledge processing framework for combustion science using foundation models" by Sharma et al. for reference.
6. Example dataset of patient queries should be included (section 3.2.3 pg 11) for clarity on features that are being classified.
7. For prompt refinement using GPT-4, the authors should include details of improvements done in the prompts and include said prompts in an appendix.
8. The database stores textual and other data format - is this embedded using a model? What search metric is used to retrieve the data? Details should be included separately.
9. The proposed method limits hallucination by selectively constricting conversation to general information - are there any instances where this technique fails?
10. Is it possible that openLLMs perform poorly because a lower quantized model is needed to run on the server? The model is selected based on "we focus on a smaller model that can load and respond swiftly" in section 3.2.4. In short, server's hardware limitation dictates the results. Authors should explain the LLM selection criteria and present performance plots in terms of inference speed. Also, the hardware specs used to conduct this analysis should be added.
11. Formatting issues:
a. Pg 10 - the method 'i' should be '(i)' and 'ii' should be '(ii)'.
b. Fig.3 on pg 18 - box plot for mixtral model is missing. The dots are not explained and are difficult to read and understand.



Reviewer #3: This field is optional. If you have any additional suggestions beyond those relevant to the questions above, please number and list them here.
 