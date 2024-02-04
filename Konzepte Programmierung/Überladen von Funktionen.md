Implementieren Sie eine Typklasse S, die die Funktion summe (vgl. Vorlesung, S.105) überladt. Neben ganzzahligen Elementen der Liste sollen auch Gleitpunktzahlen und Boolesche Werte möglich sein. Die Summe von Gleitpunktzahlen erfolge entsprechend der ganzzahligen Summenbildung. Die Summe über Boolesche Werte soll gleich dem Wahrheitswert der Disjunktion der Elemente sein.  
Geben Sie für alle drei Instanzen einen Aufruf der Funktion summe als Kommentar in Ihrem Programm an.

```haskell
class S t where
    summe :: [t]->t

instance S Int where
    summe [] = 0
    summe (x:xs) = x + summe xs
    
instance S Bool where
    summe [] = False
    summe (x:xs) = x || summe xs

instance S Float where
    summe [] = 0.0
    summe (x:xs) = x + summe xs
```
-------------------------------

	a. In der Instanz Int soll keine Redefinition erfolgen.
	Geben Sie die Instanz an und je einen Aufruf der Funktionen blumm
	und bloemm sowie das zugehörige Ergebnis.

	b. Instanziieren Sie jetzt mit Integer und redefinieren Sie die Funktion
	bloemm mit bloemm x = True.
	Geben Sie die Instanz an und je einen Aufruf der Funktionen blumm
	und bloemm sowie das zugehörige Ergebnis.

	c. Was passiert, wenn die Signatur für bloemm in der Klasse fehlt?
	Erklären Sie kurz!

```haskell
class BLA t where
    blumm:: t -> Bool
    bloemm:: t -> Bool
    blumm x = True
    bloemm x = (blumm x ) || False

instance BLA Int where
    --hier steht nichts weiter, weil nichts redefiniert werden soll
    --zugehörige Aufrufe:
        -- blumm (1::Int)
        -- Ergebnis: True
        -- bloemm (1::Int)
        -- Ergebnis: True
    
instance BLA Integer where
    bloemm x = True
    --zugehörige Aufrufe:
        -- blumm (1::Integer)
        -- Ergebnis: True
        -- bloemm (1::Integer)
        -- Ergebnis: True
```
Wenn man bloemm:: t-> Bool aus der Klasse BLA löscht kommt es zum Error, da Haskell bei den überladenen Funktionen und der Definition der Funktion bloemm nicht versteht wofür das x stehen soll.