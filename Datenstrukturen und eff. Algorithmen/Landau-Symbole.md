### #Big-O-Notation

- **Definition**: Eine Funktion f(n) ist in O(g(n)), wenn es eine Konstante  c>0 und eine Schranke  $n_0$​ gibt, so dass für alle  $n>n_0$​ gilt:  $f(n)≤c\cdot g(n)$.
- **Anwendung**: Nutzen wir oft, um die obere Schranke der Laufzeit eines Algorithmus anzugeben, also ein Worst-Case-Szenario.

### Big Omega (Ω) - Untere Schranke

- **Definition**: Eine Funktion f(n) ist in Ω(g(n)), wenn es eine Konstante c>0 und eine Schranke  $n_0$​ gibt, so dass für alle  $n>n_0​$ gilt:  $f(n)≥c \cdot g(n)$.
- **Anwendung**: Wird genutzt, um die untere Schranke der Laufzeit eines Algorithmus anzugeben, also ein Best-Case-Szenario.

### Big Theta (Θ) - Exakte Ordnung

- **Definition**: Eine Funktion f(n) ist in Θ(g(n)), wenn sie sowohl in O(g(n)) als auch in Ω(g(n)) ist.
- **Anwendung**: Verwendet man, um eine enge Schranke der Laufzeit eines Algorithmus anzugeben, also wenn obere und untere Schranke im Wesentlichen gleich sind.

### Kleines o  - Strengere obere Schranke

- **Definition**: Eine Funktion f(n) ist in o(g(n)), wenn folgendes gilt:

$$ \lim_{n->\infty} \dfrac{f(n)}{g(n)} = 0$$
- **Anwendung**: Zeigt, dass g(n) im Vergleich zu f(n) strikt schneller wächst.

### Kleines Omega ( ω) - Strengere untere Schranke

- **Definition**: Eine Funktion f(n) ist in ω(g(n)), wenn folgendes gilt:
$$ \lim_{n->\infty} \dfrac{f(n)}{g(n)} = \infty$$
- **Anwendung**: Ähnlich wie kleines o, nur dass f(n) strikt schneller wächst als g(n).

#unfinished 
//ein Beispiel jeweiles wäre noch gut