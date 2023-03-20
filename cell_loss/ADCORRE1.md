---
sort: 3
---

# AD-CORRE (FD) Loss 1 -- Symbols

Let $$k$$ be the number of embedding features, and $$n$$ is class number. 
Let $$\beta\in \mathbb{R}^{n\times n}$$, it represents the difference between matrix of ones $$1_{n\times n}$$ and 
identity matrix $$I_{n\times n}$$. 
$$\Omega_{n\times n}$$ represents the attention map for FD component. 
$$\Omega[i,j]$$ is the sum of two weights $$\omega(l_{i})$$ and $$\omega(l_{j})$$, where $$l_{i}$$ is the label of 
$$i^{th}$$ samples.

$$ \begin{align}
\beta_{n\times n}&=1_{n\times n}-I_{n\times n} \label{eq:beta} \\
\Omega_{n\times n}&=\begin{bmatrix}\omega(l_{1})+\omega(l_{1}) & \dotsm & \omega(l_{1})+\omega(l_{n}) \\ \vdots & \ddots & \vdots \\ \omega(l_{n})+\omega(l_{1}) & \dotsm & \omega(l_{n})+\omega(l_{n}) \\ \end{bmatrix} \label{eq:Omega}
\end{align} $$

Here, $$\omega(l_{i})$$ equals that $$1$$ subtracts the value at the $$[l_{i},l_{i}]$$ point of the training confusion 
matrix CONFM$$_{n\times n}$$ and pluses small positive number $$\epsilon$$.

$$ \begin{equation}
\omega(l_{i})=1-CONFM[l_{i},l_{i}]+\epsilon \label{eq:wgt}
\end{equation} $$

Next, $$\Phi[i,j]$$ is the value at the $$[i,j]$$ point of $$\Phi_{n\times n}$$, a matrix to show the harmony of each 
sample pair. 

$$ \begin{equation}
\Phi_{n\times n}=\begin{bmatrix} npSign(l_{1},l_{1}) & \dotsm & npSign(l_{1},l_{n}) \\ \vdots & \ddots & \vdots \\ npSign(l_{n},l_{1}) & \dotsm & npSign(l_{n},l_{n}) \end{bmatrix} \label{eq:Phi}
\end{equation} $$

where npSign$$(l_{i},l_{j})$$ is the sign function. 
It is +1 if the selected sample pair, $$l_{i}$$ and $$l_{j}$$, has identical label. 
Otherwise, npSign$$(l_{i},l_{j})=-1$$.

$$ npSign(l_{i},l_{j}) = \begin{cases} +1 & if\ l_{i}=l_{j}\\ -1 & otherwise \end{cases} \label{eq:sign} $$

Then, CORM$$_{l}$$ is the correlation matrix of $$l^{th}$$ embedding feature. CORM$$_{l}[i,j]$$, as the value at the 
cell $$[i,j]$$, means the correlation coefficient of embedding features $$V_{i}$$ and $$V_{j}$$, $$COR(V_{i}, V_{j})$$. 

$$ \begin{align}
COR(V_{i}, V_{j})&=\frac{\displaystyle\sum\limits_{k=1}^d (V_{ik}-\bar{V_{i}})(V_{jk}-\bar{V_{j}})}{\sqrt{(\displaystyle\sum\limits_{k=1}^d V_{ik}-\bar{V_{i}})(\displaystyle\sum\limits_{k=1}^d V_{jk}-\bar{V_{j}})}} \label{eq:COR} \\
CORM_{n\times n}&=\begin{bmatrix} COR(V_{1},V_{1}) & \dotsm & COR(V_{1},V_{n}) \\ \vdots & \ddots & \vdots \\ COR(V_{n},V_{1}) & \dotsm & COR(V_{n},V_{n}) \end{bmatrix} \label{eq:CORM}
\end{align} $$

where `d` is the dimension size of each embedding feature $$V_{i}$$.
