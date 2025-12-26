# Teilaufgabe Schüler Winter

\textauthor{Marvin Winter}

## Theorie

### Dart
Dart ist eine Open-Source-Programmiersprache, die von Google entwickelt wurde. Sie wird unter anderem für die Entwicklung von Android- und iOS-Applikationen, Webanwendungen sowie IoT-Anwendungen (Internet of Things) eingesetzt. Häufig wird Dart in Kombination mit dem Flutter-Framework verwendet. Die Sprache weist syntaktische Ähnlichkeiten zu Java, C und JavaScript auf und ist eine stark typisierte, objektorientierte Programmiersprache. [@GeeksForGeeks-Dart]

#### Sprache & Grundkonzepte (Typen, OOP)

##### Typen
Wie auch in anderen Programmiersprachen wie Java oder C++ besitzt eine Variable in Dart beim Erstellen einen bestimmten Datentyp. Datentypen definieren, welche Art von Daten gespeichert werden können, beispielsweise Zahlen, Zeichenketten oder Listen. Die wichtigsten und am häufigsten verwendeten Datentypen sind:

| Datentyp  | Keyword               |
|----------|------------------------|
| Zahlen   | int, double, num, BigInt |
| Strings  | String                 |
| Booleans | bool                   |
| Listen   | List                   |

##### OOP – Objektorientierte Programmierung
Dart ist, wie bereits zuvor erwähnt, eine objektorientierte Programmiersprache und unterstützt Konzepte wie Klassen, Objekte und Vererbung. Das folgende Codebeispiel zeigt die Verwendung von Klassen, Vererbung und Konstruktoren.
```dart
class Animal
{
  String name;
  String noise;

  // Konstruktor der Basisklasse
  Animal(this.name, this.noise);

  void makeNoise() => print(noise);
}

// Dog erbt von Animal
class Dog extends Animal
{
  // Konstruktor der Subklasse ruft den Basisklassen-Konstruktor mit super auf
  Dog(String name) : super(name, 'woof');

  @override
  void makeNoise() => print('$name makes $noise');
}

void main()
{
  // Dog Objekt wird erstellt
  final dog = Dog('Bello');
  // makeNoise() Methode wird aufgerufen
  dog.makeNoise(); // Ausgabe: Bello makes woof
}
```
Dieses Codebeispiel zeigt die Definition einer Basisklasse sowie einer davon abgeleiteten Subklasse. Zusätzlich wird dargestellt, wie Konstruktoren und Methodenüberschreibungen in Dart umgesetzt werden.

#### Null Safety
Dart verwendet ein sogenanntes *Sound Null Safety*-Konzept. Dadurch wird bereits zur Compile-Zeit sichergestellt, dass Variablen keine unerwarteten `null`-Werte annehmen. Wird beispielsweise einer Methode ein `null`-Wert übergeben, obwohl ein nicht-nullbarer Datentyp erwartet wird, führt dies zu einem Compile-Fehler.
Standardmäßig sind Variablen in Dart nicht nullfähig (*non-nullable*). Soll eine Variable dennoch den Wert `null` annehmen dürfen, muss sie explizit als nullfähig (*nullable*) deklariert werden. Dies erfolgt durch das Anhängen eines Fragezeichens (`?`) an den Datentyp. Eine solche Variable kann entweder einen konkreten Wert oder `null` enthalten. Das folgende Codebeispiel demonstriert diese Unterschiede. [@NullSafety-DartDocs]
```dart
void main()
{
  // 1) Non-nullable, nicht initialisiert
  String name1;
  // print(name1);
  // Compile-Fehler: Die Variable wurde noch nicht initialisiert

  // 2) Non-nullable, initialisiert
  String name2;
  name2 = 'Marvin';
  print(name2);
  // funktioniert, da name2 vor der Verwendung initialisiert wurde

  // 3) Nullable durch ?
  String? name3;
  print(name3);
  // funktioniert, da name3 nullfähig ist
}
```

