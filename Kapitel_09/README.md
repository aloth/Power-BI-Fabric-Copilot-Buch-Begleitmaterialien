# Kapitel 9: Vertiefende Konzepte zum Teilen und Sichern von Analysen

Nachdem Sie im Buch die grundlegenden Mechanismen zum Veröffentlichen und Teilen Ihrer Analysen kennengelernt haben, vertieft dieses Dokument zwei entscheidende Aspekte für den professionellen Einsatz in Unternehmen: die strategische Wahl der richtigen Sharing-Methode und die Absicherung Ihrer Daten durch Data Governance.

---

### Data Governance mit Vertraulichkeitsbezeichnungen (Sensitivity Labels)

Das einfache Teilen von Berichten ist eine Stärke von Power BI, birgt aber auch Risiken. Nicht alle Daten sind für alle Adressaten bestimmt. Eine robuste Governance-Strategie ist daher unerlässlich. Power BI integriert sich hierfür nahtlos in Microsoft Purview, die zentrale Plattform für Compliance und Datensicherheit.

Das Kernstück dieser Integration sind die **Vertraulichkeitsbezeichnungen**.

**Was sind Vertraulichkeitsbezeichnungen?**

Es handelt sich um zentral definierte, digitale Etiketten (z.B. „Öffentlich“, „Intern“, „Streng vertraulich“), die auf Power BI-Artefakte (Berichte, Datasets etc.) angewendet werden. Sie sind jedoch mehr als nur ein Hinweis – sie sind Träger von aktiven Sicherheitsrichtlinien.

**Zentrale Mechanismen:**

1.  **Zentrale Definition:** Die Bezeichnungen und ihre Regeln (z.B. „Export blockieren“) werden nicht in Power BI, sondern zentral im Microsoft Purview Compliance Portal von Administratoren festgelegt.
2.  **Anwendung und Vererbung:** Als Ersteller wenden Sie diese Labels in Power BI Desktop oder im Service an. Ein als „Vertraulich“ gekennzeichnetes Dataset vererbt diese Bezeichnung automatisch an alle Berichte, die darauf basieren. Der Schutz ist also konsistent.
3.  **Schutz über Power BI hinaus:** Dies ist der entscheidende Punkt. Wenn ein Benutzer Daten aus einem geschützten Bericht nach Excel exportiert, erbt die Excel-Datei automatisch dasselbe Label und dessen Schutzrichtlinien (z.B. Verschlüsselung). Die Daten bleiben also auch außerhalb von Power BI geschützt.

Die Verwendung von Vertraulichkeitsbezeichnungen ist der Schritt von einem unregulierten Self-Service-BI zu einer verwalteten und sicheren Analyseumgebung, die den Compliance-Anforderungen von Unternehmen gerecht wird.

---

### Strategisches Teilen: Die richtige Methode für jeden Anwendungsfall

Power BI bietet verschiedene Wege, Inhalte zu teilen. Die Wahl der richtigen Methode ist entscheidend für eine gute User Experience und eine saubere Verwaltung.

| Methode | Ideal für... | Wichtige Merkmale |
| :--- | :--- | :--- |
| **Direktes Teilen** (Share) | Ad-hoc-Freigaben an Einzelpersonen oder kleine, definierte Gruppen. Schnelle, informelle Abstimmungen. | - **Granular:** Sie teilen einen einzelnen Bericht oder ein Dashboard. <br> - **Unstrukturiert:** Keine Bündelung mehrerer Inhalte möglich. <br> - **Benachrichtigung:** Empfänger erhalten eine E-Mail mit einem Link. |
| **Arbeitsbereich** (Workspace) | Die **Zusammenarbeit von Entwicklern und Analysten**. Der "Maschinenraum" oder die "Werkstatt". | - **Kollaborativ:** Alle Mitglieder haben (je nach Rolle) Bearbeitungsrechte. <br> - **Unübersichtlich für Endanwender:** Zeigt alle zugehörigen Inhalte (Datasets, Dataflows etc.), was für reine Konsumenten verwirrend ist. |
| **Power BI App** | Die **formale Verteilung von fertigen Berichten** an eine breite Gruppe von Endanwendern. Der "Showroom". | - **Gebündelt:** Fasst mehrere Berichte und Dashboards zu einer professionellen Anwendung zusammen. <br> - **Saubere Oberfläche:** Konsumenten sehen nur die für sie relevanten Berichte, nicht die zugrundeliegenden Datasets. <br> - **Eigene Navigation:** Ermöglicht die Erstellung einer kuratierten Navigation und Gliederung der Inhalte. |

**Fazit:** Arbeitsbereiche sind für die **Erstellung** da, Power BI Apps für die **Konsumption**. Das direkte Teilen sollte nur für Ausnahmefälle genutzt werden.
