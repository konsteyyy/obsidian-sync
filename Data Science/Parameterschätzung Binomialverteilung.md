
### Momentenschätzer $\hat \theta$

$$\begin{align*}
    E(X_1) &\overset{!}{=} \overline{x}\\
    N \theta &\overset{!}{=} \overline{x} & | \; Erwartungswert \; Binomialverteilung\\
    \hat{\theta} &\overset{!}{=} \dfrac{\overline{x}}{N}
\end{align*}$$
---------------------

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

------------------------

#### MAP-Schätzer
###### Posterior

Wichtige Regel: $\prod\limits_{n=1}^N \theta^{x_n}=\theta^{\sum_{n=1}^Nx_n}$

##### Prior [[Betaverteilung]]:
$p_\Theta(\theta)=B^{-1}(\alpha,\beta)\theta^{\alpha-1}(1-\theta)^{\beta-1}$

$$
\begin{align*}
gem. Wahrscheinlichkeitsdichten: \\
p_{\underline X,\Theta}(\underline x,\theta)=p_{\underline X|\Theta}(\underline x|\theta) \cdot p_\Theta(\theta)
\end{align*}
$$

$$
\begin{align*}
	Randwahrscheinlichkeiten: \\
	p_{\underline X}(\underline x)&=\int^1_0 p_{\underline X,\Theta}(\underline x,\theta)\\
	&=\int^1_0 \prod^M_{n=1}\left( \begin{array}{llll}
	N\\
	x_n\\
	\end{array} \right) \theta^{x_n}(1-\theta)^{N-x_n}\cdot B^{-1}(\alpha,\beta)\theta^{\alpha-1}(1-\theta)^{\beta-1}d\theta &&|\prod_{n=1}^N \theta^{x_n}=\theta^{\sum_{n=1}^Nx_n}\\
	&= \prod^M_{n=1}\left( \begin{array}{llll}
	N\\
	x_n\\
	\end{array} \right) \int^1_0 \dfrac{\theta^{\alpha +M \overline x-1}(1-\theta)^{\beta+N-M \overline x-1}}{B(\alpha,\beta)}d\theta\\
	&= \prod^M_{n=1}\left( \begin{array}{llll}
	N\\
	x_n\\
	\end{array} \right)B^{-1}(\alpha,\beta) \int^1_0 \theta^{\alpha +M \overline x-1}(1-\theta)^{\beta+N-M \overline x-1}d\theta\\
	&= \prod^M_{n=1}\left( \begin{array}{llll}
	N\\
	x_n\\
	\end{array} \right)B^{-1}(\alpha,\beta) \int^1_0 \dfrac{B(\alpha+M\overline x,\beta+N-M\overline x)}{B(\alpha+M\overline x, \beta+N-M\overline x)}\theta^{\alpha +M \overline x-1}(1-\theta)^{\beta+N-M \overline x-1}d\theta\\
	&= \prod^M_{n=1}\left( \begin{array}{llll}
	N\\
	x_n\\
	\end{array} \right)\dfrac{B(\alpha+M\overline x,\beta+N-M\overline x)}{B(\alpha,\beta)} \int^1_0 {\dfrac{\theta^{\alpha +M \overline x-1}(1-\theta)^{\beta+N-M \overline x-1}}{B(\alpha+M\overline x, \beta+N-M\overline x)}d\theta}&&|Substitution: \alpha'=\alpha+M\overline x;\ \beta'=\beta+N-M\overline x\\
	&= \prod^M_{n=1}\left( \begin{array}{llll}
	N\\
	x_n\\
	\end{array} \right)\dfrac{B(\alpha',\beta')}{B(\alpha,\beta)}  \textcolor{magenta}{\int^1_0\dfrac{\theta^{\alpha'}(1-\theta)^{\beta'}}{B(\alpha', \beta')}d\theta}\\
	&= \prod^M_{n=1}\left( \begin{array}{llll}
	N\\
	x_n\\
	\end{array} \right)\dfrac{B(\alpha',\beta')}{B(\alpha,\beta)}
\end{align*}
$$
 
$$
\begin{align*}
Posterior: \\
p_{\Theta| \underline X}(\theta|\underline x)&=\dfrac{p_{\underline X,\Theta}(\underline x,\theta)}{p_{\underline X}(\underline x)}\\
&= \dfrac{\prod\limits^M_{n=1}\left( \begin{array}{llll}
	N\\
	x_n\\
	\end{array} \right) \theta^{x_n}(1-\theta)^{N-x_n}\cdot B^{-1}(\alpha,\beta)\theta^{\alpha-1}(1-\theta)^{\beta-1}d\theta}{\prod\limits^M_{n=1}\left( \begin{array}{llll}
	N\\
	x_n\\
	\end{array} \right)\dfrac{B(\alpha',\beta')}{B(\alpha,\beta)}}\\
	&=\dfrac{\theta^{M\overline x}(1-\theta)^{N-M\overline x}\theta^{\alpha-1}(1-\theta)^{\beta-1}}{B(\alpha',\beta')}\\
	&=\dfrac{\theta^{\alpha'-1}(1-\theta)^{\beta'-1}}{B(\alpha',\beta')}
\end{align*}
$$
##### Log-A-Posteriori Funktion:
$$
\begin{align*}
\forall \theta \in [0,1]: \ln p_{\Theta|\underline{X}}(\theta|\underline{x})  &= \ln \dfrac{1}{B(\alpha',\beta')} \theta^{\alpha'-1}(1-\theta)^{\beta'-1}\\
	&= \ln \dfrac{1}{B(\alpha',\beta')} + \ln \theta^{\alpha'-1} + \ln (1-\theta)^{\beta'-1} & | \; Logarithmusgesetz: \; \ln ab = \ln a + \ln b\\
    &= \ln \dfrac{1}{B(\alpha',\beta')} + (\alpha'-1)\ln \theta + (\beta'-1)\ln (1-\theta) & | \; Logarithmusgesetz: \ln a^b = b \cdot \ln a 
\end{align*}
$$
$$
\begin{align*}
\text{Nun leiten wir ab und bedenken: } \dfrac{d}{dy}ln(y) = \dfrac{1}{y}\\
    \dfrac{d}{d\theta} \ln p_{\Theta|\underline{X}}(\theta|\underline{x}) &= \dfrac{\alpha'-1}{\theta} - \dfrac{\beta'-1}{1-\theta}\\
    0 &\overset{!}{=} \dfrac{\alpha'-1}{\theta} - \dfrac{\beta'-1}{1-\theta}\\
    \dfrac{\alpha'-1}{\theta} &= \dfrac{\beta'-1}{1-\theta}\\
    (\alpha'-1)(1-\theta) &= (\beta'-1) \theta & | \; Ausmultiplizieren\\
    \alpha' - \alpha' \theta -1 + \theta &= \beta' \theta - \theta\\
    \alpha' -1 &= \beta' \theta - \theta + \alpha' \theta - \theta\\
    &= \theta ( \beta' + \alpha' -2)\\
    \hat \theta &= \dfrac{\alpha'-1}{\alpha'+\beta'-2}\\
\end{align*}
$$
------------

#### MP-Schätzer
$$\hat{\theta} = E(\theta|\underline x) = \dfrac{\alpha'}{\alpha'+\beta'}$$
