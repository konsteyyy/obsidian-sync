
Wichtige Definitionen für den Induktionsbeweis:
```haskell
zip ::[a]−>[b]−>[(a, b)]
zip [] ys = [] − −überschüssige Elemente abschneiden
zip xs [] = [] − −überschüssige Elemente abschneiden
zip (x : xs) (y : ys) = (x , y ) : (zip xs ys)

unzip ::[(a, b)]−>([a], [b])
unzip [] = ([], [])
unzip ((x , y ) : ps) = (x : xs, y : ys) where (xs, ys) = unzip ps

(!!)::[t]−> Int−>t
xs!!n|n<0=error "Prelude.!!: negative index"
[]!!n=error "Prelude.!!: index too large"
(x :xs)!!0=x
(x :xs)!!n=xs!!(n − 1)
```

## Beweis von Satz 1.1 (ii)
Beweis erfolgt durch Induktion über xs
##### Induktionsanfang: xs == x:[]
zZ.: $\forall ys == y:ys': (zip\ (x:[])\ (y:ys'))!!n == ((x:[])!!n,\ (y:ys')!!n)$
$$
\begin{align*}
	(zip\ (x:[])\ (y:ys'))!!n&==(zip\ (x:[])\ (y:ys'))!!0 &&|n==0,\ da\ 0\geq n < min\ (length\ (x:[]))\ (length\ (y:ys'))\\
	&==((x,y):(zip\ []\ ys'))!!0 &&|Def. 3\ zip\\
	&==((x,y):[])!!0 &&|Def. 1\ zip\\
	&==(x,y) &&|Def. 3\ (!!)\\
	&==((x:[])!!0,(y:ys')!!0) &&|Def. 3\ (!!)\\
\end{align*}
$$
##### Induktionshypothese:
$\forall xs::[a], ys::[b], n::Int: (zip\ xs\ ys)!!n == (xs!!n,\ ys!!n)$ wobei $n\geq0 \wedge n<min\ (length\ xs)\ (length\ ys)$

##### Induktionsschritt: xs== x:xs'
zZ.: $\forall ys == y:ys': (zip\ (x:xs')\ (y:ys'))!!n == ((x:xs')!!n,\ (y:ys')!!n)$

$\underline{Fall\ 1:} n==0$
$$
\begin{align*}
	(zip\ (x:xs')\ (y:ys'))!!0 &==((x,y):(zip\ xs'\ ys'))!!0 &&|Def. 3\ zip\\
	&==(x,y) &&|Def. 3\ (!!)\\
	&==((x:xs')!!0,(y:ys')!!0) &&|Def. 3\ (!!)\\
\end{align*}
$$

$\underline{Fall\ 2:} n>0 \wedge n<min\ (length\ xs)\ (length\ ys)$
$$
\begin{align*}
	(zip\ (x:xs')\ (y:ys'))!!n &==((x,y):(zip\ xs'\ ys'))!!n &&|Def. 3\ zip\\
	&== (zip\ xs'\ ys'))!!(n-1)&&|Def. 4\ (!!)\\
	&==(xs'!!(n-1),\ ys'!!(n-1)) &&|IH\\
	&==((x:xs')!!n,(y:ys')!!n) &&|Def. 4\ (!!)\\
\end{align*}
$$

