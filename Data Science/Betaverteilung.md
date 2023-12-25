#### Definition
**Eine absolut stetige ZV X mit den Werten $t\in [ 0,1]$ mit  den Wahrscheinlichkeiten (s.u) heißt betaverteilt**

---------

### Erklärung


------------

### Beispiel


----------------------- 

### [[Wahrscheinlichkeitsfunktion]]

$$
\forall x\in [0,1], \alpha\in \mathbb R_+, \beta \in \mathbb R_+:p_X(t|\alpha,\beta) =\int_{0}^{1}t \cdot B^{-1}(\alpha,\beta)t^{\alpha-1}(1-t)^{\beta-1}dt
$$

----------------
### Erwartungswert/[[Moment]]

$$E(X) = \dfrac{\alpha}{\alpha + \beta}$$ #erwartungswert

##### Herleitung:
$$
\begin{align*}
    E(X) &= \int_{0}^{1}tp_X(t|\alpha, \beta)dt & | \ Def. \ E(X)\\
    &=\int_{0}^{1}t \cdot B^{-1}(\alpha,\beta)t^{\alpha-1}(1-t)^{\beta-1}dt & | \ Def. \ p_X(t|\alpha,\beta)\\
    &= B^{-1}(\alpha,\beta)\int_{0}^{1}t \cdot t^{\alpha-1}(1-t)^{\beta-1}dt & | \ Linearität\ Konstanten\\
    &= B^{-1}(\alpha,\beta)\int_{0}^{1} t^{(\alpha+1)-1}(1-t)^{\beta-1}dt & | \ t \cdot t^{\alpha+1} = t^{(\alpha+1)-1}\\
    &= B^{-1}(\alpha,\beta) \cdot B(\alpha +1, \beta) & | \ Def. \ Betafunktion\\
    &= \dfrac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)\Gamma(\beta)} \cdot \dfrac{\Gamma(\alpha+1)\Gamma(\beta)}{\Gamma(\alpha+\beta+1)} & | \ Satz \ Betafunktion \ zu \ Gammafunktion\\
    &=\dfrac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)} \cdot \dfrac{\Gamma(\alpha+1)}{\Gamma(\alpha+\beta+1)} & | \ Kürzen\\
    &= \dfrac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)} \cdot \dfrac{\alpha\Gamma(\alpha)}{\Gamma(\alpha+\beta+1)} & |\ Satz \ Gammafunktion \ über \ Reelle \ Zahlen\\
    &= \Gamma(\alpha+\beta) \cdot \dfrac{\alpha}{\Gamma(\alpha+\beta+1)} &| \ Kürzen\\
    &= \dfrac{\alpha}{\alpha + \beta}& | \ Kürzen\\
\end{align*}
$$

-------------
### Varianz
$$
Var(X) = \dfrac{\alpha \beta}{(\alpha+\beta+1)(\alpha+\beta)^2}
$$

#varianz
##### Herleitung:
$$
\begin{align*}
    E(X^2) &= \int_{0}^{1}t^2p_X(t|\alpha, \beta)dt & | \ Def. \ E(X)\\
    &=\int_{0}^{1}t^2 \cdot B^{-1}(\alpha,\beta)t^{\alpha-1}(1-t)^{\beta-1}dt & | \ Def. \ p_X(t|\alpha,\beta)\\
    &= B^{-1}(\alpha,\beta)\int_{0}^{1}t^2 \cdot t^{\alpha-1}(1-t)^{\beta-1}dt & | \;Linearität\ Konstanten\\
    &= B^{-1}(\alpha,\beta)\int_{0}^{1} t^{\textcolor{magenta}{(\alpha+2)-1}}(1-t)^{\beta-1}dt & | \ t^2 \cdot t^{\alpha-1} = t^{(\alpha+2)-1}\\
    &= B^{-1}(\alpha,\beta) \cdot B(\alpha +2, \beta) & | \ Def. \ Betafunktion\\
    &= \dfrac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)\textcolor{magenta}{\Gamma(\beta)}} \cdot \dfrac{\Gamma(\alpha+2)\textcolor{magenta}{\Gamma(\beta)}}{\Gamma(\alpha+\beta+2)} & | \ Satz \ Betafunktion \ zu \ Gammafunktion\\
    &=\dfrac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)} \cdot \dfrac{\textcolor{magenta}{\Gamma(\alpha+2)}}{\textcolor{magenta}{\Gamma(\alpha+\beta+2)}} & | \ Kürzen\\
    &= \dfrac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)} \cdot \dfrac{(\alpha+1)\textcolor{magenta}{\Gamma(\alpha+1)}}{(\alpha+\beta+1)\textcolor{magenta}{\Gamma(\alpha+\beta+1)}} & |\ Satz \ Gammafunktion \ über \ Reelle \ Zahlen\\
    &= \dfrac{\Gamma(\alpha+\beta)}{\textcolor{magenta}{\Gamma(\alpha)}} \cdot \dfrac{(\alpha+1)\alpha\textcolor{magenta}{\Gamma(\alpha)}}{(\alpha+\beta+1)(\alpha+\beta)\Gamma(\alpha+\beta)} & |\ Satz \ Gammafunktion \ über \ Reelle \ Zahlen\\
    &= \dfrac{(\alpha+1)\alpha}{(\alpha+\beta+1)(\alpha+\beta)} &| \ Kürzen\\
    Var(X)= E(X²)-E²(X) &= \dfrac{(\alpha+1)\alpha}{(\alpha+\beta+1)(\alpha+\beta)} - \left( \dfrac{\alpha}{\alpha + \beta}\right)^2& | \ Def.\ Varianz\\
    &= \dfrac{\alpha^2+\alpha}{(\alpha+\beta+1)(\alpha+\beta)} -  \dfrac{\alpha^2}{(\alpha + \beta)^2} & | \ Ausmultiplizieren\\
    &= \dfrac{(\alpha^2+\alpha)(\alpha+\beta)^{\textcolor{magenta}{2}}- \alpha^2(\alpha+\beta+1)\textcolor{magenta}{(\alpha+\beta)}}{(\alpha+\beta+1)(\alpha+\beta)^{\textcolor{magenta}{3}}} & |\ gemeinsamer\ Nenner\\
	&= \dfrac{(\alpha^2+\alpha)(\alpha+\beta)- \alpha^2(\alpha+\beta+1)}{(\alpha+\beta+1)(\alpha+\beta)^2} & |Kürzen\\
	&= \dfrac{\alpha^3+\alpha^2\beta+\alpha^2+\alpha \beta - (\alpha^3+\alpha^2\beta+\alpha^2)}{(\alpha+\beta+1)(\alpha+\beta)^2} & |Ausmultiplizieren\ und\ Kürzen\\
	&= \dfrac{\alpha \beta}{(\alpha+\beta+1)(\alpha+\beta)^2}
\end{align*}
$$ 
---------------

#unfinished 