# Microsoft Power BI: Das Praxisbuch für Datenvisualisierung und -analyse

**Inkl. Fabric und Copilot – Offizielle Begleitmaterialien**

[![CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](LICENSE)
[![Follow on X](https://img.shields.io/twitter/follow/DasBuch?style=social)](https://x.com/DasBuch)

> **Offizielle Beispieldateien, Datensätze und Ressourcen zum Bestseller. Alles, was Sie brauchen, um die Konzepte aus dem Buch direkt auszuprobieren.**

<p align="center">
<img src="assets/images/coverart/microsoft-power-bi-taschenbuch-alexander-loth.webp" alt="Book cover: Microsoft Power BI: Das Praxisbuch für Datenvisualisierung und -analyse" width="420" />
</p>

<p align="center">
<strong>Buch kaufen:</strong> <a href="https://www.thalia.de/shop/home/artikeldetails/A1075091671">Thalia</a> · <a href="https://www.amazon.de/Microsoft-Power-Praxisbuch-Datenvisualisierung-Professional/dp/3747511023">Amazon</a>
</p>

-----

## 📚 Über das Buch

Dieses Buch ist Ihr praxisnaher Leitfaden für den Einstieg und das Vertiefen von Power BI: von der Datenanbindung und -aufbereitung über aussagekräftige Visualisierungen bis hin zu DAX, Python-Integration und interaktiven Dashboards.

**Schwerpunkte:**

  * **Microsoft Fabric:** OneLake, Medallion-Architektur und Direct Lake.
  * **Copilot:** Generative KI für DAX, Berichtserstellung und Data Storytelling.
  * **Advanced Analytics:** Python/R Integration und Machine Learning.

-----

## 🛠️ Voraussetzungen & Installation

Damit Sie alle Übungen im Buch erfolgreich durchführen können, beachten Sie bitte die folgenden Systemanforderungen.

### Software & Hardware

  * **Power BI Desktop:** Kostenlos via Microsoft Store oder [Web](https://powerbi.microsoft.com/de-de/desktop/).
  * **Betriebssystem:** Windows 10 oder neuer. *Hinweis für macOS-Nutzer:* Eine Virtualisierung (z.B. Parallels Desktop) ist erforderlich, da Power BI Desktop nicht nativ auf macOS läuft.
  * **Arbeitsspeicher:** Mindestens 8 GB RAM empfohlen.

### Lizenzierung & Fabric Kapazität

Einige fortgeschrittene Kapitel erfordern spezielle Lizenzen oder Cloud-Kapazitäten.

| Feature | Benötigte Lizenz / Kapazität | Relevante Kapitel |
| :--- | :--- | :--- |
| **Basis Berichte** | Power BI Desktop (Kostenlos) | 1-3, 6, 8 |
| **Sharing/Service** | Power BI Pro oder Premium Per User (PPU) | 9 |
| **Copilot (GenAI)** | **Fabric Kapazität (F64/P1)** oder höher\* | 1.6, 3.7, 8.7 |

> **Hinweis zu Copilot:** Die Nutzung von Copilot-Funktionen erfordert, dass der Bericht in einem Arbeitsbereich liegt, der einer bezahlten Fabric-Kapazität zugewiesen ist (mind. F2 für Entwicklung, F64 für reine Konsumenten). Stellen Sie zudem sicher, dass Ihr Tenant-Administrator den "Tenant Switch" für Copilot in den Admin-Einstellungen aktiviert hat.

-----

## 📂 Inhalte des Repositories

Dieses Repository ist exakt nach der Kapitelstruktur des Buches organisiert.

✔ **.pbix-Dateien**: Die fertigen Lösungen und Zwischenstände zu jedem Kapitel.  
✔ **Datensätze**: Rohdaten wie `Financial_Sample.xlsx`.  
✔ **Vertiefende READMEs**: Zusätzliche Erklärungen in den Unterordnern.

### Kapitelübersicht

| Kapitel | Thema | Ordner & Ressourcen |
| :---: | :--- | :--- |
| 1 | 🚀 Einführung & Setup | [Kapitel\_01](Kapitel_01) |
| 2 | 🔌 Datenquellen & Power Query | [Kapitel\_02](Kapitel_02) |
| 3 | 📊 Visualisierungen & Storytelling | [Kapitel\_03](Kapitel_03) |
| 4 | 🧮 DAX Berechnungen & Parameter | [Kapitel\_04](Kapitel_04) |
| 5 | 📈 Advanced DAX (Context, CALCULATE) | [Kapitel\_05](Kapitel_05) |
| 6 | 🗺️ Geo-Analysen & Karten | [Kapitel\_06](Kapitel_06) |
| 7 | 🔬 Analytics, Prognosen & Python/R | [Kapitel\_07](Kapitel_07) |
| 8 | 🎨 Dashboard Design & Copilot | [Kapitel\_08](Kapitel_08) |
| 9 | 🌐 Governance & Veröffentlichung | [Kapitel\_09](Kapitel_09) |

-----

## 🚀 Erste Schritte

1️⃣ **Repository klonen oder herunterladen**

  * **Für Git-Nutzer (Empfohlen):**
    ```bash
    git clone https://github.com/aloth/Power-BI-Fabric-Copilot-Buch-Begleitmaterialien.git
    ```
    *Tipp:* Durch das Klonen können Sie später einfach Updates ziehen (`git pull`).
    
  * **Ohne Git:** Klicken Sie oben rechts auf `Code` → `Download ZIP` und entpacken Sie die Datei in einen lokalen Ordner.

2️⃣ **Dateien öffnen**  
Navigieren Sie in den Ordner des jeweiligen Kapitels und öffnen Sie die `.pbix`-Datei mit Power BI Desktop. Stellen Sie sicher, dass die Pfade zu den Datensätzen (z.B. `Financial_Sample.xlsx`) korrekt sind, falls Sie Datenquellen aktualisieren.

-----

## 🐍 Python & R Setup (Kapitel 7)

Für die Übungen in **Kapitel 7.6** (Integration von Python und R für fortgeschrittene Analysen) ist eine lokale Python-Installation erforderlich. Wir empfehlen die Installation der folgenden Bibliotheken, um die Beispiele im Buch ausführen zu können.

**Installation der Abhängigkeiten:**

```bash
pip install pandas matplotlib seaborn
```

Stellen Sie sicher, dass der Pfad zu Ihrer Python-Installation in den Power BI Optionen unter *Datei -\> Optionen und Einstellungen -\> Optionen -\> Python-Skripterstellung* korrekt hinterlegt ist.

-----

## 🎁 Exklusive Partner-Angebote

Als Leser dieses Buches erhalten Sie Zugang zu exklusiven Vorteilen und Angeboten (z.B. Freischaltung der Pro-Version der Mindful Coffee App).

🔗 **[Zu den Partner-Angeboten](PARTNER_ANGEBOTE.md)**

-----

## 👥 Mitwirken & Feedback

Haben Sie einen Fehler gefunden, eine Frage zu einer Übung oder eine Idee für eine noch elegantere DAX-Lösung?

  * **Fehler melden:** Bitte nutzen Sie die [Issues](https://github.com/aloth/Power-BI-Fabric-Copilot-Buch-Begleitmaterialien/issues)-Funktion dieses Repositories.

-----

## 📖 Zitieren

Wenn Sie Inhalte aus diesem Buch in wissenschaftlichen Arbeiten verwenden, nutzen Sie bitte diesen BibTeX-Eintrag:

```bibtex
@book{loth2026powerbi,
  title      = {Microsoft Power BI: Das Praxisbuch für Datenvisualisierung und -analyse},
  shorttitle = {Power BI Praxisbuch},
  author     = {Loth, Alexander and Vogel, Peter},
  year       = {2026},
  publisher  = {mitp},
  address    = {Frechen},
  isbn       = {978-3-7475-1102-2},
  url        = {https://alexloth.com/power-bi-buch/}
}
```

-----

## 🔗 Lizenz

Diese Arbeit unterliegt den Bestimmungen einer [Creative Commons Attribution 4.0 International License](LICENSE). Das bedeutet, Sie dürfen die Inhalte teilen und bearbeiten, solange Sie die Urheber nennen.

-----

## 👤 Autoren

**Alexander Loth** – Digital Strategist @ Microsoft, Autor, MBA & ehemaliger CERN-Forscher.  

[![Website](https://img.shields.io/badge/Website-alexloth.com-blue?style=flat-square)](https://alexloth.com/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-aloth-blue?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/aloth/)
[![X (Twitter)](https://img.shields.io/badge/Follow-@xlth-black?style=flat-square&logo=x)](https://x.com/xlth)

**Peter Vogel** – Experimentalphysiker & Berater für Data Strategy, spezialisiert auf moderne Analyse-Plattformen.

-----

⭐️ **Tipp:** Wenn Ihnen diese Materialien helfen, geben Sie dem Repository gerne einen **Stern** oben rechts\! Viel Erfolg beim Analysieren Ihrer Daten\!