#### Asynchronität (Future, async/await)
Asynchronität wird in Dart eingesetzt, um zeitaufwändige Operationen auszuführen, ohne dabei den Hauptthread der Anwendung zu blockieren. Typische Anwendungsfälle sind Netzwerk- oder Datenbankzugriffe. Für die asynchrone Programmierung stellt Dart das `Future`-Konzept sowie die Schlüsselwörter `async` und `await` zur Verfügung.

Ein `Future` repräsentiert einen Wert, der erst zu einem späteren Zeitpunkt verfügbar ist. Funktionen, die mit dem Schlüsselwort `async` deklariert werden, liefern immer ein `Future` zurück. Mit `await` kann auf das Ergebnis eines `Future` gewartet werden, ohne den Programmablauf zu blockieren. Die Verwendung von `await` ist ausschließlich innerhalb von `async`-Funktionen erlaubt. Das folgende Codebeispiel zeigt eine einfache asynchrone Operation. [@GeeksForGeeks-async]

```dart
Future<String> ladeBenutzername() async {
  // Simulation eines Datenbankzugriffs
  await Future.delayed(Duration(seconds: 2));
  return 'MarvinWinter';
}

Future<void> main() async {
  print('Start');

  // wartet auf das Ergebnis der asynchronen Methode
  String name = await ladeBenutzername();

  print('Benutzer: $name');
  print('Ende');
}
```
In diesem Codebeispiel wird ein Datenbankzugriff simuliert, der asynchron ausgeführt wird. Die Methode gibt ein `Future` zurück, da das Ergebnis erst zu einem späteren Zeitpunkt verfügbar ist. Durch die Verwendung von `async` und `await` kann auf dieses Ergebnis gewartet werden, ohne den Hauptthread der Anwendung zu blockieren.

#### Packages & pubspec.yaml
In Dart werden Packages verwendet, um externe Bibliotheken und Werkzeuge in ein Projekt einzubinden und zu verwalten. Hierfür kommt der Package-Manager `pub` zum Einsatz. Die Verwaltung der Abhängigkeiten erfolgt über die Datei `pubspec.yaml`, welche zentrale Projektinformationen sowie die verwendeten Packages enthält.

Der grundlegende Aufbau einer `pubspec.yaml`-Datei ist im folgenden Beispiel dargestellt. [@packages_dartdocs]

```yaml
name: demo # Name der App

dependencies:
  demo_package: ^1.0.0 # Package-Name und Version
  # ...
```
Um die definierten Packages im Projekt zu installieren, wird der Befehl `dart pub get` im Projektverzeichnis ausgeführt.




### Flutter
Flutter ist ein von Google entwickeltes Framework zur plattformübergreifenden Entwicklung von mobilen Anwendungen für Betriebssysteme wie Android und iOS. Ziel von Flutter ist es, mit einer einzigen Codebasis Anwendungen für mehrere Plattformen zu erstellen, ohne systemspezifischen Code schreiben zu müssen.

Die mit Flutter entwickelten Anwendungen werden als native Apps kompiliert und können somit auf den jeweiligen Zielplattformen ausgeführt werden. Aufgrund dieses Ansatzes wird Flutter häufig als Cross-Plattform-Framework bezeichnet. Flutter wird in Kombination mit der Programmiersprache Dart eingesetzt, welche im vorherigen Kapitel vorgestellt wurde. [@flutter_framework]

#### Flutter-Konzept (Widgets, Widget-Tree, Build)

##### Widgets
In Flutter wird die Benutzeroberfläche vollständig aus sogenannten Widgets aufgebaut. Widgets stellen dabei die grundlegenden Bausteine der UI dar und reichen von einfachen Elementen wie `Text`, `Row`, `Column` oder `Container` bis hin zu komplexen, selbst definierten Komponenten.

Ein zentrales Konzept von Flutter ist die Möglichkeit, eigene Widgets zu erstellen. Dadurch können wiederverwendbare UI-Komponenten, beispielsweise für Login- oder Registrierungsansichten, definiert und innerhalb der gesamten Anwendung einheitlich eingesetzt werden.

