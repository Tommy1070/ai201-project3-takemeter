# TakeMeter

## Overview

TakeMeter is a text classification system built for the r/soccer community. The goal of the project is to classify soccer comments into one of four categories:

* analysis
* hot_take
* reaction
* question

The project compares a zero-shot large language model baseline using Groq against a fine-tuned DistilBERT model.

---

## Community

I selected the r/soccer community because it contains a wide variety of discussions, ranging from emotional reactions and controversial opinions to tactical analysis and questions. This diversity makes it a suitable environment for multi-class text classification.

---

## Label Definitions

### Analysis

Posts containing reasoning, statistics, tactical observations, or evidence.

Example:

> Arsenal struggled because their midfield could not progress the ball effectively.

### Hot Take

Strong opinions expressed confidently with little or no supporting evidence.

Example:

> Haaland is overrated.

### Reaction

Immediate emotional responses to events.

Example:

> WHAT A GOAL!

### Question

Posts seeking information or clarification.

Example:

> Why was the penalty overturned?

---

## Dataset Collection

Examples were collected and generated to resemble realistic r/soccer discussions. The dataset contains 252 examples distributed across four classes.

### Label Distribution

* Reaction: 66
* Hot Take: 66
* Analysis: 60
* Question: 60

---

## Baseline Model

A zero-shot classifier was implemented using Groq.

### Baseline Accuracy

**94.7%**

### Baseline Metrics

| Label    | Precision | Recall |   F1 |
| -------- | --------: | -----: | ---: |
| Analysis |      1.00 |   1.00 | 1.00 |
| Hot Take |      0.90 |   0.90 | 0.90 |
| Reaction |      0.90 |   0.90 | 0.90 |
| Question |      1.00 |   1.00 | 1.00 |

---

## Fine-Tuned Model

DistilBERT was fine-tuned on the dataset.

### Fine-Tuned Accuracy

**81.6%**

### Fine-Tuned Metrics

| Label    | Precision | Recall |   F1 |
| -------- | --------: | -----: | ---: |
| Analysis |      0.89 |   0.89 | 0.89 |
| Hot Take |      0.62 |   1.00 | 0.77 |
| Reaction |      1.00 |   0.40 | 0.57 |
| Question |      1.00 |   1.00 | 1.00 |

---

## Results Comparison

| Model                   | Accuracy |
| ----------------------- | -------: |
| Zero-shot Groq Baseline |    94.7% |
| Fine-Tuned DistilBERT   |    81.6% |

Fine-tuning resulted in a regression of approximately 13.2%.

---

## Error Analysis

The model struggled most with reaction posts. Emotional comments often overlap with hot takes, making them difficult to distinguish. Reaction achieved the lowest F1-score (0.57), indicating that many reaction comments were classified into other categories.

---

## Reflection

Although I expected the fine-tuned DistilBERT model to outperform the zero-shot baseline, the Groq baseline achieved higher accuracy (94.7%) than the fine-tuned model (81.6%). This suggests that the relatively small dataset limited the ability of DistilBERT to learn subtle distinctions between classes. Powerful large language models can perform extremely well on this task without task-specific training.

---

## AI Usage

AI tools were used to:

* Generate and refine example comments.
* Stress-test label definitions.
* Assist with debugging and troubleshooting.
* Analyze model performance and failure cases.

All labels and final decisions were manually reviewed.

---

## Files

* `data/soccer_comments.csv`
* `planning.md`
* `evaluation_results.json`
* `confusion_matrix.png`
* `README.md`

