# **Anforderungsmanagement – Digitales Taxibestellsystem**

## **1. Einleitung**

Das Anforderungsmanagement bildet einen zentralen Bestandteil der Diplomarbeit **„Digitales Taxibestellsystem“**.  
Es dient dazu, die funktionalen und nicht-funktionalen Anforderungen systematisch zu erfassen, zu strukturieren und während der Entwicklung nachzuverfolgen.  

Ziel war es, **ein verbessertes, moderneres System** zu entwickeln, das die bisherigen Schwächen des bestehenden Taxibestellsystems behebt und neue technische Möglichkeiten (z. B. Echtzeitkommunikation, moderne App-Architektur) nutzt.

Im Gegensatz zu klassischen Softwareprojekten erfolgte die **Anforderungserhebung ohne direkten Auftraggeberkontakt**.  
Das Projektteam definierte die Anforderungen **eigenständig** auf Basis einer Analyse der bestehenden Lösung und interner Überlegungen zur optimalen Benutzerführung, Funktionalität und technischen Umsetzung.

Die vollständigen User Stories sind im separaten Dokument **„User Story Refinement – Digitales Taxibestellsystem“** festgehalten und bilden die Grundlage dieses Kapitels.

---

## **2. Vorgehensweise im Anforderungsmanagement**

### **2.1 Erhebung der Anforderungen**

Die Anforderungen wurden vollständig **intern im Projektteam** erarbeitet.  
Als Ausgangspunkt diente die **bestehende Version des Taxibestellsystems**, deren Funktionsweise und Schwächen analysiert wurden.  
Anschließend wurden **Verbesserungspotenziale** identifiziert und daraus neue Anforderungen abgeleitet.  

Zur Anforderungserhebung wurden folgende Ansätze genutzt:
- **Funktionsanalyse** der bestehenden Lösung (Was funktioniert gut, was nicht?)  
- **Team-Brainstorming** zu gewünschten Verbesserungen aus Nutzer- und Entwicklerperspektive  
- **Technische Evaluierung**, welche neuen Funktionen mit aktuellen Technologien (z. B. Flutter, Supabase) umsetzbar sind  

Alle Anforderungen wurden in **User Stories** formuliert, um die gewünschte Funktion aus Sicht des Endnutzers zu beschreiben.  
Beispiel:
> *„Als Kunde möchte ich eine Fahrt buchen können, um schnell und bequem ein Taxi zu bestellen.“*

---

## 2.2 Dokumentation der Anforderungen

Die im Projekt ermittelten Anforderungen wurden in einem eigenen Dokument mit dem Titel  
**„User Storys – Digitales Taxibestellsystem“** dokumentiert.  
Dieses Dokument dient als zentrale Grundlage für Planung, Umsetzung und Nachverfolgung der Anforderungen.

Alle Anforderungen werden in Form von **User Stories** festgehalten und nach einem **einheitlichen Schema** beschrieben.  
Durch diese standardisierte Struktur wird sichergestellt, dass jede Anforderung eindeutig formuliert, nachvollziehbar dokumentiert und überprüfbar ist.

Das verwendete User-Story-Schema umfasst folgende Elemente:

| **Element** | **Beschreibung** |
|------------|------------------|
| **Req-ID** | Eindeutige Kennzeichnung der Anforderung zur eindeutigen Referenzierung |
| **Req-Heading** | Kurzbeschreibung der Anforderung |
| **Req-Text** | Beschreibung der Anforderung aus Sicht der jeweiligen Rolle (z. B. Kunde, Fahrer, Administrator oder Projektmanager) |
| **Comments** | Zusätzliche Erläuterungen, Rahmenbedingungen oder Hinweise |
| **Creator** | Ersteller der User Story |
| **Priority** | Priorisierung nach der MoSCoW-Methode (Must, Should, Could) |
| **Revision** | Versionsstand der User Story |
| **Date** | Erstellungs- bzw. Änderungsdatum |

