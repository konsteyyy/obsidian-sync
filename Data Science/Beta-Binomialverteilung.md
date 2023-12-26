#### Definition
**Eine diskrete ZV X mit den Werten $x\in \{ 0,1,...,N\}$ mit $N \in \mathbb{N}$ und den Wahrscheinlichkeiten (s.u) heißt binomialverteilt**

----------------------- 

### [[Wahrscheinlichkeitsfunktion]]

$$\forall x\in\{0,1,...,N\}, \alpha\in \mathbb{R_+}, \beta \in \mathbb{R_+}:p_X(x|N,\theta) = \left( \begin{array}{llll}
N\\
x\\ 
\end{array} \right) \dfrac{B(\alpha +x,\beta+N-x)}{B(\alpha,\beta)}$$

----------------
### Erwartungswert/[[Moment]]

$$E(X) = \dfrac{N \alpha}{\alpha+\beta}$$ #erwartungswert

##### Herleitung:

$$
\begin{align*}
     E(X) &= \sum\limits_{x} x \cdot p_X(x) && |\text{Def. Erwartungswert} \\
	 &= \sum\limits_{x=0}^{N} x \cdot p_X(x|N,\alpha,\beta) && |\text{Def. Wahrsch. Beta-Binom. S.19} \\
	 &= \sum\limits_{x=0}^{N} x \cdot \left( \begin{array}{c} N \\ x\end{array}\right) \frac{B(\alpha +x, \beta +N-x)}{B(\alpha,\beta)}&& |\text{Def. Beta-Binom. S.19} \\
	 &= \sum\limits_{x=0}^{N} x \cdot \left( \begin{array}{c} N \\ x\end{array}\right) \left(\int_{0}^{1} t^{\alpha +x-1} \cdot (1-t)^{\beta +N-x-1} dt \right)\cdot \frac{1}{B(\alpha,\beta)}&& |\text{Def. Betafunktion S.19} \\
	 &= \sum\limits_{x=0}^{N} x \cdot \left( \begin{array}{c} N \\ x\end{array}\right) \left(\int_{0}^{1} t^{\alpha-1} \cdot t^x \cdot (1-t)^{\beta-1} \cdot (1-t)^{N-x} dt \right)\cdot \frac{1}{B(\alpha,\beta)}&& |\text{Umformen} \\
	 &= \left( \int_{0}^{1} \textcolor{magenta}{\sum\limits_{x=0}^{N} x \cdot \left( \begin{array}{c} N \\ x\end{array}\right) \cdot t^x \cdot (1-t)^{N-x}} \cdot t^{\alpha-1} \cdot (1-t)^{\beta-1} dt\right)\cdot \frac{1}{B(\alpha,\beta)}&& |\text{Umordnen} \\
	 &= \left( \int_{0}^{1} N\cdot t \cdot t^{\alpha-1} \cdot (1-t)^{\beta-1} dt\right)\cdot \frac{1}{B(\alpha,\beta)}&& |\text{$E(X)$ Binomialverteilung} \\
	 &= N \cdot\textcolor{magenta}{ \left( \int_{0}^{1} t \cdot B^{-1}(\alpha,\beta) t^{\alpha-1} \cdot (1-t)^{\beta-1} dt\right)} && |\text{N herausziehen und } B^{-1}(\alpha,\beta)\ reinziehen \\
	 &= \frac{N\alpha }{\alpha +\beta } && | E(X)\ Betaverteilung \\
	 
	 
\end{align*}
$$

-------------
### Varianz

$$
Var(X) = \dfrac{N\alpha\beta}{(\alpha+\beta)^2} \dfrac{N+\alpha+\beta}{1+\alpha+\beta}
$$

#varianz
##### Herleitung:

