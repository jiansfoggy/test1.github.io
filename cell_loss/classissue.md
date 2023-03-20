---
sort: 1
---

# Why the I-CONECT dataset is hard?

Inter-class and intra-class imbalanced problems usually prevent ML model from predicting well. 
In the authors explained that inter-class imbalanced problem occurs when the number of 
samples in some classes is much larger than those in other classes, which causes the misclassification of rare class examples. 
The intra-class imbalanced dataset means that a class consists of several sub-concepts or sub-clusters. 
Moreover, at least one of the concepts or clusters is represented by significantly less number of samples than the 
others. 
The number of features from each sub-concept are unequal, which weakens the performance of classifier.

Focal loss is powerful to equalize inter-class imbalanced datasets. 
Moreover, classes with more features are easier to detect than those with less features. 
This is also called Hard-Easy sample problem. 
To address intra-class imbalanced issue, researchers have proposed methods such as feature selection, resampling, and 
designing loss function. 
For example, EPIMTS (early prediction on imbalanced multivariate time series) fused feature selection and resampling, 
which calls MUDSG to resample based on the extracted core shapelets. 
Liu _et al_. utilized soft hard example mining (SHEM) to re-balance the error density distribution. 
To achieve intra-class balancing, they assigned instance-wise sampling probabilities according to the prediction of the 
current ensemble model $$F_{t-1}(\cdot)$$. 
Other works focus on upgrading loss function. 
They proposed Discriminant Distribution-Agnostic loss (DDA loss), Weighted Center Loss (WCL), Deep Attentive Center Loss 
(DACL), and Quadruplet loss. 
These loss function are tightly related to the center loss. 
The goal of these methods is to achieve intra-class compactness and inter-class separation. 
The AD-CORRE loss presented in aims to handle inter- and intra-class imbalanced issues, but it focuses on addressing 
problem by digging the correlation between embeddings in the mini-batch level. 
Then, it embeds the influence of whole training samples into batches incrementally instead of directly. 
This has less computational cost.

In the I-CONECT dataset, the number of samples with MCI is apparently more than that with NC. 
Thus, subjects labeled in MCI are easy samples, while those labeled in NC are hard ones. 
To emphasize and increase the weight of NC, we apply Focal Loss to address the Hard-Easy sample problem. 

Within each class, the number of frames from each video are unequal. 
In the I-CONECT videos, the interviewees with MCI may behave normal cognitive sometime or active abnormal in one second. 
The proportion of normal and abnormal acting parts is imbalanced and skewed too. 
For them, the normal acting parts are counted as positive samples, while the abnormal ones are negative samples. 
For subjects with NC, the definition of positive and negative samples is reverse. 
It is very important to draw a clear boundary between positive and negative sample instead of making them compact, even 
if classifying the normal sequence as NC decreases the prediction accuracy of subjects with MCI. 
In general, I-CONECT dataset has one inter-class imbalanced problem and two intra-class imbalanced problems. 
Based on the above discussion, we aim to achieve both inter- and intra-class separation, which is different from the 
target of the aforementioned loss functions such as DDA, WCL, and DACL. 
To avoid suboptimal performance, after comprehensive thought, we are inclined to use the Adaptive Correlation (AD-CORRE) 
loss to solve the Positive-Negative sample problem.