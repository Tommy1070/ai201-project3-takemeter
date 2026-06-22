# TakeMeter Planning Document

## Community

I chose the r/soccer community because it contains a large amount of discussion with varying levels of quality. Fans regularly post reactions, opinions, questions, and detailed analyses, making it a good environment for a text classification task.

These distinctions matter because community members often value thoughtful analysis differently from emotional reactions or unsupported opinions.

---

## Labels

### Analysis

Definition:
Posts that provide structured reasoning, statistics, tactical observations, or evidence to support a claim.

Examples:

- Arsenal struggled because their midfield could not progress the ball effectively.
- Barcelona generated only 0.8 xG despite dominating possession.

### Hot Take

Definition:
Strong opinions that are expressed confidently but contain little or no supporting evidence.

Examples:

- Haaland is overrated.
- Manchester United will never win another Premier League title.

### Reaction

Definition:
Immediate emotional responses to an event with little reasoning.

Examples:

- WHAT A GOAL!
- I can't believe they bottled it again.

### Question

Definition:
Posts seeking clarification or information.

Examples:

- Why was the penalty overturned?
- What formation is Inter Milan using?

---

## Hard Edge Cases

Example:

"Messi is washed because he only scores against weak teams."

This could be classified as either Analysis or Hot Take.

Decision Rule:

If the evidence is weak, cherry-picked, or mainly decorative, classify the post as Hot Take. If the reasoning is detailed and supported, classify it as Analysis.

---

## Data Collection Plan

Data source:

- r/soccer Reddit comments

Target distribution:

- Analysis: 50 examples
- Hot Take: 50 examples
- Reaction: 50 examples
- Question: 50 examples

If one class becomes underrepresented, additional examples will be collected to balance the dataset.

---

## Evaluation Metrics

Metrics:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix

Accuracy alone is insufficient because some labels may be confused more often than others. Precision, recall, and F1-score provide better insight into class-specific performance.

---

## Definition of Success

The classifier will be considered successful if:

- Overall accuracy exceeds 75%.
- Each class achieves an F1-score above 0.70.
- The fine-tuned model outperforms the zero-shot Groq baseline.

---

## AI Tool Plan

### Label Stress Testing

ChatGPT will be used to generate ambiguous examples to refine label boundaries.

### Annotation Assistance

ChatGPT may assist in pre-labeling examples, but every label will be manually reviewed.

### Failure Analysis

ChatGPT will be used to identify patterns among misclassified examples after training.