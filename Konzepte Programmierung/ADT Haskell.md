# Umwandlung [[ADT]] in Haskell

## Beispiel Datentyp [[Liste]]

```pseudocode
spec Liste is
sorts Liste, T
operations
			nil:                 -> Liste
			cons:      T x Liste -> Liste
			append: List x Liste -> Liste
			reverse:       Liste -> Liste
vars x: T; l1, l2: Liste
axioms
			L1:         append(nil, l) = l
			L2: append(cons(x,l1), l2) = cons(x, apend(l1,l2))
			L3:           reverse(nil) = nil
			L4:     reverse(cons(x,l)) = append(reverse(l),cons(x,nil))
```

wird in Haskell zu:

```hs
data Liste x = Nil | Cons x (Liste x) deriving Show
append:: Liste x -> Liste x -> Liste x
reverse:: Liste x -> Liste x
append Nil x = x
append (Cons x l1) l2 = Cons x (append l1 l2)
reverse Nil = Nil
reverse (Cons x l) = append (reverse l) (Cons x Nil)
```

#unfinished

