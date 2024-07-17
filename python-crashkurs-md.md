# 🐍 Python Crashkurs für Praktikanten

## 📚 Inhaltsverzeichnis

1. [Grundlagen](#1-grundlagen)
2. [Datentypen und Strukturen](#2-datentypen-und-strukturen)
3. [Kontrollstrukturen](#3-kontrollstrukturen)
4. [Funktionen](#4-funktionen)
5. [Module und Bibliotheken](#5-module-und-bibliotheken)
6. [Objektorientierte Programmierung (OOP)](#6-objektorientierte-programmierung-oop)
7. [Dateien und Ausnahmebehandlung](#7-dateien-und-ausnahmebehandlung)

---

## 1. Grundlagen

### Variablen und Zuweisungen
In Python werden Variablen durch einfache Zuweisung erstellt:

```python
x = 5
name = "Max"
is_student = True
```

### Kommentare
Einzeilige Kommentare beginnen mit `#`, mehrzeilige mit `'''` oder `"""`:

```python
# Dies ist ein einzeiliger Kommentar

'''
Dies ist ein
mehrzeiliger Kommentar
'''
```

### Ein- und Ausgabe
Verwendung von `input()` und `print()`:

```python
name = input("Wie heißt du? ")
print(f"Hallo, {name}!")
```

## 2. Datentypen und Strukturen

### Zahlen
Integer (ganze Zahlen) und Float (Fließkommazahlen):

```python
alter = 25
groesse = 1.75
```

### Strings
Zeichenketten in einfachen oder doppelten Anführungszeichen:

```python
vorname = "Anna"
nachname = 'Müller'
vollstaendiger_name = f"{vorname} {nachname}"
```

### Listen
Geordnete, veränderbare Sammlungen:

```python
zahlen = [1, 2, 3, 4, 5]
zahlen.append(6)  # Fügt 6 am Ende hinzu
erster_wert = zahlen[0]  # Zugriff auf das erste Element
```

### Dictionaries
Schlüssel-Wert-Paare:

```python
person = {
    "name": "Max",
    "alter": 30,
    "stadt": "Berlin"
}
print(person["name"])  # Zugriff auf Werte
```

## 3. Kontrollstrukturen

### if-Anweisungen
Bedingte Ausführung:

```python
alter = 18
if alter >= 18:
    print("Volljährig")
elif alter >= 16:
    print("Fast volljährig")
else:
    print("Minderjährig")
```

### Schleifen
`for`-Schleife für definierte Iterationen, `while`-Schleife für bedingte Iterationen:

```python
# for-Schleife
for i in range(5):
    print(i)

# while-Schleife
count = 0
while count < 5:
    print(count)
    count += 1
```

## 4. Funktionen

Definieren und Aufrufen von Funktionen:

```python
def grüße(name):
    return f"Hallo, {name}!"

nachricht = grüße("Lisa")
print(nachricht)

# Funktion mit Standardparameter
def potenz(basis, exponent=2):
    return basis ** exponent

print(potenz(3))    # 3^2 = 9
print(potenz(3, 3)) # 3^3 = 27
```

## 5. Module und Bibliotheken

Importieren und Verwenden von Modulen:

```python
import random

zufallszahl = random.randint(1, 10)
print(f"Zufällige Zahl zwischen 1 und 10: {zufallszahl}")

from datetime import datetime

jetzt = datetime.now()
print(f"Aktuelles Datum und Uhrzeit: {jetzt}")
```

## 6. Objektorientierte Programmierung (OOP)

Klassen und Objekte:

```python
class Auto:
    def __init__(self, marke, modell):
        self.marke = marke
        self.modell = modell
    
    def fahren(self):
        return f"{self.marke} {self.modell} fährt."

mein_auto = Auto("VW", "Golf")
print(mein_auto.fahren())
```

### Erklärung von `self` und `__init__`

1. `self`:
   - `self` ist eine Konvention in Python und bezieht sich auf die Instanz der Klasse, die gerade erstellt oder verwendet wird.
   - Es ist das erste Argument jeder Methode in einer Klasse und ermöglicht den Zugriff auf die Attribute und Methoden des Objekts innerhalb der Klasse.
   - Wenn Sie eine Methode aufrufen, müssen Sie `self` nicht explizit übergeben; Python tut dies automatisch.

2. `__init__`:
   - `__init__` ist eine spezielle Methode in Python, auch als Konstruktor bekannt.
   - Sie wird automatisch aufgerufen, wenn ein neues Objekt der Klasse erstellt wird.
   - Der Zweck von `__init__` ist es, die anfänglichen Attribute des Objekts zu initialisieren.
   - In unserem Beispiel setzt `__init__` die Attribute `marke` und `modell` für jedes neue `Auto`-Objekt.

### Beispiel im Detail:

```python
class Auto:
    def __init__(self, marke, modell):
        self.marke = marke    # Erstellt und initialisiert das Attribut 'marke'
        self.modell = modell  # Erstellt und initialisiert das Attribut 'modell'
    
    def fahren(self):
        # Verwendet 'self', um auf die Attribute des Objekts zuzugreifen
        return f"{self.marke} {self.modell} fährt."

# Erstellung eines Auto-Objekts
mein_auto = Auto("VW", "Golf")
# Hier wird __init__ automatisch aufgerufen mit "VW" als 'marke' und "Golf" als 'modell'

# Aufruf der Methode 'fahren'
print(mein_auto.fahren())
# Python übergibt 'mein_auto' automatisch als 'self' an die Methode 'fahren'
```

In diesem Beispiel:
1. Wenn `mein_auto = Auto("VW", "Golf")` ausgeführt wird, ruft Python automatisch die `__init__`-Methode auf und übergibt "VW" und "Golf" als Argumente.
2. Innerhalb von `__init__` wird `self.marke = marke` ausgeführt, was bedeutet, dass das neu erstellte Objekt ein Attribut namens `marke` mit dem Wert "VW" erhält.
3. Ähnlich erhält das Objekt ein Attribut `modell` mit dem Wert "Golf".
4. Wenn später `mein_auto.fahren()` aufgerufen wird, kann die `fahren`-Methode auf diese Attribute über `self.marke` und `self.modell` zugreifen.

Die Verwendung von `self` ermöglicht es jeder Instanz der Klasse `Auto`, ihre eigenen spezifischen Werte für `marke` und `modell` zu haben, während die Methoden der Klasse für alle Instanzen gleich bleiben.

## 7. Dateien und Ausnahmebehandlung

Lesen und Schreiben von Dateien:

```python
# Datei schreiben
with open("beispiel.txt", "w") as datei:
    datei.write("Hallo, Welt!")

# Datei lesen
with open("beispiel.txt", "r") as datei:
    inhalt = datei.read()
    print(inhalt)

# Ausnahmebehandlung
try:
    zahl = int(input("Gib eine Zahl ein: "))
    ergebnis = 10 / zahl
    print(f"10 geteilt durch {zahl} ist {ergebnis}")
except ValueError:
    print("Das war keine gültige Zahl!")
except ZeroDivisionError:
    print("Division durch Null ist nicht erlaubt!")
```

---

Dieser Crashkurs deckt die wichtigsten Konzepte ab, die für die Lösung der Übungen im praxisorientierten Pythonkurs benötigt werden. Er bietet eine solide Grundlage für den Praktikanten, um die Aufgaben anzugehen und sein Verständnis von Python zu vertiefen.

Für weiterführende Informationen und detailliertere Erklärungen empfehle ich die offizielle Python-Dokumentation (https://docs.python.org/) und interaktive Lernplattformen wie Codecademy oder Python.org's eigenes Tutorial.

