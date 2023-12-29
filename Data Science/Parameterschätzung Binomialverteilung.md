
### Momentenschätzer $\hat \theta$

$$\begin{align*}
    E(X_1) &\overset{!}{=} \overline{x}\\
    N \theta &\overset{!}{=} \overline{x} & | \; Erwartungswert \; Binomialverteilung\\
    \hat{\theta} &\overset{!}{=} \dfrac{\overline{x}}{N}
\end{align*}$$

#### ML-Schätzer
$$
\begin{align*}
    Likelihood:\\
    \forall \underline x \in \{0,1,...,N\}^M: p_{\underline{X}|\Theta}(\underline{x}|\theta) &=\prod^M_{n=1}p_{X_n|\Theta}(x_n|\theta)\\
    &=\prod^M_{n=1} \left( \begin{array}{llll}
	N\\
	x_n\\
	\end{array} \right) \theta^{x_n}(1-\theta)^{N-x_n}\\
\end{align*}$$
$$
\begin{align*}
Loglikelihood:\\
 \forall \underline x \in \{0,1,...,N\}^M: \ln p_{\underline{X}|\Theta}(\underline{x}|\theta) &=\ln \prod^M_{n=1} \left( \begin{array}{llll}
	N\\
	x_n\\
	\end{array} \right) \theta^{x_n}(1-\theta)^{N-x_n}&&|Logarithmusgesetz: \; \ln ab = \ln a + \ln b \\
	&=\sum_{n=1}^M \left(\ln\left( \begin{array}{llll}
	N\\
	x_n\\
	\end{array} \right) +\ln\theta^{x_n} + \ln(1-\theta)^{N-x_n}\right) && |Linearität\ Summen\\
	&= \sum_{n=1}^M \ln\left( \begin{array}{llll}
	N\\
	x_n\\
	\end{array} \right) +\sum_{n=1}^M\ln\theta^{x_n} + \sum_{n=1}^M\ln(1-\theta)^{N-x_n}&& |Logarithmusgesetz: \ln a^b = b \cdot \ln a \\
	&= \sum_{n=1}^M \ln\left( \begin{array}{llll}
	N\\
	x_n\\
	\end{array} \right) +\sum_{n=1}^Mx_n\ln\theta + \sum_{n=1}^M(N-x_n)\ln(1-\theta) && | \overline x = \dfrac 1 N\sum_{n=1}^Nx_n \Leftrightarrow N\overline x=\sum_{n=1}^Nx_n\\
	&=\sum_{n=1}^M \ln\left( \begin{array}{llll}
	N\\
	x_n\\
	\end{array} \right) + M \overline x \ln\theta+ M(N- \overline x)\ln(1-\theta)
\end{align*}$$
$$
\begin{align*}
Loglikelihood\ ableiten:\\
\dfrac{d\ln p_{\underline{X}|\Theta}(\underline{x}|\theta)}{d\theta} &=\dfrac{ M \overline x }{\theta}+ \dfrac{M(N- \overline x)}{(1-\theta)} && |\dfrac{d}{dy}ln(y) = \dfrac{1}{y}\\
0&\overset{!}{=}\dfrac{ M \overline x }{\theta}+ \dfrac{M(N- \overline x)}{(1-\theta)}&& | gem.\ Nenner\\
0&=\dfrac{M \overline x(1-\theta)+(MN-M\overline x)\theta}{\theta(1-\theta)} |\cdot \theta(1-\theta)\\
0&=M\overline x - M\overline x\theta+ MN \theta-M\overline x \theta && |M \ ausklammern\\
0&=M(\overline x-\overline x \theta + N\theta-\overline x \theta) &&|: M\\
0&=\overline x-\overline x \theta + N\theta-\overline x \theta && |+(\overline x \theta + N\theta-\overline x \theta)\\
\overline x \theta + N\theta-\overline x \theta &= \overline x\\
N\theta&= \overline x\\
\hat \theta &= \dfrac{\overline x}{N}
\end{align*}$$

#### Posterior

Wichtige Regel: $\prod_{n=1}^N \theta^{x_n}$ = $\theta^{\sum_{n=1}^Nx_n}$

 
