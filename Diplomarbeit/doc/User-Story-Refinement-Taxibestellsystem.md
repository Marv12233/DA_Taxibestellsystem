# User Storys – Digitales Taxibestellsystem

# User Stories – Kunden-App

## FR-K1: Registrierung

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-K1 |
| **Req-Heading** | Registrierung eines Kundenkontos |
| **Req-Text** | Als Kunde möchte ich mich mit meiner E-Mail-Adresse und einem Passwort registrieren können, damit ich ein persönliches Benutzerkonto erhalte und die App vollständig nutzen kann. |
| **Comments** | Registrierung erfolgt über Supabase Auth. Eingaben werden auf gültiges E-Mail-Format und Passwortregeln überprüft. |
| **Creator** | Projektteam |
| **Priority** | Must |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-K2: Login

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-K2 |
| **Req-Heading** | Login für registrierte Kunden |
| **Req-Text** | Als Kunde möchte ich mich mit meinen Zugangsdaten anmelden können, damit ich auf mein Benutzerkonto zugreifen und Fahrten buchen kann. |
| **Comments** | Anmeldung über Supabase Auth, Speicherung eines Refresh Tokens für automatische Anmeldung. |
| **Creator** | Projektteam |
| **Priority** | Must |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-K3: Push-Benachrichtigungen

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-K3 |
| **Req-Heading** | Push-Benachrichtigungen für Kunden |
| **Req-Text** | Als Kunde möchte ich Push-Benachrichtigungen erhalten, damit ich über wichtige Ereignisse während meiner Fahrt informiert werde. |
| **Comments** | Benachrichtigungen bei Fahrerzuweisung, Fahrtbeginn und Fahrtende. |
| **Creator** | Projektteam |
| **Priority** | Should |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-K4: Fahrtenanfrage senden

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-K4 |
| **Req-Heading** | Fahrtenanfrage senden |
| **Req-Text** | Als Kunde möchte ich eine Fahrt anfragen können, indem ich meinen aktuellen Standort oder einen Abholort und ein Ziel angebe, damit ein Fahrer vermittelt werden kann. |
| **Comments** | GPS-Standort wird automatisch ermittelt, Ziel manuell gewählt, Speicherung im Backend. |
| **Creator** | Projektteam |
| **Priority** | Must |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-K5: Echtzeit-Fahrstatus

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-K5 |
| **Req-Heading** | Anzeige des Echtzeit-Fahrstatus |
| **Req-Text** | Als Kunde möchte ich den aktuellen Status meiner Fahrt in Echtzeit sehen, damit ich jederzeit über den Fortschritt informiert bin. |
| **Comments** | Statusänderungen und Fahrerposition werden in Echtzeit synchronisiert. |
| **Creator** | Projektteam |
| **Priority** | Must |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-K6: Zahlungsmethoden verwalten

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-K6 |
| **Req-Heading** | Zahlungsmethoden verwalten |
| **Req-Text** | Als Kunde möchte ich eine bevorzugte Zahlungsmethode hinterlegen können, damit die Abwicklung der Fahrtzahlung eindeutig geregelt ist. |
| **Comments** | Keine Online-Zahlung, nur Auswahl bzw. Hinterlegung der Zahlungsmethode. |
| **Creator** | Projektteam |
| **Priority** | Should |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-K7: Fahrtprotokoll

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-K7 |
| **Req-Heading** | Fahrtprotokoll einsehen |
| **Req-Text** | Als Kunde möchte ich meine vergangenen Fahrten einsehen können, damit ich einen Überblick über meine Fahrt-Historie habe. |
| **Comments** | Anzeige von Datum, Dauer, Preis, Strecke und Fahrername. |
| **Creator** | Projektteam |
| **Priority** | Could |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

# User Stories – Fahrer-App

