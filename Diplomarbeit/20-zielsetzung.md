## Zielsetzung

### Hauptziele  
Diese Arbeit beschäftigt sich mit der digitalen Vermittlung von Taxifahrten zwischen Kunden und Fahrern. Dies wird durch zwei Flutter-Apps (Kunden-App und Fahrer-App) sowie eine webbasierte Adminoberfläche realisiert.  
Der Fokus liegt dabei nicht nur auf der eigentlichen Fahrtenvermittlung, sondern auch auf der Erfassung, Speicherung und Auswertung relevanter Fahrtdaten (z. B. Start- und Endzeit, Strecke, Preis, Umsatz) in einer zentralen Datenbank.  
Um die benötigten Funktionen umsetzen und einen Proof-of-Concept erzielen zu können, werden alle drei Systemkomponenten entwickelt und über Supabase als Backend angebunden. Damit Anwender Fahrten und Systemzustände in Echtzeit einsehen und verwalten können, wird ein modernes, benutzerfreundliches Userinterface konzipiert.

### Nicht-Ziele  
Nicht Teil dieser Umsetzung ist eine vollumfängliche Abrechnungs- und Fakturierungssoftware mit Schnittstellen zu Finanzbehörden oder externen Buchhaltungssystemen, da der Fokus auf der Fahrtenvermittlung und -verwaltung liegt.  
Ebenso wird kein eigener, selbst gehosteter Backend-Stack entwickelt, sondern bewusst auf Supabase als Backend-as-a-Service zurückgegriffen.  
Funktionen wie komplexe Routenoptimierung, dynamische Preisberechnung für verschiedene Tarifmodelle oder ein öffentliches Web-Buchungsportal für Endkunden sind nicht Bestandteil des geplanten Projektumfangs und werden nur, falls es der zeitliche Rahmen erlaubt, höchstens konzeptionell betrachtet.
