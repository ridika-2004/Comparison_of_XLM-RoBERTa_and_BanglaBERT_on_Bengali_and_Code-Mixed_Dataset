# Comparison of XLM-RoBERTa and BanglaBERT on Bengali and Code-Mixed Datasets

**Authors:** Ramisa Anan Rahman, Ridika Naznin, Zannatul Adon Sabiha, Afrin Jahan Era, Ayesha Binte Anis  
**Affiliation:** Department of Computer Science and Engineering, Islamic University of Technology, Dhaka, Bangladesh

**Read the Paper:** [Paper](https://github.com/ridika-2004/Comparison_of_XLM-RoBERTa_and_BanglaBERT_on_Bengali_and_Code-Mixed_Dataset/blob/main/Comparative%20Performance%20of%20XLM-RoBERTa%20and%20BanglaBERT%20on%20Pure%20Bengali%20and%20Code-Mixed%20Text.pdf)


## Abstract

> <img src="https://github.com/user-attachments/assets/311f0bb5-faff-442c-8eab-8dbc4f625f15" align="right" width="200px"/>
> This study presents a comparative analysis of transformer-based language models for Bangla sentiment classification across multiple benchmark datasets, including Motamot, SentNoB, and BanglaBook. We evaluate the performance of two prominent models—BanglaBERT, a monolingual model pretrained specifically on Bangla corpora, and XLM-RoBERTa, a multilingual model trained on diverse languages. The experiments consider both zero-shot and fine-tuned settings to assess the models’ inherent linguistic understanding and adaptability to downstream tasks. Our results demonstrate that fine-tuning significantly improves performance for both models across all datasets. However, BanglaBERT consistently outperforms XLM-RoBERTa in most evaluation metrics, including accuracy, F1-score, and recall, while maintaining competitive precision. Notably, BanglaBERT exhibits strong zero-shot performance, whereas XLM-RoBERTa performs poorly without task-specific training, highlighting the importance of language-specific pretraining. Further analysis using confusion matrices and training dynamics reveals that BanglaBERT benefits from faster convergence and more stable learning behavior. In contrast, XLM-RoBERTa requires substantial fine-tuning to achieve comparable results. These findings emphasize the effectiveness of monolingual pretrained models for low-resource languages like Bangla and provide insights into model selection for sentiment analysis tasks.

## Datasets

### 1. Motamot Dataset

A sentiment analysis dataset focused on political opinions expressed by users across various platforms. It captures diverse public perspectives, including support, criticism, and neutral commentary on political topics.

| Split | Positive | Negative | Total |
|-------|----------|----------|-------|
| Train | 3,306 | 2,341 | 5,647 |
| Validation | 413 | 292 | 705 |
| Test | 413 | 293 | 706 |
| **Total** | 4,132 (58.54%) | 2,926 (41.46%) | **7,058** |

### 2. SentNoB Dataset

A sentiment analysis dataset constructed from real-world social media comments, reflecting diverse public opinions across multiple domains. It includes data from 13 different topics, such as politics, education, and technology.

| Split | Positive | Negative | Neutral | Total |
|-------|----------|----------|---------|-------|
| Train | 5,133 | 4,548 | 2,894 | 12,575 |
| Validation | 623 | 590 | 354 | 1,567 |
| Test | 654 | 571 | 361 | 1,586 |
| **Total** | 6,410 (40.8%) | 5,709 (36.3%) | 3,609 (22.9%) | **15,728** |

### 3. BanglaBook Dataset

A large-scale sentiment analysis dataset composed of book reviews collected from popular online bookstores such as Rokomari and Wafilife. The reviews are originally associated with user ratings, which are subsequently mapped into sentiment categories.

| Split | Positive | Negative | Total |
|-------|----------|----------|-------|
| Train | 99,110 | 6,772 | 105,882 |
| Validation | 14,159 | 967 | 15,126 |
| Test | 28,318 | 1,935 | 30,253 |
| **Total** | 141,587 (93.60%) | 9,674 (6.40%) | **151,261** |

## Implementation Details

### Dataset Preparation
- Neutral samples were removed to focus on binary sentiment classification
- Duplicate entries were eliminated to avoid bias and redundancy
- Records with null or missing values were dropped
- Text data was filtered to retain samples with 3-50 words

### Sentiment Labeling
Datasets originally containing three sentiment classes were converted into binary classification by removing the neutral class and mapping remaining labels (negative = 0, positive = 1).

### Tokenization
- Models used: `cardiffnlp/twitter-xlm-roberta-base-sentiment` and `sagorsarker/bangla-bert-base`
- Maximum sequence length: 128 tokens
- Dynamic padding applied through data collator

### Zero-Shot Evaluation
Models were directly applied to datasets without any task-specific training to assess inherent understanding of Bangla sentiment. For binary classification, a sample was classified as positive if the positive score exceeded the negative score, bypassing the neutral class.

### Fine-Tuning Setup
- 3 training epochs
- Learning rate: 2e-5
- Batch size: 16
- Weight decay: 0.01
- Model selection based on highest validation F1-score

### Evaluation Metrics
- Accuracy
- F1-Score
- Precision
- Recall
- Confusion Matrix Analysis

| <img src="https://github.com/ridika-2004/Comparison_of_XLM-RoBERTa_and_BanglaBERT_on_Bengali_and_Code-Mixed_Dataset/blob/main/images/fig1.png" width="100px" /> | <img src="https://github.com/ridika-2004/Comparison_of_XLM-RoBERTa_and_BanglaBERT_on_Bengali_and_Code-Mixed_Dataset/blob/main/images/fig2.png" width="100px" />  | <img src="https://github.com/ridika-2004/Comparison_of_XLM-RoBERTa_and_BanglaBERT_on_Bengali_and_Code-Mixed_Dataset/blob/main/images/fig4.png" width="100px" />  | <img src="https://github.com/ridika-2004/Comparison_of_XLM-RoBERTa_and_BanglaBERT_on_Bengali_and_Code-Mixed_Dataset/blob/main/images/fig5.png" width="100px" />  | <img src="https://github.com/ridika-2004/Comparison_of_XLM-RoBERTa_and_BanglaBERT_on_Bengali_and_Code-Mixed_Dataset/blob/main/images/fig7.png" width="100px" />  | <img src="https://github.com/ridika-2004/Comparison_of_XLM-RoBERTa_and_BanglaBERT_on_Bengali_and_Code-Mixed_Dataset/blob/main/images/fig8.png" width="100px" /> |
| :-: | :-: | :-: | :-: | :-: | :-: |

| <img src="https://github.com/ridika-2004/Comparison_of_XLM-RoBERTa_and_BanglaBERT_on_Bengali_and_Code-Mixed_Dataset/blob/main/images/fig10.png" width="100px" /> | <img src="https://github.com/ridika-2004/Comparison_of_XLM-RoBERTa_and_BanglaBERT_on_Bengali_and_Code-Mixed_Dataset/blob/main/images/fig11.png" width="100px" />  | <img src="https://github.com/ridika-2004/Comparison_of_XLM-RoBERTa_and_BanglaBERT_on_Bengali_and_Code-Mixed_Dataset/blob/main/images/fig13.jpeg" width="100px" />  | <img src="https://github.com/ridika-2004/Comparison_of_XLM-RoBERTa_and_BanglaBERT_on_Bengali_and_Code-Mixed_Dataset/blob/main/images/fig14.jpeg" width="100px" />  | <img src="https://github.com/ridika-2004/Comparison_of_XLM-RoBERTa_and_BanglaBERT_on_Bengali_and_Code-Mixed_Dataset/blob/main/images/fig16.jpeg" width="100px" />  | <img src="https://github.com/ridika-2004/Comparison_of_XLM-RoBERTa_and_BanglaBERT_on_Bengali_and_Code-Mixed_Dataset/blob/main/images/fig17.jpeg" width="100px" /> |
| :-: | :-: | :-: | :-: | :-: | :-: |

## Results

### Motamot Dataset

| Model | Accuracy | F1-Score | Recall | Precision |
|-------|----------|----------|--------|-----------|
| **BanglaBERT** | **88.66%** | **88.27%** | **88.09%** | 88.49% |
| XLM-RoBERTa | 85.69% | 87.58% | 86.20% | **89.00%** |

<table>
<tr>
<td valign="top">

**Training Epochs (BanglaBERT)**

| Epoch | Training Loss | Validation Loss | Accuracy | F1-Score |
|-------|---------------|-----------------|----------|----------|
| 1 | 56.22% | 42.00% | 80.99% | 83.25% |
| 2 | 39.69% | 39.07% | 82.27% | 84.96% |
| 3 | 32.83% | 44.34% | 81.70% | 85.26% |

</td>

<td valign="top">

**Training Epochs (XLM-RoBERTa)**

| Epoch | Training Loss | Validation Loss | Accuracy | F1-Score |
|-------|---------------|-----------------|----------|----------|
| 1 | 50.16% | 47.98% | 77.87% | 81.69% |
| 2 | 43.68% | 47.30% | 79.01% | 82.13% |
| 3 | 32.96% | 50.83% | 79.01% | 82.42% |

</td>
</tr>
</table>

### SentNoB Dataset

| Model | Accuracy | F1-Score |
|-------|----------|----------|
| **BanglaBERT** | **86.44%** | **86.41%** |
| XLM-RoBERTa | 86.00% | 86.00% |

<table>
<tr>
<td valign="top">

**Negative Class Performance**

| Metric | BanglaBERT | XLM-RoBERTa |
|--------|------------|-------------|
| F1-Score | 0.85 | 0.85 |
| Recall | 0.83 | 0.83 |
| Precision | 0.87 | 0.87 |

</td>

<td valign="top">

**Positive Class Performance**

| Metric | BanglaBERT | XLM-RoBERTa |
|--------|------------|-------------|
| F1-Score | 0.88 | 0.88 |
| Recall | 0.89 | 0.89 |
| Precision | 0.86 | 0.86 |

</td>
</tr>
</table>

**Training Epochs (XLM-RoBERTa):**
| Epoch | Training Loss | Validation Loss | Accuracy | F1-Score |
|-------|---------------|-----------------|----------|----------|
| 1 | 0.373 | 0.374 | 84.65% | 85.42% |
| 2 | 0.293 | 0.357 | 87.22% | 87.70% |
| 3 | 0.100 | 0.402 | 87.14% | 87.61% |

### BanglaBook Dataset

| Model | Accuracy | F1-Score | Recall | Precision |
|-------|----------|----------|--------|-----------|
| **XLM-RoBERTa** | **96.80%** | **98.31%** | 99.30% | **97.33%** |
| BanglaBERT | 96.61% | 98.21% | **99.46%** | 96.99% |

<table>
<tr>
<td valign="top">

**Training Epochs (XLM-RoBERTa)**

| Epoch | Training Loss | Validation Loss | Accuracy | F1-Score |
|-------|---------------|-----------------|----------|----------|
| 1 | 0.1568 | 0.1501 | 96.25% | 98.03% |
| 2 | 0.1065 | 0.1421 | 96.59% | 98.20% |
| 3 | 0.1111 | 0.1512 | 96.72% | 98.27% |

</td>

<td valign="top">

**Training Epochs (BanglaBERT)**

| Epoch | Training Loss | Validation Loss | Accuracy | F1-Score |
|-------|---------------|-----------------|----------|----------|
| 1 | 0.1409 | 0.1652 | 96.00% | 97.89% |
| 2 | 0.1106 | 0.1472 | 96.50% | 98.15% |
| 3 | 0.0964 | 0.1690 | 96.50% | 98.15% |

</td>
</tr>
</table>

<img src="https://github.com/ridika-2004/Comparison_of_XLM-RoBERTa_and_BanglaBERT_on_Bengali_and_Code-Mixed_Dataset/blob/main/images/fig3.png" width="100px" />  | <img src="https://github.com/ridika-2004/Comparison_of_XLM-RoBERTa_and_BanglaBERT_on_Bengali_and_Code-Mixed_Dataset/blob/main/images/fig6.png" width="100px" />  | <img src="https://github.com/ridika-2004/Comparison_of_XLM-RoBERTa_and_BanglaBERT_on_Bengali_and_Code-Mixed_Dataset/blob/main/images/fig9.png" width="100px" />  | <img src="https://github.com/ridika-2004/Comparison_of_XLM-RoBERTa_and_BanglaBERT_on_Bengali_and_Code-Mixed_Dataset/blob/main/images/fig12.png" width="100px" />  | <img src="https://github.com/ridika-2004/Comparison_of_XLM-RoBERTa_and_BanglaBERT_on_Bengali_and_Code-Mixed_Dataset/blob/main/images/fig15.jpeg" width="100px" /> | <img src="https://github.com/ridika-2004/Comparison_of_XLM-RoBERTa_and_BanglaBERT_on_Bengali_and_Code-Mixed_Dataset/blob/main/images/fig18.jpeg" width="100px" /> |
| :-: | :-: | :-: | :-: | :-: | :-: |

## Comparative Analysis & Discussion

### Motamot Dataset

After fine-tuning, both models achieved strong and comparable performance. BanglaBERT slightly outperformed XLM-RoBERTa across most evaluation metrics:
- **Accuracy:** BanglaBERT (88.66%) vs XLM-RoBERTa (85.69%)
- **F1-Score:** BanglaBERT (88.27%) vs XLM-RoBERTa (87.58%)
- **Recall:** BanglaBERT (88.09%) vs XLM-RoBERTa (86.20%)
- **Precision:** BanglaBERT (88.49%) vs XLM-RoBERTa (89.00%)

While precision is marginally higher for XLM-RoBERTa, BanglaBERT maintains a more balanced performance across all metrics, resulting in a slightly better overall classification capability. In zero-shot performance, BanglaBERT achieved moderate results (53-65%), while XLM-RoBERTa performed extremely poorly (3-6%). This indicates that BanglaBERT has a much stronger inherent understanding of Bangla text without task-specific training, where XLM-RoBERTa struggles significantly.

**What is the reason behind this performance?** The performance differences can be attributed primarily to pretraining strategies and language specialization. BanglaBERT is a monolingual model pretrained exclusively on large-scale Bangla corpora, allowing it to capture the syntactic and semantic nuances of the language, including morphology, idiomatic expressions, and context-specific meanings. This specialized pretraining results in strong zero-shot performance. In contrast, XLM-RoBERTa is a multilingual model trained on over 100 languages simultaneously, diluting its capacity to represent any single language and leading to poor zero-shot performance on Bangla-specific sentiment tasks.

### SentNoB Dataset

After fine-tuning, both models achieved strong and highly comparable performance. Unlike typical expectations, XLM-RoBERTa slightly outperformed BanglaBERT in terms of overall generalization:
- **Accuracy:** BanglaBERT (86.44%) vs XLM-RoBERTa (86.00%)
- **F1-Score:** BanglaBERT (86.41%) vs XLM-RoBERTa (86.00%)
- **Misclassified Samples:** BanglaBERT (164) vs XLM-RoBERTa (151)
- **False Positives:** BanglaBERT (96) vs XLM-RoBERTa (83)
- **False Negatives:** Both models (68)

Although BanglaBERT shows slightly higher numerical accuracy and F1-score, XLM-RoBERTa produces fewer total errors and lower false positive rates, indicating better robustness in classification. In zero-shot evaluation, XLM-RoBERTa performed very poorly with a large number of misclassifications, highlighting that fine-tuning is essential for multilingual models when dealing with noisy, low-resource datasets like SentNoB.

**What does the confusion matrix reveal?** BanglaBERT shows slightly higher false positives (96) and maintains balanced classification but tends to over-predict the positive class. XLM-RoBERTa demonstrates lower false positives (83) and more conservative, precise predictions, resulting in overall fewer misclassifications. This suggests XLM-RoBERTa is more precise, while BanglaBERT is slightly more aggressive in classification. From the convergence graphs, BanglaBERT exhibits stronger overfitting as its validation loss increases more noticeably in later epochs, while XLM-RoBERTa shows comparatively better generalization stability.

### BanglaBook Dataset

After fine-tuning, both models achieved strong and highly comparable performance. XLM-RoBERTa slightly outperformed BanglaBERT across most evaluation metrics:
- **Accuracy:** XLM-RoBERTa (96.80%) vs BanglaBERT (96.61%)
- **F1-Score:** XLM-RoBERTa (98.31%) vs BanglaBERT (98.21%)
- **Recall:** BanglaBERT (99.46%) vs XLM-RoBERTa (99.30%)
- **Precision:** XLM-RoBERTa (97.33%) vs BanglaBERT (96.99%)

While BanglaBERT achieves slightly higher recall on the Positive class, XLM-RoBERTa maintains a more balanced performance across all metrics. In zero-shot performance, BanglaBERT achieved moderate results (23.38% accuracy), while XLM-RoBERTa performed extremely poorly (0.51% accuracy). This indicates that BanglaBERT has a much stronger inherent understanding of Bangla text without task-specific training, where XLM-RoBERTa struggles significantly. The accuracy improvement for BanglaBERT is 73.23% and XLM-RoBERTa is 96.29%.

**What is the reason behind this performance?** The performance differences can be attributed primarily to pretraining strategies and language specialization. BanglaBERT's monolingual pretraining allows it to capture Bangla-specific nuances with high fidelity, enabling reasonable classification even without fine-tuning and faster adaptation requiring fewer training epochs. XLM-RoBERTa's multilingual pretraining dilutes its capacity for any single language, leading to poor zero-shot performance. However, its exposure to diverse linguistic patterns provides an advantage for book review classification, helping it generalize better across different writing styles, including Romanized Bangla (4.46% of the test set). This cross-lingual transfer capability explains why XLM-RoBERTa slightly outperforms BanglaBERT in the fine-tuned setting despite its poor zero-shot performance.

**Error Analysis:** XLM-RoBERTa makes fewer total misclassifications (969 vs 1,027), with particular strength in identifying Negative reviews—producing 104 fewer false positives than BanglaBERT. This indicates XLM-RoBERTa is better at correctly classifying the minority Negative class. Conversely, BanglaBERT demonstrates superior performance on Positive reviews, producing 46 fewer false negatives, making it slightly better at capturing positive sentiment.


## Summary of Model Performance

| Dataset | Model | Accuracy | F1-Score | Best Epoch |
|---------|-------|----------|----------|------------|
| **Motamot** | BanglaBERT | 88.66% | 88.27% | 2 |
| | XLM-RoBERTa | 85.69% | 87.58% | 2 |
| **SentNoB** | BanglaBERT | 86.44% | 86.41% | 2 |
| | XLM-RoBERTa | 86.00% | 86.00% | 2 |
| **BanglaBook** | BanglaBERT | 96.61% | 98.21% | 2 |
| | XLM-RoBERTa | 96.80% | 98.31% | 3 |


## Key Findings

1. **Zero-Shot Performance:** BanglaBERT consistently outperforms XLM-RoBERTa in zero-shot settings across all datasets, demonstrating stronger inherent understanding of Bangla text. BanglaBERT achieved moderate results (23-65%), while XLM-RoBERTa performed extremely poorly (0.5-6%).

2. **Fine-Tuning Effectiveness:** Both models show significant improvement after fine-tuning. XLM-RoBERTa shows the most dramatic improvement (up to +96.29%), as it starts from a much weaker baseline.

3. **Domain Adaptation:** Performance varies by domain:
   - **Motamot (Political):** BanglaBERT excels (88.66% accuracy)
   - **SentNoB (Social Media):** Comparable performance, with XLM-RoBERTa showing better robustness
   - **BanglaBook (Book Reviews):** XLM-RoBERTa marginally outperforms

4. **Convergence Behavior:** BanglaBERT converges faster, achieving peak performance at epoch 2 across all datasets. XLM-RoBERTa requires more training (epoch 2-3) to reach optimal performance.

5. **Error Patterns:** BanglaBERT tends to have more false positives (over-predicts positive sentiment), while XLM-RoBERTa shows more conservative predictions with fewer total errors.

6. **Multilingual Advantage:** XLM-RoBERTa's exposure to diverse linguistic patterns benefits tasks with code-mixed or Romanized Bangla text, helping it achieve competitive or slightly better results after sufficient fine-tuning.


## Conclusion

This study demonstrates that both BanglaBERT and XLM-RoBERTa are effective for sentiment analysis on Bangla datasets after fine-tuning, achieving >85% accuracy across all evaluated datasets. BanglaBERT exhibits superior zero-shot capabilities and faster convergence due to its language-specific pretraining. XLM-RoBERTa requires more extensive fine-tuning but can achieve competitive or slightly better results on certain domains, particularly those with code-mixed or diverse writing styles.

**Key Recommendations:**
- For applications requiring strong zero-shot performance or rapid deployment with limited training data, BanglaBERT is the preferred choice.
- For tasks involving code-mixed or informal Bangla text where sufficient labeled data is available, XLM-RoBERTa can achieve comparable results with slightly better robustness.
- Ensemble methods combining both models could potentially achieve even higher performance by leveraging their complementary strengths.

