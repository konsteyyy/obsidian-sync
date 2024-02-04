![[Pasted image 20240131160901.png]]


A priori Typen:
![[Pasted image 20240131161201.png]]

A posteriori Typen:
![[Pasted image 20240131161218.png]]

Gültigkeitsbereich: scope of variables
Lebensdauer: 
![[Pasted image 20240131161346.png]]

Ablaufmechanismus:
![[Pasted image 20240131161604.png]]
![[Pasted image 20240131161624.png]]
--------------

Schreiben Sie in Sather-K eine Klasse KUGEL, welche eine Kugel im Raum durch ihren Mittelpunkt und ihren Radius beschreibt.  
Implementieren Sie folgenden Methoden:  
Setzen des Mittelpunktes: setMitte(mx,my,mz:INT)  
Setzen vom Radius: setRadius(r:FLT)  
Berechnen der Oberfläche: oberflaeche:FLT  
Berechnen des Volumens: volumen:FLT

.  
Die Klasse enthält ausserdem die main-Funktion, in der die Oberfläche und das Volumen der Einheitskugel berechnet und ausgegeben werden.

**Hinweis:**  
Runden Sie π

auf 5 Nachkommastellen.  
Schreiben Sie die main-Methode ohne Argumente.

```eiffel
class KUGEL is
        r:FLT;
        mx, my, mz:INT;
        pi:FLT := 3.14159;
        
        setRadius(r:FLT) is
            self.r:= r;
        end;
        
        setMitte(mx,my,mz:INT) is
            self.mx := mx;
            self.my := my;
            self.mz := mz;
        end;
        
        oberflaeche:FLT is
            res:= (4.0 * self.pi * self.r^2) as FLT;
        end;
        
        volumen:FLT is
            res:= (4.0/3.0 * self.r^3 * self.pi) as FLT;    
        end;
        
        main is
            setRadius(1);
            setMitte(0,0,0);
            TEXT::sout<< "Oberflaeche = " << oberflaeche << "\n";
            TEXT::sout<< "Volumen = " << volumen << "\n" ;
        end;
end;
```


![[Pasted image 20240131162007.png]]
![[Pasted image 20240131162024.png]]
![[Pasted image 20240131162059.png]]
```eiffel
class UEBERLADEN is

    ueber(a:INT;b:FLT):INT is
        res:=a* b as INT;
    end;
    
    ueber(a,b:INT):INT is
        res:=a*b;
    end;
    
    ueber(a,b:FLTD):FLTD is
        res:=a*b;
    end;
    
    --ueber(2,3)
    --M={ueber(INT,INT), ueber(INT,FLT), ueber(FLTD, FLTD)}
    --M'={ueber(INT,INT)}
    
    --ueber(2.1,3)
    --M={ueber(FLTD, FLTD)}
    --M'={ueber(FLTD, FLTD)}

    --ueber(2,3.1)
    --M={ueber(INT,FLT), ueber(FLTD, FLTD)}
    --M'={ueber(INT,FLT)}
    
    --ueber(2.1,3.1)
    --M={ueber(FLTD,FLTD)}
    --M'={ueber(FLTD,FLTD)}
end;
```

---------------------
Schreiben Sie eine Klasse HIGHERORDER.  
Die Klasse enthält zwei Prozeduren loopSE (Schleife von Start nach Ende) und loopES (Schleife von Ende nach Start).  
Beide Prozeduren bekommen eine Prozedur (INT,INT):INT und ein Array von INT-Werten als Eingabeparameter und wenden in einer Schleife in jeder Iteration die übergebene Prozedur auf dem bisherigen Ergebnis und dem nächsten/vorherigen Wert im Array an. Das neue Ergebnis in jeder Schleifeniteration ist das Ergebnis des Prozeduraufrufs. Das Ergebnis wird von loopSE bzw. loopES zurückgegeben.  
loopSE startet mit dem ersten Wert des Arrays und durchläuft das Array in der Reihenfolge von vorne nach hinten.  
loopES

startet mit dem letzten Wert des Arrays und durchläuft das Array in der Reihenfolge von hinten nach vorne.

Schreiben Sie eine Prozedur chooseLoop

, welche aus der Konsole einen INT-Wert einliest. Wenn der Wert 0 ist, wird die Prozedur loopSE, wenn der Wert 1 ist, wird die Prozedur loopES

zurück gegeben.

Schreiben Sie eine Prozedur run

mit den gleichen Eingabeparametern wie die Schleifen-Prozeduren, aber ohne Ergebnistyp. run soll von chooseLoop eine der Schleifen-Prozeduren auswählen lassen und an die ausgewählte Schleifenfunktion die übergebene Prozedur und Array übergeben und das Ergebnis in eine Zeile in die Konsole ausgeben.

