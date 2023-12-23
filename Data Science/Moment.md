* Spezialfall k=0 := Erwartungswert

$$E(X)= \sum_x x \cdot p_X(x)$$
[[Summenzeichen]]
* lässt sich auch verbal folgendermaßen formulieren:
	* "Das gewichtete arithmetische Mittel aller Ereignisse der Zufallsvariable"

-------------------------------
### k-tes Moment der diskreten [[Zufallsvariable]] X
$$\lambda_k(X) = \sum_xx^k \cdot p_X(x)$$
-----------------
### Beispiel X=Regen

Ereignis | Wahrscheinlichkeit
----- | -------
$x_1$ = Regen | 0,3
$x_2 = \overline{Regen}$ |0,7

Wenn wir für Regen = 2 und $\overline{Regen}$ = 3, dann gilt:

$E(X) = 2 \cdot 0,3 + 3 \cdot 0,7 = 2,7$

-----------------
### Linearität Erwartungswert

##### Für beliebige diskrete ZV X und beliebige reelle Zahlen a und b gilt :
$$E(a X + b) = a E(X) + b$$

##### Beweis:
$$\begin{align*}
    E(aX+b) &= \sum\limits_{x} (ax+b) \cdot p_{X} (x) &&|\text{Def. Erwartungswert} \\
    &= \sum\limits_{x} \left(axp_{X}(x) + bp_{X}(x) \right) &&|\text{Distributivgesetz Multiplikation}\\
    &= \sum\limits_{x} axp_{X} (x) +\sum\limits_{x} bp_{X} (x) &&|\text{Summe aufspalten}\\ % Assoziativgesetz!!!
    &= a \cdot \sum\limits_{x} xp_{X}(x) + b \cdot \sum\limits_{x} p_{X}(x) &&|\text{Linearität Summenzeichen}\\ 
    &= a\cdot E(X) + b \sum\limits_{x} p_{X}(x) &&|\text{Def. E(X)}\\
    &= a\cdot E(X) + b && |\sum\limits_{x} p_{X}(x) = 1
\end{align*} $$

#finished 

