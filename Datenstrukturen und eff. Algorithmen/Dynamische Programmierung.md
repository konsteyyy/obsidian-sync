* ist eine Methode zum effizienten Lösen einer breiten Klasse von Such- und Optimierungsproblemen
* Lösungen von Unterproblemen werden gespeichert und bei Bedarf wiederverwendet
	* senkt Redundanz
	* steigert Berechnungseffizienz
	* Memoisierung
---------------------------
### einfaches Beispiel: fibonacci(n)

* bisher rekursiv:

![[fibonacci_berechnungsbaum.png]]
* bei großen n aber sehr ineffizient, da sehr viele Berechnungen redundant
	* für f(5) muss f(2) alleine schon 3 Mal berechnet werden
* Laufzeit von O($2^n$) 

```pseudocode
function fibonacci(n)
    if n = 0 then
        return 0
    else if n = 1 then
        return 1
    else
        return fibonacci(n-1) + fibonacci(n-2)
    end if
end function
```
------------
# Bottom Up Ansatz
* stattdessen jetzt mit einem Array:
[0,1,1,2,3,5]

* [[Laufzeit]] jetzt O(n)
```pseudocode
function fibonacci(n)
    create array fib[0..n]
    fib[0] = 0
    fib[1] = 1
    for i from 2 to n
        fib[i] = fib[i-1] + fib[i-2]
    end for
    return fib[n]
end function
```
--------------
# Top Down
* eine effizientere Art des rekursiven Ansatzes:
* speichere Ergebnisse in einem Array und überprüfe vor jeder Berechnung, ob es davon bereits ein Ergebnis gibt
* [[Laufzeit]] jetzt ebenfalls O(n)
```pseudocode
function fibonacci(n)
    create array memo[0..n] initialized with -1  # -1 indicates uncomputed value
    
    # Initialize base cases
    memo[0] = 0
    memo[1] = 1
    
    return fib(n, memo)
end function

function fib(n, memo)
    # If the value was already computed, return it
    if memo[n] != -1 then
        return memo[n]
    end if
    
    # Otherwise, calculate it, store it, and return it
    memo[n] = fib(n-1, memo) + fib(n-2, memo)
    return memo[n]
end function

```
