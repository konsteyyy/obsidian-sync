
Gegeben sei der ADT Schlange mit den Operationen, 

Schlange
```pseudocode
createQueue:    -> Queue    Konstruktor, Erzeugen einer leeren Schlange
enq: Queue x T   -> Queue    Konstruktor, Einfügen eines El. am Schlangenende
front: Queue    -> T        Auslesen des vordersten Elements (Kopf) der Schlange
deq: Queue      -> Queue    Löschen des Kopfes der Schlange
isEmpty: Queue  -> Bool     Prüfen, ob Schlange leer ist

axioms
S1: isEmpty(ceateQueue) = true
S2: isEmpty(enq(s,t)) = false
S3: front(enq(createQueue,t)) = t
S4: front(enq(enq(s,t1 ),t2 )) = front(enq(s,t1 )
S5: deq(enq(createQueue,t)) = createQueue
S6: deq(enq(enq(s,t1 ),t2 )) = enq(deq(enq(s,t1 )),t2 )
```
Implementieren Sie in einem Haskell-Programm eine Schlange durch **Konstruktoren**, ähnlich wie [[ADT Liste]]
```haskell
data Schlange t = CreateSchlange | Enq (Schlange t) t deriving Show
front:: Schlange t -> t
deq:: Schlange t -> Schlange t
isEmpty:: Schlange t -> Bool
isEmpty CreateSchlange = True
isEmpty (Enq s t) = False
front (Enq CreateSchlange t) = t
front (Enq (Enq s t1) t2) = front (Enq s t1)
deq (Enq CreateSchlange t) = CreateSchlange
deq (Enq (Enq s t1) t2) = Enq (deq (Enq s t1)) t2
```

Implementieren Sie nun in einem Haskell-Programm eine Schlange durch **Listen**.
```haskell
type Schlange t = [t]
createQueue:: Schlange t
enq:: Schlange t -> t -> Schlange t
front:: Schlange t -> t
deq:: Schlange t -> Schlange t
isEmpty:: Schlange t -> Bool
isEmpty [] = True
isEmpty _= False
enq s t = s ++ [t]
createQueue = []
front s = head s
deq s = tail s
```

#unfinished 
