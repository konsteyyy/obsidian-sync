
Beispiel:
* $\lambda \in \mathbb R_+$ wird von [[Gammaverteilung]] gezogen 
* diskrete ZV K wird von [[Poissonverteilung]] und dem zuvor gezogenen $\theta$ gezogen

$$
\forall \lambda \in \mathbb{R_+}:p_\Lambda (\lambda) = \beta^{\alpha}\Gamma^{-1}(\alpha) \lambda^{\alpha-1} e^{-\beta \lambda}$$
$$\forall k\in \mathbb{N}: p_{K|\Lambda}(k|\lambda) = \dfrac{\lambda^k}{k!}e^{-\lambda}$$
#### gemeinsame Wahrscheinlichkeitsdichtefunktion

$$
\begin{align*}
    \forall \lambda \in \mathbb{R_+},k\in \mathbb{N}: p_{K,\Lambda}(k,\lambda) &= p_\Lambda (\lambda) \cdot p_{K|\Lambda}(k|\lambda)\\
    &= \beta^{\alpha}\Gamma^{-1}(\alpha) \lambda^{\alpha-1} e^{-\beta \lambda} \cdot \dfrac{\lambda^k}{k!}e^{-\lambda}\\
    &=  \beta^{\alpha}\Gamma^{-1}(\alpha) \dfrac{\lambda^{a+k-1}}{k!}e^{-\beta \lambda-\lambda}\\
    &= \beta^{\alpha}\Gamma^{-1}(\alpha) \dfrac{\lambda^{a+k-1}}{k!}e^{-(\beta+1)\lambda}
\end{align*}
$$
#### Randwahrscheinlichkeitsfunktion := [[Negative Binomialverteilung]]

$$
\begin{align*}
    \forall k\in \mathbb{N}: p_K(k) &=  \int_0^{\infty} \beta^{\alpha}\Gamma^{-1}(\alpha) \dfrac{\lambda^{a+k-1}}{k!}e^{-(\beta+1)\lambda} d\lambda \\
    &= \beta^{\alpha} \Gamma^{-1}(\alpha) \dfrac{1}{k!} \int_0^{\infty}\lambda^{a+k-1}e^{-(\beta+1)\lambda}d\lambda & | \; Def. \; Linearität \; Konstanten\\
    &= \beta^{\alpha} \Gamma^{-1}(\alpha) \dfrac{1}{k!} \int_0^{\infty} (\dfrac{t}{\beta+1})^{\alpha +k-1}e^{-t}\dfrac{dt}{\beta+1} & | \; Subst.: \; t=(\beta+1)\lambda \Leftrightarrow \lambda = \dfrac{t}{\beta+1}\\
    &= \dfrac{\beta^{\alpha}}{\beta+1}\Gamma^{-1}(\alpha) \dfrac{1}{k!} \int_0^{\infty} \dfrac{t^{\alpha +k-1}}{(\beta+1)^{\alpha +k-1}}e^{-t}dt & | \; Potenzgesetz \; und \; \beta+1 \; aus\; dem\; Integral\; ziehen\\
    &= \dfrac{\beta^{\alpha}}{(\beta+1)^{\alpha +k}}\Gamma^{-1}(\alpha) \dfrac{1}{k!} \int_0^{\infty} t^{\alpha +k-1}e^{-t}dt & | \; Nenner \; aus \; Integral\\
    &= \dfrac{\beta^{\alpha}}{(\beta+1)^{\alpha +k}}\cdot \dfrac{\Gamma(a+k)}{\Gamma(\alpha)k!} & | \; Def. \; Gammafunktion \; mit \; \alpha+k\\
    &=\dfrac{\beta^{\alpha}}{(\beta+1)^{\alpha +k}}\cdot \dfrac{\Gamma(a+k)}{\Gamma(\alpha)\Gamma(k+1)} & | \; Satz \; Gammafunktion\\
    &=\dfrac{\Gamma(a+k)}{\Gamma(\alpha)\Gamma(k+1)} \cdot \dfrac{1}{(\beta +1)^k} \cdot \dfrac{\beta^{\alpha}}{(\beta+1)^{\alpha}}  \\
    &= \dfrac{\Gamma(a+k)}{\Gamma(\alpha)\Gamma(k+1)} \cdot (\dfrac{1}{\beta +1})^k \cdot (\dfrac{\beta}{\beta+1})^{\alpha}  \\
    &= \dfrac{\Gamma(a+k)}{\Gamma(\alpha)\Gamma(k+1)} \cdot (\dfrac{1}{\beta +1})^k \cdot (\dfrac{\beta+1-1}{\beta+1})^{\alpha} & | \; Erweiterung\; mit\; +1-1\\
    &= \dfrac{\Gamma(a+k)}{\Gamma(\alpha)\Gamma(k+1)} \cdot (\dfrac{1}{\beta +1})^k \cdot (\dfrac{\beta+1}{\beta+1} - \dfrac{1}{\beta+1})^{\alpha}\\
    &= \dfrac{\Gamma(a+k)}{\Gamma(\alpha)\Gamma(k+1)} \cdot (\dfrac{1}{\beta +1})^k \cdot (1 - \dfrac{1}{\beta+1})^{\alpha}\\
    &= \dfrac{\Gamma(a+k)}{\Gamma(\alpha)\Gamma(k+1)} \cdot \theta^k \cdot (1 - \theta)^{\alpha} & | \; Subst.: \; \theta=\dfrac{1}{\beta+1}\\