Grundsätzlich wird zwischen zwei Arten von Widgets unterschieden: `StatelessWidget` und `StatefulWidget`. Ein `StatelessWidget` beschreibt eine Benutzeroberfläche, die sich nach dem Aufbau (*build*) nicht mehr verändert. Es eignet sich für statische Inhalte, deren Darstellung unabhängig vom internen Zustand ist. Ein `StatefulWidget` hingegen besitzt einen veränderbaren Zustand (*State*), wodurch sich die Benutzeroberfläche dynamisch an Benutzerinteraktionen oder interne Änderungen anpassen kann. Die folgenden Codebeispiele zeigen den Unterschied zwischen diesen beiden Widget-Typen. [@flutter_docs]

Stateless Widget:
```dart
class UserInfoTile extends StatelessWidget {
  final String username;
  final IconData icon;

  const UserInfoTile({
    super.key,
    required this.username,
    required this.icon,
  });

  @override
  Widget build(BuildContext context) {
    return Container(
      padding: const EdgeInsets.all(12),
      decoration: BoxDecoration(
        color: Colors.blue.shade50,
        borderRadius: BorderRadius.circular(8),
      ),
      child: Row(
        children: [
          Icon(icon, color: Colors.blue),
          const SizedBox(width: 8),
          Text(
            username,
            style: const TextStyle(
              fontSize: 16,
              fontWeight: FontWeight.w500,
            ),
          ),
        ],
      ),
    );
  }
}
```
Das dargestellte `StatelessWidget` eignet sich beispielsweise für eine Profil- oder Listenansicht, bei der ausschließlich statische Informationen angezeigt werden.
```dart
UserInfoTile(
  username: 'Marvin Winter',
  icon: Icons.person,
)
```
StatefullWidget:
```dart
class UserInfoTile extends StatefulWidget {
  final String username;
  final IconData icon;

  const UserInfoTile({
    super.key,
    required this.username,
    required this.icon,
  });

  @override
  State<UserInfoTile> createState() => _UserInfoTileState();
}

class _UserInfoTileState extends State<UserInfoTile> {
  bool isFavorite = false;

  @override
  Widget build(BuildContext context) {
    return Container(
      padding: const EdgeInsets.all(12),
      decoration: BoxDecoration(
        color: Colors.blue.shade50,
        borderRadius: BorderRadius.circular(8),
      ),
      child: Row(
        children: [
          Icon(widget.icon, color: Colors.blue),
          const SizedBox(width: 8),
          Expanded(
            child: Text(
              widget.username,
              style: const TextStyle(
                fontSize: 16,
                fontWeight: FontWeight.w500,
              ),
            ),
          ),
          IconButton(
            onPressed: () => setState(() => isFavorite = !isFavorite),
            icon: Icon(isFavorite ? Icons.star : Icons.star_border),
            color: isFavorite ? Colors.amber : Colors.grey,
          ),
        ],
      ),
    );
  }
}
```
Das gezeigte `StatefulWidget` ermöglicht es dem Benutzer, einen Status (z. B. Favorit) direkt zu verändern. Die Benutzeroberfläche wird dabei dynamisch an den aktuellen Zustand angepasst.
```dart
UserInfoTile(
  username: 'Marvin Winter',
  icon: Icons.person,
)
```

##### Widget-Tree
Der Widget-Tree beschreibt in Flutter die hierarchische Struktur der Widgets, aus denen eine Benutzeroberfläche aufgebaut ist. Jedes Widget kann dabei weitere untergeordnete Widgets enthalten, wodurch eine baumartige Struktur entsteht.

Die Anordnung der Widgets im Widget-Tree bestimmt unmittelbar das Layout der Benutzeroberfläche. So kann beispielsweise ein `Text`-Widget innerhalb eines `Center`-Widgets platziert werden, um den Text zentriert darzustellen. Jedes Widget besitzt dabei ein übergeordnetes Element, wobei der Widget-Tree stets ein einzelnes Wurzel-Widget aufweist. [@flutter_docs]

