# Übungen Thema 7.5

## Aufgaben

Aufgaben zum Thema.

Danke an Hari Thavachchelvam für die Idee zur Aufgabenstellung. 

### Aufgabe 7.5.1: Datenbank auslesen und sortieren

Laden sie als erstes die Datei [`quiz.db`](https://raw.githubusercontent.com/janikvonrotz/python.casa/main/topic-7-5/quiz.db) herunter und speichern sie es in einem Ordner. Erstellen sie die Datei `quiz.py` im selben Ordner.

Schauen sie sich die Datenbank mit VSCode an und beantworten sie diese Fragen:
* Wieviele Datensätze gibt es?
* Welche Spalte identifiziert die Datensätze eindeutig und wie heisst diese?
* Welcher Datentyp hat diese Spalte?

Erstellen sie nun ein Progamm um einen bestimmten Datensatz auszulesen. Ergänzen sie dazu die Markierungen `?????` im folgenden Code:

```py
import sqlite3

# Verbindung, Cursor
connection = sqlite3.connect("?????.db")
cursor = connection.cursor()

# SQL-Abfrage
sql = "SELECT * FROM questions WHERE ????? = 403"

# Absenden der SQL-Abfrage und Empfang des Ergebnis
cursor.execute(sql)

# Ausgabe des Ergebnis
for datensatz in cursor:
    print("Frage: ", datensatz[1])
    print("Antworten: ", datensatz[2:6])

# Verbindung beenden
connection.close()
```

### Aufgabe 7.5.2: Abfrage mit Input

Mit dem `input` Befehl können wir nach einer bestimmten Frage-ID und Antwort-Nummer fragen. Erweitern sie das Skript aus der vorhergehenden Aufgabe mit dem Befehl.

Dazu diese Inputs:

```py
# SQL-Abfrage mit Eingabe
frage = input("Bitte geben sie eine Frage-ID ein: ")
sql = "SELECT * FROM questions WHERE questionID = " + frage
```

```py
	# Eingabe Antwort
    antwort = input("Ihre Antwort 1-4: ")
```

```py
    # Ausgabe korrekt/falsch
    korrekt = str(datensatz[6])
    if korrekt == antwort:
        print("\nDie Antwort ist korrekt!\n")
    else:
        print("\nDie Antwort ist falsch!\n")
```

**Zusatzaufgabe**

Können sie das Programm in einer Schleife schalten, bis man die richtige Antwort gefunden hat?

Erstellen sie eine eine Frage-ID nach Zufall und filtern sie verfügbaren Fragen anhand des Schwierigkeits-Grades.