$$
\begin{align*}
    E(X^2) &= \sum\limits_{x} x^2 \cdot p_X(x) && |\text{Def. Erwartungswert} \\
	&= \sum\limits_{x=0}^{N} x^2 \cdot p_X(x|N,\alpha,\beta) && |\text{Def. Wahrsch. Beta-Binom. S.19} \\
	&= \sum\limits_{x=0}^{N} x^2 \cdot \left( \begin{array}{c} N \\ x\end{array}\right) \frac{B(\alpha +x, \beta +N-x)}{B(\alpha,\beta)}&& |\text{Def. Beta-Binom. S.19} \\
	&= \sum\limits_{x=0}^{N} x^2 \cdot \left( \begin{array}{c} N \\ x\end{array}\right) \left(\int_{0}^{1} t^{\alpha +x-1} \cdot (1-t)^{\beta +N-x-1} dt \right)\cdot \frac{1}{B(\alpha,\beta)}&& |\text{Def. Betafunktion S.19} \\
	&= \sum\limits_{x=0}^{N} x^2 \cdot \left( \begin{array}{c} N \\ x\end{array}\right) \left(\int_{0}^{1} t^{\alpha-1} \cdot t^x \cdot (1-t)^{\beta-1} \cdot (1-t)^{N-x} dt \right)\cdot \frac{1}{B(\alpha,\beta)}&& |\text{Umformen} \\
	&= \left( \int_{0}^{1} \textcolor{magenta}{\sum\limits_{x=0}^{N} x^2 \cdot \left( \begin{array}{c} N \\ x\end{array}\right) \cdot t^x \cdot (1-t)^{N-x}} \cdot t^{\alpha-1} \cdot (1-t)^{\beta-1} dt\right)\cdot \frac{1}{B(\alpha,\beta)}&& |\text{Umordnen} \\
	&= \left( \int_{0}^{1} (N^2t^2-Nt^2+Nt)  \cdot t^{\alpha-1} \cdot (1-t)^{\beta-1} dt\right)\cdot \frac{1}{B(\alpha,\beta)}&& |\text{$E(X^2)$ Binomialverteilung} \\
	&= \left( \int_{0}^{1} N(Nt^2-t^2+t)  \cdot t^{\alpha-1} \cdot (1-t)^{\beta-1} dt\right)\cdot \frac{1}{B(\alpha,\beta)} && |Ausklammern\\
	&= N\left( \int_{0}^{1} (Nt^2-t^2+t)  \cdot B^{-1}(\alpha,\beta)t^{\alpha-1} \cdot (1-t)^{\beta-1} dt\right) && |Konstante\ rausziehen\\
	&= N\left( \int_{0}^{1} Nt^2  \cdot B^{-1}(\alpha,\beta)t^{\alpha-1} \cdot (1-t)^{\beta-1} dt-\int_{0}^{1} t^2  \cdot B^{-1}(\alpha,\beta)t^{\alpha-1} \cdot (1-t)^{\beta-1} dt+ \textcolor{magenta}{\int_{0}^{1} t  \cdot B^{-1}(\alpha,\beta)t^{\alpha-1} \cdot (1-t)^{\beta-1} dt}\right)&&|Linearität\ Integrale\\
	&= N\left( \int_{0}^{1} Nt^2  \cdot B^{-1}(\alpha,\beta)t^{\alpha-1} \cdot (1-t)^{\beta-1} dt-\textcolor{magenta}{\int_{0}^{1} t^2  \cdot B^{-1}(\alpha,\beta)t^{\alpha-1} \cdot (1-t)^{\beta-1} dt}+\dfrac{\alpha}{\alpha+\beta}\right)&&|E(X)\ Betaverteilung\\
	&= N\left( \int_{0}^{1} Nt^2  \cdot B^{-1}(\alpha,\beta)t^{\alpha-1} \cdot (1-t)^{\beta-1} dt-\dfrac{\alpha^2+\alpha}{(\alpha+\beta+1)(\alpha+\beta)}+\dfrac{\alpha}{\alpha+\beta}\right)&&|E(X^2)\ Betaverteilung\\
	&= N\left( N\textcolor{magenta}{\int_{0}^{1} t^2  \cdot B^{-1}(\alpha,\beta)t^{\alpha-1} \cdot (1-t)^{\beta-1} dt}-\dfrac{\alpha^2+\alpha}{(\alpha+\beta+1)(\alpha+\beta)}+\dfrac{\alpha}{\alpha+\beta}\right)&&|N\ rausziehen\\
	&= N\left( \dfrac{N(\alpha^2+\alpha)}{(\alpha+\beta+1)(\alpha+\beta)}-\dfrac{\alpha^2+\alpha}{(\alpha+\beta+1)(\alpha+\beta)}+\dfrac{\alpha}{\alpha+\beta}\right)&&|E(X^2)\ Betaverteilung\\
	&= N\left( \dfrac{N\alpha^2+N\alpha-\alpha^2-\alpha+\alpha(\alpha+\beta+1)}{(\alpha+\beta+1)(\alpha+\beta)}\right) &&|gemeinsamer\ Nenner\\
	&= N\left( \dfrac{N\alpha^2+N\alpha-\alpha^2-\alpha+\alpha^2+\alpha\beta+\alpha}{(\alpha+\beta+1)(\alpha+\beta)}\right)&&|Ausmultiplizieren\\
	&= N\left( \dfrac{N\alpha^2+N\alpha+\alpha\beta}{(\alpha+\beta+1)(\alpha+\beta)}\right)\\
	Var(X)=E(X^2)-E^2(X) &= \dfrac{N^2\alpha^2+N^2\alpha+N\alpha\beta}{(\alpha+\beta+1)(\alpha+\beta)} - \left(\dfrac{N\alpha}{\alpha+\beta}\right)^2 && |Def.\ Varianz  \\
	&= \dfrac{(N^2\alpha^2+N^2\alpha+N\alpha\beta)(\alpha+\beta)-N^2\alpha^2(\alpha+\beta+1)}{(\alpha+\beta+1)(\alpha+\beta)^2} && |gemeinsamer\ Nenner\\
	&= \dfrac{N^2\alpha^3+N^2\alpha^2+N\alpha^2\beta+N^2\alpha^2\beta+N^2\alpha\beta+N\alpha\beta^2-N^2\alpha^3-N^2\alpha^2\beta-N^2\alpha^2}{(\alpha+\beta+1)(\alpha+\beta)^2} &&|Ausmultiplizieren\\
	&=\dfrac{N\alpha^2\beta+N^2\alpha^2\beta+N\alpha\beta^2}{(\alpha+\beta+1)(\alpha+\beta)^2} &&|Kürzen\\
	&=\dfrac{N\alpha\beta(\alpha+\beta+N}{(\alpha+\beta+1)(\alpha+\beta)^2}
\end{align*}
$$

-------

#unfinished 