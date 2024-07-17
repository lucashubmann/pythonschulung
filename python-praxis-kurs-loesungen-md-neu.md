# 🐍 Praxisorientierter Pythonkurs: Lösungen

## 📚 Inhaltsverzeichnis

1. [Wiederholung der Grundlagen](#1-wiederholung-der-grundlagen-mit-praktischen-beispielen)
2. [Funktionen und Module in der Praxis](#2-funktionen-und-module-in-der-praxis)
3. [Einführung in OOP mit einem einfachen Taschenrechner](#3-einführung-in-oop-mit-einem-einfachen-taschenrechner)
4. [Erweiterung des Taschenrechners](#4-erweiterung-des-taschenrechners)
5. [Abschlussprojekt: Dateimanager](#5-abschlussprojekt-dateimanager)

---

## 1. Wiederholung der Grundlagen mit praktischen Beispielen

### 🛒 Lösung 1.1: Einkaufsliste

```python
def artikel_hinzufuegen(liste, artikel):
    liste.append(artikel)
    print(f"{artikel} wurde zur Liste hinzugefügt.")

def artikel_entfernen(liste, artikel):
    if artikel in liste:
        liste.remove(artikel)
        print(f"{artikel} wurde von der Liste entfernt.")
    else:
        print(f"{artikel} ist nicht in der Liste.")

def liste_anzeigen(liste):
    if liste:
        print("Einkaufsliste:")
        for item in liste:
            print(f"- {item}")
    else:
        print("Die Einkaufsliste ist leer.")

def main():
    einkaufsliste = []
    while True:
        print("\n1. Artikel hinzufügen")
        print("2. Artikel entfernen")
        print("3. Liste anzeigen")
        print("4. Beenden")
        
        wahl = input("Wählen Sie eine Option (1-4): ")
        
        if wahl == "1":
            artikel = input("Welchen Artikel möchten Sie hinzufügen? ")
            artikel_hinzufuegen(einkaufsliste, artikel)
        elif wahl == "2":
            artikel = input("Welchen Artikel möchten Sie entfernen? ")
            artikel_entfernen(einkaufsliste, artikel)
        elif wahl == "3":
            liste_anzeigen(einkaufsliste)
        elif wahl == "4":
            print("Programm wird beendet.")
            break
        else:
            print("Ungültige Eingabe. Bitte versuchen Sie es erneut.")

if __name__ == "__main__":
    main()
```

### 🌡️ Lösung 1.2: Temperaturumrechner

```python
def celsius_to_fahrenheit(celsius):
    return (celsius * 9/5) + 32

def fahrenheit_to_celsius(fahrenheit):
    return (fahrenheit - 32) * 5/9

def main():
    while True:
        print("\nTemperaturumrechner")
        print("1. Celsius zu Fahrenheit")
        print("2. Fahrenheit zu Celsius")
        print("3. Beenden")
        
        wahl = input("Wählen Sie eine Option (1-3): ")
        
        if wahl == "3":
            print("Programm wird beendet.")
            break
        
        try:
            temperatur = float(input("Geben Sie die Temperatur ein: "))
        except ValueError:
            print("Ungültige Eingabe. Bitte geben Sie eine Zahl ein.")
            continue
        
        if wahl == "1":
            ergebnis = celsius_to_fahrenheit(temperatur)
            print(f"{temperatur}°C entspricht {ergebnis:.2f}°F")
        elif wahl == "2":
            ergebnis = fahrenheit_to_celsius(temperatur)
            print(f"{temperatur}°F entspricht {ergebnis:.2f}°C")
        else:
            print("Ungültige Option. Bitte wählen Sie 1, 2 oder 3.")

if __name__ == "__main__":
    main()
```

## 2. Funktionen und Module in der Praxis

### 🔐 Lösung 2.1: Passwortgenerator

```python
import random
import string

def generiere_passwort(laenge, buchstaben=True, zahlen=True, sonderzeichen=True):
    zeichen = ""
    if buchstaben:
        zeichen += string.ascii_letters
    if zahlen:
        zeichen += string.digits
    if sonderzeichen:
        zeichen += string.punctuation
    
    if not zeichen:
        return "Fehler: Mindestens eine Zeichenart muss ausgewählt sein."
    
    passwort = ''.join(random.choice(zeichen) for _ in range(laenge))
    return passwort

def main():
    print("Passwortgenerator")
    laenge = int(input("Wie lang soll das Passwort sein? "))
    buchstaben = input("Buchstaben verwenden? (j/n): ").lower() == 'j'
    zahlen = input("Zahlen verwenden? (j/n): ").lower() == 'j'
    sonderzeichen = input("Sonderzeichen verwenden? (j/n): ").lower() == 'j'
    
    passwort = generiere_passwort(laenge, buchstaben, zahlen, sonderzeichen)
    print(f"Generiertes Passwort: {passwort}")

if __name__ == "__main__":
    main()
```

### 💱 Lösung 2.2: Währungsumrechner

```python
# waehrungsumrechner.py
def eur_to_usd(eur):
    return eur * 1.18

def usd_to_eur(usd):
    return usd / 1.18

def eur_to_jpy(eur):
    return eur * 129.55

def jpy_to_eur(jpy):
    return jpy / 129.55

# hauptprogramm.py
import waehrungsumrechner as wu

def main():
    while True:
        print("\nWährungsumrechner")
        print("1. EUR zu USD")
        print("2. USD zu EUR")
        print("3. EUR zu JPY")
        print("4. JPY zu EUR")
        print("5. Beenden")
        
        wahl = input("Wählen Sie eine Option (1-5): ")
        
        if wahl == '5':
            print("Programm wird beendet.")
            break
        
        try:
            betrag = float(input("Geben Sie den Betrag ein: "))
        except ValueError:
            print("Ungültige Eingabe. Bitte geben Sie eine Zahl ein.")
            continue
        
        if wahl == '1':
            ergebnis = wu.eur_to_usd(betrag)
            print(f"{betrag} EUR = {ergebnis:.2f} USD")
        elif wahl == '2':
            ergebnis = wu.usd_to_eur(betrag)
            print(f"{betrag} USD = {ergebnis:.2f} EUR")
        elif wahl == '3':
            ergebnis = wu.eur_to_jpy(betrag)
            print(f"{betrag} EUR = {ergebnis:.2f} JPY")
        elif wahl == '4':
            ergebnis = wu.jpy_to_eur(betrag)
            print(f"{betrag} JPY = {ergebnis:.2f} EUR")
        else:
            print("Ungültige Option. Bitte wählen Sie 1-5.")

if __name__ == "__main__":
    main()
```

## 3. Einführung in OOP mit einem einfachen Taschenrechner

### 🧮 Lösung 3: Einfacher Taschenrechner

```python
class Taschenrechner:
    def addieren(self, a, b):
        return a + b
    
    def subtrahieren(self, a, b):
        return a - b
    
    def multiplizieren(self, a, b):
        return a * b
    
    def dividieren(self, a, b):
        if b == 0:
            return "Fehler: Division durch Null!"
        return a / b

def main():
    rechner = Taschenrechner()
    
    while True:
        print("\nTaschenrechner")
        print("1. Addition")
        print("2. Subtraktion")
        print("3. Multiplikation")
        print("4. Division")
        print("5. Beenden")
        
        wahl = input("Wählen Sie eine Operation (1-5): ")
        
        if wahl == '5':
            print("Programm wird beendet.")
            break
        
        try:
            zahl1 = float(input("Geben Sie die erste Zahl ein: "))
            zahl2 = float(input("Geben Sie die zweite Zahl ein: "))
        except ValueError:
            print("Ungültige Eingabe. Bitte geben Sie Zahlen ein.")
            continue
        
        if wahl == '1':
            ergebnis = rechner.addieren(zahl1, zahl2)
            print(f"{zahl1} + {zahl2} = {ergebnis}")
        elif wahl == '2':
            ergebnis = rechner.subtrahieren(zahl1, zahl2)
            print(f"{zahl1} - {zahl2} = {ergebnis}")
        elif wahl == '3':
            ergebnis = rechner.multiplizieren(zahl1, zahl2)
            print(f"{zahl1} * {zahl2} = {ergebnis}")
        elif wahl == '4':
            ergebnis = rechner.dividieren(zahl1, zahl2)
            print(f"{zahl1} / {zahl2} = {ergebnis}")
        else:
            print("Ungültige Option. Bitte wählen Sie 1-5.")

if __name__ == "__main__":
    main()
```

## 4. Erweiterung des Taschenrechners

### 🚀 Lösung 4: Erweiterter Taschenrechner

```python
import math

class ErweiterterTaschenrechner:
    def __init__(self):
        self.letztes_ergebnis = 0
        self.protokoll = []

    def _protokollieren(self, operation, a, b, ergebnis):
        self.protokoll.append(f"{operation}: {a} {operation} {b} = {ergebnis}")
        self.letztes_ergebnis = ergebnis

    def addieren(self, a, b):
        ergebnis = a + b
        self._protokollieren("+", a, b, ergebnis)
        return ergebnis

    def subtrahieren(self, a, b):
        ergebnis = a - b
        self._protokollieren("-", a, b, ergebnis)
        return ergebnis

    def multiplizieren(self, a, b):
        ergebnis = a * b
        self._protokollieren("*", a, b, ergebnis)
        return ergebnis

    def dividieren(self, a, b):
        if b == 0:
            self._protokollieren("/", a, b, "Fehler: Division durch Null!")
            return "Fehler: Division durch Null!"
        ergebnis = a / b
        self._protokollieren("/", a, b, ergebnis)
        return ergebnis

    def potenzieren(self, basis, exponent):
        ergebnis = math.pow(basis, exponent)
        self._protokollieren("^", basis, exponent, ergebnis)
        return ergebnis

    def wurzel(self, a):
        if a < 0:
            self._protokollieren("√", a, "", "Fehler: Negative Zahl unter der Wurzel!")
            return "Fehler: Negative Zahl unter der Wurzel!"
        ergebnis = math.sqrt(a)
        self._protokollieren("√", a, "", ergebnis)
        return ergebnis

    def zeige_protokoll(self):
        print("\nBerechnungsprotokoll:")
        for eintrag in self.protokoll:
            print(eintrag)

def main():
    rechner = ErweiterterTaschenrechner()
    
    while True:
        print("\nErweiterter Taschenrechner")
        print("1. Addition")
        print("2. Subtraktion")
        print("3. Multiplikation")
        print("4. Division")
        print("5. Potenzieren")
        print("6. Wurzel")
        print("7. Letztes Ergebnis anzeigen")
        print("8. Protokoll anzeigen")
        print("9. Beenden")
        
        wahl = input("Wählen Sie eine Operation (1-9): ")
        
        if wahl == '9':
            print("Programm wird beendet.")
            break
        
        if wahl == '7':
            print(f"Letztes Ergebnis: {rechner.letztes_ergebnis}")
            continue
        
        if wahl == '8':
            rechner.zeige_protokoll()
            continue
        
        try:
            if wahl in ['1', '2', '3', '4', '5']:
                zahl1 = float(input("Geben Sie die erste Zahl ein: "))
                zahl2 = float(input("Geben Sie die zweite Zahl ein: "))
            elif wahl == '6':
                zahl1 = float(input("Geben Sie die Zahl ein: "))
        except ValueError:
            print("Ungültige Eingabe. Bitte geben Sie Zahlen ein.")
            continue
        
        if wahl == '1':
            ergebnis = rechner.addieren(zahl1, zahl2)
        elif wahl == '2':
            ergebnis = rechner.subtrahieren(zahl1, zahl2)
        elif wahl == '3':
            ergebnis = rechner.multiplizieren(zahl1, zahl2)
        elif wahl == '4':
            ergebnis = rechner.dividieren(zahl1, zahl2)
        elif wahl == '5':
            ergebnis = rechner.potenzieren(zahl1, zahl2)
        elif wahl == '6':
            ergebnis = rechner.wurzel(zahl1)
        else:
            print("Ungültige Option. Bitte wählen Sie 1-9.")
            continue
        
        print(f"Ergebnis: {ergebnis}")

if __name__ == "__main__":
    main()
```

## 5. Abschlussprojekt: Dateimanager

### 📁 Lösung 5: Einfacher Dateimanager

```python
import os
import shutil
from datetime import datetime

class Datei:
    def __init__(self, pfad):
        self.pfad = pfad

    def info(self):
        stat = os.stat(self.pfad)
        return {
            "Name": os.path.basename(self.pfad),
            "Größe": f"{stat.st_size} Bytes",
            "Erstelldatum": datetime.fromtimestamp(stat.st_ctime).strftime('%Y-%m-%d %H:%M:%S'),
            "Letzte Änderung": datetime.fromtimestamp(stat.st_mtime).strftime('%Y-%m-%d %H:%M:%S')
        }

class Verzeichnis:
    def __init__(self, pfad):
        self.pfad = pfad

    def inhalt(self):
        return os.listdir(self.pfad)

    def erstelle(self, name):
        neuer_pfad = os.path.join(self.pfad, name)
        os.mkdir(neuer_pfad)
        print(f"Verzeichnis '{name}' wurde erstellt.")

class Dateimanager:
    def __init__(self):
        self.aktuelles_verzeichnis = os.getcwd()

    def zeige_inhalt(self):
        verzeichnis = Verzeichnis(self.aktuelles_verzeichnis)
        print(f"\nInhalt von {self.aktuelles_verzeichnis}:")
        for item in verzeichnis.inhalt():
            print(item)

    def wechsle_verzeichnis(self, pfad):
        neuer_pfad = os.path.join(self.aktuelles_verzeichnis, pfad)
        if os.path.isdir(neuer_pfad):
            os.chdir(neuer_pfad)
            self.aktuelles_verzeichnis = neuer_pfad
            print(f"Verzeichnis gewechselt zu: {self.aktuelles_verzeichnis}")
        else:
            print("Ungültiges Verzeichnis.")

    def erstelle_verzeichnis(self, name):
        verzeichnis = Verzeichnis(self.aktuelles_verzeichnis)
        verzeichnis.erstelle(name)

    def kopiere_datei(self, quelle, ziel):
        quell_pfad = os.path.join(self.aktuelles_verzeichnis, quelle)
        ziel_pfad = os.path.join(self.aktuelles_verzeichnis, ziel)
        try:
            shutil.copy2(quell_pfad, ziel_pfad)
            print(f"Datei '{quelle}' wurde nach '{ziel}' kopiert.")
        except FileNotFoundError:
            print("Datei nicht gefunden.")
        except shutil.SameFileError:
            print("Quelle und Ziel sind identisch.")

    def verschiebe_datei(self, quelle, ziel):
        quell_pfad = os.path.join(self.aktuelles_verzeichnis, quelle)
        ziel_pfad = os.path.join(self.aktuelles_verzeichnis, ziel)
        try:
            shutil.move(quell_pfad, ziel_pfad)
            print(f"Datei '{quelle}' wurde nach '{ziel}' verschoben.")
        except FileNotFoundError:
            print("Datei nicht gefunden.")

    def loesche(self, name):
        pfad = os.path.join(self.aktuelles_verzeichnis, name)
        try:
            if os.path.isfile(pfad):
                os.remove(pfad)
                print(f"Datei '{name}' wurde gelöscht.")
            elif os.path.isdir(pfad):
                shutil.rmtree(pfad)
                print(f"Verzeichnis '{name}' und dessen Inhalt wurden gelöscht.")
            else:
                print(f"'{name}' ist weder eine Datei noch ein Verzeichnis.")
        except FileNotFoundError:
            print(f"'{name}' nicht gefunden.")
        except PermissionError:
            print(f"Keine Berechtigung zum Löschen von '{name}'.")

    def zeige_info(self, name):
        pfad = os.path.join(self.aktuelles_verzeichnis, name)
        if os.path.exists(pfad):
            datei = Datei(pfad)
            info = datei.info()
            print("\nDatei-Informationen:")
            for key, value in info.items():
                print(f"{key}: {value}")
        else:
            print(f"'{name}' nicht gefunden.")

def main():
    manager = Dateimanager()
    
    while True:
        print("\nDateimanager")
        print("1. Inhalt anzeigen")
        print("2. Verzeichnis wechseln")
        print("3. Verzeichnis erstellen")
        print("4. Datei kopieren")
        print("5. Datei verschieben")
        print("6. Datei/Verzeichnis löschen")
        print("7. Datei-Informationen anzeigen")
        print("8. Beenden")
        
        wahl = input("Wählen Sie eine Option (1-8): ")
        
        if wahl == '1':
            manager.zeige_inhalt()
        elif wahl == '2':
            pfad = input("Geben Sie den Pfad ein: ")
            manager.wechsle_verzeichnis(pfad)
        elif wahl == '3':
            name = input("Geben Sie den Namen des neuen Verzeichnisses ein: ")
            manager.erstelle_verzeichnis(name)
        elif wahl == '4':
            quelle = input("Geben Sie den Namen der Quelldatei ein: ")
            ziel = input("Geben Sie den Namen der Zieldatei ein: ")
            manager.kopiere_datei(quelle, ziel)
        elif wahl == '5':
            quelle = input("Geben Sie den Namen der zu verschiebenden Datei ein: ")
            ziel = input("Geben Sie den Zielpfad ein: ")
            manager.verschiebe_datei(quelle, ziel)
        elif wahl == '6':
            name = input("Geben Sie den Namen der zu löschenden Datei/des zu löschenden Verzeichnisses ein: ")
            manager.loesche(name)
        elif wahl == '7':
            name = input("Geben Sie den Namen der Datei ein: ")
            manager.zeige_info(name)
        elif wahl == '8':
            print("Programm wird beendet.")
            break
        else:
            print("Ungültige Option. Bitte wählen Sie 1-8.")

if __name__ == "__main__":
    main()
```