# Evaluations/Metrics in ML

This note is about some basic, popular metrics in ML/DS.

## ROC/PR curve
useful link: [roc and pr curves](https://machinelearningmastery.com/roc-curves-and-precision-recall-curves-for-classification-in-python/)

### ROC & AUC
True Positive Rate = True Positives / (True Positives + False Negatives)\\
False Positive Rate = False Positives / (False Positives + True Negatives)

The ROC curve is a useful tool for a few reasons:
- The curves of different models can be compared directly in general or for different thresholds.
- The area under the curve (AUC) can be used as a summary of the model skill.

### Precision-Recall curve
Precision = True Positives / (True Positives + False Positives)\\
Recall = True Positives / (True Positives + False Negatives)

## Compare
Generally, the use of ROC curves and precision-recall curves are as follows:

- ROC curves should be used when there are roughly equal numbers of observations for each class.
- Precision-Recall curves should be used when there is a moderate to large class imbalance.

The reason for this recommendation is that ROC curves present an optimistic picture of the model on datasets with a class imbalance.