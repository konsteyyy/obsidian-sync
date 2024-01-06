Schreiben Sie erneut eine Funktion in [[Haskell]] `ggTa:: Int -> Int -> Int`, die den größten gemeinsamen Teiler zweier natürlichen Zahlen bestimmt. Benutzen Sie dazu die Anweisung `if-then-else` aus [[Muster]].

Lösung:
```haskell
ggTa:: Int->Int->Int
ggTa n m = if m==0 
           then n 
           else 
               if n==0
               then m
               else
                   if n>m
                   then ggTa (n-m) m
                   else ggTa n (m-n)
```

Schreiben Sie erneut eine Funktion `ggTb:: Int -> Int -> Int`, die den größten gemeinsamen Teiler zweier natürlichen Zahlen bestimmt. Benutzen Sie nun Wächter aus [[Muster]].

Lösung:

```haskell
ggTb:: Int -> Int -> Int
ggTb n m | n==0 = m
         | m==0 = n
         | n>m = ggTb (n-m) m
         | otherwise = ggTb n (m-n)
```