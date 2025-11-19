# Kapitel 4: Vertiefende Konzepte zu Berechnungen und Parametern

Dieses Dokument ergänzt die im Buch vorgestellten Konzepte zu Aggregationen, Berechnungen und Parametern. Der Fokus liegt hier auf grundlegenden Prinzipien und fortgeschrittenen Konzepten, die Ihnen helfen, nicht nur funktionierende, sondern auch robuste und verständliche DAX-Lösungen zu entwickeln.

---

### Best Practices für Berechnungen: Robuste und wartbare Formeln erstellen

Die Erstellung von Berechnungen ist ein zentraler Bestandteil der Arbeit mit Power BI. Die folgenden etablierten Vorgehensweisen (Best Practices) legen den Grundstein für professionelle und performante Berichte.

#### 1. Explizite anstelle von impliziten Berechnungen verwenden

* **Implizite Berechnung:** Entsteht, wenn Sie ein numerisches Feld (z.B. `Umsatz`) direkt in ein Visual ziehen. Power BI führt automatisch eine Aggregation (z.B. Summe) durch. Diese Logik ist jedoch nicht zentral im Modell definiert.
* **Explizite Berechnung:** Wird von Ihnen als DAX-Formel erstellt, z.B. `Gesamtumsatz = SUM(Finanzdaten[Umsatz])`.

**Empfehlung:** Verwenden Sie **ausschließlich explizite Berechnungen**. Dies stellt sicher, dass Ihre Geschäftslogik zentral, wiederverwendbar und eindeutig definiert ist.

#### 2. Sichere Division mit der DIVIDE()-Funktion

Eine Division durch Null führt in DAX zu einem Fehler. Anstatt den Divisionsoperator (`/`) zu verwenden, sollte immer die `DIVIDE()`-Funktion genutzt werden.

* **Unsicher:** `[Gewinn] / [Umsatz]`
* **Robust:** `DIVIDE([Gewinn], [Umsatz])`

`DIVIDE()` fängt den Fehler bei einer Division durch Null automatisch ab und gibt standardmäßig ein leeres Ergebnis (`BLANK`) zurück, was in Visuals korrekt dargestellt wird.

#### 3. Lesbarkeit und Performance durch Variablen (VAR) verbessern

Bei komplexeren Formeln sollten Sie Zwischenergebnisse in Variablen speichern. Das `VAR...RETURN`-Konstrukt ist hierfür essenziell.

**Beispiel mit Variablen:**
```DAX
Gewinnentwicklung Vorjahr % =
VAR AktuellerGewinn = [Gesamtumsatz] - [Gesamtkosten]
VAR Vorjahresgewinn =
    CALCULATE(
        [Gesamtumsatz] - [Gesamtkosten],
        SAMEPERIODLASTYEAR('Datum'[Datum])
    )
RETURN
    DIVIDE(
        AktuellerGewinn - Vorjahresgewinn,
        Vorjahresgewinn
    )
````

**Vorteile:**

  * **Lesbarkeit:** Die Formel wird in logische, verständliche Schritte unterteilt.
  * **Performance:** Ausdrücke in Variablen werden nur einmal berechnet, auch wenn sie mehrfach verwendet werden.

-----

### Ein grundlegendes Konzept verstehen: Der Filterkontext

Jede DAX-Berechnung wird innerhalb eines sogenannten **Filterkontexts** (Filter Context) ausgeführt. Dies ist die "Umgebung" aus aktiven Filtern, die auf das Datenmodell wirken, wenn eine Berechnung stattfindet.

Das Verständnis dieses Konzepts ist der Schlüssel zur Beherrschung von DAX.

**Beispiel:**
Sie haben die einfache Berechnung `Gesamtumsatz = SUM(Finanzdaten[Umsatz])`.

1.  **In einer KPI-Karte (Card Visual):** Es gibt keinen lokalen Filter. Der Filterkontext ist leer (abgesehen von Seitenslicern). Die Berechnung liefert den **Gesamtumsatz über alle Daten**.
2.  **In einer Tabellenzeile für "Deutschland":** Der Filterkontext für diese Zelle ist `Länder[Land] = "Deutschland"`. Dieselbe Berechnung `[Gesamtumsatz]` liefert nun den **Umsatz nur für Deutschland**.

Jedes Element in einem Visual (eine Zeile in einer Tabelle, ein Balken in einem Diagramm, eine Zelle in einer Matrix) definiert einen eigenen Filterkontext. Ihre DAX-Berechnungen reagieren dynamisch auf diesen Kontext. Die Funktion `CALCULATE()`, die Sie in Kapitel 5 kennenlernen, ist das mächtigste Werkzeug in DAX, weil sie es Ihnen erlaubt, diesen Filterkontext gezielt zu **manipulieren**.
