
### Momentenschätzer $\hat \lambda$

$$\begin{align*}
    E(X_1) &\overset{!}{=} \overline{x}\\
    \hat \lambda &= \overline{x} & | \; Erwartungswert \; Binomialverteilung\\
\end{align*}$$

--------------

#### ML-Schätzer
$$
\begin{align*}
    Likelihood:\\
    \forall \underline x \in \mathbb{N}^D: p_{\underline{X}|\Lambda}(\underline{x}|\lambda) &=\prod^N_{n=1}p_{X_n|\Lambda}(x_n|\lambda)\\
    &=\prod^N_{n=1} \dfrac{\lambda^{x_n}}{x_n!}e^{-\lambda}
\end{align*}
$$
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
\end{align*}
$$
-------------------------

#### MAP-Schätzer
##### Posterior

Wichtige Regel: $\prod\limits_{n=1}^N \lambda^{x_n}=\lambda^{\sum_{n=1}^Nx_n}$
##### Prior [[Gammaverteilung]]:
$p_\Lambda(\lambda)=\beta^\alpha\Gamma^{-1}(\alpha)\lambda^{\alpha-1}e^{-\beta\lambda}$

$$
\begin{align*}
gem. Wahrscheinlichkeitsdichten: \\
p_{\underline X,\Lambda}(\underline x,\lambda)=p_{\underline X|\Lambda}(\underline x|\lambda) \cdot p_\Lambda(\lambda)
\end{align*}
$$

$$
\begin{align*}
	Randwahrscheinlichkeiten: \\
	p_{\underline X}(\underline x)&=\int^1_0 p_{\underline X,\Lambda}(\underline x,\lambda)\\
	&=\int^1_0 \prod^N_{n=1}p_{X_n|\Lambda}(x_n|\lambda)\\
    &=\int^1_0\prod^N_{n=1} \dfrac{\lambda^{x_n}}{x_n!}e^{-\lambda}\cdot \beta^\alpha\Gamma^{-1}(\alpha)\lambda^{\alpha-1}e^{-\beta\lambda}d\lambda &&|\prod_{n=1}^N \theta^{x_n}=\theta^{\sum_{n=1}^Nx_n}\\
	&= \prod^N_{n=1}\dfrac{\beta^\alpha}{x_n!\Gamma(\alpha)} \int^1_0 \lambda^{\alpha+M\overline x-1}e^{-\beta\lambda-\lambda}d\lambda &&|Substitution: \alpha'=\alpha+M\overline x;\ \beta'=\beta-1\\
	&= \prod^N_{n=1}\dfrac{\beta^\alpha}{x_n!\Gamma(\alpha)} \int^1_0 \lambda^{\alpha'}e^{-\beta'\lambda}d\lambda &&|Erweitern\\
	&= \prod^N_{n=1}\dfrac{\beta^\alpha}{x_n!\Gamma(\alpha)} \int^1_0 \dfrac{\beta'^{\alpha'}\Gamma(\alpha')}{\beta'^{\alpha'}\Gamma(\alpha')} \lambda^{\alpha'}e^{-\beta'\lambda}d\lambda\\
	&= \prod^N_{n=1}\dfrac{\beta^\alpha\Gamma(\alpha')}{x_n!\Gamma(\alpha)\beta'^{\alpha'}} \int^1_0 \dfrac{\beta'^{\alpha'}}{\Gamma(\alpha')} \lambda^{\alpha'}e^{-\beta'\lambda}d\lambda\\
	&= \prod^N_{n=1}\dfrac{\beta^\alpha\Gamma(\alpha')}{x_n!\Gamma(\alpha)\beta'^{\alpha'}} \textcolor{magenta}{\int^1_0 \beta'^{\alpha'}\Gamma^{-1}(\alpha') \lambda^{\alpha'}e^{-\beta'\lambda}d\lambda} &&|Gammaverteilung\\
	&= \prod^N_{n=1}\dfrac{\beta^\alpha\Gamma(\alpha')}{x_n!\Gamma(\alpha)\beta'^{\alpha'}}
\end{align*}
$$
 
$$
\begin{align*}
Posterior: \\
p_{\Lambda| \underline X}(\lambda|\underline x)&=\dfrac{p_{\underline X,\Lambda}(\underline x,\lambda)}{p_{\underline X}(\underline x)}\\
	&= \dfrac{\prod\limits^N_{n=1} \dfrac{\lambda^{x_n}}{x_n!}e^{-\lambda}\cdot \beta^\alpha\Gamma^{-1}(\alpha)\lambda^{\alpha-1}e^{-\beta\lambda}}{\prod\limits^N_{n=1}\dfrac{\beta^\alpha\Gamma(\alpha')}{x_n!\Gamma(\alpha)\beta'^{\alpha'}}}\\
		&=\dfrac{\lambda^{N \overline x}e^{-\lambda} \lambda^{\alpha-1}e^{-\beta\lambda}\beta'^{\alpha'}}{\Gamma(\alpha')}\\
	&=\beta'^{\alpha'}\Gamma^{-1}(\alpha') \lambda^{\alpha'-1}e^{-\beta'\lambda}
\end{align*}
$$

##### Log-A-Posteriori Funktion
$$
\begin{align*}
    \forall \lambda \in \mathbb{R}_+: \ln p_{\Lambda|\underline X}(\lambda|\underline x) &= \ln \beta'^{\alpha'} \Gamma^{-1}(\alpha') \lambda^{\alpha'-1}e^{-\beta'\lambda}\\
    &=\ln \beta'^{\alpha'} + \ln \Gamma^{-1}(\alpha') + \ln \lambda^{\alpha'-1} + \ln e^{-\beta'\lambda} &| \; Logarithmusgesetz: \; \ln ab = \ln a + \ln b\\
    &={\alpha'} \ln \beta' - \ln \Gamma(\alpha') + (\alpha'-1)\ln \lambda -\beta'\lambda & | \; Logarithmusgesetz: \ln a^b = b \cdot \ln a 
\end{align*}
$$
$$
\begin{align*}
    \text{Nun leiten wir ab und bedenken: } \dfrac{d}{dy}ln(y) = \dfrac{1}{y}\\
    \dfrac{d}{d\lambda} \ln p_{\Lambda|\underline X}(\lambda|\underline x) &= \dfrac{\alpha'-1}{\lambda} -1\\
    0 &\overset{!}{=} \dfrac{\alpha'-1}{\lambda} -1\\
    1 &= \dfrac{\alpha'-1}{\lambda}\\
    \hat{\lambda} &= \alpha'-1
\end{align*}
$$
-------------------

#### MP-Schätzer

$$\hat{\lambda} = E(\lambda|\underline x) = \dfrac{\alpha'}{\beta'}$$