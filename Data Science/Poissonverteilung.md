### Definition
**Eine diskrete ZV X mit den Werten $x \in \mathbb{N}$ und den Wahrscheinlichkeiten (s.u) heißt poissonverteilt

### [[Wahrscheinlichkeitsfunktion]]

$$\forall \lambda \in \mathbb{R}_+, x \in \mathbb{N} : p_X(x|\lambda) = x \dfrac{\lambda^x}{x!} e^{-\lambda}$$

----------------

### Erwartungswert/[[Moment]]

$$E(X) = \lambda$$

#erwartungswert
#### Herleitung:

$$ 
\begin{align*}
E(X) &=\sum_{x=0}^{\infty} x \dfrac{\lambda^x}{x!} e^{-\lambda} && |Def.\ p_X(x|\lambda)\ Poissonverteilung\\
&=\sum_{x=1}^{\infty} x \dfrac{\lambda^x}{x!} e^{-\lambda} && |Indexverschiebung\ um\ 1\\
&=\sum_{x=1}^{\infty} x \dfrac{\textcolor{aqua}\lambda \lambda^{x-1}}{\textcolor{aqua}x(x-1)!} e^{-\lambda}
 && | Fakultätsregel\ a!=a(a-1)!\\
&=\textcolor{aqua}\lambda \sum_{x=1}^{\infty} \dfrac{\lambda^{x-1}}{(x-1)!} e^{-\lambda} && |Linearität\ Summenzeichen\\
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
&=\sum_{\textcolor{aqua}{x=1}}^{\infty} x² \dfrac{\lambda^x}{x!} e^{-\lambda} && |Indexverschiebung\ um\ 1\\
&=\sum_{x=1}^{\infty} x² \dfrac{\textcolor{aqua}\lambda \lambda^{x-1}}{\textcolor{aqua}x(x-1)!} e^{-\lambda}
 && | Fakultätsregel\ a!=a(a-1)!\\
&=\textcolor{aqua}\lambda \sum_{x=1}^{\infty} x\dfrac{\lambda^{x-1}}{(x-1)!} e^{-\lambda} && |Konstanten\ aus\ Summe\\
&=\lambda \sum_{x'=0}^{\infty} (\textcolor{aqua}{x'+1})\dfrac{\lambda^{x'}}{x'!} e^{-\lambda} && |Substitution: x'=x-1\\
&=\lambda \left( \sum_{x'=0}^{\infty} x'\dfrac{\lambda^{x'}}{x'!} e^{-\lambda} + \sum_{x'=0}^{\infty} \dfrac{\lambda^{x'}}{x'!} e^{-\lambda}\right) && |Linearität\ Summe\\
&= \lambda (\lambda +1) && | Def. E(X')\ und\ Normiertheit\ der\ Wahrscheinlichkeiten\\
Var(X) = E(X²)-E²(X) &= \lambda²+\lambda-\lambda²\\
&= \lambda
\end{align*}
$$

#varianz

#unfinished 