Implementieren Sie eine Typklasse VEK, die eine Funktion faktor enthält. Die Funktion soll sowohl das Produkt zweier Int-Werte als auch das Skalarprodukt zweier gleichlanger Vektoren (Datentyp Vektor) berechnen können.

_Hinweis_: Definieren Sie den Datentyp Vektor

durch  
data Vektor = VEKTOR [Int] deriving Show.

```haskell
module VEK where -- diese Zeile bitte nicht aendern

data Vektor = VEKTOR [Int] deriving Show

class VEK t where
    faktor::t->t->Int
    
instance VEK Int where
    faktor a b = a*b
    
instance VEK Vektor where
    faktor (VEKTOR []) (VEKTOR []) = 0
    faktor (VEKTOR (v1:vs1)) (VEKTOR (v2:vs2)) = v1 * v2 + faktor (VEKTOR vs1) (VEKTOR vs2)
```

-------------

Implementieren Sie eine Typklasse EQ2 als Unterklasse von der {\scshape Haskell}-Klasse Num

.  
Diese Typklasse soll zwei Funktionen enthalten:

```
  (===)::a->a->Bool (Infix-Operation)
  myMult::a->a->a
```

Instanziieren Sie mit den Typen Float und Double.  
Die Funktion (=) soll für den Typ Float genau dann True liefern, wenn die Werte vor dem Komma gleich sind, sonst False.  
Für den Typ Double soll False bei gleichen Vorkommawerten das Ergebnis sein, andernfalls True.  
Die Funktion _myMult x y_ soll _x*y^2_ berechnen.

```haskell
class Num a => EQ2 a where
    (===)::a->a->Bool
    myMult::a->a->a
    myMult x y = x*y^2
    
instance EQ2 Float where
    x === y = (truncate x) == (truncate y)
    
instance EQ2 Double where
    x === y = not ((truncate x) == (truncate y))
```
--------------------

Implementieren Sie eine HASKELL-Funktion `digits2int:: [Int] -> Int`, die eine Liste von Ziffern in die entsprechende natürliche Zahl transformiert. Die leere Liste soll die 0 darstellen.  
So z.B. [2,4,3,1]⇝2431.

```haskell
digits2int :: [Int] -> Int
digits2int [] = 0;
digits2int (x:xs) = x * (10 ^ (length xs)) + digits2int xs
```