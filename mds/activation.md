# Activation

## Def

- **ReLU**

> - $\textrm{ReLU}(x) = \left \{ \begin{array}{l} x & x \ge 0 \\ 0 & x \lt 0 \end{array} \right. = \max(x,0) = x^+$
>   - $\textrm{ReLU}$ stands for _Rectified Linear Unit_
>   - _pros_
>     - $\textrm{ReLU}$ is a very common activation function, because it has been shown empirically that it allows faster training of deep neural architectures on large and complex datasets
>     - it is very fast to compute
>   - _cons_
>     - $\textrm{ReLU}$ is not differentiable at $0$, although it can be differentiated anywhere else, so the derivative on $0$ is usually arbitrarily chosen to be $0$ or $1$
>     - differently from other activation function, the output of $\textrm{ReLU}$ is unbounded

## Oss

- **Hp**
    - $a \in \mathbb{R}$
- **Th**
    - $\textrm{ReLU}(a \cdot x)= a \cdot \textrm{ReLU}(x)$
- **Dim**
    - $\textrm{ReLu}(a \cdot x) = \max(a \cdot x, 0) = a \cdot \max(x, 0) = a \cdot \textrm{ReLU}(x)$

## Def

- **Softplus**

> - $\textrm{softplus}(x)= \ln(1 + e^x)$
>   - it is a smoother version of $\textrm{ReLU}$

## Def

- **Sigmoid**

> - $\sigma(x):= \dfrac{1}{1 + e^{-x}}$

## Oss

- **Th**
    - $\sigma(x) = 1 - \sigma(-x)$
- **Dim**
    - $\sigma(x) = \dfrac{1}{1 + e^{-x}} = \dfrac{1 \cdot e^x}{(1 + e^{-x})\cdot e^{x}}=\dfrac{e^x}{e^x  + 1} = \dfrac{1 - e^x + 1}{e^x + 1}=1 - \dfrac{1}{1 + e^x}=1 - \sigma(-x)$

## Def

- **Sine**

> - $\sin(x)$

## Def

- **Hyperbolic tangent**

> - $\tanh(x) = \dfrac{e^x - e^{-x}}{e^x + e^{-x}}$
>   - because of this alternative definition of the hyperbolic tangent, it's possible to easily evaluate the derivative of $\tanh$

## Oss

- **Th**
    - $\dfrac{d}{dx}\tanh(x) = \textrm{sech}^2(x)$
- **Dim**
    - $\dfrac{d}{dx}\tanh(x)=\dfrac{d}{dx}\left(\dfrac{e^x - e^{-x}}{e^x + e^{-x}}\right)=\dfrac{(e^x + e^{-x})\cdot\dfrac{d}{dx}(e^x-e^{-x})-(e^x-e^{-x})\cdot\dfrac{d}{dx}(e^x + e^{-x})}{(e^x +e^{-x})^2}=\dfrac{(e^x + e^{-x})\cdot (e^x+e^{-x})-(e^x-e^{-x})\cdot(e^x-e^{-x})}{(e^x+e^{-x})^2}=\dfrac{(e^{2x}+1+1+e^{-2x})-(e^{2x}-1-1+e^{-2x})}{(e^x+e^{-x})^2}=\dfrac{4}{(e^x+e^{-x})^2}=\left(\dfrac{2}{e^x+e^{-x}}\right)^2=\textrm{sech}^2(x)$

## Def

- **Softmax**

> - $x =\left(\begin{array}{c}x_1 \\ \vdots \\ x_n\end{array}\right)$
> - $\textrm{softmax}(x) = \dfrac{1}{\displaystyle{\sum_{i =1}^n{e^{x_i}}}}\left( \begin{array}{c} e^{x_1} \\ \vdots \\ e^{x_n} \end{array}\right)$
>   - $\textrm{softmax}$ is useful to turn a vector into a probability distribution
>   - note that, to turn an array into a probability distribution it is only needed to divide each coefficient by the sum of the terms, but this approach assumes every coefficient of the vector is positive, otherwise the sum of the terms doesn't make sense
>   - thus, $\forall i \in [1, n] \quad e^{x_i}$ trasforms every $x_i$ into a positive value, but it preserves the distinction between negative and positive values; in particular, negative values are going to be less than $1$, while positive values are going to be bigger than $1$
>   - this also implies that a function such that $x^2$ won't work, because it is not an injective funciton, and does not preserve the information about the sign of the original number
>   - note that, when considering $\textrm{softmax}$ the operations performed on one single value $x_i$ of the input vector $x$, the function is differentiable, thus optimizable through backpropagation

## Oss

- **Hp**
    - $x =\left(\begin{array}{c}x_1 \\ \vdots \\ x_n\end{array}\right)$
- **Th**
    - $\textrm{softmax}(x + \lambda) = \textrm{softmax}(x)$
- **Dim**
    - $\textrm{softmax}(x + \lambda) = \dfrac{1}{\displaystyle{\sum_{i =1}^n{e^{x_i + \lambda}}}}\left( \begin{array}{c} e^{x_1 + \lambda} \\ \vdots \\ e^{x_n + \lambda} \end{array}\right) = \dfrac{1}{\displaystyle{\sum_{i =1}^n{(e^{x_i}\cdot e^ \lambda)}}}\left( \begin{array}{c} e^{x_1}\cdot e^\lambda \\ \vdots \\ e^{x_n}\cdot e^\lambda \end{array}\right)= \dfrac{e^\lambda}{e^\lambda \cdot \displaystyle{\sum_{i =1}^n{e^{x_i}x}}}\left( \begin{array}{c} e^{x_1}\\ \vdots \\ e^{x_n} \end{array}\right) = \dfrac{1}{\displaystyle{\sum_{i =1}^n{e^{x_i}}}}\left( \begin{array}{c} e^{x_1} \\ \vdots \\ e^{x_n} \end{array}\right) = \textrm{softmax}(x)$

