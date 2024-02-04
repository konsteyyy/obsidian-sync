


#### ML-Schätzer für $\mu$
$$
\begin{align*}
    Likelihood:\\
    \forall \underline x \in \bigg\{0,1,...,N\bigg\}: p_{\underline{X}}(\underline{x}|\mu,\sigma^2) &=\prod^N_{n=1}p_{X_n}(x_n|\mu,\sigma^2)\\
    &=\dfrac{1}{(2\pi\sigma^2)^{N/2}}\prod^N_{n=1}e^{-\dfrac{1}{2\sigma^2}(x_n-\mu)^2}\\
\end{align*}$$
$$
\begin{align*}
Loglikelihood:\\
 \forall \underline x \in \bigg\{0,1,...,N\bigg\}: \ln p_{\underline{X}}(\underline{x}|\mu,\sigma^2) &=-\dfrac{1}{2\sigma^2} \sum^N_{n=1}(x_n-\mu)^2 - \dfrac{N}{2}ln\sigma^2-\dfrac{N}{2}\ln(2\pi) &&|siehe\ Vorlesung \\
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
	$p_M(\mu)=N(\mu|\mu_0,\sigma^2_0)= \dfrac{1}{\sqrt{2\pi \sigma_0^2}} exp\bigg\{-\dfrac{1}{2\sigma^2_0}(\mu-\mu_0)^2\bigg\}$

##### Likelihood:
$p_{\underline X | M}(\underline x|\mu)= \prod\limits^N_{n=1}\dfrac{1}{\sqrt{2\pi \sigma^2}}exp\bigg\{-\dfrac{1}{2 \sigma^2}(x_n-\mu)^2\bigg\}$

