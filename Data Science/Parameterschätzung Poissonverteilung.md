
### Momentenschätzer $\hat \lambda$

$$\begin{align*}
    E(X_1) &\overset{!}{=} \overline{x}\\
    \hat \lambda &= \overline{x} & | \; Erwartungswert \; Binomialverteilung\\
\end{align*}$$

#### ML-Schätzer
$$
\begin{align*}
    Likelihood:\\
    \forall \underline x \in \mathbb{N}^D: p_{\underline{X}|\Lambda}(\underline{x}|\lambda) &=\prod^N_{n=1}p_{X_n|\Lambda}(x_n|\lambda)\\
    &=\prod^N_{n=1} \dfrac{\lambda^{x_n}}{x_n!}e^{-\lambda}\\
\end{align*}$$
$$
\begin{align*}
Loglikelihood:\\
 \forall \underline x \in \mathbb{N}^D: \ln p_{\underline{X}|\Theta}(\underline{x}|\theta) &=\ln \prod^N_{n=1} \dfrac{\lambda^{x_n}}{x_n!}e^{-\lambda}&&|Logarithmusgesetz: \; \ln ab = \ln a + \ln b \\
	&=\sum_{n=1}^N \left(\ln \lambda^{x_n} - \ln x_n! + \ln e^{-\lambda}  \right)&& |Linearität\ Summen\\
	&= \sum_{n=1}^Mx_n \ln \lambda^{x_n}-\sum_{n=1}^N\ln x_n! +\sum_{n=1}^N\ln e^{-\lambda}&& |Logarithmusgesetz: \ln a^b = b \cdot \ln a \\
	&= \sum_{n=1}^Mx_n \ln\lambda-\sum_{n=1}^N\ln x_n! - \lambda \sum_{n=1}^N\ln e && | \overline x = \dfrac 1 N\sum_{n=1}^Nx_n \Leftrightarrow N\overline x=\sum_{n=1}^Nx_n\\
	&=N\overline x \ln \lambda-\sum_{n=1}^N\ln x_n! - \lambda N
\end{align*}$$
$$
\begin{align*}
Loglikelihood\ ableiten:\\
\dfrac{d\ln p_{\underline{X}|\Lambda}(\underline{x}|\lambda)}{d\theta} &=\dfrac{ N \overline x }{\lambda}-N\\
0&\overset{!}{=}\dfrac{ N \overline x }{\lambda}-N&& | +N\\
N&=\dfrac{N\overline x}{\lambda} && | \cdot \lambda\\
N\lambda &= N \overline x && | : N\\
\hat\lambda &= \overline x\\
\end{align*}$$

#### Posterior
 
