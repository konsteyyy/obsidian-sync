[[Haskell]]

```haskell
0 dimtest::[Int]->String 
1 dimtest x = case x of 
2             []           -> "leere Liste" 
3              y:i:xs      -> "lange Liste" 
4              i:xs        -> "nicht leere Liste" 
5              i:j:k:xs    -> "sehr lange Liste"
```

$\underline{dimtest[1,3]}$
(1) [1,3] passt auf x
(2) [1,3] == [] $\leadsto$ 1:[3] == [] $\leadsto$ 1:3:[] == [] $\leadsto$ False
(3) passt [1,3] auf y:i:xs ? $\leadsto$ passt 1:[3] auf y:i:xs ? $\leadsto$ passt 1:3:[] auf y:i:xs $\leadsto$ True

= "lange Liste"

## Redundante [[Muster]]
(5) ist ein redundantes Muster, da der Case niemals stattfinden kann. Alle Listen der Form i:j:k:xs werden nämlich bereits in Zeile 3 verwertet
