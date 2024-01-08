


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

#### MP-Schätzer

##### Prior [[Gaußverteilung]]:
$p_M(\mu)=N(\mu|\mu_0,\sigma^2_0)\propto exp\{-\dfrac{1}{2\sigma^2_0}(\mu-\mu_0)^2\}$

##### Likelihood:
$p_{\underline X | M}(\underline x|\mu)\propto \prod\limits^N_{n=1}exp\{-\dfrac{1}{2 \sigma^2}(x_n-\mu)^2\}$

##### Posterior:
$$
\begin{align*}
p_{M|\underline X}(\mu|\underline x)&=\dfrac{p_{\underline X|M}(\underline x|\mu) \cdot p_M(\mu)}{p_{\underline X}(\underline x)}\\
&\propto p_{\underline X|M}(\underline x|\mu) \cdot p_M(\mu) &&|p_{\underline X}(\underline x)\ hängt\ nicht\ von\ \mu\ ab\\
&=\prod^N_{n=1}exp\{-\dfrac{1}{2\sigma^2}(x_n-\mu)^2\} \cdot exp\{-\dfrac{1}{2\sigma^2_0}(\mu-\mu_0)^2\}
\end{align*}
$$

##### Log-A-Posteriori Funktion:
$$
\begin{align*}
	\forall \mu \in \mathbb R: \ln p_{M|\underline X}(\mu|\underline x) &= \ln \prod^N_{n=1}exp\{-\dfrac{1}{2\sigma^2}(x_n-\mu)^2\} \cdot exp\{-\dfrac{1}{2\sigma^2_0}(\mu-\mu_0)^2\}\\
	&= \sum^N_{n=1}\ln exp\{-\dfrac{1}{2\sigma^2}(x_n-\mu)^2\} + \ln exp\{-\dfrac{1}{2\sigma^2_0}(\mu-\mu_0)^2\} && | \; Logarithmusgesetz: \; \ln ab = \ln a + \ln b\\
    &= \sum^N_{n=1}-\dfrac{1}{2\sigma^2}(x_n-\mu)^2   -\dfrac{1}{2\sigma^2_0}(\mu-\mu_0)^2 && | \ \ln e^x = x\\
    &=\sum^N_{n=1}-\dfrac{\tau}{2}(x_n-\mu)^2   -\dfrac{\tau_0}{2}(\mu-\mu_0)^2 && |\ \tau=\dfrac{1}{\sigma^2}\ und\ \tau_0=\dfrac{1}{\sigma^2_0}\\
    &=-\dfrac{\tau}{2}\sum^N_{n=1}(x_n^2-2x_n \mu + \mu^2)   -\dfrac{\tau_0}{2}(\mu^2-2\mu\mu_0+\mu_0^2) \\
    &=-\dfrac{\tau}{2}\sum^N_{n=1}x_n^2+\dfrac{\tau}{2}\sum^N_{n=1}2x_n \mu -\dfrac{\tau}{2}\sum^N_{n=1} \mu^2  -\dfrac{\tau_0}{2}\mu^2+\dfrac{\tau_0}{2}2\mu\mu_0+\dfrac{\tau_0}{2}\mu_0^2 && |Ausmultiplizieren\\
    &=-\dfrac{\tau}{2}\sum^N_{n=1}x_n^2+\dfrac{\tau}{2}2N\overline x \mu -\dfrac{\tau}{2}N\mu^2  -\dfrac{\tau_0}{2}\mu^2+\dfrac{\tau_0}{2}2\mu\mu_0+\dfrac{\tau_0}{2}\mu_0^2\\
    &=\mu^2\left(-\dfrac{\tau}{2}N-\dfrac{\tau_0}{2} \right) + \mu\left(\tau N \overline x + \tau_0\mu_0 \right)+\dfrac{\tau_0}{2}\mu_0^2 - \dfrac{\tau}{2}\sum^N_{n=1}x_n^2 && | nach\ \mu\ ausklammern\\
    a=-\dfrac{\tau}{2}N-\dfrac{\tau_0}{2} ;\ & b=\tau N \overline x + \tau_0\mu_0;\ c=\dfrac{\tau_0}{2}\mu_0^2 - \dfrac{\tau}{2}\sum^N_{n=1}x_n^2\\
    &=a\mu^2+b\mu+c &&| Substitution\\
    &=a(\mu^2+\dfrac{b}{a}\mu)+c\\
    &=a(\mu^2+\dfrac{b}{a}\mu+\dfrac{b}{2a}-\dfrac{b}{2a})+c\\
    &=a(\mu+\dfrac{b}{2a})^2-\dfrac{b^2}{4a^2}+c\\
    &=\left(-\dfrac{\tau}{2}N-\dfrac{\tau_0}{2}\right)\left(\mu +  \dfrac{\tau N \overline x + \tau_0\mu_0}{-\dfrac{\tau}{2}N-\dfrac{\tau_0}{2}}\right)^2-\dfrac{(\tau N \overline x + \tau_0\mu_0)^2}{4 \cdot(-\dfrac{\tau}{2}N-\dfrac{\tau_0}{2})^2}+c\\
    &=\left(-\dfrac{1}{2}(\tau N+\tau_0)\right)\left(\mu -  \dfrac{2\tau N \overline x + \tau_0\mu_0}{\tau N+\tau_0}\right)^2- c'&&| c' = \dfrac{(\tau N \overline x + \tau_0\mu_0)^2}{4 \cdot(-\dfrac{\tau}{2}N-\dfrac{\tau_0}{2})^2}+c
\end{align*}
$$

------------

#### MP-Schätzer
$$\hat{\mu} = E(\mu|\underline x) = \dfrac{2\tau N \overline x + \tau_0\mu_0}{\tau N+\tau_0}$$
