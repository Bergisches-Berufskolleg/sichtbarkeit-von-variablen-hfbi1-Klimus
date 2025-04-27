# Python: Sichtbarkeit von Variablen
Variablen im Quellcode sind nur in bestimmten Bereichen sichtbar.

## Gobale Variablen
**Definition**: Globale Variablen werden außerhalb von Funktionen definiert und sind im gesamten Programm verfügbar.  
**Sichtbarkeit**: Sie können von jeder Funktion aus gelesen werden, aber um sie innerhalb einer Funktion zu ändern, muss das Schlüsselwort `global` verwendet werden.  
**Shadowing**: Lokale Variablen mit gleichem Namen wie eine globale Variable überdeckt die globale. 

**Beispiel für das Lesen einer globalen Variable:**
```
zahl = 10 # Globale Variable

def drucke_zahl():
    print(zahl)  # Zugriff auf die globale Variable

drucke_zahl()  # Ausgabe: 10
```

**Beispiel für das Ändern einer globalen Variable:**
```
zahl = 10  # Globale Variable

def funktion():
    global zahl
    zahl = 20  # Ändert die globale Variable

funktion()
print(zahl)  # Ausgabe: 20
```

**Beispiel für Shadowing (Überdecken von Variablen):**
```
x = 10  # Globale Variable

def funktion():
    x = 20  # Lokale Variable überdeckt die globale Variable
    print(x)  # Ausgabe: 20

funktion()
print(x)  # Ausgabe: 10
```

## Lokale Variablen
**Definition**: Lokale Variablen werden innerhalb einer Funktion definiert und sind nur innerhalb dieser Funktion sichtbar.  
**Sichtbarkeit**: Sie existieren nur während der Ausführung der Funktion und sind außerhalb der Funktion nicht zugänglich.
```
def berechne_summe():
    a = 5  # Lokale Variable
    b = 3  # Lokale Variable
    summe = a + b
    return summe

print(berechne_summe())  # Ausgabe: 8
# print(summe)  # Fehler: NameError, da 'summe' außerhalb der Funktion nicht zugänglich ist
```

### Verschachtelte Funktionen
**Definition**: Eine Lokale Variable einer äußeren (umgebenden) Funktion.
**Sichtbarkeit**: Lokale Variablen einer äußeren Funktion können von einer inneren Funktion gelesen werden, aber um sie zu ändern, muss das Schlüsselwort `nonlocal`verwendet werden. 

**Beispiel für das Lesen eine lokalen Variable der äußeren Funktion**:
```
def aeußere_funktion():
    x = 10  # Variable der äußeren Funktion

    def innere_funktion():
        print(x)  # Zugriff auf die Variable der äußeren Funktion

    innere_funktion()

aeußere_funktion()  # Ausgabe: 10
```

**Beispiel für das Ändern eine lokalen Variable der äußeren Funktion**:
```
def aeußere_funktion():
    x = 5  # Variable der äußeren Funktion

    def innere_funktion():
        nonlocal x
        x = 10  # Ändert die Variable der äußeren Funktion

    innere_funktion()
    print(x)  # Ausgabe: 10

aeußere_funktion()
```

## Zusammenfassung der Schlüsselwörter
| Schlüsselwort   | Zweck                                                                 |
|-----------------|----------------------------------------------------------------------|
| `global`        | Zugriff und Änderung einer globalen Variable innerhalb einer Funktion |
| `nonlocal`      | Zugriff und Änderung einer Variablen aus einer äußeren Funktion       |

## Aufgabe
Gehen Sie zur folgenden Seite und Lösen Sie die Multiple Choice Aufgaben:
[Multiple Choice zu Sichtbarkeit von Variablen](https://bergisches-berufskolleg.github.io/python-kurs-starter-funktionen-pks-svv/) 

**Hinweis**: In diesem Tutorial muss kein Quellcode geschrieben und hochgeladen werden. Es geht lediglich um Theory samt Selbstüberprüfung per Multple Choice.
