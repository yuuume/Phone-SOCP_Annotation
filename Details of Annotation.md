<!-- 
用于 SOCP 任务的自动化标注流程分为两个主要阶段：Subject-Object-Aspect-Preference四元组的提取和方面类别的分类。通过这种两步法，prompt会简化，并使 LLM能够更高效地完成每个子任务，从而提升提取过程的准确性。
通过这种两步法，prompt会简化，并使 LLM能够更高效地完成每个子任务，从而提升提取过程的准确性。

我们首先选取比较评论，指导 LLM 逐步提取比较主体、比较客体、比较方面以及比较偏好。
随后，我们将这一指导过程作为历史信息提供给 LLM，使它具备识别比较要素的能力。在拥有历史标注作为上下文的情况下，我们只需输入新的评论文本，LLM 便能直接提取其中的比较要素。下表展示了这一指导流程。

在提取完比较四元组之后，下一阶段是将其中的方面元素分类到预先定义的类别。下面展示了方面类别分类的提示。
-->


The automated annotation process for the SOCP task is divided into two main phases: **Subject-Object-Aspect-Preference Quadruplet Extraction** and **Aspect Category Classification**. 
This two-step approach simplifies the prompt, enabling the LLM to handle each task more efficiently and improving the accuracy of the extraction process.
<br>
<br>

## Subject-Object-Aspect-Preference Quadruplet Extraction

We first select comparison reviews and guide the LLM to extract the comparative subject, comparative object, comparative aspect, and comparative preference step by step. 
This guiding process is then provided as historical information to the LLM, enabling it to extract the comparative elements. 
With historical annotations as context, we can directly input new review texts, allowing the LLM to extract the comparative elements. The following table shows the guiding process.
<br>

Role | Conversation
---- | ----
Human | Here’s a review of the Google Pixel 6 Pro: “...It surpasses the Samsung Galaxy S21 Ultra especially in terms of photographic detail. it also has a great processor performance and runs smoother compared to the iPhone 13...” Which other phone models were compared with the Google Pixel 6 Pro in the review?
LLM | The Google Pixel 6 Pro was compared with the following smartphones: Samsung Galaxy S21 Ultra and Apple iPhone 13.
Human | In the reviews, which smartphone features were compared between the Google Pixel 6 Pro and others? Did the Google Pixel 6 Pro perform better, worse, or the Equal?
LLM | In the reviews, the Google Pixel 6 Pro was compared with other smartphones in the following aspects: Camera Performance: Compared to the Samsung Galaxy S21 Ultra, the Google Pixel 6 Pro’s camera is better at capturing details. Processor Performance: Compared to the iPhone 13, the Google Pixel 6 Pro’s processor performance is superior and runs more smoothly.
Human | Great, now you need to organize the results into JSON format as follows: \{”subject”: The smartphone purchased, ”object”: The other smartphone models being compared, ”aspect”: The smartphone attribute being compared, ”preference”: Indicates whether the purchased smartphone is better, worse, or the Equal\}. Each JSON object represents one comparison. Note that ”preference” can only be one of ”BETTER,” ”WORSE,” or ”Equal.”
LLM | \[\{”subject”: ”Google Pixel 6 Pro”, ”object”: ”Samsung Galaxy S21 Ultra”, ”aspect”: ”Camera Performance”, ”preference”: ”BETTER”}, {”subject”: ”Google Pixel 6 Pro”, ”object”: ”Apple iPhone 13”, ”aspect”: ”Processor Performance”, ”preference”: ”BETTER”\}\]
Human | Great! Next, I will provide you with some reviews, each review being independent. You need to output the results in JSON format according to the above requirements. If the review does not directly mention other phone models for comparison, output [].
LLM | Of course, I am ready. Please provide the phone reviews, and I will convert them into JSON format according to your requirements.
Human | Here’s a review of the Samsung Z Flip5: “The packaging was intact, the shipping was fast, the seller’s service was good, it’s compact and exquisite, highly functional, and the price is also more favorable than in physical stores.”
LLM | []
Human | {A review text}

<br>

## Aspect Category Classification

After extracting the comparison quaternions, the next phase involves categorizing the aspect element into predefined categories. 
The prompt of Aspect Category Classification is shown below:
<br>
<br>
In ABSA tasks within the mobile phone domain, the aspect category is defined by concatenating Entity and Attribute in the format Entity#Attribute. <br>
Entity must be selected from the list: {the list of predefined entity labels}, and Attribute must be chosen from the list: {the list of predefined attribute labels}.<br>
Given a review and a list of comparative aspects, please determine the category for each aspect in the list. Output a list (e.g., \[Entity\#Attribute\]) without any explanation. <br>
Review: “\{review text\}”. <br>
Aspect: \{the list of aspects\}.<br>
Output:

