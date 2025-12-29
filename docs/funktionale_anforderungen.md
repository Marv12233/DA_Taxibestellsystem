# Funktionale Anforderungen – Kunden-App

## FR-K1: Registrierung
Die App muss es Kunden ermöglichen, ein Benutzerkonto über Supabase Auth zu erstellen.
- Eingaben: E-Mail, Passwort
- Validierung: E-Mail-Format, Passwortregeln
- Ergebnis: Konto wird in Supabase erstellt und aktiviert.

## FR-K2: Login
Die App muss Nutzern ermöglichen, sich über Supabase Auth anzumelden.
- Speicherung eines Refresh Tokens
- Automatische Anmeldung bei erneutem App-Start möglich.

## FR-K3: Push-Benachrichtigungen
Die App muss Push-Nachrichten empfangen können:
- Fahrer wurde gefunden
- Fahrer ist unterwegs
- Fahrt abgeschlossen

## FR-K4: Fahrtenanfrage senden
Die App muss dem Kunden erlauben, eine Fahrt anzufragen.
- Übermittlung des aktuellen GPS-Standorts
- Auswahl eines Zielstandortes
- Speicherung der Anfrage in Supabase

## FR-K5: Echtzeit-Fahrstatus
Die App muss den Status der Fahrt in Echtzeit anzeigen.
- Fahrer unterwegs
- Fahrer angekommen
- Fahrt läuft
- Fahrt abgeschlossen
- Echzeit Standort verfolgung des Fahrers

Daten werden über Supabase Realtime synchronisiert.

## FR-K6: Zahlungsmethoden verwalten
Die App muss das Hinzufügen folgender Zahlungsmethoden ermöglichen:
- Barzahlung
- SumUp (Über SDK oder externen Token)
- Bezahlung auf Rechnung

Die App verarbeitet keine Online-Zahlungen, nur die Hinterlegung der Methode.

## FR-K7: Fahrtprotokoll
Die App muss vergangene Fahrten anzeigen.
- Datum und Uhrzeit
- Fahrtdauer
- Preis
- Strecke
- Name des Fahrers

# Funktionale Anforderungen – Fahrer-App

## FR-F1: Login
Die Fahrer-App muss eine Anmeldung über Supabase Auth ermöglichen.

## FR-F2: Push-Benachrichtigungen
Die App muss Fahrer über neue Fahrten informieren:
- Neue Anfrage
- Stornierung
- Systemmeldungen

## FR-F3: Fahrten annehmen oder ablehnen
Fahrer müssen eingehende Anfragen annehmen oder ablehnen können.
- Statusänderung wird an Backend übertragen
- Kunde erhält Rückmeldung

## FR-F4: Lokalisierung nächster Fahrer / Fahrtanfragen
Die App muss nahegelegene Fahrten basierend auf Fahrerstandort anzeigen.

## FR-F5: Navigation zum Kunden
Die App muss eine Navigation über OpenStreetMap oder OSRM API ermöglichen.
- Routenanzeige
- Start der Navigation über integrierte Karte oder externe App

## FR-F6: Start und Stopp der Fahrt
Die App muss Fahrern ermöglichen, eine Fahrt zu starten oder zu beenden.
Backend speichert:
- Startzeitpunkt
- Endzeitpunkt
- Strecke
- Berechneter Preis

## FR-F7: Fahrerstatus
Die Fahrer-App muss folgende Status setzen und an das Backend senden können:
- Verfügbar
- Besetzt
- Offline

## FR-F8: Umsatzübersicht
Die App muss folgende Umsatzdaten anzeigen:
- Tagesumsatz
- Monatsumsatz
- Jahresumsatz
- Filtermöglichkeiten

# Funktionale Anforderungen – Admin-Webinterface

## FR-A1: Benutzerverwaltung
Das Admin-Interface muss folgende Funktionen bereitstellen:
- Fahrer registrieren
- Fahrer bearbeiten
- Fahrer löschen
- Kundendaten löschen

## FR-A2: Fahrtübersicht
Das System muss folgende Fahrten einsehen lassen:
- Aktive Fahrten
- Geplante Fahrten
- Vergangene Fahrten

## FR-A3: Echtzeit-Fahrerstandorte
Das Admin-Interface muss alle aktiven Fahrer auf einer Karte anzeigen.
- Live-Positionsdaten
- Darstellung des Fahrerstatus

## FR-A4: Statistiken und Auswertungen
Das System muss statistische Auswertungen anzeigen:
- Umsatz pro Zeitraum
- Anzahl der Fahrten pro Tag
- Beliebteste Routen
- Aktivste Fahrer


