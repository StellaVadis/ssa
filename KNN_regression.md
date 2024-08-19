# Model Structure 

dwq


$$
\begin{align}
d^{[i]} &= \left(x - x^{[i]}\right)^2, \quad i = 1,2,\cdots, n \\
d &= \left[d^{[1]}, d^{[2]}, \cdots, d^{[m]}\right]^T \\
\delta &= \text{rank}_3(d) \\
M(x) &= \frac{1}{2} \\
\end{align}
$$


dqw
where:
\begin{itemize}
    \item \( d \) is the distance between \( x \) and \( X \)
    \item \(\delta\) is the distance threshold based on the 3rd ranked distance
    \item \(\mathbb{I}(\cdot)\) is the indicator function, which is 1 if the condition inside is true, and 0 otherwise
    \item \( Y^{[i]} \) are the response values corresponding to the \( i \)-th nearest neighbors
\end{itemize}

# Training Algorithm
This model does not contain parameters to be trained.
