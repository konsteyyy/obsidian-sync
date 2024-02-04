
Welche Funktionen in den folgenden Typklassen sind Kernfunktionen und
welche abgeleitete Funktionen?

```haskell
class MyOrd a where
    (==):: a->a->Bool  -- ist eine Kernfunktion
    (/=):: a->a->Bool  -- ist eine abgeleitete Funktion
    (<) :: a->a->Bool  -- ist eine Kernfunktion
    (<=):: a->a->Bool  -- ist eine Kernfunktion
    (>) :: a->a->Bool  -- ist eine abgeleitete Funktion
    (>=):: a->a->Bool  -- ist eine abgeleitete Funktion
    p /= q = not (p==q)
    p >= q = not (p<q)
    p > q = not (p<=q)
```

```haskell
class MyNum a where
    (+)::a->a->a    -- ist eine Kernfunktion
    (-)::a->a->a    -- ist eine abgeleitete Funktion
    negate::a->a    -- ist eine Kernfunktion
    abs::a->a       -- ist eine abgeleitete Funktion
    (*)::a->a->a    -- ist eine Kernfunktion
    signum::a->a    -- ist eine Kernfunktion
    a-b = a + (negate b)
    abs a = a * (signum a)
```