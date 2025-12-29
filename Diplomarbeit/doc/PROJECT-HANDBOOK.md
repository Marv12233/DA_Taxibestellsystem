#  Projekthandbuch – Digitales Taxibestellsystem

## 1. Einleitung
- **Zweck des Projekthandbuchs:**  
  Dieses Dokument beschreibt die Organisation, Planung und Vorgehensweise für die Umsetzung des digitalen Taxibestellsystems im Rahmen der Diplomarbeit. Es dient als verbindliche Grundlage für alle Teammitglieder und stellt sicher, dass Entwicklung, Dokumentation und Zusammenarbeit koordiniert erfolgen.

- **Geltungsbereich:**  
  Das Projekthandbuch gilt für alle Mitglieder des Projektteams und beschreibt die gemeinsame Arbeitsweise für alle Teilmodule (Fahrer-App, Kunden-App, Admin-Webinterface, Projektmanagement).

- **Version & Änderungsverlauf:**  

| Version | Datum       | Autor              | Änderung                   |
|---------|-------------|-------------------|----------------------------|
| 3.0     | 29.12.2025  | Marvin Luschenz    | Aktualisierte Version Projekthandbuch |

---

## 2. Projektorganisation
- **Projektleiter:** Marvin Luschenz (Projektmanagement)  
- **Team & Rollen:**  

| Rolle / Bereich          | Name             | Verantwortlichkeiten |
|---------------------------|-----------------|----------------------|
| Projektmanagement         | Marvin Luschenz | Steuerung, Planung, Dokumentation, Kommunikation |
| Fahrer-App (Flutter)      | David Iszovits  | Entwicklung, GPS-Verarbeitung, Live-Daten, Offline-Fähigkeit |
| Kunden-App (Flutter)      | Marvin Winter   | Entwicklung, Fahrtenbuchung, Auth, Echtzeit-Tracking |
| Admin- & Webinterface     | Nikola Maksic   | Entwicklung, Verwaltung, Rollen & Rechte, Datenstruktur |

- **Eskalationswege:**  
  1. Entwickler → Projektleiter (Marvin L.)  
  2. Projektleiter → Betreuer  

---

## 3. Projektziele und -abgrenzung
- **Projektauftrag / Vision:**  
  Entwicklung eines digitalen Taxibestellsystems, das Fahrgästen eine einfache Buchung ermöglicht, Fahrern eine Echtzeitübersicht bietet und Administratoren die Verwaltung digitalisiert.

- **Ziele:**  
  - Entwicklung einer **Fahrer-App** (Flutter, Echtzeit-Standort, Supabase-Integration)  
  - Entwicklung einer **Kunden-App** (Flutter, Buchung, Echtzeit-Tracking, sichere Authentifizierung)  
  - Entwicklung eines **Admin-Webinterfaces** (Browser-basiert, Verwaltung von Kunden, Fahrern und Fahrten)  
  - Aufbau eines **Supabase-Backends** als zentrale Plattform für Datenhaltung und Echtzeit-Kommunikation  
  - Anwendung agiler Projektmanagement-Methoden (Kanban)  

- **Nicht-Ziele / Abgrenzung:**  
  - Keine Integration mit externen Payment-Gateways (Kreditkarte, PayPal etc.)  
  - Keine KI-basierte Routenoptimierung  
  - Kein Support für Betriebssysteme außerhalb Android/iOS und Browser  

- **Stakeholder:**  
  - Partnerunternehmen (Auftraggeber)  
  - Fahrgäste (Endkunden)  
  - Fahrer  
  - Admins/Disponenten  
###  3.1 Bezug zu den Sustainable Development Goals (SDGs)

Das Projekt **„Digitales Taxibestellsystem“** trägt zur Erreichung mehrerer globaler Nachhaltigkeitsziele der Vereinten Nationen (UN) bei.  
Durch die Digitalisierung des Taxiverkehrs, moderne App-Entwicklung und effiziente Zusammenarbeit werden Innovation, Nachhaltigkeit und Wirtschaftswachstum gefördert.

---

