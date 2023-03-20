---
sort: 3
---

# AD-CORRE(FD) Loss 1 -- Four Horsemen

Before displaying the equation of AD-CORRE(FD), we start from the four key elements of AD-CORRE(FD).
They are Variance Eraser (Beta Matrix $$\beta_{n\times n}$$), Attention Map Matrix ($$\Omega_{n\times n}$$),
Harmony Matrix ($$\Phi_{n\times n}$$), and Correlation Matrix (CORM).

## Variance Eraser, Beta Matrix $$\beta_{n\times n}$$

---

AD-CORRE(FD) emphasizes the correlation between embedding features instead of the variance of each embedding feature. 
Thus, as equation shows, AD-CORRE(FD) defines the $$\beta$$ matrix $$\beta_{n\times n}$$ as the difference of matrix of 
ones $$1_{n\times n}$$ and the identity matrix $$I_{n\times n}$$, where $$n$$ is the size of minibatch.

$$ \begin{equation}
\beta_{n\times n}=1_{n\times n}-I_{n\times n} \label{eq:beta} \\
\end{equation} $$

$$\beta_{n\times n}$$ sets the diagonal of the correlation matrix to zero and remove the influence of variance.

## Attention Map Matrix, $$\Omega_{n\times n}$$

---

Let $$l_{i}$$ be the label of $$i^{th}$$ sample in the minibatch, $$i\in [0,n]$$. The corresponding confusion 
matrix is CONFM$$_{n\times n}$$. CONFM$$[l_{i},l_{i}]$$ is the value at the cell $$[l_{i},l_{i}]$$.

Subsequently, AD-CORRE(FD) defines $$\omega(l_{i})$$ as that $$1$$ subtracts CONFM$$[l_{i},l_{i}]$$ and pluses small 
positive number $$\epsilon$$. It is summarized as follow.

$$ \begin{equation}
\omega(l_{i})=1-CONFM[l_{i},l_{i}]+\epsilon \label{eq:wgt}
\end{equation} $$

From $$\omega(l_{i})$$, AD-CORRE(FD) defines the attention map matrix $$\Omega_{n\times n}$$, which consists of the 
sum of $$\omega(l_{i})$$ of sample `i` and that of sample `j`.

$$ \begin{equation}
\Omega_{n\times n}=\begin{bmatrix}\omega(l_{1})+\omega(l_{1}) & \dotsm & \omega(l_{1})+\omega(l_{n}) \\ \vdots & \ddots & \vdots \\ \omega(l_{n})+\omega(l_{1}) & \dotsm & \omega(l_{n})+\omega(l_{n}) \\ \end{bmatrix} \label{eq:Omega}
\end{equation} $$

$$\Omega_{n\times n}$$ is also the weight factor of AD-CORRE(FD).

## Harmony Matrix, $$\Phi_{n\times n}$$

---

AD-CORRE(FD) defines the sign function as follow.

$$ \begin{equation} 
npSign(l_{i},l_{j}) = \begin{cases} +1 & if\ l_{i}=l_{j}\\ -1 & otherwise \end{cases} \label{eq:sign} 
\end{equation} $$

It is +1 if the selected sample pair, $$l_{i}$$ and $$l_{j}$$, has identical label. 
Otherwise, npSign$$(l_{i},l_{j})=-1$$.

Given that minibatch has size `n`, AD-CORRE(FD) thereby defines the corresponding matrix $$\Phi_{n\times n}$$ in the 
following equation.

$$ \begin{equation}
\Phi_{n\times n}=\begin{bmatrix} npSign(l_{1},l_{1}) & \dotsm & npSign(l_{1},l_{n}) \\ \vdots & \ddots & \vdots \\ npSign(l_{n},l_{1}) & \dotsm & npSign(l_{n},l_{n}) \end{bmatrix} \label{eq:Phi}
\end{equation} $$

where $$\Phi[i,j]$$ is the value at the cell $$[i,j]$$. $$\Phi_{n\times n}$$ reflects the labels' similarity and harmony 
of each sample pair. 
To be shorter, we rename $$\Phi_{n\times n}$$ as the harmony matrix.

## Correlation Matrix, CORM

---

Starting from covariance coefficient, $$COR(V_{i}, V_{j})$$, between two embedding features, $$V_{i}$$ and $$V_{j}$$,
($$i,j\in[0,n]$$), AD-CORRE(FD) defines the correlation matrix of all embedding features. 
For example, CORM$$_{ef}$$ is the correlation matrix of $$ef^{th}$$ embedding feature. 
CORM$$_{ef}[i,j]$$, as the value at the cell $$[i,j]$$, means $$COR(V_{i}, V_{j})$$.
The follows are related equations.

$$ \begin{align}
COR(V_{i}, V_{j})&=\frac{\displaystyle\sum\limits_{a=1}^d (V_{ia}-\bar{V_{i}})(V_{ja}-\bar{V_{j}})}{\sqrt{(\displaystyle\sum\limits_{a=1}^d V_{ia}-\bar{V_{i}})(\displaystyle\sum\limits_{a=1}^d V_{jk}-\bar{V_{j}})}} \label{eq:COR} \\
CORM_{n\times n}&=\begin{bmatrix} COR(V_{1},V_{1}) & \dotsm & COR(V_{1},V_{n}) \\ \vdots & \ddots & \vdots \\ COR(V_{n},V_{1}) & \dotsm & COR(V_{n},V_{n}) \end{bmatrix} \label{eq:CORM}
\end{align} $$

where `d` is the dimension size of each embedding feature $$V_{i}$$.

Next page shows how the above four elements compose the AD-CORRE(FD).