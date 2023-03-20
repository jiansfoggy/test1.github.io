---
sort: 5
---

# HP-Loss

Finally, the follow equation shows that the HP Loss is the sum of Focal Loss and AD-CORRE (FD). 

$$ \begin{equation}
HP\ Loss = FL(p_{mci})+\lambda*AD-CORRE(FD) \label{eq:HPLoss}
\end{equation} $$

where $$\lambda=0.5$$ follows the pattern of AD-CORRE Loss.

# Contribution on the Loss Function

- We develop the HP loss by combining Focal loss and AD-CORRE(FD). 

```note
The HP loss addresses the inter- and intra-class imbalanced issues and helps the model pay attention on classes with 
less samples and subjects with short video length.
```