![hierarchische Struktur eines Widget-Trees [@widgetTreePicture]](Diplomarbeit/img/Winter/widgetTree_diagram.png){width=300px}

##### Build
Der Build-Prozess in Flutter beschreibt die Schritte, mit denen der Quellcode in eine ausführbare Anwendung überführt wird. Während der Entwicklung wird die Anwendung im Debug-Modus meist *Just-in-Time* (JIT) kompiliert, während für den Release-Modus eine *Ahead-of-Time* (AOT)-Kompilierung erfolgt. Aus dem Quellcode wird dabei zunächst der Widget-Tree aufgebaut, welcher anschließend über die Render-Pipeline, unter anderem mithilfe der Grafikbibliothek Skia, auf dem Bildschirm dargestellt wird.

Zusätzlich werden im Build-Prozess definierte Assets aus der `pubspec.yaml` in das App-Bundle integriert. Abschließend wird die Anwendung plattformspezifisch als APK oder AAB für Android, als IPA für iOS oder als Web-Build erzeugt. [@flutterBuild]


#### Layout & Responsive/Adaptive UI
In Flutter wird das gesamte Layout einer Benutzeroberfläche mithilfe von Widgets realisiert. Dabei existieren sowohl sichtbare Widgets, wie beispielsweise `Text` oder `Icon`, als auch nicht sichtbare Widgets, wie `Row`, `Column` oder `Grid`, welche zur Anordnung und Ausrichtung der sichtbaren Elemente dienen. Ein Layout entsteht, indem mehrere Widgets miteinander verschachtelt und zu komplexeren Strukturen zusammengesetzt werden.

Ein einfaches Beispiel für ein Layout ist die Zentrierung eines Textelements mithilfe eines `Center`-Widgets. [@flutter_docs]

```dart
const Center(
  child: Text('Hello World'),
);
```
In diesem Beispiel wird das `Center`-Widget verwendet, um den Text zentriert auf dem Bildschirm darzustellen. Für komplexere Layouts können Widgets wie `Row` und `Column` eingesetzt werden, um Elemente horizontal oder vertikal anzuordnen.

Im Zusammenhang mit der Benutzeroberfläche spielt zudem das Konzept der responsiven und adaptiven Gestaltung eine zentrale Rolle. Eine responsive Benutzeroberfläche passt die Anordnung und Größe der UI-Elemente an den verfügbaren Bildschirmplatz an. Eine adaptive Benutzeroberfläche hingegen wählt abhängig von der Gerätekategorie, beispielsweise Smartphone oder Tablet, ein geeignetes Layout sowie passende Interaktionskonzepte aus. [@flutter_docs]

#### Formulare & Eingaben
Flutter stellt verschiedene Widgets zur Verarbeitung von Benutzereingaben bereit. Für Texteingaben werden hauptsächlich `TextField` und `TextFormField` verwendet. Während `TextField` grundlegende Eingabefunktionen bietet, stellt `TextFormField` erweiterte Funktionen zur Verfügung, die insbesondere für die Verwendung in Formularen geeignet sind, wie beispielsweise Validierung sowie die Callbacks `onSaved` und `onChanged`.

Zur Verwaltung mehrerer Eingabefelder kann das `Form`-Widget eingesetzt werden. Innerhalb eines Formulars lassen sich mehrere `TextFormField`-Widgets gruppieren und gemeinsam validieren, speichern oder zurücksetzen. Der Zugriff auf den aktuellen Zustand eines Formulars erfolgt über einen `GlobalKey<FormState>`, wodurch Funktionen wie `validate()`, `save()` oder `reset()` ausgelöst werden können.

Die Validierung von Formulareingaben erfolgt feldweise über Validator-Funktionen. Gibt ein Validator `null` zurück, gilt die Eingabe als gültig. Andernfalls wird eine entsprechende Fehlermeldung unter dem jeweiligen Eingabefeld angezeigt. Das folgende Codebeispiel zeigt ein einfaches Formular mit Validierung und Speicherung der Eingabedaten. [@flutter_docs]

