Eine Matrix sei als Liste von Zeilen definiert. Jede Zeile sei als Liste von Werten definiert. Alle Werte der Matrix haben den gleichen Typ.  
Schreiben Sie eine Haskell-Funktion trans::Num a => [[a]]-> [[a]], die aus einer gegebenen Matrix die transponierte Matrix erzeugt.

```haskell
trans::Num a => [[a]] -> [[a]]
-- Basisfall
trans [] = []

-- hat die Liste nur eine Zeile mit n Elementen, erstelle Matrix mit n Spalten
-- jede Zeile hat dann genau ein Element
trans [x] = [[y] | y <- x]

-- Rekursiv: merge immer die ersten Elemente aus den Listen zu einer Liste zusammen 
-- und rufe trans mit den restlichen Listen auf
trans (x:xs) = merge x (trans xs)
    where
        merge [] ys = []
        merge (a:as) (b:bs) = (a:b) : merge as bs
```