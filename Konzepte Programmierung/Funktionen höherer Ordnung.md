Implementieren Sie eine HASKELL-Funktion

`sizeOf :: [a] -> Int`

welche die Länge einer Liste mittels der Funktion höherer Ordnung `foldl` und einer anonymen Funktion berechnet. Es sollen keine weiteren bereits in HASKELL implementierten Funktionen (z.B. length,…) verwendet werden.

So wird bei der Eingabe von z.B. [2,4,3,14]die 4 ausgegeben.

Lösung:

```haskell
sizeOf::[a]->Int

sizeOf = foldl (\a _ ->a+1) 0
```
------------
Schreiben Sie eine HASKELL-Funktion `sieve`, welche wie ein Rüttelsieb mit verschiedenen Lochgrößen arbeitet:

Die Werte aus einer Liste werden mit den Prädikaten aus einer weiteren Liste geprüft. Die Prädikate, Funktionen mit einem Parameter und einem booleschen Rückgabewert, werden nacheinander angewandt. Liefert ein Prädikat **True**, so wird der Wert in die entsprechende Ergebnisliste einsortiert, bis mit diesem Sieb alles durchgerüttelt ist. Dann wird mit dem nächsten Prädikat/ Sieb geprüft/ gesiebt. Werte, für die kein Prädikat erfüllt ist, kommen in eine eigene Liste.

Dabei soll die Signatur der Funktion `sieve` lauten

`sieve :: [(Int-> Bool)] -> [Int] -> [[Int]]`

Beispiel: sieve $[(<3),(>7),odd]  [1,2,3,4,5,6,7,8,9,10]$ $\leadsto$ $[[1,2], 8,9,10], 3,5,7], 4,6]]$

```haskell
sieve :: [(Int -> Bool)] -> [Int] -> [[Int]]
sieve [] xs = [xs]
sieve _ [] = []
sieve ps xs = [filter p xs] ++ sieve (tail ps) (filter (\x -> not (p x)) xs)
                    where p = head ps
```
