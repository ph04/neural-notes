# Activation

## Def

- **Softmax**

> - $\mathbb{F}$ field
> - $V$ vector space over $\mathbb{F}$
> - $v \in V \mid \left(\begin{array}{c}x_1 \\ \vdots \\ x_n\end{array}\right)$
> - $\textrm{softmax}(v) = \dfrac{1}{\displaystyle{\sum_{i =1}^n{e^{x_i}}}}\left( \begin{array}{c} e^{x_1} \\ \vdots \\ e^{x_n} \end{array}\right)$
>   - $\textrm{softmax}$ is useful to turn a vector into a probability distribution
>   - note that, to turn an array into a probability distribution it is only needed to divide each coefficient by the sum of the terms, but this approach assumes every coefficient of the vector is positive, otherwise the sum of the terms doesn't make sense
>   - thus, $\forall i \in [1, n] \quad e^{x_i}$ trasforms every $x_i$ into a positive value, but it preserves the distinction between negative and positive values; in particular, negative values are going to be less than $1$, while positive values are going to be bigger than $1$
>   - this also implies that a function such that $x^2$ won't work, because it is not an injective funciton, and does not preserve the information about the sign of the original number
>   - note that $\textrm{softmax}$ is differentiable, thus optimizable through backpropagation

## Oss

- **Hp**
    - $\mathbb{F}$ field
    - $V$ vector space over $\mathbb{F}$
    - $\lambda \in \mathbb{F}$
    - $v \in V \mid \left(\begin{array}{c}x_1 \\ \vdots \\ x_n\end{array}\right)$
- **Th**
    - $\textrm{softmax}(v + \lambda) = \textrm{softmax}(v)$
- **Dim**
    - $\textrm{softmax}(v + \lambda) = \dfrac{1}{\displaystyle{\sum_{i =1}^n{e^{x_i + \lambda}}}}\left( \begin{array}{c} e^{x_1 + \lambda} \\ \vdots \\ e^{x_n + \lambda} \end{array}\right) = \dfrac{1}{\displaystyle{\sum_{i =1}^n{(e^{x_i}\cdot e^ \lambda)}}}\left( \begin{array}{c} e^{x_1}\cdot e^\lambda \\ \vdots \\ e^{x_n}\cdot e^\lambda \end{array}\right)= \dfrac{e^\lambda}{e^\lambda \cdot \displaystyle{\sum_{i =1}^n{e^{x_i}x}}}\left( \begin{array}{c} e^{x_1}\\ \vdots \\ e^{x_n} \end{array}\right) = \dfrac{1}{\displaystyle{\sum_{i =1}^n{e^{x_i}}}}\left( \begin{array}{c} e^{x_1} \\ \vdots \\ e^{x_n} \end{array}\right) = \textrm{softmax}(v)$