```dart
final _formKey = GlobalKey<FormState>(); // GlobalKey wird hier erstellt
String _name = "";

Column(
  children: [
    // normales TextField (keine Form-Features wie validator/onSaved)
    TextField(
      decoration: const InputDecoration(labelText: "Irgendein TextField"),
      onChanged: (v) => debugPrint("TextField changed: $v"),
    ),

    // Form gruppiert mehrere FormFields
    Form(
      key: _formKey, // GlobalKey wird für Form gesetzt, dadurch kann man den State dann im Row Widget aufrufen
      child: Column(
        children: [
          TextFormField(
            decoration: const InputDecoration(labelText: "Name"),
            onChanged: (v) => debugPrint("onChanged: $v"),
            validator: (v) => (v == null || v.trim().isEmpty)
                ? "Bitte Name eingeben" // Fehlermeldung wird unter dem Feld angezeigt
                : null, // null = passt
            onSaved: (v) => _name = v!.trim(),
          ),

          Row(
            children: [
              ElevatedButton(
                onPressed: () {
                  // validate() triggert alle validatoren in der Form
                  if (_formKey.currentState!.validate()) {
                    _formKey.currentState!.save(); // ruft onSaved auf
                    debugPrint("Gespeichert: $_name");
                  }
                },
                child: const Text("Submit"),
              ),
              const SizedBox(width: 12),
              OutlinedButton(
                onPressed: () => _formKey.currentState!.reset(), // setzt Felder zurück
                child: const Text("Reset"),
              ),
            ],
          ),
        ],
      ),
    ),
  ],
);
```
![klassisches FormWidget](Diplomarbeit/img/Winter/TextFormField.png){width=300px}

#### PDF & Drucken (pdf, printing)
In Flutter können PDF-Dokumente mithilfe externer Packages erstellt und verarbeitet werden. Das Package `pdf` ermöglicht die programmgesteuerte Erstellung von PDF-Dateien, die Text, Bilder und weitere Layout-Elemente enthalten können. Nach dem Einbinden der entsprechenden Dependency in der Datei `pubspec.yaml` kann die PDF-Erstellung direkt innerhalb der Anwendung erfolgen.

Das folgende Codebeispiel zeigt die Erstellung eines einfachen PDF-Dokuments mit einer zentrierten Textausgabe.

```dart
final pdf = pw.Document();

pdf.addPage(
  pw.Page(
    pageFormat: PdfPageFormat.a4,
    build: (pw.Context context) {
      return pw.Center(
        child: pw.Text('Hello World'),
      );
    },
  ),
);
```
[@pdf]

Für das Drucken oder Teilen von PDF-Dokumenten kommt das Package `printing` zum Einsatz. Dieses ermöglicht es, die plattformspezifische Druckumgebung von Android und iOS zu öffnen und erstellte PDF-Dokumente auszudrucken oder zu speichern. Das folgende Beispiel zeigt das Teilen eines PDF-Dokuments.

```dart
await Printing.sharePdf(
  bytes: await pdf.save(),
  filename: 'my-document.pdf',
);

```
[@printing]

#### Lokalisierung & Formatierung (flutter_localization, intl)
In Flutter wird die Lokalisierung einer Anwendung mithilfe des Packages `flutter_localization` umgesetzt. Unter Lokalisierung versteht man die Anpassung der Anwendung an verschiedene Sprachen, beispielsweise Deutsch oder Englisch. Dabei kann festgelegt werden, welche Sprachen von der Anwendung unterstützt werden. Die Auswahl der Sprache erfolgt üblicherweise automatisch anhand der Systemsprache des Endgeräts, kann jedoch auch explizit vorgegeben werden.

Das Package `flutter_localization` stellt jedoch keine automatische Übersetzung eigener Texte bereit, sondern übersetzt ausschließlich die standardisierten UI-Elemente von Flutter selbst. Für die Übersetzung eigener Inhalte sowie für weitergehende Formatierungsaufgaben wird das Package `intl` verwendet. Dieses ermöglicht unter anderem die Lokalisierung von Texten sowie die länderspezifische Formatierung von Datums-, Zeit- und Währungswerten.

