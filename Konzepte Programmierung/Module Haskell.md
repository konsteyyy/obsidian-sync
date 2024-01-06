Implementieren Sie in einem Haskell-Programm ein Modul `module RatOps` zum Rechnen  
mit rationalen Zahlen, dargestellt durch einen Bruch aus ganzzahligem Zähler und ganzzahligem  
Nenner. Im Programm werde der Datentyp Rat durch ein Paar (Zähler,Nenner) von  
Integer-Werten beschrieben: `type Rat = (Integer, Integer)`.  
Defnieren Sie die Funktionen Addition `addR`, Subtraktion `subR`, Multiplikation `mulR` und  
Division `divR` mit den vorgegebenen Signaturen:

`addR :: Rat− > Rat− > Rat`  
`subR :: Rat− > Rat− > Rat`  
`mulR :: Rat− > Rat− > Rat`  
`divR :: Rat− > Rat− > Rat` .

Weitere Bedinungen für die Defnitionen dieser Funktionen sind:

- Alle berechneten Brüche, d.h. alle Funktionswerte, sind gekürzt.  
    Sie können dafür die Haskell-Funktion gcd nutzen.  
    Versuchen Sie, durch Beispielrechnung ihre Defnition zu erkennen.
- Für den Nenner n (des Ergebnisses) gilt n ≥

- 0
- Ist der Nenner n in einem beliebigen Operanden einer Funktion = 0, so ist (0,0) der  
    Wert der Funktion (Ergebnis).
- Ist der Zähler eines Funktionswertes gleich 0, so ist (0,1) auszugeben.
- Einige Beispiele mit Funktionswerten:  
    `mulR (2,4) (-1,-2) Ergebnis: (-1,-4)`  
    `mulR (3,2) (8,3) Ergebnis: (4,1)`  
    `addR (3,2) (4,0) Ergebnis: (0,0)`  
    `subR (3,6) (4,2) Ergebnis: (-3,2)`

Lösung:
```haskell
module RatOps where
type Rat = (Integer, Integer)
addR::Rat->Rat->Rat
subR::Rat->Rat->Rat
mulR::Rat->Rat->Rat
divR::Rat->Rat->Rat
simplify::Rat->Rat
simplify (a, b) 
    | a==0 = (0,1)
    | b==0 = (0,0)
    | otherwise = (a `div` g, b `div` g)
                   where g = gcd a b

-- 1/2 + 3/4 = 5/4, weil gemeinsamer Nenner: nenner1*nenner2 und dann zaehler erweitern
addR (zaehler1, nenner1)  (zaehler2,nenner2) = simplify (zaehler1*nenner2 + zaehler2*nenner1 , nenner1 * nenner2)

-- addR, bloss mit negativem zweiten zaehler
subR (zaehler1, nenner1)  (zaehler2,nenner2) = addR (zaehler1, nenner1) (-zaehler2, nenner2)

-- nenner und zaehler je multiplizieren
mulR (zaehler1, nenner1)  (zaehler2,nenner2) = simplify (zaehler1 * zaehler2, nenner1 * nenner2)

-- mul mit dem Kehrwert des zweiten Bruchs
divR (zaehler1, nenner1)  (zaehler2,nenner2) = mulR (zaehler1, nenner1) (nenner2, zaehler2)
```
---------------

Betrachten Sie erneut das Modul RatOps der rationalen Zahlen mit den vier Funktionen aus der 3. Aufgabe. Schreiben Sie ein neues Modul `module RatUseA`, das dieses benutzt. Es sollen nur die Funktionen `addR` und `subR` importiert werden. Verändern Sie das Modul `module RatOps`, falls notwendig. Defnieren Sie eine neue Funktion `potR` im neuen Modul, die das Potenzieren einer rationalen Zahl realisiert. Die Signatur der Funktion sei `potR::Rat -> Int -> Rat`, d.h. der 2. Parameter gibt an, wie oft der erste potenziert wird. Es gelten die analogen Bedingungen, z.B Kürzen usw. wie in der Aufgabe RatOps.

```haskell
module RatUseA where
import RatOps (Rat, addR, subR, simplify)

potR::Rat->Int->Rat

potR (zaehler, nenner) e
    | e==0 = (1,1)
    | e==1 = (zaehler,nenner)
    | otherwise = potR (simplify (zaehler * zaehler, nenner * nenner)) (e-1)
```

Betrachten Sie wieder das Modul RatOps der rationalen Zahlen mit den vier Funktionen aus der Aufgabe RatOps. Jetzt werden alle vier Funktionen des Moduls module RatOps qualifziert in das neue Modul `module RatUseB` importiert. Defnieren Sie im neuen Modul (erneut) eine Funktion `divR :: Rat− > Rat− > Rat`, die eine (gegebenenfalls andere) Fallunterscheidung verwendet.

Qualifiziertes Importieren bedeutet, dass die exportierten Funktionen nur zusammen mit dem Modulnamen verwendet werden können

```haskell
module RatUseB where
import qualified RatOps

divR:: RatOps.Rat->RatOps.Rat->RatOps.Rat

divR (zaehler1, nenner1)  (zaehler2,nenner2)
    | nenner1 == 0 || nenner2==0 = (0,0)
    | zaehler1 == 0 || zaehler2== 0 = (1,0)
    | otherwise =  RatOps.mulR (zaehler1, nenner1) (nenner2, zaehler2)
```