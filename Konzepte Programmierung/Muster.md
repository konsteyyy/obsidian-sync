[[Haskell]]
#### Bewachte Muster

```hs
summiere2 n | n==0 = 0
			| n>=1 = n + summiere2 (n-1)
```

#### If Else Then
```hs
summiere2 n = if n==0 
              then 0 
              else n+summiere2 (n-1)
```

#### Case Of
```hs
0 dimtest::[Int]->String 
1 dimtest x = case x of 
2             []           -> "leere Liste" 
3              y:i:xs      -> "lange Liste" 
4              i:xs        -> "nicht leere Liste" 
5              i:j:k:xs    -> "sehr lange Liste"
```

#finished 