### Definition
**Eine diskrete ZV X mit den Werten $x \in \mathbb{N}$ und den Wahrscheinlichkeiten (s.u) heißt poissonverteilt**

----------------------

### Erklärung
* wird verwendet, um die Anzahl der Ereignisse in einem festen Zeitintervall/Raumintervall zu modellieren
* $\lambda$ steht dabei für das Zeit-/Raumintervall

--------------

### Beispiel

Angenommen, man betreibt eine Website, bei der im Durchschnitt 5 Kundenanfragen pro Stunde eingehen
Gesucht: $p_X(x|\lambda)$ ...Wahrscheinlichkeit dafür, dass in 2 Stunden x Anfragen eingehen:
* $\lambda$ = 2 $\cdot$ 5=10 (Anzahl Anfragen pro 2 Stunden)
* $x\in \mathbb N$ (Ereignis x=1,2,3,...)
* $p_X(1|10)=\dfrac{10¹}{1!} \cdot e^{-10}= 0,0454\%$                     -> Die Wahrscheinlichkeit, dass in 2 Stunden nur eine Anfrage an die Website gestellt werden, ist 0,0454%
* $p_X(10|10)=\dfrac{10^{10}}{10!} \cdot e^{-10}= 12,511\%$                 -> Die Wahrscheinlichkeit, dass in 2 Stunden insgesamt 10 Anfragen an die Website gestellt werden, ist 12,511%

---------------

### [[Wahrscheinlichkeitsfunktion]]

$$\forall \lambda \in \mathbb{R}_+, x \in \mathbb{N} : p_X(x|\lambda) = \dfrac{\lambda^x}{x!} e^{-\lambda}$$

----------------

### Erwartungswert/[[Moment]]

$$E(X) = \lambda$$

#erwartungswert
#### Herleitung:

$$ 
\begin{align*}
E(X) &=\sum_{x=0}^{\infty} x \dfrac{\lambda^x}{x!} e^{-\lambda} && |Def.\ p_X(x|\lambda)\ Poissonverteilung\\
&=\sum_{x=1}^{\infty} x \dfrac{\lambda^x}{x!} e^{-\lambda} && |Indexverschiebung\ um\ 1\\
&=\sum_{x=1}^{\infty} x \dfrac{\textcolor{magenta}\lambda \lambda^{x-1}}{\textcolor{magenta}x(x-1)!} e^{-\lambda}
 && | Fakultätsregel\ a!=a(a-1)!\\
&=\textcolor{magenta}\lambda \sum_{x=1}^{\infty} \dfrac{\lambda^{x-1}}{(x-1)!} e^{-\lambda} && |Linearität\ Summenzeichen\\
&=\lambda \sum_{x'=0}^{\infty} \dfrac{\lambda^{x'}}{x'!} e^{-\lambda} && |Substitution: x'=x-1\\
&=\lambda && |\sum_{x'=0}^\infty p_{X'}(x'|\lambda) = 1
\end{align*}
$$

-----------
### Varianz

$$
Var(X) = \lambda
$$

#### Herleitung:

$$
\begin{align*}
E(X^2) &=\sum_{x=0}^{\infty} x² \dfrac{\lambda^x}{x!} e^{-\lambda} && |Def.\ p_X(x|\lambda)\ Poissonverteilung\\
&=\sum_{\textcolor{magenta}{x=1}}^{\infty} x² \dfrac{\lambda^x}{x!} e^{-\lambda} && |Indexverschiebung\ um\ 1\\
&=\sum_{x=1}^{\infty} x² \dfrac{\textcolor{magenta}\lambda \lambda^{x-1}}{\textcolor{magenta}x(x-1)!} e^{-\lambda}
 && | Fakultätsregel\ a!=a(a-1)!\\
&=\textcolor{magenta}\lambda \sum_{x=1}^{\infty} x\dfrac{\lambda^{x-1}}{(x-1)!} e^{-\lambda} && |Konstanten\ aus\ Summe\\
&=\lambda \sum_{x'=0}^{\infty} (\textcolor{magenta}{x'+1})\dfrac{\lambda^{x'}}{x'!} e^{-\lambda} && |Substitution: x'=x-1\\
&=\lambda \left( \sum_{x'=0}^{\infty} x'\dfrac{\lambda^{x'}}{x'!} e^{-\lambda} + \sum_{x'=0}^{\infty} \dfrac{\lambda^{x'}}{x'!} e^{-\lambda}\right) && |Linearität\ Summe\\
&= \lambda (\lambda +1) && | Def. E(X')\ und\ Normiertheit\ der\ Wahrscheinlichkeiten\\
Var(X) = E(X²)-E²(X) &= \lambda²+\lambda-\lambda²\\
&= \lambda
\end{align*}
$$

#varianz

#finished 