```eiffel
class HIGHERORDER is
    loopSE(proc: procedure(INT,INT):INT; arr: ARRAY[*](INT)):INT is
        i:INT;
        i:=1;
        res:= arr[0];
        
        while (i < arr.asize) loop
            res := proc(res, arr[i]);
            i := i + 1;
        end;
    end;
    
    loopES(proc: procedure(INT,INT):INT; arr: ARRAY[*](INT)):INT is
        i:INT;
        i:= arr.asize - 2;
        res:= arr[arr.asize - 1];
        
        while (i >= 0) loop
            res := proc(res, arr[i]);
            i := i - 1;
        end;
    end;
    
    chooseLoop:procedure(procedure(INT,INT):INT, ARRAY[*](INT)):INT is
        c:INT;
        TEXT::sin >> c;
        if c=0 then
            res:=bind loopSE(,);
        else
            res:=bind loopES(,);
        end;--if
    end; --chooseLoop
    
    run(proc: procedure(INT,INT):INT; arr: ARRAY[*](INT)) is 
        x:procedure(procedure(INT,INT):INT, ARRAY[*](INT)):INT;
        erg:INT;
        x:=chooseLoop;
        erg:=x(proc,arr);
        TEXT::sout<<erg<<"\n";
    end; --run
end;
```


![[Pasted image 20240131163151.png]]
AoA
```eiffel
class KUNDE is
    KundenID:INT;
    shared anz:INT;
    konten:$SET($KONTO) := #SET_LIST($KONTO);
    createKunde(id:INT):SAME is
        res:=#SAME;
        res.KundenID:=id;
        --noch auszufüllen
    end;
    getKundenID:INT is
        --noch ausfüllen
    end;
end;

class KONTO is
    kontoinhaber:STRING;
    kontostand:FLT;
    kunde:KUNDE;
    createKonto(kunde:KUNDE; kontostand:FLT):SAME is
        res:=#SAME;
        res.kunde:=kunde;
    end;
    getKontoinhaber:STRING is
        --noch ausfüllen 
    end;
    getKontostand:FLT is
        --noch ausfüllen
    end;    
    getKunde:KUNDE is
        --noch ausfüllen
    end;
    setKunde(kunde:KUNDE) is
        --noch ausfüllen
    end;
end;
```

AmA
```eiffel
class KUNDE is
    KundenID:INT;
    shared anz:INT;
    besitzt:$SET($BESITZT) := #SET_LIST($BESITZT);
    createKunde(id:INT):SAME is
        res:=#SAME;
        res.KundenID:=id;
        --noch auszufüllen
    end;
    getKundenID:INT is
        --noch ausfüllen
    end;
end;

class BESITZT is
    kunde:$KUNDE;
    konto:$KONTO;
    init(kunde:$KUNDE; konto:$KONTO) is
        self.kunde:=kunde;
        self.konto:=konto;
        self.kunde.besitzt.insert(self);
        self.konto.besitzt:=self;
    end;
end;

class KONTO is
    kontoinhaber:STRING;
    kontostand:FLT;
    besitzt:$BESITZT;
    createKonto(kunde:KUNDE; kontostand:FLT):SAME is
        res:=#SAME;
        res.kunde:=kunde;
    end;
    getKontoinhaber:STRING is
        --noch ausfüllen 
    end;
    getKontostand:FLT is
        --noch ausfüllen
    end;    
    getKunde:KUNDE is
        --noch ausfüllen
    end;
    setKunde(kunde:KUNDE) is
        --noch ausfüllen
    end;
end;
```
Bei neuem Link muss in beiden Attributen das jeweilig andere Objekt
eingeführt werden\\
+ neuKunde.konten.insert(konto) und
konto.kunde.insert(neuKunde)\\

-> fehleranfällig

-------------

Hoare Kalkül

![[Pasted image 20240131163532.png]]

![[Pasted image 20240203170548.png]]
$$\begin{align} 
Hoare\ für\ Tripel:&& \{a=x+1\}x:=x+1;x:=2*x;\{\cdots\}  \\
(1)&&\{a=x+1\}x:=x+1;\{a=x\}&&(Zuw)\\
(2)&&\{a=x\}x:=2*x;\{2a=x\}&&(Zuw)\\
(3)&&\{a=x+1\}x:=x+1;x:=2*x\{2a=x\}&&(Seq) (1)(2)
\end{align}$$

$$\begin{align} 
(1)&\{x<0\}res:=-x;\{res\geq0\}&&(Zuw)\\
(2)&\{x< 0 \land true\} \Rightarrow \{x<0\}&&(Aussagenlogik)\\
(3)&\{x< 0 \land true\}res:=-x;\{res\geq0\}&&(scharf) (1)(2)\\
(4)&\{x\geq0\}res:=x;\{res\geq0\} && (Zuw)\\
(5)&\{x\geq 0 \land true\} \Rightarrow \{x\geq0\} &&(Aussagenlogik)\\
(6)&\{x\geq 0 \land true\}res:=x;\{res\geq0\} &&(scharf)(4)(5)\\
(7)&\{true\}if\ x<0\ then\ res:=-x;\ else\ res:=x\ end;\{res\geq0\}&&(if)(5)(6)
\end{align}$$
