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

$$\begin{align*}
    E(X) &= \sum\limits_{x} x \cdot p_X(x) && |\text{Def. Erwartungswert} \\
	 &= \sum\limits_{x=0}^{N} x \cdot p_X(x|N,\alpha,\beta) && |\text{Def. Wahrsch. Beta-Binom. S.19} \\
	 &= \sum\limits_{x=0}^{N} x \cdot \left( \begin{array}{c} N \\ x\end{array}\right) \frac{B(\alpha +x, \beta +N-x)}{B(\alpha,\beta)}&& |\text{Def. Beta-Binom. S.19} \\
	 &= \sum\limits_{x=0}^{N} x \cdot \left( \begin{array}{c} N \\ x\end{array}\right) \left(\int_{0}^{1} t^{\alpha +x-1} \cdot (1-t)^{\beta +N-x-1} dt \right)\cdot \frac{1}{B(\alpha,\beta)}&& |\text{Def. Betafunktion S.19} \\
	 &= \sum\limits_{x=0}^{N} x \cdot \left( \begin{array}{c} N \\ x\end{array}\right) \left(\int_{0}^{1} t^{\alpha-1} \cdot t^x \cdot (1-t)^{\beta-1} \cdot (1-t)^{N-x} dt \right)\cdot \frac{1}{B(\alpha,\beta)}&& |\text{Umformen} \\
	 &= \left( \int_{0}^{1} \textcolor{magenta}{\sum\limits_{x=0}^{N} x \cdot \left( \begin{array}{c} N \\ x\end{array}\right) \cdot t^x \cdot (1-t)^{N-x}} \cdot t^{\alpha-1} \cdot (1-t)^{\beta-1} dt\right)\cdot \frac{1}{B(\alpha,\beta)}&& |\text{Umordnen} \\
	 &= \left( \int_{0}^{1} N\cdot t \cdot t^{\alpha-1} \cdot (1-t)^{\beta-1} dt\right)\cdot \frac{1}{B(\alpha,\beta)}&& |\text{$E(X)$ Binomialverteilung} \\
	 &= N \cdot \left( \int_{0}^{1} t \cdot t^{\alpha-1} \cdot (1-t)^{\beta-1} dt\right)\cdot \frac{1}{B(\alpha,\beta)}&& |\text{Konstanten herausziehen} \\
	 &= N \cdot \left( \int_{0}^{1}  t^{(\alpha+1)-1} \cdot (1-t)^{\beta-1} dt\right)\cdot \frac{1}{B(\alpha,\beta)}&& |\text{Potenzgesetze} \\
	 &= N \cdot \frac{B(\alpha+1,\beta)}{B(\alpha,\beta)}&& |\text{Betafunktion, univar. S.19} \\
	 &= N \cdot \frac{\Gamma(\alpha+1)\cdot \textcolor{magenta}{\Gamma(\beta)}}{\Gamma(\alpha +1+\beta)} \cdot \frac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)\cdot \textcolor{magenta}{\Gamma(\beta)}}&& |\text{Satz 3 S.19} \\
	 &= N \cdot \frac{\Gamma(\alpha+1) \cdot \Gamma(\alpha+\beta)}{\Gamma(\alpha +1+\beta)\cdot \Gamma(\alpha)} && |\text{Kürzen} \\
	 &= N \cdot \frac{\alpha\textcolor{magenta}{\Gamma(\alpha)} \cdot \Gamma(\alpha+\beta)}{\Gamma(\alpha +1+\beta)\cdot \textcolor{magenta}{\Gamma(\alpha)}} && |\text{Satz 2 S. 19} \\
	 &= N \cdot \frac{\alpha \cdot \Gamma(\alpha+\beta)}{\Gamma(\alpha +1+\beta)} && |\text{Kürzen} \\
	 &= N \cdot \frac{\alpha \cdot \textcolor{magenta}{\Gamma(\alpha+\beta)}}{(\alpha + \beta)\textcolor{magenta}{\Gamma(\alpha+\beta)}} && |\text{Satz 2. S.19}  \\
	 &= N \cdot \frac{\alpha }{(\alpha +\beta )} && |\text{Kürzen} 
\end{align*}$$

-------------
### Varianz

$$
Var(X) = \dfrac{N\alpha\beta}{(\alpha+\beta)^2} \dfrac{N+\alpha+\beta}{1+\alpha+\beta}
$$

##### Herleitung:

$$
test
$$

#varianz

#unfinished 