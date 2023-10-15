### Allgemeine Informationen

- Eine **Liste** ist eine geordnete Sammlung von Elementen.
- Elemente können jeglichen Datentyp haben: Zahlen, Strings, Objekte etc.
- Die Elemente einer Liste können zugegriffen, verändert, hinzugefügt oder entfernt werden.
![[Pasted image 20231015130113.png]]
### Eigenschaften einer Liste

1. **Geordnet**: Die Elemente haben eine definierte Reihenfolge.
2. **Dynamisch**: Listen können während der Laufzeit modifiziert werden (Elemente können hinzugefügt oder entfernt werden).
3. **Zugriff**: Zugriff auf Elemente kann direkt über den Index oder sequenziell erfolgen.
4. **Heterogenität** (in vielen Programmiersprachen): Listen können Elemente unterschiedlicher Typen enthalten.

### Basisoperationen

- **Lesen**: Zugriff auf ein Element an einer bestimmten Position.
- **Einfügen**: Hinzufügen eines Elements an einer bestimmten Position.
- **Löschen**: Entfernen eines Elements.
- **Länge abfragen**: Bestimmen der Anzahl von Elementen in der Liste.
- **Suchen**: Finden der Position eines Elements in der Liste.

### Implementierung

Listen können auf verschiedene Weisen implementiert werden, wie etwa durch:

- **Arrays**: Speicherung in einem kontinuierlichen Speicherbereich. Bietet schnellen direkten Zugriff, aber das Einfügen und Löschen kann aufwändig sein.
- **Verkettete Listen**: Jedes Element verweist auf das nächste (und manchmal auch auf das vorherige) Element. Einfügen und Löschen sind schnell, während der direkte Zugriff langsamer ist.
	- können sowohl einfach verkettet, als auch doppelt verkettet sein
### [[Laufzeit]] von Listen-Operationen

- **Arrays**:
    - Zugriff: �(1)O(1)
    - Einfügen/Löschen: �(�)O(n)
    - Suche (ohne sortierte Liste): �(�)O(n)
- **Verkettete Listen**:
    - Zugriff: �(�)O(n)
    - Einfügen/Löschen: �(1)O(1) (wenn der Knoten bekannt ist)
    - Suche: �(�)O(n)
#finished 