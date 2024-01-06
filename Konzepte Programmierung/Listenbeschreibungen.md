Implementieren Sie eine Funktion `zeroOne:: [String]`, die die Liste aller Zeichenketten der Form 0n1n für n=0,1,2,... in aufsteigender Länge ausgibt.

Lösung:
```haskell
zeroOne :: [String]
zeroOne = [replicate n '0' ++ replicate n '1' | n <- [0..]]
```

-----------------------

Schreiben Sie eine Haskell-Funktion $applyList::[Int->Int]->Int->[Int]$, die eine Liste von Funktionen
(jede vom Typ Int->Int) und ein Element vom Typ Int als Argument übernimmt und eine Liste mit den Ergebnissen,  
die bei der Anwendung jeder Funktion auf das Element entstehen, ausgibt.  
Schreiben Sie eine Variante applyList1 mit Rekursion und eine Variante applyList2 mit Listenbeschreibung.  
Beispiel: $applyList\ [(+10),(*4),(∖ x->x-3)]\ 2$ liefert $[12,8,-1]$.

Lösung:
```haskell
applyList1::[Int->Int]->Int->[Int]
applyList1 [] _ = []
applyList1 functions element = [func element] ++ applyList1 (tail functions) element where func = head functions

applyList2::[Int->Int]->Int->[Int]
applyList2 functions element = [f x | f<-functions, x<-[element]]
```