Das folgende Codebeispiel zeigt die Formatierung eines Geldbetrags im österreichischen Zahlenformat. [@intl, @flutter_docs]

```dart
final eur = NumberFormat.currency(locale: 'de_AT', symbol: 'EUR');
print(eur.format(1234.56)); // 1.234,56 EUR
```

### App-Architektur
Eine durchdachte App-Architektur ist ein wesentlicher Faktor für die Wartbarkeit und Erweiterbarkeit einer Anwendung. Ziel ist es, die Benutzeroberfläche (UI) klar von der Anwendungslogik, den Services sowie dem Backend- und Datenzugriff zu trennen. Durch diese Trennung der Verantwortlichkeiten wird der Code übersichtlicher und besser wartbar.

Bereits vor Beginn der Implementierung sollte eine sinnvolle Projekt- und Ordnerstruktur definiert werden. Eine klare Architektur erleichtert die Weiterentwicklung der Anwendung und unterstützt eine logische Gliederung der einzelnen Komponenten.

#### Projekt-/Ordnerstruktur
Eine klare Projekt- und Ordnerstruktur trägt wesentlich zur Übersichtlichkeit und Wartbarkeit einer Anwendung bei. In Flutter-Projekten hat es sich bewährt, den Code in mehrere logisch getrennte Hauptordner zu gliedern. Häufig verwendete Verzeichnisse sind `config`, `core`, `models`, `screens` und `widgets`.

Im Ordner `config` werden zentrale Konfigurationsdateien abgelegt, beispielsweise Themes zur Definition von Farb- und Stileinstellungen für Light- und Dark-Mode. Der Ordner `core` enthält grundlegende Komponenten wie Services, Provider, Hilfsklassen (*Utils*) sowie globale Konstanten.  

Datenmodelle, beispielsweise zur Abbildung von Datenbanktabellen oder API-Strukturen, werden im Ordner `models` definiert. Die sichtbaren Seiten der Anwendung werden im Ordner `screens` abgelegt. Dieser kann weiter unterteilt werden, etwa in einen Bereich für Authentifizierung (z. B. Login und Registrierung) und einen Hauptbereich für die eigentlichen Anwendungsseiten.

Wiederverwendbare UI-Komponenten werden im Ordner `widgets` gesammelt. Dazu zählen beispielsweise benutzerdefinierte Eingabefelder oder andere häufig genutzte UI-Elemente, die in mehreren Screens eingesetzt werden.
![klassisches Ordnerstruktur](Diplomarbeit/img/Winter/Ordnerstruktur.png){width=300px}

#### Schichtenmodell
Das Schichtenmodell beschreibt die klare Trennung der Anwendung in mehrere logische Ebenen, insbesondere in Benutzeroberfläche (UI), Service-Schicht und Backend beziehungsweise Datenzugriff. Diese Struktur wird durch die zuvor beschriebene Projekt- und Ordnerstruktur zusätzlich unterstützt.

Die Kommunikation zwischen den einzelnen Schichten erfolgt dabei in einer klar definierten Reihenfolge. Die Benutzeroberfläche interagiert ausschließlich mit der Service-Schicht, welche die Geschäftslogik kapselt und bei Bedarf Anfragen an das Backend oder den Datenzugriff weiterleitet, beispielsweise für Datenbankoperationen oder API-Aufrufe.

Durch diese Trennung der Verantwortlichkeiten wird die Wartbarkeit und Erweiterbarkeit der Anwendung deutlich verbessert. Zudem erleichtert das Schichtenmodell die Zusammenarbeit im Team, da einzelne Komponenten unabhängig voneinander entwickelt und angepasst werden können.
![Schichtenmodell der App-Architektur](Diplomarbeit/img/Winter/Schichtenmodell.png){width=400px}

