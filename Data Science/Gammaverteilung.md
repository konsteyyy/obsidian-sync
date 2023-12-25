#### Definition
**Eine absolut stetige ZV X mit den Werten $t\in \mathbb R_+$ mit  den Wahrscheinlichkeiten (s.u) heißt gammaverteilt**

---------

### Erklärung


------------

### Beispiel


----------------------- 

### [[Wahrscheinlichkeitsfunktion]]

$$
\forall x\in \mathbb R_+, \alpha\in \mathbb R_+, \beta \in \mathbb R_+:p_X(t|\alpha,\beta) =\int^{\infty}_0t \cdot \beta^{\alpha} \cdot \Gamma^{-1}(\alpha) t^{\alpha-1} \cdot e^{-\beta t} dt
$$

----------------
### Erwartungswert/[[Moment]]

$$E(X) = \dfrac{\alpha}{\beta}$$ #erwartungswert

##### Herleitung:
$$
 \begin{align*}
    E(X) &=\int^{\infty}_0t \cdot p_X(t|\alpha,\beta) dt & | \; Def.\; E(X) \\
    &= \int^{\infty}_0t \cdot \beta^{\alpha} \cdot \Gamma^{-1}(\alpha) t^{\alpha-1} \cdot e^{-\beta t} dt & | \;Def. \; Gammaverteilungswahrscheinlichkeit\\
    &=\dfrac{\beta^{\alpha}}{\Gamma(\alpha)}\int^{\infty}_0t \cdot t^{\alpha-1} \cdot e^{-\beta t} dt & |\; Linearität \;Konstanten \\
    &=\dfrac{\beta^{\alpha}}{\Gamma(\alpha)}\int^{\infty}_0 t^{\textcolor{magenta}{(\alpha+1)-1}} \cdot e^{-\beta t} dt & |\; t \cdot t^{\alpha-1}=t^{(\alpha+1)-1}\\
    &=\dfrac{\beta^{\alpha}}{\Gamma(\alpha)}\int^{\infty}_0 (\dfrac{u}{\beta})^{(\alpha+1)-1} \cdot e^{-u} \frac{du}{\beta} & |\; Substitution\;u=\beta t <=> t= \dfrac{u}{\beta}\\
    &=\dfrac{\beta^{\alpha}}{\Gamma(\alpha)}\int^{\infty}_0 \dfrac{u^{(\alpha+1)-1}}{\beta^{(\alpha+1)-1}} \cdot e^{-u} \frac{du}{\beta} & |\; Potenzgesetz\; Division\\
    &=\dfrac{\beta^{\alpha}}{\Gamma(\alpha)\textcolor{magenta}{\beta^{\alpha}}}\int^{\infty}_0 u^{(\alpha+1)-1} \cdot e^{-u} \frac{du}{\beta} & |\; Linearität\; Konstanten\\
    &=\dfrac{\beta^{\alpha}}{\Gamma(\alpha)\beta^{\alpha}} \frac{\Gamma(\alpha+1)}{\beta} & |\; Def. \; Gammafunktion\\
    &= \dfrac{\beta^{\alpha}}{\Gamma(\alpha)\beta^{\alpha}} \frac{\alpha \Gamma(\alpha)}{\beta} & |\; \Gamma(\alpha+1)=\alpha \Gamma(\alpha)\\
    &= \dfrac{\alpha}{\beta} & |\; Kürzen
\end{align*}
$$

-------------
### Varianz
$$
Var(X) = \dfrac{\alpha}{\beta^2}
$$

#varianz
##### Herleitung:

$$
 \begin{align*}
    E(X^2) &=\int^{\infty}_0t^2 \cdot p_X(t|\alpha,\beta) dt & | \; Def.\; E(X) \\
    &= \int^{\infty}_0t^2 \cdot \beta^{\alpha} \cdot \Gamma^{-1}(\alpha) t^{\alpha-1} \cdot e^{-\beta t} dt & | \;Def. \; Gammaverteilungswahrscheinlichkeit\\
    &=\dfrac{\beta^{\alpha}}{\Gamma(\alpha)}\int^{\infty}_0t^2 \cdot t^{\alpha-1} \cdot e^{-\beta t} dt & |\; Linearität \;Konstanten \\
    &=\dfrac{\beta^{\alpha}}{\Gamma(\alpha)}\int^{\infty}_0 t^{\textcolor{magenta}{(\alpha+2)-1}} \cdot e^{-\beta t} dt & |\; t \cdot t^{\alpha-1}=t^{(\alpha+1)-1}\\
    &=\dfrac{\beta^{\alpha}}{\Gamma(\alpha)}\int^{\infty}_0 (\dfrac{u}{\beta})^{(\alpha+2)-1} \cdot e^{-u} \frac{du}{\beta} & |\; Substitution\;u=\beta t <=> t= \dfrac{u}{\beta}\\
    &=\dfrac{\beta^{\alpha}}{\Gamma(\alpha)}\int^{\infty}_0 \dfrac{u^{(\alpha+2)-1}}{\beta^{(\alpha+2)-1}} \cdot e^{-u} \frac{du}{\beta} & |\; Potenzgesetz\; Division\\
    &=\dfrac{\beta^{\alpha}}{\Gamma(\alpha)\textcolor{magenta}{\beta^{\alpha+1}}}\int^{\infty}_0 u^{(\alpha+2)-1} \cdot e^{-u} \frac{du}{\beta} & |\; Linearität\; Konstanten\\
    &=\dfrac{\beta^{\alpha}}{\Gamma(\alpha)\beta^{\alpha+1}} \frac{\Gamma(\alpha+2)}{\beta} & |\; Def. \; Gammafunktion\\
    &= \dfrac{\beta^{\alpha}}{\Gamma(\alpha)\beta^{\alpha+1}} \frac{(\alpha+1) \Gamma(\alpha+1)}{\beta} & |\; \Gamma(\alpha+2)=(\alpha+1) \Gamma(\alpha+1)\\
    &= \dfrac{\beta^{\alpha}}{\Gamma(\alpha)\beta^{\alpha+1}} \frac{(\alpha+1) \alpha \Gamma(\alpha)}{\beta} & |\; \Gamma(\alpha+1)=\alpha \Gamma(\alpha)\\
    &= \dfrac{\alpha^2+\alpha}{\beta^2}\\
    Var(X) = E(X^2) - E^2(X) &= \dfrac{\alpha^2+\alpha}{\beta^2} - \left( \dfrac{\alpha}{\beta}\right)^2 & |\; Def.\ Varianz\\
    &= \dfrac{\alpha^2+\alpha-\alpha^2}{\beta^2} \\
    &=  \dfrac{\alpha}{\beta^2}
\end{align*}
$$ 
---------------

#unfinished 