Durch diese Struktur wird eine klare Trennung zwischen fachlicher Beschreibung, organisatorischer Priorisierung und ergänzenden Informationen ermöglicht.  
Gleichzeitig erleichtert das Schema die Nachvollziehbarkeit von Änderungen sowie die Zuordnung der Anforderungen zu einzelnen Projektbereichen.

### Beispielhafte User Stories

Nachfolgend sind ausgewählte User Stories dargestellt, die exemplarisch zeigen, wie Anforderungen im Projekt dokumentiert wurden.

---

#### Beispiel 1: FR-K4 – Fahrtenanfrage senden (Kunden-App)

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-K4 |
| **Req-Heading** | Fahrtenanfrage senden |
| **Req-Text** | Als Kunde möchte ich eine Fahrt anfragen können, indem ich meinen aktuellen Standort und ein Ziel angebe, damit ein Fahrer für meine Fahrt vermittelt werden kann. |
| **Comments** | Der aktuelle Standort wird automatisch über GPS ermittelt, das Ziel wird vom Nutzer ausgewählt. |
| **Creator** | Projektteam |
| **Priority** | Must |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

#### Beispiel 2: FR-F5 – Navigation zum Kunden (Fahrer-App)

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-F5 |
| **Req-Heading** | Navigation zum Kunden |
| **Req-Text** | Als Fahrer möchte ich eine Navigation zum Abholort des Kunden starten können, damit ich den Kunden effizient und ohne Umwege erreiche. |
| **Comments** | Die Navigation erfolgt über eine integrierte Kartenansicht oder eine externe Navigationsanwendung. |
| **Creator** | Projektteam |
| **Priority** | Should |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

#### Beispiel 3: FR-A1 – Benutzerverwaltung (Admin-Webinterface)

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-A1 |
| **Req-Heading** | Benutzerverwaltung |
| **Req-Text** | Als Administrator möchte ich Fahrer registrieren, bearbeiten und löschen können, damit Benutzerkonten zentral verwaltet werden können. |
| **Comments** | Verwaltung umfasst das Anlegen neuer Fahrer sowie die Pflege bestehender Fahrerprofile. |
| **Creator** | Projektteam |
| **Priority** | Must |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

Diese Beispiele verdeutlichen die einheitliche Struktur der User Stories sowie die klare Formulierung aus Sicht der jeweiligen Rolle.  
Durch dieses Schema können Anforderungen eindeutig beschrieben, priorisiert und im Projektverlauf nachvollzogen werden.

### **2.3 Priorisierung und Aufwandsschätzung**

Die Priorisierung der Anforderungen erfolgte mit der **MoSCoW-Methode**:
- **Must-have:** essenzielle Funktionen für das Grundsystem (z. B. Fahrtbuchung, GPS-Ortung)  
- **Should-have:** wichtige, aber nicht zwingend notwendige Erweiterungen (z. B. Live-Tracking)  
- **Could-have:** optionale Komfortfunktionen (z. B. Fahrthistorie)

Der **Aufwand** wurde mit **Story Points** geschätzt, um die relative Komplexität der einzelnen Aufgaben zu bewerten.  
Diese Schätzungen basierten auf Teamdiskussionen und Erfahrungen mit Flutter-Entwicklungen.  
Sie dienten als Grundlage für die interne Zeitplanung und zur Strukturierung der Arbeit im Kanban-Board.

---

### **2.4 Verwaltung und Nachverfolgung**

Das Anforderungsmanagement wurde zentral über das **GitHub-Projektboard des Projektleiters** gesteuert.  
Jede User Story wurde als **Issue oder Karte** erfasst und durchlief definierte Stati:

> **Backlog → In Progress → Review → Done**

Dadurch war jederzeit ersichtlich, welche Anforderungen sich in Bearbeitung befinden und welche abgeschlossen wurden.  
Jedes Teammitglied arbeitete in seinem eigenen Repository und synchronisierte den Fortschritt regelmäßig über das zentrale Board.  
So konnte trotz getrennter Entwicklungsumgebungen eine **einheitliche Übersicht über den Projektfortschritt** gewährleistet werden.