##### Posterior:
$$
\begin{align*}
{\small}
p_{M|\underline X}(\mu|\underline x)&=\dfrac{p_{\underline X|M}(\underline x|\mu) \cdot p_M(\mu)}{p_{\underline X}(\underline x)}\\
&\propto p_{\underline X|M}(\underline x|\mu) \cdot p_M(\mu) &&|p_{\underline X}(\underline x)\ hängt\ nicht\ von\ \mu\ ab\\
&=\Bigg[\prod\limits^N_{n=1}\dfrac{1}{\sqrt{2\pi \sigma^2}}exp\bigg\{-\dfrac{1}{2 \sigma^2}(x_n-\mu)^2\bigg\}\Bigg] \cdot\dfrac{1}{\sqrt{2\pi \sigma_0^2}} exp\bigg\{-\dfrac{1}{2\sigma^2_0}(\mu-\mu_0)^2\bigg\}\\
&=\dfrac{1}{\sqrt{2\pi \sigma^2}}\Bigg[\prod\limits^N_{n=1}exp\bigg\{-\dfrac{1}{2 \sigma^2}(x_n-\mu)^2\bigg\}\Bigg]\cdot\dfrac{1}{\sqrt{2\pi \sigma_0^2}} exp\bigg\{-\dfrac{1}{2\sigma^2_0}(\mu-\mu_0)^2\bigg\}\\
&\propto \Bigg[\prod\limits^N_{n=1}exp\bigg\{-\dfrac{1}{2 \sigma^2}(x_n-\mu)^2\bigg\}\Bigg]\cdot exp\bigg\{-\dfrac{1}{2\sigma^2_0}(\mu-\mu_0)^2\bigg\}\\
&=\Bigg[exp\bigg\{\sum\limits^N_{n=1}-\dfrac{1}{2 \sigma^2}(x_n-\mu)^2\bigg\}\Bigg]\cdot exp\bigg\{-\dfrac{1}{2\sigma^2_0}(\mu-\mu_0)^2\bigg\} &&| \prod\limits_{n=1}^N e^{x_n}=e^{\sum_{n=1}^Nx_n}\\
&=exp\bigg\{-\dfrac{1}{2 \sigma^2}\sum\limits^N_{n=1}(x_n-\mu)^2-\dfrac{1}{2\sigma^2_0}(\mu-\mu_0)^2\bigg\}&&|e^a \cdot e^b=e^{a+b}\\
	&=exp\bigg\{-\dfrac{1}{2 \sigma^2}\sum\limits^N_{n=1}(x_n^2-2x_n\mu+\mu^2)-\dfrac{1}{2\sigma^2_0}(\mu^2-2\mu\mu_0+\mu_0^2)\bigg\} && |binomische\ Formel\\
	&=exp\bigg\{-\dfrac{1}{2 \sigma^2}\sum\limits^N_{n=1}x_n^2+\dfrac{1}{2 \sigma^2}\sum\limits^N_{n=1}2x_n\mu-\dfrac{1}{2 \sigma^2}\sum\limits^N_{n=1}\mu^2-\dfrac{1}{2\sigma^2_0}\mu^2+\dfrac{1}{2\sigma^2_0}2\mu\mu_0-\dfrac{1}{2\sigma^2_0}\mu_0^2\bigg\} &&|Klammern\ auflösen\\
	&=exp\bigg\{-\dfrac{1}{2 \sigma^2}\sum\limits^N_{n=1}x_n^2+\dfrac{2N\overline x}{2 \sigma^2}\mu-\dfrac{N}{2 \sigma^2}\mu^2-\dfrac{1}{2\sigma^2_0}\mu^2+\dfrac{1}{2\sigma^2_0}2\mu\mu_0-\dfrac{1}{2\sigma^2_0}\mu_0^2\bigg\} && |Def.\ \overline x\\
		&\propto exp\bigg\{\mu^2\left(-\dfrac{N}{2 \sigma^2}-\dfrac{1}{2\sigma^2_0}\right)+\mu\left(\dfrac{N\overline x}{\sigma^2}+\dfrac{\mu_0}{\sigma^2_0}\right)\bigg\}\\
		&=exp\bigg\{-\dfrac{1}{2}\mu^2\left(\dfrac{N}{\sigma^2}+\dfrac{1}{\sigma^2_0}\right)+\mu\left(\dfrac{N\overline x}{\sigma^2}+\dfrac{\mu_0}{\sigma^2_0}\right)\bigg\}\\
		&\propto exp\bigg\{-\dfrac{1}{2}\left(\dfrac{N}{\sigma^2}+\dfrac{1}{\sigma^2_0}\right)\left(\mu-\left(\dfrac{\sigma^2}{N\sigma_0^2+\sigma^2}\mu_0+\dfrac{N\sigma^2_0}{N+\sigma^2}\mu_{ML}\right)\right)^2\bigg\} &&|siehe\ quadratische\ Ergänzung\ unten\\
		&=exp\Big\{-\dfrac{1}{2}\tau_N(\mu-\mu_N)^2\Big\}\\
		&=exp\Big\{-\dfrac{1}{2\sigma^2_N}(\mu-\mu_N)^2\Big\}
		\\
		
		\underline{Quadratische\ Ergänzung:}\\
		&\tau_N=\dfrac{N}{\sigma^2}+\dfrac{1}{\sigma^2_0}\\
		&\tau_N\mu_N=\dfrac{N\overline x}{\sigma^2}+\dfrac{\mu_0}{\sigma^2_0}\\
		&\Leftrightarrow \mu_N = \left(\dfrac{N\overline x}{\sigma^2}+\dfrac{\mu_0}{\sigma^2_0}\right) \cdot \dfrac{1}{\tau_N}\\
		&=\dfrac{N\overline x}{\sigma^2\tau_N}+\dfrac{\mu_0}{\sigma^2_0\tau_N}\\
		&=\dfrac{N\overline x}{\sigma^2(\dfrac{N}{\sigma^2}+\dfrac{1}{\sigma^2_0})}+\dfrac{\mu_0}{\sigma^2_0(\dfrac{N}{\sigma^2}+\dfrac{1}{\sigma^2_0})}\\
		&=\dfrac{N\overline x}{N+\dfrac{\sigma^2}{\sigma^2_0}}+\dfrac{\mu_0}{\dfrac{N\sigma_0^2}{\sigma^2}+1} &&|Erweitern\\
		&=\dfrac{\sigma^2_0}{\sigma^2_0}\dfrac{N\overline x}{N+\dfrac{\sigma^2}{\sigma^2_0}}+\dfrac{\sigma^2}{\sigma^2}\dfrac{\mu_0}{\dfrac{N\sigma_0^2}{\sigma^2}+1}\\
		&=\dfrac{\sigma^2}{N\sigma_0^2+\sigma^2}\mu_0+\dfrac{N\sigma^2_0}{N+\sigma^2}\mu_{ML} &&|\mu_{ML} = \overline x
\end{align*}
$$



------------

#### MP-Schätzer
$$\hat{\mu} = \mu_N = \dfrac{\sigma^2}{N\sigma_0^2+\sigma^2}\mu_0+\dfrac{N\sigma^2_0}{N+\sigma^2}\mu_{ML}$$