#### Wiederverwendbare Komponenten (Widgets)
Unter wiederverwendbaren Komponenten versteht man in Flutter selbst erstellte Widgets, die mehrfach innerhalb einer Anwendung eingesetzt werden können. In vielen Anwendungen sollen bestimmte UI-Elemente, wie beispielsweise Buttons oder Eingabefelder, ein einheitliches Design sowie identische Funktionalitäten aufweisen.

Durch die Kapselung dieser Elemente in eigene Widgets können sie zentral definiert und in verschiedenen Screens wiederverwendet werden. Dies reduziert Code-Duplikate, erhöht die Lesbarkeit des Quellcodes und erleichtert die Wartung sowie Erweiterung der Anwendung.

#### Fehlerbehandlung & Nutzerfeedback
Eine strukturierte Fehlerbehandlung ist ein wesentlicher Bestandteil einer stabilen Anwendung. Fehler können beispielsweise durch eine fehlende Internetverbindung oder nicht verfügbare Standortdaten entstehen. In solchen Fällen sollte die Anwendung nicht abstürzen, sondern kontrolliert auf die jeweilige Situation reagieren.

Durch den Einsatz von `try-catch`-Blöcken können auftretende Exceptions abgefangen und entsprechend behandelt werden. Zusätzlich ist es wichtig, dem Benutzer ein verständliches Feedback bereitzustellen, etwa in Form von Hinweisen oder Fehlermeldungen. Parallel dazu können Fehlersituationen protokolliert werden, um diese während der Entwicklung oder im Betrieb nachvollziehen und analysieren zu können.

#### Lokale Persistenz (shared_preferences)
Unter lokaler Persistenz versteht man die Speicherung von Daten direkt auf dem Endgerät des Benutzers. In Flutter kann hierfür das Package `shared_preferences` verwendet werden. Dieses ermöglicht das dauerhafte Ablegen einfacher Schlüssel-Wert-Paare, die auch nach dem Neustart der Anwendung verfügbar bleiben.

Typische Anwendungsfälle für lokale Persistenz sind das Speichern von Benutzereinstellungen, wie beispielsweise der gewählte Dark- oder Light-Mode, sowie das Merken des Anmeldestatus eines Benutzers. Durch die lokale Speicherung dieser Informationen wird die Benutzerfreundlichkeit der Anwendung erhöht, da wiederkehrende Eingaben vermieden und individuelle Einstellungen beibehalten werden können.


### State-Management
Unter State-Management versteht man die Verwaltung und Weitergabe von Zustandsdaten innerhalb einer Anwendung. Dazu zählen beispielsweise Benutzereingaben, aktuelle UI-Zustände oder geladene Daten, die von mehreren Widgets benötigt werden. Ziel des State-Managements ist es, diese Informationen konsistent zu speichern, zu aktualisieren und zwischen verschiedenen Komponenten der Benutzeroberfläche bereitzustellen.

Flutter bietet unterschiedliche Möglichkeiten zur Verwaltung von State. Einfache Zustände können direkt innerhalb von `StatefulWidget`s gehalten werden. Für komplexere Anwendungen kommen Mechanismen wie `ChangeNotifier` und `Listenable` zum Einsatz, die eine strukturierte Trennung von UI und Logik ermöglichen. Darüber hinaus kann State auch über Konstruktoren an untergeordnete Widgets weitergegeben werden. Die Auswahl der jeweiligen Methode hängt vom Umfang und der Komplexität der Anwendung ab. [@flutter_docs]

#### Begriff „State“
Der Begriff *State* bezeichnet in Flutter den aktuellen Zustand einer Anwendung. Dazu zählen alle Informationen und Objekte, die Einfluss auf die Darstellung der Benutzeroberfläche haben, wie beispielsweise Benutzereingaben, ausgewählte Elemente oder geladene Daten. Darüber hinaus umfasst der State auch Zustände, die zur Verwaltung von Ressourcen oder zur Steuerung des Anwendungsverhaltens erforderlich sind. [@flutter_docs]

#### Grundkonzept von Provider (ChangeNotifier)
Für ein strukturiertes State-Management in Flutter kann das Package `provider` eingesetzt werden. Zentrales Element dieses Ansatzes ist der `ChangeNotifier`, welcher den aktuellen Zustand einer Anwendung kapselt und Änderungen an diesem Zustand verwaltet.

