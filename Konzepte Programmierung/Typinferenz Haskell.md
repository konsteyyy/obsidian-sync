

### Typisierungsregeln:
![[Pasted image 20240130151801.png]]
![[Pasted image 20240130151753.png]]
Beispiel:

Betrachten Sie die folgende Haskell-Funktion reverse:
```haskell
reverse :: [Int] -> [Int]
reverse [] = []
reverse (x:xs) = (reverse xs) ++ [x]
```
Zeigen Sie durch Typinferenz, dass die Funktion reverse korrekt typisiert ist.
Geben Sie bei jedem Typisierungsschritt die verwendete Regel an.
Insbesondere gilt:
$$
\begin{align*}
x :: Int, [] :: [Int], xs :: [Int],\\
(++) :: [Int]− > [Int]− > [Int],\\
(:) :: Int− > [Int]− > [Int] \in \Gamma_ν.
\end{align*}
$$
Lösung:
$$
\begin{align}
    \Gamma &\vdash []::[Int] & (Ax)\\
    \Gamma &\vdash reverse \; [] = []\checkmark & (Fun) (1)\\
    \Gamma &\vdash x::Int &(Ax)\\
    \Gamma &\vdash (:)::Int -> [Int] -> [Int] &(Ax)\\
    \Gamma &\vdash xs::[Int] & (Ax)\\
    \Gamma &\vdash ((:)\; x)::[Int] -> [Int] &(App) (3), (4)\\
    \Gamma &\vdash (x:xs) ::[Int] &(App) (5),(6)\\
    \Gamma &\vdash reverse::[Int]->[Int] &(Ax)\\
    \Gamma &\vdash (++)::[Int]->[Int]->[Int] & (Ax)\\
    \Gamma &\vdash (reverse \; xs)::[Int] &(App) (8),(5)\\
    \Gamma &\vdash (x:[])::[Int] & (App) (6),(1)\\
    \Gamma &\vdash (++) \; (reverse \; xs)::[Int] -> [Int] &(App) (9),(10)\\
    \Gamma &\vdash (reverse \; xs) \; ++ \; (x:[])::[Int] & (App) (12),11)\\
    \Gamma &\vdash reverse \; (x:xs) = (reverse \; xs) \; ++ \; (x:[]) \checkmark & (Fun) (7),(13)
\end{align}
$$

#### ... mit Typvariablen:
![[Pasted image 20240130163121.png]]
Beispiel:

![[Pasted image 20240131123351.png]]

![[Pasted image 20240131151655.png]]

![[Pasted image 20240131152202.png]]