## FR-F1: Login

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-F1 |
| **Req-Heading** | Login für Fahrer |
| **Req-Text** | Als Fahrer möchte ich mich mit meinen Zugangsdaten anmelden können, damit ich auf meine Fahrer-App zugreifen und Fahrten übernehmen kann. |
| **Comments** | Anmeldung erfolgt über Supabase Auth. |
| **Creator** | Projektteam |
| **Priority** | Must |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-F2: Push-Benachrichtigungen

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-F2 |
| **Req-Heading** | Push-Benachrichtigungen für Fahrer |
| **Req-Text** | Als Fahrer möchte ich Push-Benachrichtigungen erhalten, damit ich über neue Fahrten, Stornierungen und Systemmeldungen informiert werde. |
| **Comments** | Benachrichtigungen bei neuen Anfragen, Stornierungen und wichtigen Systemereignissen. |
| **Creator** | Projektteam |
| **Priority** | Must |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-F3: Fahrten annehmen oder ablehnen

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-F3 |
| **Req-Heading** | Fahrten annehmen oder ablehnen |
| **Req-Text** | Als Fahrer möchte ich eingehende Fahrtenanfragen annehmen oder ablehnen können, damit ich selbst entscheiden kann, welche Fahrten ich übernehme. |
| **Comments** | Statusänderung wird an das Backend übertragen, Kunde erhält eine Rückmeldung. |
| **Creator** | Projektteam |
| **Priority** | Must |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-F4: Lokalisierung nächster Fahrten

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-F4 |
| **Req-Heading** | Anzeige nahegelegener Fahrten |
| **Req-Text** | Als Fahrer möchte ich nahegelegene Fahrten basierend auf meinem aktuellen Standort sehen, damit ich passende Anfragen schneller annehmen kann. |
| **Comments** | Anzeige erfolgt standortbasiert über GPS-Daten. |
| **Creator** | Projektteam |
| **Priority** | Should |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-F5: Navigation zum Kunden

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-F5 |
| **Req-Heading** | Navigation zum Kunden |
| **Req-Text** | Als Fahrer möchte ich eine Navigation zum Kunden starten können, damit ich den Abholort effizient erreiche. |
| **Comments** | Navigation über OpenStreetMap oder OSRM, Nutzung einer integrierten Karte oder externer Navigations-App. |
| **Creator** | Projektteam |
| **Priority** | Should |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-F6: Start und Stopp der Fahrt

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-F6 |
| **Req-Heading** | Fahrt starten und beenden |
| **Req-Text** | Als Fahrer möchte ich eine Fahrt starten und beenden können, damit die Fahrt korrekt dokumentiert und abgerechnet wird. |
| **Comments** | Backend speichert Startzeit, Endzeit, Strecke und berechneten Preis. |
| **Creator** | Projektteam |
| **Priority** | Must |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-F7: Fahrerstatus

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-F7 |
| **Req-Heading** | Fahrerstatus setzen |
| **Req-Text** | Als Fahrer möchte ich meinen aktuellen Status setzen können, damit das System weiß, ob ich für neue Fahrten verfügbar bin. |
| **Comments** | Status: verfügbar, besetzt oder offline; Status wird an das Backend übermittelt. |
| **Creator** | Projektteam |
| **Priority** | Must |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-F8: Umsatzübersicht

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-F8 |
| **Req-Heading** | Umsatzübersicht für Fahrer |
| **Req-Text** | Als Fahrer möchte ich meine Umsätze einsehen können, damit ich einen Überblick über meine Einnahmen habe. |
| **Comments** | Anzeige von Tages-, Monats- und Jahresumsatz mit Filtermöglichkeiten. |
| **Creator** | Projektteam |
| **Priority** | Could |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

# User Stories – Admin-Webinterface

## FR-A1: Benutzerverwaltung

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-A1 |
| **Req-Heading** | Verwaltung von Fahrern |
| **Req-Text** | Als Administrator möchte ich Fahrer registrieren, bearbeiten und löschen können, damit ich Benutzerkonten zentral verwalten kann. |
| **Comments** | Verwaltung umfasst Anlegen, Aktualisieren und Entfernen von Fahrerprofilen. |
| **Creator** | Projektteam |
| **Priority** | Must |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-A2: Fahrtübersicht und Verwaltung

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-A2 |
| **Req-Heading** | Fahrtübersicht und Steuerung |
| **Req-Text** | Als Administrator möchte ich alle aktiven, geplanten und vergangenen Fahrten einsehen und verwalten können, damit der Betrieb effizient gesteuert werden kann. |
| **Comments** | Funktionen: Fahrtstatus ändern, Fahrten zuweisen, Fahrten stornieren inkl. Angabe eines Grundes. |
| **Creator** | Projektteam |
| **Priority** | Must |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-A3: Echtzeit-Fahrerstandorte

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-A3 |
| **Req-Heading** | Anzeige von Fahrerstandorten in Echtzeit |
| **Req-Text** | Als Administrator möchte ich alle aktiven Fahrer in Echtzeit auf einer Karte sehen, damit ich einen Überblick über deren Positionen und Status habe. |
| **Comments** | Anzeige von Live-Positionsdaten sowie Fahrerstatus (verfügbar, besetzt, offline). |
| **Creator** | Projektteam |
| **Priority** | Should |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-A4: System-Logs und Fehler

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-A4 |
| **Req-Heading** | Einsicht in System-Logs |
| **Req-Text** | Als Administrator möchte ich technische System-Logs einsehen können, damit Fehler und Probleme im System analysiert werden können. |
| **Comments** | Anzeige von API-Fehlern, Authentifizierungsfehlern, Fahrtenfehlern und App-Fehlermeldungen. |
| **Creator** | Projektteam |
| **Priority** | Should |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-A5: Statistiken und Auswertungen

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-A5 |
| **Req-Heading** | Statistische Auswertungen |
| **Req-Text** | Als Administrator möchte ich statistische Auswertungen einsehen können, damit ich den Betrieb analysieren und fundierte Entscheidungen treffen kann. |
| **Comments** | Auswertungen zu Umsatz, Anzahl der Fahrten, beliebtesten Routen und aktivsten Fahrern. |
| **Creator** | Projektteam |
| **Priority** | Could |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

