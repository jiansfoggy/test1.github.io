---
sort: 1
---

# Why the I-CONECT dataset is hard?

Simply using binary cross entropy (BCE) loss function to train the MC-ViViT is not enough to achieve good performance. 
The reason is that the I-CONECT dataset is imbalanced.

- Inter-class imbalanced problem. The distribution of MCI and NC subjects are uneven. There are more MCI subjects than NC.
- Intra-class imbalanced problem 1. Within each class, the number of frames from each video are unequal. They are in different length.
- Intra-class imbalanced problem 2. Within each video, the proportion of normal and abnormal acting parts is imbalanced and skewed.

```tip
In our study, subjects labeled in MCI are easy samples, while those labeled in NC are hard ones.
Classes with more features are easier to detect than those with less features. 
Hence, Inter-class imbalanced problem is also known as Hard-Easy sample problem.
```

```tip
In our study, the parts of showing MCI symptoms are counted as positive samples, while the normal ones are negative samples.  
For subjects with NC, the definition of positive and negative samples is reverse.  
Some subjects may not behave any symptoms of MCI, but act like NC in some video clips, which restricts MC-ViViT from 
extracting enough MCI related features. 
This is also called Positive-Negative sample problem.
```

In summary, I-CONECT dataset has one inter-class imbalanced problem and two intra-class imbalanced problems. 

```note
Inter-class and intra-class imbalanced problems usually prevent ML model from predicting well. 
The inter-class imbalanced problem occurs when the number of samples in some classes is much larger than those in other 
classes, which causes the misclassification of rare class examples. 
The intra-class imbalanced dataset means that a class consists of several sub-concepts or sub-clusters. 
Moreover, at least one of the concepts or clusters is represented by significantly less number of samples than the 
others. 
The number of features from each sub-concept are unequal, which weakens the performance of classifier.
```

# Solutions

- Inter-class imbalanced problem/Hard-Easy sample problem. The Focal loss is powerful to emphasize and increase the weight of NC.
- Intra-class imbalanced problem/Positive-Negative sample problem. The AD-CORRE(FD) loss focuses on addressing digging 
the correlation between embeddings in the mini-batch level, which benefits on drawing a clear boundary between positive 
and negative sample instead of making them compact like the other loss functions.

```note
AD-CORRE(FD) is less computationally expensive because it embeds the influence of whole training samples into batches 
incrementally instead of directly. 
```

```note
Typical methods for intra-class imbalanced issue: feature selection, resampling, and designing loss function. 
For example, EPIMTS (early prediction on imbalanced multivariate time series) fused feature selection and resampling, 
which calls MUDSG to resample based on the extracted core shapelets. Soft hard example mining (SHEM) can re-balance the 
error density distribution. SHEM assigned instance-wise sampling probabilities according to the prediction of the 
current ensemble model $$F_{t-1}(\cdot)$$.

Another direction is the variants of the center loss, such as Discriminant Distribution-Agnostic loss (DDA loss), 
Weighted Center Loss (WCL), Deep Attentive Center Loss (DACL), and Quadruplet loss. 
```

```tip
The goal of typical methods is to achieve intra-class compactness and inter-class separation. 
In our study, we aim to draw a clear boundary instead of making them compact, even 
if classifying the normal sequence as NC decreases the prediction accuracy of subjects with MCI. 
```

In general, I-CONECT dataset is hard to train. Purely utilizing cross entropy loss is far from converging the MC-ViViT
well. The Focal loss and AD-CORRE(FD) loss are powerful to address the imbalanced problem.