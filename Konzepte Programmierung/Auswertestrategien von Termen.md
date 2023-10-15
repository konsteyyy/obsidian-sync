### faule Auswertung (lazy evaluation)
* "von außen nach innen, von links nach rechts"
* man schaut sich zu erst die äußerste Ebene an und geht an dieser alle Axiome durch


### gierige Auswertung (eager evaluation)
* "von Innen nach Außen"
* man schaut sich zu erst die innerste Ebene an und guckt ob an dieser ein Axiom funktioniert

### Beispiel:
Axioms:
(1) plus(n,Null) = n 
(2) plus(n,Succ(m)) = Succ(plus(n,m)) 
(3) mal(n,Null) = Null 
(4) mal(n,Succ(m)) = plus(mal(n,m),n)

---------------------

plus Null (Succ Null)
L1 -> no Matching on plus
L2 -> Succ (plus Null Null)
L1 -> Succ Null
done