# User Stories – Projektmanagement

## FR-PM1: Projektplanung erstellen

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-PM1 |
| **Req-Heading** | Projektplanung erstellen |
| **Req-Text** | Ich als Projektmanager möchte eine strukturierte Projektplanung erstellen, damit Ziele, Zeitrahmen und Aufgaben von Beginn an klar definiert sind. |
| **Comments** | Planung umfasst Zeitplanung, Meilensteine und grundlegende Ressourcenübersicht. |
| **Creator** | Projektmanager |
| **Priority** | Must |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-PM2: Aufgaben verwalten und priorisieren

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-PM2 |
| **Req-Heading** | Aufgabenverwaltung |
| **Req-Text** | Ich als Projektmanager möchte Aufgaben erfassen, priorisieren und nachverfolgen können, damit der Projektfortschritt transparent und steuerbar bleibt. |
| **Comments** | Aufgabenverwaltung erfolgt über ein Kanban-Board mit definierten Status. |
| **Creator** | Projektmanager |
| **Priority** | Must |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-PM3: Projektfortschritt überwachen

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-PM3 |
| **Req-Heading** | Fortschrittsüberwachung |
| **Req-Text** | Ich als Projektmanager möchte den aktuellen Projektfortschritt regelmäßig überwachen, damit Abweichungen vom Plan frühzeitig erkannt werden. |
| **Comments** | Überwachung anhand Aufgabenstatus, Meilensteinen und internen Abstimmungen. |
| **Creator** | Projektmanager |
| **Priority** | Must |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-PM4: Kommunikation im Projekt koordinieren

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-PM4 |
| **Req-Heading** | Projektkommunikation koordinieren |
| **Req-Text** | Ich als Projektmanager möchte die Kommunikation im Projekt koordinieren, damit Informationen vollständig, zeitgerecht und nachvollziehbar weitergegeben werden. |
| **Comments** | Koordination von Abstimmungen, Weitergabe relevanter Informationen an Team und Betreuer. |
| **Creator** | Projektmanager |
| **Priority** | Must |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-PM5: Risiken identifizieren und steuern

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-PM5 |
| **Req-Heading** | Risikomanagement |
| **Req-Text** | Ich als Projektmanager möchte Projektrisiken frühzeitig identifizieren und bewerten, damit geeignete Maßnahmen zur Risikominimierung gesetzt werden können. |
| **Comments** | Risiken werden regelmäßig überprüft und priorisiert. |
| **Creator** | Projektmanager |
| **Priority** | Should |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-PM6: Änderungen entscheiden und dokumentieren

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-PM6 |
| **Req-Heading** | Änderungs- und Entscheidungsmanagement |
| **Req-Text** | Ich als Projektmanager möchte über Änderungsanforderungen entscheiden und diese dokumentieren, damit der Projektumfang kontrolliert bleibt. |
| **Comments** | Änderungen werden bewertet und nachvollziehbar festgehalten. |
| **Creator** | Projektmanager |
| **Priority** | Should |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-PM7: Qualität sicherstellen

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-PM7 |
| **Req-Heading** | Qualitätssicherung |
| **Req-Text** | Ich als Projektmanager möchte die Qualität der Projektergebnisse überprüfen, damit die definierten Anforderungen und Qualitätsziele eingehalten werden. |
| **Comments** | Überprüfung anhand Abnahmekriterien und interner Reviews. |
| **Creator** | Projektmanager |
| **Priority** | Should |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |

---

## FR-PM8: Projektabschluss durchführen

| Feld | Inhalt |
|------|--------|
| **Req-ID** | FR-PM8 |
| **Req-Heading** | Projektabschluss |
| **Req-Text** | Ich als Projektmanager möchte das Projekt strukturiert abschließen, damit Ergebnisse bewertet, dokumentiert und reflektiert werden können. |
| **Comments** | Projektabschluss inkl. Abnahme, Lessons Learned und Abschlussbewertung. |
| **Creator** | Projektmanager |
| **Priority** | Must |
| **Revision** | 1.0 |
| **Date** | 23.09.2025 |





