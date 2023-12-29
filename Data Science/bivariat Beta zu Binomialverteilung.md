
Beispiel:
* $\theta \in [0,1]$ wird von [[Betaverteilung]] gezogen 
* diskrete ZV K wird von Binomialverteilung und dem zuvor gezogenen $\theta$ gezogen

$$
\forall \theta \in [0,1]: p_\Theta(\theta)=B^{-1}(\alpha,\beta)\theta^{\alpha-1}(1-\theta)^{\beta-1} \; | \; Def. \; Betaverteilung \; mit \; t:=\theta$$
$$\forall k \in \{0,1,...,N\}: p_{K|\Theta}(k|\theta)=\left( \begin{array}{llll}
N\\
k\\
\end{array} \right)\theta^k(1-\theta)^{N-k} \; | \; Def. \; Binomialverteilung \; mit \; x:=k$$
#### gemeinsame Wahrscheinlichkeitsdichtefunktion

$$
\begin{align*}
    \forall \theta \in [0,1],k \in \{0,1,...,N\}:\rightarrow p_{K,\Theta}(k,\theta)&=p_\Theta(\theta) \cdot p_{K|\Theta}(k|\theta)\\
    &=B^{-1}(\alpha,\beta)\theta^{\alpha-1}(1-\theta)^{\beta-1} \cdot \left( \begin{array}{llll}
N\\
k\\
\end{array} \right)\theta^k(1-\theta)^{N-k}\\
    &=\underline{\underline{B^{-1}(\alpha,\beta)\left( \begin{array}{llll}
N\\
k\\
\end{array} \right)\theta^{\alpha+k-1}(1-\theta)^{\beta+N-k-1}}}
\end{align*}
$$
#### Randwahrscheinlichkeitsfunktion := Beta-Binomialverteilung

$$
\begin{align*}
    \forall k \in \{0,1,...,N\}:p_K(k)&= \int_0^1 p_{K,\theta}(k,\theta) d\theta & | \; Def. \; Randwahrscheinlichkeitsdichtefunktion\\
    &= \int_0^1B^{-1}(\alpha,\beta)\left( \begin{array}{llll}
N\\
k\\
\end{array} \right)\theta^{\alpha+k-1}(1-\theta)^{\beta+N-k-1} d\theta\\
    &=\left( \begin{array}{llll}
N\\
k\\
\end{array} \right) B^{-1}(\alpha,\beta) \int_0^1 \theta^{\alpha+k-1}(1-\theta)^{\beta+N-k-1} d\theta & |\; Linearität \; Konstanten\\
&= \left( \begin{array}{llll}
N\\
k\\
\end{array} \right) B^{-1}(\alpha,\beta) \cdot B(\alpha+k,\beta+N-k) &|\;Def. \; Betafunktion \; mit \;\alpha:=\alpha+k \; und \; \beta := \beta+N-k\\
    &= \left( \begin{array}{llll}
N\\
k\\
\end{array} \right) \dfrac{B(\alpha+k,\beta+N-k)}{B(\alpha,\beta)} 
\end{align*}
$$

#### Randwahrscheinlichkeitsdichtefunktion := Betaverteilung
$$  p_\Theta(\theta) := siehe\ oben$$

#### bedingte Wahrscheinlichkeitsfunktion $p_{K|\Theta}(k|\theta)$ := Binomialverteilung

$$p_{K|\Theta}(k|\theta):= siehe\ oben $$

#### bedingte Wahrscheinlichkeitsdichtefunktion $p_{\Theta|K}$ := Betaverteilung

$$\begin{align*}
    p_{\Theta|K}(k|\theta) &= \dfrac{p_{K,\Theta} (k,\theta)}{p_K(k)} & | \; Def. \; bedingte \; Wahrscheinlichkeitsfunktion\\
    &= \dfrac{B^{-1}(\alpha,\beta)\left( \begin{array}{llll}
N\\
k\\
\end{array} \right)\theta^{\alpha+k-1}(1-\theta)^{\beta+N-k-1}}{\left( \begin{array}{llll}
N\\
k\\
\end{array} \right) \dfrac{B(\alpha+k,\beta+N-k)}{B(\alpha,\beta)} }\\
    &=\dfrac{\theta^{\alpha+k-1}(1-\theta)^{\beta+N-k-1}}{B(\alpha+k,\beta+N-k)} & | \; Substitution:\ \alpha'=\alpha+k; \beta'=\beta+N-k\\
    &= B^{-1}(\alpha',\beta')\theta^{\alpha'-1}(1-\theta)^{\beta'-1} &| \; Umstellen
\end{align*}$$


#### Unabhängigkeit:
#unfinished 