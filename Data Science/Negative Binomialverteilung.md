#### Definition
**Eine diskrete ZV X mit den Werten $x \in \mathbb{N}$ und den Wahrscheinlichkeiten (s.u) heißt binomialverteilt**

----------------------- 

### [[Wahrscheinlichkeitsfunktion]]

$$
\forall x\in \mathbb{N}, \alpha\in \mathbb{R_+},\lambda\in[0,1]:p_X(x|\alpha,\theta) = \dfrac{\Gamma(\alpha+x)}{\Gamma(\alpha)\Gamma(x+1)} \theta^x(1-\theta)^\alpha
$$

----------------
### Erwartungswert/[[Moment]]

$$E(X) = \dfrac{\alpha \theta}{(1-\theta)}$$ #erwartungswert

##### Herleitung:

$$
\begin{align*}
    E(X) &= \sum_{x=0}^\infty xp_X(x|\alpha,\theta) \\
    &= \sum_{x=0}^\infty x\dfrac{\Gamma(\alpha+x)}{\Gamma(\alpha)\Gamma(x+1)} \theta^x(1-\theta)^{\alpha} & | Def. Negative\ Binomialverteilungswahrscheinlichkeit\\
	&= \sum_{\textcolor{magenta}{x=1}}^\infty x \dfrac{\Gamma(\alpha+x)}{\Gamma(\alpha)\Gamma(x+1)} \theta^x(1-\theta)^{\alpha} & | Indexverschiebung\ um\ 1\\
	&= \sum_{x=1}^\infty \textcolor{magenta}x \dfrac{\Gamma(\alpha+x)}{\Gamma(\alpha)\textcolor{magenta}{x\Gamma(x)}} \theta^x(1-\theta)^{\alpha} & |\forall x\in\mathbb{R}:\Gamma(x+1)=x\Gamma(x)\\
	&= \sum_{x=1}^\infty \ \dfrac{\Gamma(\alpha+x)}{\Gamma(\alpha)\Gamma(x)} \textcolor{magenta}\theta\theta^{x-1}(1-\theta)^{\alpha} & |a^x = aa^{x-1} \text{ und } kürzen\\
	&= \textcolor{magenta}{\theta} \sum_{x=1}^\infty \dfrac{\Gamma(\alpha+x)}{\Gamma(\alpha)\Gamma(x)} \theta^{x-1}(1-\theta)^{\alpha} & | Konstanten\ aus\ Summe\ ziehen\\
	&= \theta \sum_{x=1}^\infty \dfrac{\Gamma(\alpha+x)}{\Gamma(\alpha)\Gamma(x)} \theta^{x-1} \dfrac{(1-\theta)^{\alpha}(1-\alpha)}{(1-\alpha)} & |Erweitern\ mit\ \dfrac {(1-\alpha)}{(1-\alpha)}\\
	&= \dfrac{\theta}{1-\theta} \sum_{x=1}^\infty \dfrac{\Gamma(\alpha+x)}{\Gamma(\alpha)\Gamma(x)} \theta^{x-1} (1-\theta)^{\textcolor{magenta}{\alpha+1}} & |a^b\cdot a = a^{b+1}\ und\ Konstanten\ aus\ Summe\\
	&= \dfrac{\theta}{1-\theta} \sum_{x=1}^\infty \textcolor{magenta}{\dfrac{\alpha}{\alpha}}\dfrac{\Gamma(\alpha\textcolor{magenta}{+1}+x\textcolor{magenta}{-1})}{\Gamma(\alpha)\Gamma(x)} \theta^{x-1} (1-\theta)^{{\alpha+1}} & |Erweitern\ mit\ +1-1\ und\ \dfrac{\alpha}{\alpha}\\
	&= \dfrac{\alpha\theta}{1-\theta} \sum_{x=1}^\infty \dfrac{\Gamma(\alpha+1+x-1)}{\textcolor{magenta}{\alpha\Gamma(\alpha)}\Gamma(x)} \theta^{x-1} (1-\theta)^{{\alpha+1}} & |Konstante\ aus\ Summe\ ziehen\ und\ \forall \alpha \in \mathbb R_+: \Gamma(\alpha+1) = \alpha\Gamma(\alpha)\\
	&= \dfrac{\alpha\theta}{1-\theta} \sum_{x=1}^\infty \dfrac{\Gamma(\alpha+1+x-1)}{\Gamma(\alpha+1)\Gamma(x)} \theta^{x-1} (1-\theta)^{{\alpha+1}} & |Substitution: \alpha'=\alpha+1\ und\ x'=x-1\\
	&= \dfrac{\alpha\theta}{1-\theta} \sum_{x'=0}^\infty \textcolor{magenta}{\dfrac{\Gamma(\alpha'+x')}{\Gamma(\alpha')\Gamma(x'+1)} \theta^{x'} (1-\theta)^{{\alpha'}}}&|Def. Negative\ Binomialverteilungswahrscheinlichkeiten\\
	&= \dfrac{\alpha\theta}{1-\theta} \sum_{x'=0}^\infty p_{X'}(x'|\alpha',\theta) & |Normiertheit\ Wahrscheinlichkeitsfunktionen \\
	&= \dfrac{\alpha\theta}{1-\theta}
\end{align*}
$$

-------------
### Varianz

$$
Var(X) = \dfrac{\alpha \theta}{(1-\theta)^2}
$$

#varianz
##### Herleitung:

$$
\begin{align*}
    E(X^2) &= \sum_{x=0}^\infty x^2p_X(x|\alpha,\theta) \\
    &= \sum_{x=0}^\infty x^2\dfrac{\Gamma(\alpha+x)}{\Gamma(\alpha)\Gamma(x+1)} \theta^x(1-\theta)^{\alpha} & | Def. Negative\ Binomialverteilungswahrscheinlichkeit\\
	&= \sum_{\textcolor{magenta}{x=1}}^\infty x^2 \dfrac{\Gamma(\alpha+x)}{\Gamma(\alpha)\Gamma(x+1)} \theta^x(1-\theta)^{\alpha} & | Indexverschiebung\ um\ 1\\
	&= \sum_{x=1}^\infty \textcolor{magenta}{x^2} \dfrac{\Gamma(\alpha+x)}{\Gamma(\alpha)\textcolor{magenta}{x\Gamma(x)}} \theta^x(1-\theta)^{\alpha} & |\forall x\in\mathbb{R}:\Gamma(x+1)=x\Gamma(x)\\
	&= \sum_{x=1}^\infty x \dfrac{\Gamma(\alpha+x)}{\Gamma(\alpha)\Gamma(x)} \textcolor{magenta}\theta\theta^{x-1}(1-\theta)^{\alpha} & |a^x = aa^{x-1} \text{ und } kürzen\\
	&= \textcolor{magenta}{\theta} \sum_{x=1}^\infty x\dfrac{\Gamma(\alpha+x)}{\Gamma(\alpha)\Gamma(x)} \theta^{x-1}(1-\theta)^{\alpha} & | Konstanten\ aus\ Summe\ ziehen\\
	&= \theta \sum_{x=1}^\infty x\dfrac{\Gamma(\alpha+x)}{\Gamma(\alpha)\Gamma(x)} \theta^{x-1} \dfrac{(1-\theta)^{\alpha}(1-\alpha)}{(1-\alpha)} & |Erweitern\ mit\ \dfrac {(1-\alpha)}{(1-\alpha)}\\
	&= \dfrac{\theta}{1-\theta} \sum_{x=1}^\infty x\dfrac{\Gamma(\alpha+x)}{\Gamma(\alpha)\Gamma(x)} \theta^{x-1} (1-\theta)^{\textcolor{magenta}{\alpha+1}} & |a^b\cdot a = a^{b+1}\ und\ Konstanten\ aus\ Summe\\
	&= \dfrac{\theta}{1-\theta} \sum_{x=1}^\infty x\textcolor{magenta}{\dfrac{\alpha}{\alpha}}\dfrac{\Gamma(\alpha\textcolor{magenta}{+1}+x\textcolor{magenta}{-1})}{\Gamma(\alpha)\Gamma(x)} \theta^{x-1} (1-\theta)^{{\alpha+1}} & |Erweitern\ mit\ +1-1\ und\ \dfrac{\alpha}{\alpha}\\
	&= \dfrac{\alpha\theta}{1-\theta} \sum_{x=1}^\infty x\dfrac{\Gamma(\alpha+1+x-1)}{\textcolor{magenta}{\alpha\Gamma(\alpha)}\Gamma(x)} \theta^{x-1} (1-\theta)^{{\alpha+1}} & |Konstante\ aus\ Summe\ ziehen\ und\ \forall \alpha \in \mathbb R_+: \Gamma(\alpha+1) = \alpha\Gamma(\alpha)\\
	&= \dfrac{\alpha\theta}{1-\theta} \sum_{x=1}^\infty (x'+1)\dfrac{\Gamma(\alpha+1+x-1)}{\Gamma(\alpha+1)\Gamma(x)} \theta^{x-1} (1-\theta)^{{\alpha+1}} & |Substitution: \alpha'=\alpha+1\ und\ x'=x-1\\
	&= \dfrac{\alpha\theta}{1-\theta} \left(\sum_{x'=0}^\infty x'\textcolor{magenta}{\dfrac{\Gamma(\alpha'+x')}{\Gamma(\alpha')\Gamma(x'+1)} \theta^{x'} (1-\theta)^{{\alpha'}}}+1 \right)&|Def. Negative\ Binomialverteilungswahrscheinlichkeiten\\
	&= \dfrac{\alpha\theta}{1-\theta} \left(\sum_{x'=0}^\infty x'p_{X'}(x'|\alpha',\theta)+1 \right) & |E(X)\ Negative\ Binomialverteilung \\
	&= \dfrac{\alpha\theta}{1-\theta} \cdot \left(\dfrac{\alpha' \theta}{1-\theta}+1 \right)\\
	&= \dfrac{\alpha\theta}{1-\theta} \cdot \left(\dfrac{(\alpha+1) \theta}{1-\theta}+1 \right) & |Rücksubstitution\\
	&= \dfrac{\alpha^2\theta^2 + \alpha\theta^2}{(1-\theta)^2} + \dfrac{\alpha \theta}{1-\theta} & |Ausmultiplizieren\\
	Var(X) = E(X^2)-E^2(X) &= \dfrac{\alpha^2\theta^2 + \alpha\theta^2}{(1-\theta)^2} + \dfrac{\alpha \theta}{1-\theta} - \left( \dfrac{\alpha\theta}{1-\theta}\right)^2 & |Def.\ Varianz\\
	&= \dfrac{\alpha^2\theta^2 + \alpha\theta^2}{(1-\theta)^2} + \dfrac{\alpha \theta- \alpha\theta^2}{(1-\theta)^2} - \dfrac{\alpha^2\theta^2}{(1-\theta)^2} & | Auf\ gemeinsamen\ Nenner\ bringen\\
	&= \dfrac{\alpha \theta}{(1-\theta)^2}
\end{align*}
$$

---------------

#unfinished 