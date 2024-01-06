Gegeben ist ein n×n Schachbrett.  
Platzieren Sie n Läufer so auf dem Schachbrett (Generieren), dass sie sich nicht schlagen können (Testen).  
Implementieren Sie eine Funktion laeufer::Int -> [[(Int,Int)]], die alle möglichen Platzierungen ausgibt.  
Hinweis: Zwei Läufer können sich gegenseitig schlagen, wenn sie in denselben Diagonalen stehen.

```haskell
-- testen, ob sich die Laeufer diagonal schlagen koennen
schlagen (i,j) (k,l) = (i-j)==(k-l) || i+j==k+l 

-- testen, ob man die Lauefer platzieren kann
platziert1 (i,j) [] = True
platziert1 (i,j) ((k,l):xs) = not (schlagen (i,j) (k,l)) && platziert1 (i,j) xs

-- kandidaten generieren, die sich nicht schlagen
kandidaten m 0 = [[]]
kandidaten m n = [((i,j):xs) | xs<-(kandidaten m (n-1)), i<-[0..m-1], j<-[0..m-1], platziert1 (i,j) xs]

-- alle moeglichen Kandidaten ausgeben
laeufer::Int->[[(Int,Int)]]
laeufer 0 = [[]]
laeufer n = [xs |xs<-kandidaten n n, length xs == n]
```
