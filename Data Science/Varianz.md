### Definition
* der Wert $Var(X):=E(|X-E(X)|^k)$ heißt Varianz der diskreten ZV X

#Präzision
* Reziproke der Varianz ($Var^{-1}(X)$)

#Standardabweichung
* $\sigma(X):=\sqrt{Var(X)}$ heißt Standardabweichung der diskreten ZV X

-----------

##### Verschiebungssatz:
Für beliebige diskrete ZV X gilt:

$$Var(X)=E(X^2)-E^2(X)$$

##### Beweis:
$$
\begin{align*}
    Var(X)&=E((X-E(X))^2) & \text{ | Def. Varianz}\\
    &=E(X^2-2XE(X)+(E(X))^2) & \text{ | Binomische Formel}\\
    &=\sum_x (x^2-2xE(X)+E^2(X))p_X(x) & |Def.\ Erwartugnswert\\
    &=\sum_x x^2 p_X(x)-\sum_x2xE(X)p_X(x)+\left(\sum_xxp_X(x)\right)^2 & |Linearität\ Summe\\
    &=E(X^2)-2 \sum_xx(\sum_yyp_X(y))p_X(x) + E^2(X) & \text{ | Def. E(X)}\\
    &=E(X^2)-2 \sum_xxp_X(x)\sum_yyp_X(y) + E^2(X) & \text{ | Kommutativität Multiplikation}\\
    &=E(X^2)-2E(X)E(X)+E^2(X) & \text{ | Def. E(X)}\\
    &=E(X^2)-2E^2(X)+E^2(X) & \text{ | Umformung}\\
    &=E(X^2)-E^2(X) & \text{ | Zusammenfassen}
\end{align*}
$$

* äquivalent zu absolut stetigen ZV X mit Integralen statt [[Summenzeichen]]

-----------

##### Skalierungsregel:
Für beliebige ZV X gilt:

$$ Var(aX+b) = a^2Var(X)$$

##### Beweis:
$$
\begin{align*}
    &Var(aX+b)\\
    &=E((aX+b)^2)-(E(aX+b))^2 & \text{ | Def. Var(X)}\\
    &=\sum_x(ax+b)^2p_X(x)-(a \cdot E(X) + b)^2 & \text{ | Def. \(E(X^2)\) und Beweis siehe Linearität Erwartungswert}\\
    &=\sum_x(a^2x^2p_X(x)+2axbp_X(x)+b^2p_X(x))-(a \cdot E(X) + b)^2 & \text{ | Binom. Formel und Ausmultipliziert}\\
    &=\sum_xa^2x^2p_X(x)+\sum_x2axbp_X(x)+\sum_xb^2p_X(x)-(a \cdot E(X) + b)^2 & \text{ | Einzelne Summanden auseinanderziehen}\\
    &=a^2\sum_xx^2p_X(x)+2ab\sum_xxp_X(x)+b^2\sum_xp_X(x)-(a \cdot E(X) + b)^2 & \text{ | Konstanten aus Summe ziehen}\\
    &=a^2E(X^2)+2abE(X)+b^2-(a \cdot E(X) + b)^2 & \text{ | Def. E(X\(^2\)), E(X) und } \sum_xp_X(x)=1\\
    &=a^2E(X^2)+2abE(X)+b^2-a^2(E(X))^2 - 2aE(X)b - b^2) & \text{ | Klammer auflösen}\\
    &=a^2E(X^2)-a^2(E(X))^2 & \text{ | zusammenfassen}\\
    &=a^2(E(X^2-(E(X))^2) & \text{ | Ausklammern}\\
    &=a^2Var(X) & \text{ | Def. Var(X)}
\end{align*}
$$
siehe [[Moment]]

* äquivalent zu absolut stetigen ZV mit Integralen statt [[Summenzeichen]]

#finished 