Der State wird dabei in einem sogenannten Provider gespeichert. Sobald sich der Zustand ändert, informiert der `ChangeNotifier` automatisch alle abhängigen Widgets über diese Änderung, sodass die Benutzeroberfläche entsprechend aktualisiert wird. Dadurch wird eine klare Trennung zwischen UI und Zustandslogik erreicht.

Ein typisches Anwendungsbeispiel ist die Verwaltung des App-Themes. In einem Theme-Provider kann der aktuelle Modus, beispielsweise Light- oder Dark-Mode, gespeichert werden. Änderungen am Theme-Zustand werden über den Provider an die gesamte Anwendung weitergegeben, wodurch ein konsistentes Erscheinungsbild sichergestellt wird. [@provider]

#### Datenfluss und UI-Updates (notifyListeners)
Die Methode `notifyListeners()` stellt das zentrale Element für UI-Updates im Provider-basierten State-Management dar. Sie wird innerhalb eines `ChangeNotifier` aufgerufen, sobald sich der gespeicherte Zustand ändert.

Widgets können über Mechanismen wie `Provider.of(context)` oder `Consumer<T>` an einen Provider gebunden werden. Diese Widgets registrieren sich damit als Listener und werden automatisch benachrichtigt, sobald `notifyListeners()` aufgerufen wird. Infolge dieser Benachrichtigung wird die betroffene Benutzeroberfläche neu aufgebaut (*rebuild*), sodass der aktuelle Zustand korrekt dargestellt wird.

Durch dieses Vorgehen wird ein klarer und nachvollziehbarer Datenfluss zwischen Zustandsverwaltung und Benutzeroberfläche gewährleistet, ohne dass direkte Abhängigkeiten zwischen einzelnen Widgets entstehen. [@provider]

### Navigation & Routing in Flutter
Unter Navigation versteht man in Flutter den Wechsel zwischen verschiedenen Seiten (Screens) einer Anwendung. Dieser Seitenwechsel wird über den `Navigator` und das zugrunde liegende Routing-System realisiert. Dabei können neue Seiten geöffnet, bestehende geschlossen oder ganze Navigationsstapel verändert werden.

Typische Anwendungsfälle sind beispielsweise der Wechsel vom Login-Screen zur Startseite nach einer erfolgreichen Anmeldung oder das Öffnen von Detailansichten aus Listen. Flutter stellt hierfür unterschiedliche Navigationsansätze bereit, unter anderem imperatives Routing mit dem `Navigator` sowie deklaratives Routing mithilfe eines Routers. [@flutter_docs]

#### Navigator-Grundlagen

#### Auth-Gate / Session-Handling
#### Navigation im Hauptbereich (z.B. Tabs/Flows)

### Standort & Karten in Flutter
#### Berechtigungen (permission_handler)
#### Standortbestimmung (geolocator)
#### Kartenanzeige (flutter_map, latlong2)
#### Live-Position & Marker (flutter_map_location_marker)
#### Suche & Geocoding (nominatim_flutter, flutter_typeahead)
#### Routing/Route-Line (OSRM + http)

### Supabase
#### Supabase Überblick (Auth, Database, Realtime)
#### Authentifizierung (supabase_flutter)
#### Datenzugriff (CRUD)
#### Realtime / Subscriptions
#### Datenmodelle & Mapping (JSON $\leftrightarrow$ Dart)

### Authentifizierung & Sicherheit (RLS/Policies)
#### Session & Token-Grundidee
#### Row Level Security (RLS)
#### Policies (SELECT/INSERT/UPDATE/DELETE)
#### Datenschutz bei Standortdaten

### UI/UX
#### Designprinzipien (klar, schnell, mobil)
#### Feedback & States (Loading/Empty/Error)
#### Konsistente Komponenten (Theme/Styles)
#### Barrierefreiheit & Sprache



## Praktische Arbeit











