```haskell
foldr :: (a−>b−>b)−>b−>[a]−>b
foldr f z [] = z
foldr f z (x : xs) = f x (foldr f z xs)
foldl :: (a−>b−>a)−>a−>[b]−>a
foldl f z [] = z
foldl f z (x : xs) = foldl f (f z x ) xs
```
Folgende Eigenschaften gelten zudem:
```pseudocode
f u (f′ v w ) == f′ (f u v ) w
f u z == f′ z u
```

#unfinished 