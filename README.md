# MMLU-CF Dataset
MMLU-CF is a contamination-free and more challenging multiple-choice question benchmark. This dataset contains 10K questions each for the validation set and test set, covering various disciplines.

[Datasets](huggingface.com)|[Paper](arxiv.com)|[Github](github.com)

## 1. The Contribution of MMLU-CF.

 - The open-source nature of these benchmarks and the broad sources of training data for LLMs have inevitably led to benchmark contamination, resulting in unreliable evaluation results. To alleviate this issue, we propose MMLU-CF.
 - To avoid unintentional data leakage, we source data from a broader domain and design three decontamination rules.
 - To prevent malicious data leakage, we divide the benchmark into validation and test sets with similar difficulty and subject distributions.The test set remains closed-source to ensure reliable results, while the validation set is publicly available to promote transparency and facilitate independent verification.
 - Our evaluation of mainstream LLMs reveals that the powerful GPT-4o achieves merely a 5-shot score of 73.4\% and a 0-shot score of 71.9\% on the test set, which indicates the effectiveness of our approach in creating a more rigorous and contamination-free evaluation standard.
   
[Fig2]()


## 2. How to Evaluate Your Models on the MMLU-CF Validation/Test set?

#### (1) For Huggingface models, following the steps outlined below and obtaining the validation set results, the test set results can then be accessed via GitHub Issues. 
  1. **Validation Set Evaluation**: Obtaining the validation results for your model using LLM evaluation tools, [OpenCompass](https://github.com/open-compass/opencompass). We have already added **MMLU-CF** to [OpenCompass](https://github.com/open-compass/opencompass) for this purpose.
  2. **Test Set Evaluation**: With the validation results, submit a GitHub issue on the [MMLU-CF](https://github.com/) GitHub homepage to request the test set results. Please follow the format below:
Example:
```
Title: 
Test Request - add HF model [meta-llama/Llama-3.2-1B]

Content:
Result on validation results: 68.5%
```
  **Notably**:
   - Ensure you use the format with square brackets `[ ]` as shown. The model name **meta-llama/Llama-3.2-1B** corresponds to the name on HuggingFace.
   - We will automatically submit your model. The time to receive the results depends on the number of models being evaluated, but it typically takes **1-2 weeks**.

#### (2) For API models, if [OpenCompass](https://github.com/open-compass/opencompass) updates the model interface, you can obtain the test set results by sending a temporary key to [Email](yangyu.huang@microsoft.com) after receiving the validation set results.


## 3. What is the Difference between MMLU-CF and MMLU?
MMLU focus on the breadth, reasoning without considering contamination prevention. We apply three decontamination rules to mitigate unintentional data leakage while collecting data from a broader domain. Meanwhile, our MMLU-CF benchmark maintains the test set closed-source to prevent malicious data leakage.

[Fig1, Fig4, ]

| Model                           | MMLU 5-shot (%) | MMLU-CF 5-shot Test (%) | MMLU-CF 5-shot Validation (%) | 5-shot $\Delta$ (%) | MMLU-CF 0-shot Test (%) | MMLU-CF 0-shot Validation (%) | 0-shot $\Delta$ (%) |
|----------------------------------|-----------------|--------------------------|------------------------------|----------------------|-------------------------|------------------------------|-----------------------|
| **API**                          |                 |                          |                              |                      |                         |                              |                       |
| GPT-4o      | 88.0            | 73.4                     | 73.4                         | +0.0                 | 71.9                    | 72.4                         | -0.5                  |
| GPT-4-Turbo  | 86.5            | 70.4                     | 70.1                         | +0.3                 | 68.9                    | 68.7                         | +0.1                  |
| GPT-4o-mini      | 81.8            | 65.5                     | 65.1                         | +0.4                 | 66.0                    | 65.3                         | +0.7                  |
| Gemini-1.5-Flash  | 78.7      | 64.8                     | 64.9                         | -0.1                 | 56.7                    | 56.9                         | -0.2                  |
| GPT-3.5-Turbo       | 71.4            | 58.2                     | 59.0                         | -0.8                 | 57.2                    | 58.1                         | -0.9                  |
| **Large**                        |                 |                          |                              |                      |                         |                              |                       |
| Qwen2.5-72B-instruct | 85.3          | 71.6                     | 71.3                         | +0.3                 | 70.6                    | 70.4                         | +0.2                  |
| Llama-3-70B-instruct  | 82.0    | 68.9                     | 68.8                         | +0.1                 | 68.1                    | 67.4                         | +0.7                  |
| Llama-3.3-70B-instruct  | 86.3    | 68.8                     | 67.8                         | +1.0                 | 67.6                    | 67.5                         | +0.1                  |
| Llama-3.1-70B-instruct   | 86.0   | 68.7                     | 68.1                         | +0.6                 | 70.4                    | 69.7                         | +0.7                  |
| Phi-3.5-MoE-instruct  | 78.9     | 64.6                     | 64.5                         | +0.1                 | 63.1                    | 62.1                         | +1.0                  |
| Qwen2-72B-instruct   | 82.3       | 63.7                     | 64.3                         | -0.6                 | 62.4                    | 62.5                         | -0.1                  |
| Mixtral-8x22B-instruct  | 76.2 | 62.8                     | 62.5                         | +0.3                 | 65.3                    | 64.8                         | +0.5                  |
| Qwen1.5-72B-chat  | 75.6        | 59.8                     | 60.2                         | -0.4                 | 59.1                    | 59.6                         | -0.5                  |
| Llama-2-70B-chat   | 68.9      | 52.2                     | 51.8                         | +0.4                 | 51.2                    | 50.9                         | +0.3                  |
| **Medium**                        |                 |                          |                              |                      |                         |                              |                       |
| Qwen2.5-32B-instruct   | 83.9          | 69.7                     | 68.8                         | +0.9                 | 68.9                    | 68.8                         | +0.1                  |
| Phi-4-14B   | 84.8  | 67.8                     | 68.5                         | -0.7                 | 68.5                    | 69.4                         | -0.9                  |
| Qwen2.5-14B-instruct | 79.9         | 66.4                     | 66.1                         | +0.3                 | 67.0                    | 66.0                         | +1.0                  |
| Phi-3-medium-instruct  | 77.9    | 64.2                     | 64.2                         | +0.0                 | 62.5                    | 62.7                         | -0.2                  |
| Gemma2-27B    | 75.2            | 63.9                     | 63.5                         | +0.4                 | 64.2                    | 64.0                         | +0.2                  |
| Yi-1.5-34B-chat | 76.8          | 61.3                     | 60.5                         | +0.8                 | 60.6                    | 59.5                         | +1.1                  |
| Mixtral-8x7B-instruct-v0.1  | 70.5 | 58.3                    | 57.1                         | -1.2                 | 58.9                    | 58.5                         | +0.4                  |
| Deepseek-v2-lite-chat  | 55.7     | 49.3                     | 48.7                         | +0.6                 | 48.2                    | 47.7                         | +0.5                  |
| Baichuan-2-13B-chat  | 57.3   | 48.3                     | 48.6                         | -0.3                 | 47.1                    | 48.1                         | -1.0                  |
| Llama-2-13B-chat  | 54.8     | 42.8                     | 42.1                         | +0.7                 | 44.8                    | 44.6                         | +0.2                  |
| **Small**                        |                 |                          |                              |                      |                         |                              |                       |
| Qwen2.5-7B-instruct  | 75.4          | 61.3                     | 60.4                         | +0.9                 | 59.3                    | 58.6                         | +0.7                  |
| Qwen2-7B-instruct | 70.5        | 58.1                     | 57.9                         | +0.2                 | 58.3                    | 57.4                         | +0.9                  |
| Glm-4-9B-chat | 72.4         | 57.8                     | 57.9                         | -0.1                 | 58.6                    | 58.7                         | -0.1                  |
| Internlm-2.5-7B-chat   | 72.8 | 57.3                     | 56.8                         | +0.5                 | 57.9                    | 56.9                         | +1.0                  |
| Llama-3-8B-instruct  | 68.4    | 57.3                     | 56.5                         | +0.8                 | 56.4                    | 55.4                         | +1.0                  |
| Llama-3.1-8B-instruct  | 68.1   | 57.1                     | 57.9                         | -0.8                 | 56.1                    | 56.1                         | +0.0                  |
| Gemma-2-9B    | 71.3            | 53.7                     | 53.3                         | +0.4                 | 32.1                    | 31.2                         | +0.9                  |
| Yi-1.5-6B-chat | 62.8            | 52.8                     | 51.4                         | +1.4                 | 52.2                    | 51.9                         | +0.3                  |
| Mistral-7B-instruct-v0.3   | 60.3 | 50.7                     | 50.9                         | -0.2                 | 51.1                    | 50.9                         | +0.2                  |
| Baichuan-2-7B-chat | 52.9   | 44.5                     | 43.9                         | +0.6                 | 43.9                    | 44.0                         | -0.1                  |
| Llama-2-7B-chat   | 45.3    | 39.4                     | 38.5                         | +0.9                 | 41.9                    | 40.9                         | +1.0                  |
| **Mini**                         |                 |                          |                              |                      |                         |                              |                       |
| Phi-3-mini-instruct (3.8B)   | 70.9 | 57.9                     | 58.1                         | -0.2                 | 58.2                    | 57.5                         | +0.7                  |
| Phi-3.5-mini-instruct (3.8B)   | 69.1 | 57.9                     | 57.4                         | +0.5                 | 58.3                    | 57.7                         | +0.6                  |
| Qwen2.5-3B-instruct  | 64.4           | 55.9                     | 56.4                         | -0.5                 | 54.3                    | 53.9                         | +0.4                  |
| Qwen2.5-1.5B-instruct | 50.7         | 51.2                     | 51.0                         | +0.2                 | 50.7                    | 50.4                         | +0.3                  |
| Qwen2-1.5B-instruct   | 52.4      | 47.1                     | 47.5                         | -0.4                 | 45.2                    | 44.5                         | +0.7                  |
| Gemma-2-2B  | 51.3            | 43.9                     | 42.4                         | +1.5                 | 30.5                    | 29.4                         | +0.9                  |
| Qwen2.5-0.5B-instruct  | 24.1        | 41.9                     | 41.1                         | +0.8                 | 36.0                    | 34.9                         | +1.1                  |
| Internlm-2-chat-1.8b   | 47.1  | 40.5                     | 39.4                         | +1.1                 | 41.2                    | 39.8                         | +1.4                  |
| Qwen2-0.5B-instruct   | 37.9      | 38.3                     | 38.3                         | +0.0                 | 33.5                    | 33.5                         | +0.0                  |

## 4. Properties of Partitioning Test and Validation Sets.
We partition the benchmark dataset into test and validation sets, then calculate the absolute score difference as $\Delta$ for LLMs, it not only helps prevent test set leakage but also offers the following benefits: Firstly, as shown in Table, before the validation set is publicly released, about 60\% of $\Delta$ values are less than 0.5, and 96\% of $\Delta$ values are below 1.0. This indicates that the evaluation results of LLMs are significantly consistent across the test and validation sets, demonstrating the effectiveness of the validation set in evaluating model generalization. Once the validation set is made public, potential data leakage can cause the models to overfit on the validation set, leading to an increase in $\Delta$ values. Thus, the design of $\Delta$ serves as a method to monitor whether benchmarks might be compromised. This approach helps ensure the fairness and integrity of the benchmarks, preventing models from exploiting leaked data to artificially enhance their performance.

## 5. Data Construction Pipeline.
The pipeline involves (1) MCQ Collection to gather a diverse set of questions; (2) MCQ Cleaning to ensure quality; (3) Difficulty Sampling to ensure an appropriate difficulty distribution for questions; (4) LLMs checking: The LLMs, including GPT-4o, Gemini, and Claude, are reviewing the accuracy and safety of the data; and (5) Contamination-Free Processing to prevent data leakage and maintain dataset purity. Ultimately, this process results in the MMLU-CF, consisting of 10,000 questions for the closed-source test set and 10,000 for the open-source validation set.

## 6. Contact
We have identified some mistakes in the dataset. If you come across any issues, please submit the corresponding question_id on the issue page, and we will address it promptly. Our team is dedicated to maintaining and improving this dataset over time to ensure its ongoing quality!

For any inquiries or concerns, feel free to reach out to us via Github: @fistyee and @huangyangyu or [email](yangyu.huang@microsoft.com).
## 7. Citation

