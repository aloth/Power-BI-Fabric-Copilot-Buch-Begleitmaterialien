# Kapitel 1: Vertiefende Konzepte

## Power BI & Fabric Lizenzen im Überblick

Die Wahl der richtigen Lizenz ist eine der häufigsten praktischen Hürden. Die Einführung von Microsoft Fabric hat die Optionen erweitert. Diese Tabelle soll Ihnen eine klare Übersicht verschaffen.

| Lizenz / SKU          | Typ                  | Zielgruppe                                       | Kernfunktionalität & Abgrenzung                                                                                             |
| --------------------- | -------------------- | ------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------- |
| **Power BI Free** | Nutzer-basiert       | Einzelanwender, Lernende                         | Erstellen von Berichten für den persönlichen Gebrauch in "Mein Arbeitsbereich". **Kein Teilen oder Konsumieren von geteilten Inhalten möglich.** |
| **Power BI Pro** | Nutzer-basiert       | Business-Anwender, kleine & mittlere Teams       | Standardlizenz für die Zusammenarbeit. Ermöglicht das Veröffentlichen, Teilen und Konsumieren von Berichten in App-Arbeitsbereichen. |
| **Power BI PPU** | Nutzer-basiert       | Power User, Analysten in größeren Unternehmen    | Bietet **alle Premium-Funktionen** (z.B. große Datenmodelle, Paginated Reports, Deployment Pipelines) auf einer Pro-Nutzer-Basis. |
| **Power BI Premium** | Kapazitäts-basiert   | Große Unternehmen, unternehmensweites BI         | Dedizierte Rechenleistung (P-SKU) für hohe Performance und große Nutzerzahlen. Free-Nutzer können Inhalte konsumieren, die auf dieser Kapazität gehostet werden. |
| **Fabric Capacity** | Kapazitäts-basiert   | Organisationen, die die gesamte Fabric-Plattform nutzen | Einheitliche Rechenleistung (F-SKU) für **alle Fabric-Workloads** (Power BI, Data Factory, Synapse etc.). **Wichtig:** Zum Teilen und Veröffentlichen von Power BI-Inhalten benötigen die Entwickler weiterhin eine **Power BI Pro-Lizenz**. |
| **Fabric Free** | Nutzer-basiert       | Einzelanwender, Lernende (Fabric-Kontext)        | Ermöglicht das Ausprobieren **aller Fabric-Funktionen**, einschließlich Power BI. Inhalte können aber nur im eigenen "OneLake" gespeichert werden. |

**Fazit:** Für die Zusammenarbeit mit Power BI-Berichten bleibt die **Pro-Lizenz** der Standard für jeden Entwickler und jeden konsumierenden Nutzer (der nicht auf einer Premium-Kapazität liest). Fabric-Kapazitäten ersetzen die Notwendigkeit von Premium-Kapazitäten und erweitern diese um zusätzliche Daten-Services.

-----

## Die drei Speichermodi von Power BI

In Kapitel 1 laden Sie Ihre ersten Daten in Power BI. Hinter den Kulissen hat Power BI dabei den **Import-Modus** verwendet. Hier werden die drei verschiedenen Wege vorgestellt, wie Power BI auf Daten zugreifen kann.

1.  **Import (Standard & häufigster Modus)**

      - **Was passiert?** Die Daten werden aus der Quelle kopiert, komprimiert und in der `.pbix`-Datei gespeichert (VertiPaq-Engine).
      - **Vorteile:** Maximale Performance, da alle Berechnungen in der schnellen In-Memory-Engine von Power BI stattfinden. Voller DAX- und Power Query-Funktionsumfang.
      - **Nachteile:** Daten sind nur so aktuell wie der letzte Refresh. Die Größe des Datasets ist durch den Arbeitsspeicher begrenzt.

2.  **DirectQuery**

      - **Was passiert?** Power BI speichert nur die Metadaten (Tabellen- und Spaltennamen). Jede Interaktion im Bericht (z.B. Klick auf einen Slicer) erzeugt eine Live-Abfrage an die Quelldatenbank.
      - **Vorteile:** Daten sind immer in Echtzeit. Ideal für sehr große Datenmodelle (Big Data), die nicht importiert werden können.
      - **Nachteile:** Performance hängt vollständig von der Geschwindigkeit der Quelldatenbank ab. Nicht alle DAX- und Power Query-Funktionen sind verfügbar.

3.  **Direct Lake (Der neue Modus mit Fabric)**

      - **Was passiert?** Ein revolutionärer Hybridansatz. Power BI liest Parquet-Dateien direkt aus dem Microsoft Fabric OneLake, ohne Daten zu importieren oder zu duplizieren.
      - **Vorteile:** Kombiniert die Performance des Import-Modus mit der Echtzeit-Fähigkeit von DirectQuery für Daten, die in Fabric gespeichert sind.
      - **Nachteile:** Funktioniert nur für Daten, die sich im Fabric OneLake befinden.

Dieses Wissen hilft Ihnen, die richtige Architektur für Ihre zukünftigen Projekte zu planen.
