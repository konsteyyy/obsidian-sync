#### Schlussregeln im Sequenzenkalkül

![[Pasted image 20240130151624.png]]

Beispiel:
Zeigen Sie mit Hilfe der Schlussregeln im Sequenzen-Kalkül:
$\{\neg q \vee r, q\} \vdash r$
Geben Sie bei jedem Schluss die verwendete Regel an.

Lösung:
$$\begin{align}
    \{\neg r, \neg q,q\} &\vdash q & (Ax)\\
    \{\neg r, \neg q,q\} &\vdash \neg q & (Ax)\\
    \{\neg q, q\} &\vdash r & (Wid) (1),(2)\\
    \{r,q\} &\vdash r & (Ax)\\
    \{\neg q \vee r, q\} &\vdash r & (Disj-A) (3),(4)
\end{align}$$