| SDG | Ziel | Beitrag des Projekts |
|:--:|:--|:--|
| [![SDG 8 – Menschenwürdige Arbeit und Wirtschaftswachstum](https://sdgs.un.org/sites/default/files/goals/E_SDG_Icons-08.jpg)](https://sdgs.un.org/goals/goal8) | **SDG 8 – Menschenwürdige Arbeit und Wirtschaftswachstum** | Durch die Digitalisierung von Arbeitsprozessen im Taxigewerbe werden Aufträge effizienter verteilt und Arbeitsbedingungen moderner gestaltet. |
| [![SDG 9 – Industrie, Innovation und Infrastruktur](https://sdgs.un.org/sites/default/files/goals/E_SDG_Icons-09.jpg)](https://sdgs.un.org/goals/goal9) | **SDG 9 – Industrie, Innovation und Infrastruktur** | Das Projekt fördert digitale Innovation und schafft eine nachhaltige, app-basierte Infrastruktur für die regionale Mobilität. |
| [![SDG 11 – Nachhaltige Städte und Gemeinden](https://sdgs.un.org/sites/default/files/goals/E_SDG_Icons-11.jpg)](https://sdgs.un.org/goals/goal11) | **SDG 11 – Nachhaltige Städte und Gemeinden** | Durch optimierte Routenplanung und digitale Fahrtvermittlung werden Leerfahrten reduziert und die urbane Mobilität nachhaltiger gestaltet. |
| [![SDG 17 – Partnerschaften zur Erreichung der Ziele](https://sdgs.un.org/sites/default/files/goals/E_SDG_Icons-17.jpg)](https://sdgs.un.org/goals/goal17) | **SDG 17 – Partnerschaften zur Erreichung der Ziele** | Die enge Zusammenarbeit zwischen Team, Schule und Partnerunternehmen zeigt den Wert von Kooperation und Wissenstransfer. |

**Fazit:**  
Das digitale Taxibestellsystem unterstützt nachhaltige Stadtentwicklung, fördert Innovation im Mobilitätssektor und stärkt partnerschaftliche Zusammenarbeit im Sinne der globalen Nachhaltigkeitsziele.

---

## 4. Vorgehensmodell & Projektphasen
- **Vorgehensmodell:**  
  Agiles Vorgehen mit **Kanban** (GitHub Projects).  

- **Phasen und Meilensteine:**  

| Phase                | Meilenstein                          | Termin (TODO)     | Verantwortlich |
|-----------------------|--------------------------------------|------------------|----------------|
| Analyse & Konzeption  | Projektplan, Architektur-Entwurf     |                  | Team |
| Implementierung       | Prototypen pro Modul                 |                  | Entwickler |
| Integration           | Supabase-Anbindung aller Module      |                  | Team |
| Test & Qualitätssich. | Systemtests, Bugfixes                |                  | Team |
| Dokumentation         | Diplomarbeit, Projekthandbuch final  |                  | Team |
| Abschluss             | Abgabe Diplomarbeit, Präsentation    |                  | Alle |

---

## **4.1 Anforderungsmanagement**

Das Anforderungsmanagement bildet die Grundlage für die strukturierte Entwicklung des Projekts **„Digitales Taxibestellsystem“**.  
Da das Team eigenständig ein verbessertes System gegenüber einer bestehenden Lösung entwickelt, wurden die Anforderungen **intern im Team** erarbeitet – ohne direkte Abstimmung mit einem Auftraggeber.

---

### Vorgehensweise

Zu Beginn des Projekts wurde das bestehende Taxibestellsystem analysiert, um Schwachstellen sowie Optimierungspotenziale zu identifizieren.  
Auf Basis dieser Analyse definierte das Projektteam neue funktionale und nicht-funktionale Anforderungen, die strukturiert in Form von **User Stories** erfasst wurden.

Jede User Story beschreibt eine konkrete Anforderung aus Sicht der jeweiligen Rolle (z. B. Kunde, Fahrer, Administrator oder Projektmanager) und folgt einem einheitlichen Dokumentationsschema.  
Dieses Schema stellt sicher, dass alle Anforderungen klar formuliert, nachvollziehbar dokumentiert und eindeutig referenzierbar sind.

Eine User Story enthält dabei folgende Elemente:

- **Req-ID** zur eindeutigen Identifikation der Anforderung  
- **Req-Heading** als kurze, prägnante Überschrift  
- **Req-Text** zur Beschreibung der Anforderung aus Nutzerperspektive  
- **Comments** für ergänzende Hinweise, Rahmenbedingungen oder Erläuterungen  
- **Creator** zur Zuordnung des Erstellers  
- **Priority** gemäß MoSCoW-Methode (Must, Should, Could)  
- **Revision** zur Versionskennzeichnung  
- **Date** zur zeitlichen Einordnung der Anforderung  

Alle User Stories sind im separaten Dokument  
**„User Storys – Digitales Taxibestellsystem“**  
vollständig dokumentiert und bilden die Grundlage für Planung, Umsetzung und Nachverfolgung der Anforderungen.

### **Priorisierung & Verwaltung**

Die Priorisierung erfolgt mit der **MoSCoW-Methode** (Must, Should, Could) und die Aufwandsschätzung über **Story Points**.  
Die Verwaltung der Anforderungen und Aufgaben erfolgt zentral im **GitHub-Projektboard des Projektleiters**, welches für die gesamte Projektplanung genutzt wird.  

Dort durchlaufen alle Aufgaben die Phasen:  
> **Backlog → In Progress → Review → Done**

---

### **Validierung**

Die Validierung der Anforderungen erfolgt **intern im Team** durch manuelle Tests, Code Reviews und den Abgleich mit den festgelegten **Akzeptanzkriterien**.  
So wird sichergestellt, dass alle definierten Anforderungen technisch korrekt umgesetzt und funktional erfüllt sind.

---

### **Abbildung X: Ablauf des internen Anforderungsmanagements**

> **Analyse bestehendes System → Ableitung neuer Anforderungen → User Stories → Priorisierung → Umsetzung → Validierung**


## 5. Projektplanung
- **Zeitplan:**  
   - Im Github mit GithubProjects festgehalten 

- **Ressourcenplanung:**  
  - Hardware: Entwicklungsrechner, Smartphones (iOS & Android), Testgeräte  
  - Software: Flutter SDK, Supabase, GitHub, VS Code/Android Studio, Notion  
  - Kollaboration: GitHub Projects, Notion, Discord/Slack/Teams  

- **Budgetplanung:**  
  - Nutzung von **kostenlosen/Studierenden-Lizenzen** für Supabase & GitHub  
  - Keine externen Kosten geplant  

---

## 6. Kommunikation
- **Meetingstruktur:**  
  - Monatliche Teammeeting (Jour Fixe)  
  - Wöchentliche Abstimmung über Chat (Discord/Teams)  
  - Sprint-Demos bei Meilensteinen  

- **Berichtswege:**  
  - Entwickler → Projektleiter → Betreuer/Auftraggeber  

- **Dokumentationsplattform:**  
  - GitHub (Code, Issues, Projekthandbuch)  
  - Notion (Protokolle, Wissenssammlung)  

---

## 7. Dokumentation & Ablage
- **Namenskonventionen:**  
  - Branch-Namen: `feature/<name>`, `bugfix/<name>`  
  - Commit-Messages: Englisch, prägnant  

- **Ordnerstruktur (Beispiel):**  
```
/driver-app
/customer-app
/admin-interface
/docs
   PROJECT_HANDBOOK.md
...
```

- **Versionierung:**  
  GitHub Flow mit Pull Requests & Code Reviews  

---

## 8. Qualitätsmanagement
- **Qualitätsziele:**  
  - Funktionierende Apps mit stabiler Backend-Anbindung  
  - Intuitive Benutzerführung (UX)  
  - Sauber dokumentierter Code  

- **Teststrategie:**  
  - Unit Tests in Flutter  
  - Integrationstests Backend $\leftrightarrow$ Apps  
  - Manuelle Usability-Tests  

- **Reviewprozesse:**  
  - Code Review via Pull Requests  
  - Abnahme durch Projektleiter vor Merge  

---

## 9. Risikomanagement

Das Risikomanagement dient dazu, potenzielle Gefahren für den Projektverlauf frühzeitig zu erkennen, zu bewerten und geeignete Gegenmaßnahmen zu definieren.  
Im Rahmen dieser Diplomarbeit liegt der Fokus darauf, Risiken realistisch einzuschätzen und durch organisatorische sowie planerische Maßnahmen negative Auswirkungen auf Zeitplan, Qualität und Projekterfolg zu minimieren.

---

### Top Risiken des Projekts

| Risiko | Auswirkung | Wahrscheinlichkeit | Maßnahmen | Verantwortlich |
|------|-----------|-------------------|-----------|----------------|
| **Technische Probleme mit Supabase** | Verzögerungen im Projektverlauf, notwendige Umplanung oder Anpassung der Architektur | Mittel | Einarbeitung anhand offizieller Dokumentation, Nutzung von Community-Ressourcen, Evaluierung möglicher Alternativen (z. B. Firebase) | Projektteam |
| **Zeitliche Engpässe aufgrund paralleler Diplomarbeitsbelastung** | Reduzierte Umsetzungsqualität, Zeitdruck gegen Projektende | Hoch | Klare Zeitplanung, Priorisierung wesentlicher Funktionen, regelmäßige Fortschrittskontrolle | Marvin L. |
| **Unerfahrenheit mit fortgeschrittenen Flutter-Funktionen** | Implementierungsprobleme, erhöhter Einarbeitungsaufwand | Mittel | Nutzung von Tutorials, Dokumentationen, Pair Programming und frühzeitige Prototypen | Entwickler |
| **Fehlende oder eingeschränkte Testgeräte (iOS/Android)** | Eingeschränkte Testabdeckung, mögliche plattformspezifische Fehler | Niedrig | Nutzung von Emulatoren, Simulatoren und ggf. Leihgeräten | Projektteam |
| **Unklare oder unvollständige Anforderungen zu Projektbeginn** | Nachträgliche Änderungen, zusätzlicher Aufwand | Mittel | Strukturierte Anforderungsanalyse, laufende Überprüfung und Dokumentation der User Stories | Projektmanager |
| **Kommunikationsprobleme im Projektteam** | Missverständnisse, doppelte Arbeit, Verzögerungen | Niedrig bis Mittel | Regelmäßige Abstimmungen, klare Zuständigkeiten, zentrale Dokumentation | Projektmanager |
| **Überschätzung des Umsetzungsumfangs** | Nicht alle geplanten Funktionen können umgesetzt werden | Mittel | Realistische Zieldefinition, Fokus auf Must-have-Anforderungen, frühzeitige Abgrenzung | Projektmanager |
| **Fehlende Erfahrung im Projektmanagement** | Unsicherheiten bei Planung, Priorisierung und Entscheidungsfindung | Mittel | Nutzung erlernter Projektmanagement-Methoden, kontinuierliche Reflexion, Anpassung der Planung | Marvin L. |
| **Technische Abhängigkeiten zwischen Modulen** | Verzögerungen durch blockierende Schnittstellen | Niedrig bis Mittel | Klare Definition von Schnittstellen, Abstimmung zwischen Modulverantwortlichen | Projektteam |
| **Fehlerhafte oder unvollständige Dokumentation** | Bewertungsabzüge, geringere Nachvollziehbarkeit | Niedrig | Laufende Pflege der Dokumentation, regelmäßige Überprüfung | Projektmanager |

---

## 10. Änderungs- & Entscheidungsmanagement
- **Change Requests:**  
  - Änderungen werden im Team diskutiert  
  - Entscheidung durch Projektleiter  
  - Dokumentation im GitHub Project Board  

- **Freigaben:**  
  - Projektleiter (intern)  
  - Betreuer (extern)  

---

## 11. Berichtswesen & Controlling
- **Statusberichte:**  
  - Wöchentliche Kurzberichte im Notion/Discord  
  - Fortschritts-Tracking über GitHub Projects  

- **Kennzahlen / KPIs:**  
  - Anzahl geschlossener Issues  
  - TODO: Fertiggestellte User Stories  
  - Testabdeckung  

---

## 12. Projektabschluss
- **Abnahmekriterien:**  
  - Fahrer-App, Kunden-App und Admin-Webinterface sind funktional  
  - Backend funktioniert in Echtzeit und ist stabil  
  - Dokumentation (Diplomarbeit + Projekthandbuch) abgeschlossen  

- **Lessons Learned:**  
   TODO: Wird am Projektende ergänzt.  

- **Übergabeprozesse:**  
  - Code im GitHub Repository  
  - Abschlussbericht / Diplomarbeit  
  - Übergabe an Partnerunternehmen  
