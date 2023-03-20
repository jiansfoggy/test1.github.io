---
sort: 2
---

# Focal Loss

Focal Loss solves the imbalance of the Hard-Easy samples by generating the weight based on sample numbers. 
It derives from $$\alpha$$-balanced Cross Entropy loss. 
Then, adding a modulating factor $$(1-p_{mci})^{\gamma}$$ to the cross entropy loss, with tunable focusing parameter 
$$\gamma>0$$, makes the final Focal Loss. 
The above can be summarized as the follow equation.

$$ FL(p_{mci}) = -\alpha_{mci}(1-p_{mci})^{\gamma}log(p_{mci}) \label{eq:focaloss} $$

where $$\alpha$$ is a weighting factor. 
$$\alpha\in[0,1]$$ for class MCI and $$1-\alpha$$ for class NC. 
$$p_{mci}$$ represents the probability of the frame sequence attributing to MCI. 

$$ p_{mci} = \begin{cases} p & if\ y=MCI\\ 1-p & otherwise \end{cases} $$

where `p` is the model's predict score, `y` is the predicted label.
