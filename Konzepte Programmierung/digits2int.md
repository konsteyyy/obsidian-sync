Implementieren Sie eine HASKELL-Funktion `digits2int:: [Int] -> Int`, die eine Liste von Ziffern in die entsprechende natürliche Zahl transformiert. Die leere Liste soll die 0 darstellen.  
So z.B. [2,4,3,1]⇝2431.

```haskell
digits2int :: [Int] -> Int
digits2int [] = 0;
digits2int (x:xs) = x * (10 ^ (length xs)) + digits2int xs
```