# Kapitel 5: Vertiefende Konzepte für DAX

Dieses Kapitel im Buch führt Sie in die Grundlagen von DAX (Data Analysis Expressions) ein. Diese `README.md`-Datei dient als Ergänzung und vertieft gezielt Konzepte, die für die Erstellung robuster und performanter DAX-Lösungen entscheidend sind.

---

## DAX Best Practices: Ein Leitfaden für sauberen Code

Guter DAX-Code ist nicht nur korrekt, sondern auch lesbar, wartbar und performant. Bevor Sie komplexe Modelle bauen, sollten Sie sich folgende grundlegende Prinzipien aneignen:

1.  **Immer explizite Measures verwenden:** Ziehen Sie niemals ein numerisches Feld direkt in ein Visual. Erstellen Sie stattdessen immer ein explizites Measure.
    * **Schlecht:** Feld `Umsatz` in ein Visual ziehen (implizites Measure).
    * **Gut:** Ein Measure erstellen: `Gesamtumsatz = SUM(Finanzdaten[Umsatz])`.
    Dies stellt sicher, dass die Geschäftslogik an einem zentralen Ort definiert ist und in allen Visuals konsistent verwendet wird.

2.  **Variablen (`VAR`) nutzen:** Bei längeren Formeln sollten Sie Zwischenergebnisse in Variablen speichern.
    * **Verbessert die Lesbarkeit:** Komplexe Logik wird in logische Schritte unterteilt.
    * **Verbessert die Performance:** Ein Ausdruck in einer Variable wird nur einmal berechnet und kann dann mehrfach wiederverwendet werden.

3.  **Sichere Division mit `DIVIDE()`:** Verwenden Sie anstelle des Divisionsoperators (`/`) immer die `DIVIDE()`-Funktion. Sie fängt den Fehler bei einer Division durch Null automatisch ab und gibt standardmäßig `BLANK()` (oder einen optionalen Alternativwert) zurück.

---

## Fensterfunktionen in DAX: WINDOW, OFFSET und INDEX

Für eine bestimmte Klasse von analytischen Berechnungen bietet DAX eine Gruppe leistungsfähiger Funktionen, die oft als „Fensterfunktionen“ (Window Functions) bezeichnet werden. Die Kernfunktionen dieser Gruppe – `WINDOW`, `OFFSET` und `INDEX` – sind speziell dafür konzipiert, Berechnungen über einen definierten Bereich (ein „Fenster“) von Zeilen auszuführen.

Dieser Ansatz vereinfacht viele Szenarien, wie gleitende Durchschnitte oder Periodenvergleiche. Die Formeln werden dadurch oft lesbarer, wartbarer und können in bestimmten Fällen auch performanter sein als alternative, komplexere DAX-Muster.

#### Die Kernkonzepte: `ORDERBY` und `PARTITIONBY`

Das Verhalten der Fensterfunktionen wird durch zwei essenzielle Hilfsfunktionen gesteuert. Sie definieren den Kontext, in dem die Berechnung stattfindet:

* **`ORDERBY`:** Legt die Sortierreihenfolge der Daten fest, bevor die Berechnung ausgeführt wird. In der Regel handelt es sich hierbei um eine Datums-, Zeit- oder Indexspalte.
* **`PARTITIONBY`:** Gruppiert die Daten in Partitionen. Die Berechnung wird dann für jede dieser Gruppen separat und unabhängig von den anderen durchgeführt (z.B. für jede Produktkategorie einzeln).

Diese beiden Funktionen werden als Argumente innerhalb der Hauptfunktionen verwendet, um das Datenfenster präzise zu definieren.

#### `WINDOW`: Berechnungen über einen relativen Zeilenbereich

Die `WINDOW`-Funktion eignet sich für Berechnungen, die sich über einen Bereich von Zeilen erstrecken, der relativ zur aktuell betrachteten Zeile ist. Ein typischer Anwendungsfall ist die Berechnung eines gleitenden Durchschnitts.

**DAX-Measure:**
```DAX
Umsatz 3-Monats-Schnitt =
AVERAGEX(
    WINDOW(
        -2, -- Start: 2 Perioden vor der aktuellen (relative Position)
        0,  -- Ende: Die aktuelle Periode (relative Position)
        ALLSELECTED('Datum'[MonatJahr]), -- Die Tabelle/Spalte, über die iteriert wird
        ORDERBY('Datum'[MonatJahr], ASC) -- Die Sortierreihenfolge
    ),
    [Gesamtumsatz] -- Der Ausdruck, der für jede Zeile im Fenster berechnet wird
)
````

#### `OFFSET`: Werte aus einer benachbarten Zeile abrufen

Die `OFFSET`-Funktion dient dazu, einen Wert aus einer Zeile mit einem bestimmten Abstand zur aktuellen Zeile abzurufen. Während Time-Intelligence-Funktionen wie `DATEADD` auf Datumsspalten spezialisiert sind, bietet `OFFSET` einen allgemeineren Mechanismus, der auf jeder sortierbaren Spalte funktioniert.

**DAX-Measure:**

```dax
Umsatz Vormonat (OFFSET) =
CALCULATE(
    [Gesamtumsatz],
    OFFSET(
        -1, -- Verschiebe den Kontext um eine Position zurück
        ALLSELECTED('Datum'[MonatJahr]),
        ORDERBY('Datum'[MonatJahr], ASC)
    )
)
```

#### `INDEX`: Auf eine absolute Position innerhalb einer Partition zugreifen

Im Gegensatz zu relativen Funktionen wie `WINDOW` und `OFFSET` greift die `INDEX`-Funktion auf eine Zeile an einer absoluten Position innerhalb einer definierten Partition zu.

**DAX-Measure:**

```dax
Umsatzstärkstes Produkt pro Kategorie =
CALCULATE(
    SELECTEDVALUE('Produkte'[Produktname]),
    INDEX(
        1, -- Nimm die erste Position in der sortierten Liste
        ALLSELECTED('Produkte'[Produktname]),
        ORDERBY([Gesamtumsatz], DESC), -- Sortiere die Produkte nach Umsatz absteigend
        PARTITIONBY('Produkte'[Kategorie]) -- Führe dies für jede Kategorie separat durch
    )
)
```
