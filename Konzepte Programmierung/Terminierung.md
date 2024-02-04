Zeigen Sie, dass das Haskell-Programm Sortieren sort (vgl. Vorlesung, S.36)
terminiert. Geben Sie eine Terminierungsfunktion τ sowohl für sort als auch
insert an und weisen Sie ihre strenge Monotonie nach.

```haskell
sort [] = []
sort (x : xs) = insert x (sort xs)
insert x [] = [x ]
insert x (y : ys) = if x <y then x : y : ys
                    else y : (insert x ys)
```

![[Pasted image 20240131153436.png]]

-----------------

Betrachten Sie das folgende Haskell-Programm reverse:
reverse :: [Int] -> [Int]
reverse [] = []
reverse (x:xs) = (reverse xs) ++ [x]
a) Geben Sie die Vor- und Nachbedingungen für die Funktion reverse an.
b) Zeigen Sie nun, dass die Funktion reverse terminiert. Wählen Sie dazu
eine geeignete Terminierungsfunktion τ für den Nachweis aus.

![[Pasted image 20240131153536.png]]

------------------------

![[Pasted image 20240131153655.png]]
![[Pasted image 20240131153713.png]]