# TakeMeter Project Planning

## Community

I selected the r/soccer Reddit community because it contains a variety of discussion styles ranging from detailed tactical analysis to emotional reactions and opinion-based hot takes. This variety makes it well suited for a discourse classification task.

## Labels

### Analysis

Posts that support claims using evidence, statistics, tactical reasoning, or historical comparisons.

Examples:

* Manchester City generated more chances because their midfield overloaded the left side.
* Salah's expected goals have declined over the past three seasons.

### Hot Take

Strong opinions with little or no supporting evidence.

Examples:

* Haaland is overrated.
* Arsenal will never win another Premier League title.

### Reaction

Emotional responses to events with little reasoning.

Examples:

* WHAT A GOAL!
* I can't believe they bottled that lead!

## Hard Edge Cases

Some posts combine opinions with evidence.

Example:

"Player X is overrated because he only scored 3 goals this season."

Decision Rule:

If evidence is used to construct a reasoned argument, classify as Analysis.

If evidence is mainly used to support a bold opinion, classify as Hot Take.

## Data Collection Plan

I will collect and label at least 200 comments from r/soccer. I will attempt to maintain a balanced distribution across all labels.

If one label becomes underrepresented, I will collect additional examples for that label until the dataset is reasonably balanced.

## Evaluation Metrics

* Accuracy
* Precision
* Recall
* F1 Score
* Confusion Matrix

Accuracy measures overall performance.

Precision measures how often predictions for a label are correct.

Recall measures how many true examples of a label are identified.

F1 Score balances precision and recall.

The confusion matrix helps identify which labels are commonly confused.

## Definition of Success

The classifier will be considered successful if it achieves:

* Accuracy of at least 70%
* F1 Score of at least 0.65 for each label

These thresholds would indicate the model can meaningfully distinguish between different discussion styles within the community.

## AI Tool Plan

### Label Stress Testing

I will use ChatGPT to generate ambiguous examples that sit between labels to test whether my definitions are clear and consistent.

### Annotation Assistance

I may use ChatGPT to suggest labels for examples, but I will manually review every example before including it in the dataset.

### Failure Analysis

After evaluation, I will use ChatGPT to help identify common patterns among incorrect predictions and verify those patterns myself.
