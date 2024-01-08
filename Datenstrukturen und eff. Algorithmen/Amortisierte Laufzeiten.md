Amortisierte Laufzeiten sind ein Konzept aus der Algorithmusanalyse, bei dem es darum geht, den durchschnittlichen Zeit- oder Ressourcenaufwand für eine Serie von Operationen in einem Datenalgorithmus zu bestimmen. Die Idee ist, dass, obwohl einige Operationen sehr teuer sein können, der durchschnittliche Aufwand über eine Serie von Operationen hinweg oft viel geringer ist.

Es gibt verschiedene Methoden zur Berechnung amortisierter Laufzeiten, die bekanntesten sind:

1. **Aggregatmethode**: Hierbei berechnet man die Gesamtkosten für eine Serie von Operationen und teilt diese durch die Anzahl der Operationen.
    
2. **Die Buchhalter-Methode (Accounting-Methode)**: Bei dieser Methode ordnet man jeder Operation einen bestimmten "amortisierten Kosten"-Wert zu. Man kann sich das vorstellen, als würde man für kostengünstige Operationen "sparen", um teurere Operationen später zu "bezahlen".
    
3. **Das Potential-Methode**: Diese Methode verwendet eine Potentialfunktion, die den Zustand der Datenstruktur nach jeder Operation bewertet. Die Kosten einer Operation werden dann als die tatsächlichen Kosten plus die Änderung des Potentials definiert.