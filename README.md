# TakeMeter: r/soccer Discourse Classification

## Overview

This project fine-tunes a DistilBERT text classifier to categorize discussions from the r/soccer Reddit community into three discourse categories:

* Analysis
* Hot_Take
* Reaction

The project also compares the fine-tuned model against a zero-shot baseline using Groq's Llama 3.3 70B model.

---

## Community

I selected the r/soccer Reddit community because it contains a wide variety of discussion styles, including tactical analysis, emotional reactions, and opinion-based commentary. This makes it a good environment for discourse classification.

---

## Labels

### Analysis

Posts that support claims using evidence, statistics, tactical reasoning, or historical comparisons.

Example:

> City's attacking shape relies on inverted fullbacks. Their fullbacks complete 8.2 passes in the final third per game.

### Hot_Take

Strong opinions with little or no supporting evidence.

Example:

> Haaland is overrated. Remove him and City would still dominate because their system is carrying him.

### Reaction

Emotional responses to events with little reasoning.

Example:

> WHAT A GOAL! I'M GOING ABSOLUTELY MENTAL!

---

## Dataset

* Total examples: 209
* Analysis: 63
* Hot_Take: 66
* Reaction: 80

The dataset consists of labeled soccer-related comments covering players, managers, transfers, tactics, leagues, and match events.

---

## Model

Fine-tuned model:

* DistilBERT (`distilbert-base-uncased`)
* Epochs: 3
* Batch size: 16
* Learning rate: 2e-5

No hyperparameter modifications were made from the starter notebook defaults.

---

## Results

### Fine-Tuned DistilBERT

| Metric   | Value |
| -------- | ----: |
| Accuracy | 0.844 |
| Macro F1 |  0.85 |

Per-class performance:

| Label    | Precision | Recall |   F1 |
| -------- | --------: | -----: | ---: |
| Analysis |      0.90 |   0.90 | 0.90 |
| Hot_Take |      0.69 |   0.90 | 0.78 |
| Reaction |      1.00 |   0.75 | 0.86 |

### Zero-Shot Baseline (Groq)

| Metric   | Value |
| -------- | ----: |
| Accuracy | 1.000 |

### Comparison

| Model                   | Accuracy |
| ----------------------- | -------: |
| Groq Zero-Shot Baseline |    1.000 |
| Fine-Tuned DistilBERT   |    0.844 |

The zero-shot baseline outperformed the fine-tuned DistilBERT model on the test set.

---

## Error Analysis

Example misclassifications:

### Reaction → Hot_Take

Text:

> YES YES YES! THAT'S IT! WE'RE GOING TO WIN THE LEAGUE!

The model interpreted an emotional celebration as an opinion or prediction.

### Analysis → Hot_Take

Text:

> City's attacking shape relies on inverted fullbacks. Their fullbacks complete 8.2 passes in the final third per game.

Although statistical evidence was present, the model incorrectly classified the comment as a hot take.

### Hot_Take → Analysis

Text:

> Messi has won six Ballon d'Ors because the media is biased. Ronaldo was always better.

The use of the word "because" made the model interpret the statement as analytical reasoning rather than opinion.

---

## Reflection

The fine-tuned DistilBERT model achieved 84.4% accuracy on the test set, demonstrating that it successfully learned distinctions between analysis, hot takes, and reactions.

However, the Groq zero-shot baseline achieved perfect accuracy on the same test set. One possible explanation is that the categories were highly separable and contained strong linguistic signals. Analysis comments often contained statistics and tactical language, hot takes contained strong opinions, and reactions frequently used emotional language and capitalization. These cues made classification relatively easy for a large language model without additional training.

If I continued this project, I would collect more real-world Reddit comments, increase dataset size, and create more ambiguous examples to better evaluate model generalization.
