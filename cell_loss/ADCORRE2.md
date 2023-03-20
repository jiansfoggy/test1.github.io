---
sort: 4
---

# AD-CORRE(FD) Loss 2 -- All For One

After learning the four key components, let's see the main body.

In short word, AD-CORRE(FD) is a weighted mean absolute error. 

$$ \begin{equation}\label{eq:fd}
FD = \frac{1}{kn^{2}}\displaystyle\sum\limits_{l=0}^k\displaystyle\sum\limits_{i=0}^n\displaystyle\sum\limits_{j=0}^n \beta[i,j]\Omega[i,j]|\Phi[i,j]-CORM_{l}[i,j]|, 
\end{equation} $$

where $$k$$ is the class number. 
The difference between $$\Phi_{n\times n}$$ and CORM$$_{n\times n}$$ is the core of the AD-CORRE(FD) loss.

In general, AD-CORRE(FD) focuses on the correlation between the samples within the mini-batch. 
This prevents the imbalanced dataset from affecting the prediction. 

# Why does AD-CORRE(FD) suit for I-CONECT dataset?

Its intention is to ignore the frames-imbalanced issue and positive and negative sample problem, and to only focus on 
the classification task in mini-batch level. 
The intervention of AD-CORRE(FD) avoids the deeper conflict. 
In addition, AD-CORRE(FD) substantially decreases the computation complexity because it only analyzes the similarity 
between embeddings. It accumulatively collects the class distribution information from the previous batches to perfect its 
adaptive weight.
This is also the reason that AD-CORRE(FD) benefits on detecting minority samples.

```tip
Intuitively, there are two ways to address intra-class imbalance. Given a class, assigning weights for each subject 
based on the frame numbers. Or, attributing different weights to positive and negative sequences within the same video. 
Either way will stimulate more dispute and cause the problem complexity going exacerbation.
```