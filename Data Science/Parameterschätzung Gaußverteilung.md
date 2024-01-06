
### Momentenschätzer $\hat \theta$

$$\begin{align*}
    E(X_1) &\overset{!}{=} \overline{x}\\
    N \theta &\overset{!}{=} \overline{x} & | \; Erwartungswert \; Binomialverteilung\\
    \hat{\theta} &\overset{!}{=} \dfrac{\overline{x}}{N}
\end{align*}$$
---------------------

#### ML-Schätzer für $\mu$
$$
\begin{align*}
    Likelihood:\\
    \forall \underline x \in \{0,1,...,N\}: p_{\underline{X}}(\underline{x}|\mu,\sigma^2) &=\prod^N_{n=1}p_{X_n}(x_n|\mu,\sigma^2)\\
    &=\dfrac{1}{(2\pi\sigma^2)^{N/2}}\prod^N_{n=1}e^{-\dfrac{1}{2\sigma^2}(x_n-\mu)^2}\\
\end{align*}$$
$$
\begin{align*}
Loglikelihood:\\
 \forall \underline x \in \{0,1,...,N\}: \ln p_{\underline{X}}(\underline{x}|\mu,\sigma^2) &=-\dfrac{1}{2\sigma^2} \sum^N_{n=1}(x_n-\mu)^2 - \dfrac{N}{2}ln\sigma^2-\dfrac{N}{2}\ln(2\pi) &&|siehe\ Vorlesung \\
	&=-\dfrac{1}{2\sigma^2} \sum^N_{n=1}(x_n^2-2x_n\mu+\mu^2) - \dfrac{N}{2}ln\sigma^2-\dfrac{N}{2}\ln(2\pi) && |Binomische\ Formel\\
	&= -\dfrac{1}{2\sigma^2} \left(\sum^N_{n=1}x_n^2-\sum^N_{n=1}2x_n\mu+\sum^N_{n=1}\mu^2\right) - \dfrac{N}{2}ln\sigma^2-\dfrac{N}{2}\ln(2\pi) && |Linearität\ Summe\\
	&= -\dfrac{1}{2\sigma^2} \sum^N_{n=1}x_n^2 + \dfrac{1}{2\sigma^2}2N\overline x\mu -\dfrac{1}{2\sigma^2} N\mu^2 - \dfrac{N}{2}ln\sigma^2-\dfrac{N}{2}\ln(2\pi) && | \overline x = \dfrac 1 N\sum_{n=1}^Nx_n \Leftrightarrow N\overline x=\sum_{n=1}^Nx_n\\
	
\end{align*}$$
$$
\begin{align*}
Loglikelihood\ nach\ \mu \ ableiten:\\
\dfrac{d\ln p_{\underline{X}}(\underline{x}|\mu,\sigma^2)}{d\mu} &=\dfrac{2N\overline x}{2\sigma^2}- \dfrac{2N\mu}{2\sigma^2} && |\dfrac{d}{dy}ln(y) = \dfrac{1}{y}\\
0&\overset{!}{=}\dfrac{N\overline x}{\sigma^2}- \dfrac{N\mu}{\sigma^2}&& | 2\ kürzen\\
\dfrac{N\mu}{\sigma^2}&=\dfrac{N\overline x}{\sigma^2} && |\cdot \sigma^2\\
N\mu&=N\overline x && |:N\\
\hat \mu &=\overline x
\end{align*}$$
#### ML-Schätzer für $\tau$, wobei $\tau = \dfrac{1}{\sigma^2}$

$$
\begin{align*}
Loglikelihood\ nach\ \sigma^2 \ ableiten:\\
\dfrac{d\ln p_{\underline{X}}(\underline{x}|\mu,\sigma^2)}{d\sigma^2} &=\dfrac{2}{2\sigma^3}\sum^N_{n=1}(x_n-\mu)^2- \dfrac{2N}{2\sigma} && |\dfrac{d}{dy}ln(y) = \dfrac{1}{y}\\
0&\overset{!}{=}\dfrac{2}{2\sigma^3}\sum^N_{n=1}(x_n-\mu)^2- \dfrac{2N}{2\sigma}&& | +\dfrac{2N}{2\sigma}\ und\ kürzen\\
\dfrac{N}{\sigma}&=\dfrac{1}{\sigma^3}\sum^N_{n=1}(x_n-\mu)^2 && |\cdot \sigma^3 : N\\
\dfrac{\sigma^3}{\sigma}&=\dfrac{1}{N}\sum^N_{n=1}(x_n-\mu)^2 && |\sigma \ kürzen\\
\sigma^2&=\dfrac{1}{N}\sum^N_{n=1}(x_n-\mu)^2 && |\tau = \dfrac{1}{\sigma^2}\\
\hat \tau &= N\dfrac{1}{\sum^N_{n=1}(x_n-\mu)^2}
\end{align*}$$
------------------------

#### MAP-Schätzer

Wichtige Regel: $\prod\limits_{n=1}^N \theta^{x_n}=\theta^{\sum_{n=1}^Nx_n}$

##### Prior [[Gaußverteilung]]:
$p_M(\mu)=N(\mu|\mu_0,\sigma^2_0)=\dfrac{1}{(2\pi\sigma^2_0)^{1/2}}e^{-\dfrac{1}{2\sigma^2_0}(\mu-\mu_0)^2}$

$$
\begin{align*}
gem. Wahrscheinlichkeitsdichten: \\
p_{\underline X,M}(\underline x,\mu)&=p_{\underline X|M}(\underline x|\mu) \cdot p_M(\mu)\\
&=\dfrac{1}{(2\pi\sigma^2)^{N/2}}\prod^N_{n=1}e^{-\dfrac{1}{2\sigma^2}(x_n-\mu)^2} \cdot \dfrac{1}{(2\pi\sigma^2_0)^{1/2}}e^{-\dfrac{1}{2\sigma^2_0}(\mu-\mu_0)^2}
\end{align*}
$$

$$
\begin{align*}
	Randwahrscheinlichkeiten: \\
	p_{\underline X}(\underline x)&=\int^1_0 \dfrac{1}{(2\pi\sigma^2)^{N/2}}\prod^N_{n=1}e^{-\dfrac{1}{2\sigma^2}(x_n-\mu)^2} \cdot \dfrac{1}{(2\pi\sigma^2_0)^{1/2}}e^{-\dfrac{1}{2\sigma^2_0}(\mu-\mu_0)^2}\\
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