\end{align*}
$$
=> Substitution an der Stelle legitim, da $\dfrac{1}{\beta+1} \in [0,1]$

#### Randwahrscheinlichkeitsdichtefunktion := [[Gammaverteilung]]
$$  \forall \lambda \in \mathbb{R_+}: p_\Lambda(\lambda) := siehe\ oben$$

#### bedingte Wahrscheinlichkeitsfunktion $p_{K|\Theta}(k|\theta)$ := [[Poissonverteilung]]

$$\forall k\in \mathbb{N}: p_{K|\Lambda}(k|\lambda):= siehe\ oben $$

#### bedingte Wahrscheinlichkeitsdichtefunktion $p_{\Theta|K}$ := [[Gammaverteilung]]

$$\begin{align*}
    \forall \lambda \in \mathbb{R_+}: p_{\Lambda|K}(\lambda|k) &= \dfrac{p_{K,\Lambda}(k,\lambda)}{p_{K}(k)} \\
    &= \dfrac{\beta^{\alpha}\Gamma^{-1}(\alpha) \dfrac{\lambda^{a+k-1}}{k!}e^{-(\beta+1)\lambda}}{\dfrac{\Gamma(a+k)}{\Gamma(\alpha)\Gamma(k+1)} \cdot (\dfrac{1}{\beta +1})^k \cdot (1 - \dfrac{1}{\beta+1})^{\alpha}}\\
    &= \dfrac{\beta^{\alpha} \dfrac{\lambda^{a+k-1}}{k!}e^{-(\beta+1)\lambda}}{\dfrac{\Gamma(a+k)}{\Gamma(k+1)} \cdot (\dfrac{1}{\beta +1})^k \cdot (1 - \dfrac{1}{\beta+1})^{\alpha}}\\
    &= \beta^\alpha\dfrac{\lambda^{\alpha+k+1}}{k!}e^{-(\beta+1)\lambda}\dfrac{\Gamma(k+1)}{\Gamma(\alpha+k)}(\beta+1)^{\alpha+k-1}\\
    &= \beta^\alpha\dfrac{\lambda^{\alpha+k+1}}{k!}e^{-(\beta+1)\lambda}\dfrac{k!}{\Gamma(\alpha+k)}(\beta+1)^{\alpha+k-1}\\
    &= \beta^\alpha\Gamma^{-1}(\alpha+k)(\beta+1)^{\alpha+k-1}\lambda^{\alpha+k+1}e^{-(\beta+1)\lambda} \\
    &= \beta^\alpha\Gamma^{-1}(\alpha+k)(\beta+1+\lambda)^{\alpha+k-1}e^{-(\beta+1)\lambda} \\
\end{align*}$$


#### Unabhängigkeit:
#unfinished 