---

### **2.5 Validierung**

Die Validierung der Anforderungen erfolgte **intern im Team**.  
Es gab keine laufende Abstimmung mit einem externen Auftraggeber; die Beurteilung erfolgte ausschließlich anhand der **selbst definierten Akzeptanzkriterien** aus dem *User Story Refinement*-Dokument.  

Zur Validierung wurden folgende Maßnahmen genutzt:
- **Manuelle Tests** der Apps auf Android- und iOS-Geräten  
- **Code Reviews** innerhalb des Teams  
- **Vergleich mit den definierten Akzeptanzkriterien** jeder User Story  
- **Endbewertung** des Gesamtsystems im Hinblick auf die festgelegten Projektziele  

Ziel war es, eine funktionsfähige und qualitativ hochwertige Lösung zu entwickeln, die die bestehenden Anwendungen deutlich verbessert.

---

## **3. Ablauf des internen Anforderungsmanagements**

```
 ┌──────────────────────────────────────────────┐
 │ Analyse des bestehenden Taxibestellsystems   │
 │ (Funktions- & Schwächenanalyse)              │
 └────────────┬─────────────────────────────────┘
              │
              ▼
 ┌──────────────────────────────────────────────┐
 │ Ableitung neuer Anforderungen                │
 │ (Verbesserungsideen, Team-Brainstorming,     │
 │ technische Machbarkeit)                      │
 └────────────┬─────────────────────────────────┘
              │
              ▼
 ┌──────────────────────────────────────────────┐
 │ Dokumentation als User Stories               │
 │ (Ziel, Akzeptanzkriterien, Tasks)            │
 │ im „User Story Refinement“-Dokument          │
 └────────────┬─────────────────────────────────┘
              │
              ▼
 ┌──────────────────────────────────────────────┐
 │ Priorisierung & Aufwandsschätzung            │
 │ (MoSCoW, Story Points)                       │
 └────────────┬─────────────────────────────────┘
              │
              ▼
 ┌──────────────────────────────────────────────┐
 │ Umsetzung & Nachverfolgung                   │
 │ (GitHub Project Board:                      │
 │ Backlog → In Progress → Review → Done)       │
 └────────────┬─────────────────────────────────┘
              │
              ▼
 ┌──────────────────────────────────────────────┐
 │ Interne Validierung                          │
 │ (Tests, Code Reviews, Abgleich mit           │
 │ Akzeptanzkriterien)                          │
 └──────────────────────────────────────────────┘
```

> **Abbildung X:** Ablauf des internen Anforderungsmanagements im Projekt *„Digitales Taxibestellsystem“*

---

## **4. Zusammenfassung**

Das Anforderungsmanagement des Projekts *„Digitales Taxibestellsystem“* war vollständig intern organisiert.  
Statt externe Anforderungen umzusetzen, entwickelte das Team ein **eigenes, verbessertes Systemkonzept**, basierend auf einer systematischen Analyse der bisherigen Lösung.  

Durch den Einsatz von **User Stories**, **MoSCoW-Priorisierung**, **Story Points** und der **zentralen GitHub-Projektsteuerung** konnte das Team ein strukturiertes, agiles Vorgehen sicherstellen.  
Dieses Vorgehen ermöglichte eine zielgerichtete Umsetzung und eine nachvollziehbare Verbindung zwischen Planung, Umsetzung und Test.

---

## **5. Literaturhinweise**

- ISO/IEC/IEEE 29148:2018 – *Systems and Software Engineering – Requirements Engineering.*  
- Pohl, Klaus (2010): *Requirements Engineering. Grundlagen, Prinzipien, Techniken.* dpunkt.verlag.  
- Balzert, Helmut (2011): *Lehrbuch der Softwaretechnik 1 – Softwareentwicklung.* Spektrum Akademischer Verlag.  
- Sommerville, Ian (2016): *Software Engineering.* Pearson Education.  
