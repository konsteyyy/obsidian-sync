#### Definition
**Eine diskrete ZV X mit den Werten $x\in \{ 0,1,...,N\}$ mit $N \in \mathbb{N}$ und den Wahrscheinlichkeiten (s.u) heißt binomialverteilt**

----------------------- 

### [[Wahrscheinlichkeitsfunktion]]

$$
\forall x\in\{0,1,...,N\}, \lambda\in[0,1]:p_X(x|N,\theta) = \left( \begin{array}{llll}
N\\
x\\ 
\end{array} \right) \theta ^x (1-\theta)^{N-x}
$$

----------------
### Erwartungswert/[[Moment]]

$$E[X] = N \theta$$ #erwartungswert

##### Herleitung:
$$
\begin{align*}
    E[X] &=\sum_xxp_X(x)\\
    &= \sum_{x=0}^Nxp_X(x|N,\theta) & \\
    &= \sum_{x=0}^Nx\left( \begin{array}{llll}
N\\
x\\
\end{array} \right) \theta ^x (1-\theta)^{N-x} & | Def. Binomialverteilungswahrscheinlichkeit\\
&= \sum_{\textcolor{magenta}{x=1}}^Nx\left( \begin{array}{llll}
N\\
x\\
\end{array} \right) \theta ^x (1-\theta)^{N-x} & | Indexverschiebung\ um\ 1\\
&= \sum_{x=1}^N \textcolor{magenta}x \dfrac{N!}{\textcolor{magenta}{x(x-1)!} (N-x)!} \theta^x (1-\theta)^{N-x} & |x!=x(x-1)!\ und\ kürzen\\
&= \sum_{x=1}^N \dfrac{\textcolor{magenta}N(N-1)!}{(x-1)! ((N-1)-(x-1))!} \textcolor{magenta}\theta \theta^{x-1} (1-\theta)^{(N-1)-(x-1)} & |a^x = aa^{x-1} \text{ und } (a-b) = ((a-1)-(b-1))\\
&= {N\theta} \sum_{x=1}^N \dfrac{(N-1)!}{(x-1)! ((N-1)-(x-1))!} \theta^{x-1} (1-\theta)^{(N-1)-(x-1)} & | \text{ Faktoren aus der Summe ziehen }\\
&= N\theta \sum_{x'=0}^{N'} \dfrac{N'!}{x'! (N'-x')!} \theta^{x'} (1-\theta)^{N'-x'} & |Substitution:\ x'=x-1 <=> x=x'+1 \ und \ N'=N-1\\
&= N\theta \sum_{x'=0}^{N'} \left( \begin{array}{llll}
N'\\
x\\
\end{array} \right) \theta^{x'} (1-\theta)^{N'-x'}\\
&= N\theta & | \text{ weil } \sum_{x'=0}^{N'}p_{X'}(x'|N',\theta) = 1 
\end{align*}
$$

-------------
### Varianz
$$
Var(X) = N\theta(1-\theta)
$$

#varianz
##### Herleitung:
$$
\begin{align*}
    E(X^2) &= \sum_{x=0}^Nx^2p_X(x|N,\theta)  \\
    &= \sum_{x=0}^Nx^2\left( \begin{array}{llll}
N\\
x\\
\end{array} \right) \theta ^x (1-\theta)^{N-x} & |Def. Binomialverteilungswahrscheinlichkeit\\
&= \sum_{\textcolor{magenta}{x=1}}^Nx^2\left( \begin{array}{llll}
N\\
x\\
\end{array} \right) \theta ^x (1-\theta)^{N-x} & | Indexverschiebung\ um\ 1\\
&= \sum_{x=1}^N \textcolor{magenta}{x²} \dfrac{N!}{\textcolor{magenta}{x(x-1)!} (N-x)!} \theta^x (1-\theta)^{N-x} & |x!=x(x-1)!\ und\ kürzen\\
&= \sum_{x=1}^N x\dfrac{N(N-1)!}{(x-1)! ((N-1)-(x-1))!} \theta \theta^{x-1} (1-\theta)^{(N-1)-(x-1)} & |a^x = aa^{x-1} \text{ und } (a-b) = ((a-1)-(b-1))\\
&= \textcolor{magenta}{N\theta} \sum_{x=1}^N x\dfrac{(N-1)!}{(x-1)! ((N-1)-(x-1))!} \theta^{x-1} (1-\theta)^{(N-1)-(x-1)} & | \text{ Faktoren aus der Summe ziehen }\\
&= N\theta \sum_{x'=0}^{N'} \textcolor{magenta}{(x'+1)} \dfrac{N'!}{x'! (N'-x')!} \theta^{x'} (1-\theta)^{N'-x'} & |Substitution:\ x'=x-1 <=> x=x'+1 \ und \ N'=N-1\\
&= N\theta \left( \sum_{x'=0}^{N'} x' \dfrac{N'!}{x'! (N'-x')!} \theta^{x'} (1-\theta)^{N'-x'} + \textcolor{magenta}{\sum_{x'=0}^{N'} \dfrac{N'!}{x'! (N'-x')!} \theta^{x'} (1-\theta)^{N'-x'}} \right) & |Linearität\ der\ Summation\\
&= N\theta \left( \sum_{x'=0}^{N'} x' \textcolor{magenta}{\dfrac{N'!}{x'! (N'-x')!} \theta^{x'} (1-\theta)^{N'-x'}} + 1 \right) & |Normiertheit\ der\ Wahrscheinlichkeitsfunktion\\
&= N\theta \left( \textcolor{magenta}{\sum_{x'=0}^{N'} x' p_{X'}(x'|N',\theta)} + 1 \right) & | Def. Binomialverteilungswahrscheinlichkeit\\
&= N\theta \left( N'\theta  + 1 \right) & |Def. E(X')\\
&= N \theta ((N-1)\theta + 1)\\
&= N\theta(N\theta-\theta+1)\\
&= N^2 \theta^2-N\theta^2+N\theta\\
Var(X)= E(X^2)-E^2(X) &=N^2 \theta^2-N\theta^2+N\theta - N^2\theta^2 & |Verschiebungssatz\\
&=N\theta - N\theta^2\\
&=N\theta ( 1-\theta)
\end{align*}
$$

---------------

#unfinished 