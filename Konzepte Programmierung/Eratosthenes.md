```haskell
teiler:: Integer -> [Integer]
prim:: Integer -> Bool
nteprimzahl:: Int -> Integer

teiler n = [i|i<-[1..n], rem n i == 0]
prim n = teiler n == [1,n]
nteprimzahl n = [p|p<-[2..], prim p]!!n

-- 7163759 Reduktionen fuer nteprimzahl 302


eratosthenes:: [Integer]
eratosthenes = sieb 2 [2..]
sieb :: Integer -> [Integer] -> [Integer]
sieb k xs = prim++(sieb (k+1) (diff xs nichtprim))
    where prim = takeWhile(< k*k) xs
          nichtprim = foldl merge [] allevielfache
          allevielfache = map vielfache prim
vielfache:: Integer -> [Integer]
vielfache x = [x*j|j<-[1..]]
merge:: [Integer] -> [Integer] -> [Integer]
merge [] ys = ys
merge xs [] = xs
merge (x:xs) (y:ys) | x<=y = x : merge xs (y:ys)
                    | otherwise = y : merge (x:xs) ys
diff:: [Integer] -> [Integer] -> [Integer]
diff [] x = []
diff x [] = x
diff (x:xs) (y:ys) | x==y = diff xs ys
                   | x>y = diff (x:xs) ys
                   | x<y = x:diff xs (y:ys)

-- 288216 Reduktionen fuer eratosthenes!!302
-- Die rekursive Variante oben "nteprimzahl" benoetigt 24x so lange fuer die 302te Primzahl wie eratosthenes
```
