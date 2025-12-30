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

Der grundlegende Aufbau einer `pubspec.yaml`-Datei ist im folgenden Beispiel dargestellt. [@Packages-DartDocs]

```yaml
name: demo # Name der App

dependencies:
  demo_package: ^1.0.0 # Package-Name und Version
  # ...
```
Um die definierten Packages im Projekt zu installieren, wird der Befehl `dart pub get` im Projektverzeichnis ausgeführt.




### Flutter
Flutter ist ein von Google entwickeltes Framework zur plattformübergreifenden Entwicklung von mobilen Anwendungen für Betriebssysteme wie Android und iOS. Ziel von Flutter ist es, mit einer einzigen Codebasis Anwendungen für mehrere Plattformen zu erstellen, ohne systemspezifischen Code schreiben zu müssen.

Die mit Flutter entwickelten Anwendungen werden als native Apps kompiliert und können somit auf den jeweiligen Zielplattformen ausgeführt werden. Aufgrund dieses Ansatzes wird Flutter häufig als Cross-Plattform-Framework bezeichnet. Flutter wird in Kombination mit der Programmiersprache Dart eingesetzt, welche im vorherigen Kapitel vorgestellt wurde. [@Flutter_Framework]

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

![hierarchische Struktur eines Widget-Trees [@widgetTreePicture]](img/Winter/widgetTreeDiagram.png){width=300px}

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
![klassisches FormWidget](img/Winter/TextFormField.png){width=300px}

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
![klassisches Ordnerstruktur](img/Winter/Ordnerstruktur.png){width=300px}

#### Schichtenmodell
Das Schichtenmodell beschreibt die klare Trennung der Anwendung in mehrere logische Ebenen, insbesondere in Benutzeroberfläche (UI), Service-Schicht und Backend beziehungsweise Datenzugriff. Diese Struktur wird durch die zuvor beschriebene Projekt- und Ordnerstruktur zusätzlich unterstützt.

Die Kommunikation zwischen den einzelnen Schichten erfolgt dabei in einer klar definierten Reihenfolge. Die Benutzeroberfläche interagiert ausschließlich mit der Service-Schicht, welche die Geschäftslogik kapselt und bei Bedarf Anfragen an das Backend oder den Datenzugriff weiterleitet, beispielsweise für Datenbankoperationen oder API-Aufrufe.

Durch diese Trennung der Verantwortlichkeiten wird die Wartbarkeit und Erweiterbarkeit der Anwendung deutlich verbessert. Zudem erleichtert das Schichtenmodell die Zusammenarbeit im Team, da einzelne Komponenten unabhängig voneinander entwickelt und angepasst werden können.
![Schichtenmodell der App-Architektur](img/Winter/Schichtenmodell.png){width=400px}

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
Der `Navigator` verwaltet in Flutter die Navigation zwischen einzelnen Seiten (Screens) einer Anwendung. Dabei arbeitet er mit sogenannten Routen. Eine Route bezeichnet dabei eine Seite beziehungsweise einen Screen, der über einen eindeutigen Namen identifiziert werden kann, zum Beispiel `/login` für eine Login-Seite.

Der Navigator organisiert die Routen in Form eines Stacks. Neue Seiten werden mit der Methode `push()` oben auf den Stack gelegt und anschließend angezeigt. Mit `pop()` wird die oberste Seite vom Stack entfernt, sodass die zuvor angezeigte Seite wieder sichtbar wird.

Ein typisches Beispiel ist der Wechsel zwischen Login- und Registrierungsseite: Wird von der Login-Seite aus die Registrierung geöffnet, wird diese per `push()` auf den Stack gelegt. Nach erfolgreicher Registrierung kann über `pop()` zur Login-Seite zurückgekehrt werden, ohne dass diese neu aufgebaut werden muss. [@flutter_docs]

#### Auth-Gate / Session-Handling
Ein Auth-Gate steuert den Zugriff auf bestimmte Bereiche einer Anwendung basierend auf dem Anmeldestatus eines Benutzers. Es überprüft, ob ein Benutzer aktuell angemeldet ist, und entscheidet daraufhin, welche Seiten der App angezeigt oder gesperrt werden. In der Praxis bedeutet dies beispielsweise, dass nicht angemeldete Benutzer nur den Login- oder Registrierungsbereich sehen, während angemeldete Benutzer auf den Hauptbereich der Anwendung zugreifen können.

Das Session-Handling beschäftigt sich mit der Verwaltung dieses Anmeldestatus. Dabei werden Sitzungsdaten gespeichert, überwacht und bei erneutem Start der Anwendung wiederhergestellt. Grundlage können unter anderem Sessions eines externen Authentifizierungssystems wie Supabase sein. Diese Sitzungsinformationen können zusätzlich lokal, etwa mithilfe von `shared_preferences`, persistiert werden, um Benutzer nach einem Neustart der App weiterhin angemeldet zu halten. [@supabase_sessions]

#### Navigation mit BottomNavigationBar
Eine benutzerfreundliche Möglichkeit zur Navigation zwischen den Hauptbereichen einer App ist die Verwendung einer `BottomNavigationBar`. Dabei befindet sich am unteren Rand des Bildschirms eine dauerhaft sichtbare Navigationsleiste mit mehreren Auswahlpunkten, beispielsweise „Startseite“, „Nachrichten“ oder „Profil“.

Durch die Auswahl eines Eintrags in der `BottomNavigationBar` kann zwischen den zugehörigen Seiten gewechselt werden, ohne dass der Benutzer die Orientierung in der App verliert. In Flutter wird die Umsetzung über die Klasse `BottomNavigationBar` beziehungsweise über die modernere `NavigationBar` realisiert. [@dart-docs]
![Beispiel einer BottomNavigationBar in Flutter](img/Winter/bottomNavExample.png){width=300px}

### Standort & Karten in Flutter
Zur Arbeit mit Standortdaten und Karten in Flutter werden in der Regel mehrere Packages kombiniert eingesetzt. Für den Zugriff auf den Gerätestandort ist zunächst die Einholung der entsprechenden Berechtigungen erforderlich, was beispielsweise mit dem Package `permission_handler` umgesetzt werden kann.

Die eigentliche Standortbestimmung erfolgt häufig mithilfe des Packages `geolocator`, das Funktionen zur Ermittlung der aktuellen Position sowie zu Entfernungs- und Richtungsberechnungen bereitstellt. Für die Darstellung von Karten können Bibliotheken wie `flutter_map` in Kombination mit Kartendiensten wie OpenStreetMap verwendet werden. Ergänzend kommen Packages wie `latlong2` zur Verarbeitung geografischer Koordinaten zum Einsatz.

#### Berechtigungen (permission_handler)
Für den Zugriff auf sensible Funktionen eines Endgeräts, wie Kamera oder Standort, ist in modernen Betriebssystemen eine ausdrückliche Benutzerberechtigung erforderlich. In Flutter kann die Verwaltung dieser Berechtigungen mithilfe des Packages `permission_handler` umgesetzt werden. Dieses ermöglicht das Abfragen des aktuellen Berechtigungsstatus sowie das Anfordern der benötigten Rechte direkt aus der Anwendung heraus.

Die Anfrage von Berechtigungen erfolgt asynchron. Der Benutzer kann verschiedene Entscheidungen treffen, beispielsweise das dauerhafte Erteilen, das einmalige Verweigern oder das permanente Ablehnen einer Berechtigung („Nie wieder fragen“). Das folgende Codebeispiel zeigt eine mögliche Implementierung zur Anforderung der Standortberechtigung. [@permission_handler]


```dart
Future<bool> ensureLocationPermission() async {
  // 1) Aktuellen Status abfragen
  var status = await Permission.location.status;

  if (status.isGranted) {
    // Standortberechtigung ist bereits erteilt
    return true;
  }

  if (status.isDenied) {
    // Noch nie gefragt oder abgelehnt (aber nicht permanent)
    // => jetzt anfragen
    status = await Permission.location.request();
  }

  if (status.isPermanentlyDenied) {
    // User hat "Nie wieder fragen" ausgewählt
    // => ggf. Dialog zeigen und zu den App-Einstellungen leiten
    await openAppSettings();
    return false;
  }

  if (status.isRestricted) {
    // iOS: z.B. durch Elternkontrolle eingeschränkt
    // Hier kannst du nur informieren, ändern kann das die App nicht
    return false;
  }

  if (status.isLimited) {
    // "ungefähre" Standortfreigabe
    // Für viele Apps okay, sonst entsprechend informieren
    return true; // oder false, je nach Anforderung
  }

  return status.isGranted;
}
```

#### Standortbestimmung (geolocator)
Zur Ermittlung des aktuellen Gerätestandorts kann in Flutter das Package `geolocator` verwendet werden. Neben der Bestimmung der aktuellen Position ermöglicht es auch die Berechnung von Distanzen zwischen zwei geografischen Koordinaten sowie weitere standortbezogene Abfragen.

Vor der Standortbestimmung muss überprüft werden, ob der Benutzer die erforderlichen Berechtigungen erteilt hat und ob die Standortdienste des Geräts aktiviert sind. Anschließend kann die aktuelle Position beispielsweise über die Methode `Geolocator.getCurrentPosition()` abgefragt werden. [@geolocator]

#### Kartenanzeige (flutter_map, latlong2)
Zur Darstellung von Karten in Flutter kann das Package `flutter_map` verwendet werden. Damit lässt sich über das `FlutterMap`-Widget eine interaktive Karte in die Anwendung einbinden, die typische Funktionen wie Zoomen und Verschieben unterstützt. Häufig werden dafür OpenStreetMap-Kartenkacheln verwendet. Zur Verbesserung der Benutzerfreundlichkeit können Karten sowohl im hellen als auch im dunklen Design eingebunden werden.
![Beispiel einer mit flutter_map eingebundenen OpenStreetMap-Karte](img/Winter/mapExample.png){width=300px}

Für die Arbeit mit geografischen Koordinaten wird ergänzend das Package `latlong2` eingesetzt. Es stellt Datentypen für Längen- und Breitengrade bereit und ermöglicht unter anderem die Berechnung von Distanzen zwischen zwei Koordinatenpunkten. [@latlong2]
```dart
final int meters = distance(
  LatLng(52.518611, 13.408056),
  LatLng(51.519475, 7.46694444),
);

```

#### Live-Position & Marker (flutter_map_location_marker)
Neben statischen Markern, die direkt über das Package `flutter_map` gesetzt werden können, besteht häufig die Anforderung, die aktuelle Position des Benutzers in Echtzeit darzustellen. Für diesen Zweck kann das Package `flutter_map_location_marker` eingesetzt werden, das speziell zur Erweiterung von `flutter_map` entwickelt wurde.

Es ermöglicht die kontinuierliche Aktualisierung der Benutzerposition sowie die Darstellung eines dynamischen Positionsmarkers auf der Karte. Darüber hinaus können Marker hinsichtlich Form, Farbe und Symbolik individuell gestaltet werden, sodass sie an das Design der jeweiligen Anwendung angepasst werden können.
![Beispiel eines Positionsmarkers mit flutter_map_location_marker](img/Winter/mapMarkerExample.png){width=300px}

#### Suche & Geocoding (nominatim_flutter, flutter_typeahead)
Mithilfe des Packages `nominatim_flutter` können Geocoding-Funktionen in Flutter integriert werden. Unter Geocoding versteht man die Umwandlung zwischen Adressen und geografischen Koordinaten. Beim Reverse Geocoding werden Koordinaten in eine lesbare Adresse umgewandelt, beispielsweise von Breiten- und Längengrad zu einem Ortsnamen wie „Wien“. Umgekehrt können auch Adressen oder Postleitzahlen in Koordinaten übersetzt werden.

In Verbindung mit dem Package `flutter_typeahead` lassen sich Suchfelder mit automatischen Vorschlägen realisieren. Während der Eingabe werden bereits passende Ortsvorschläge angezeigt, etwa bei der Eingabe von „Leo“ der Vorschlag „Leoben“. Diese Kombination ermöglicht eine komfortable und benutzerfreundliche Ortssuche, wie sie auch in großen Kartendiensten eingesetzt wird. [@nominatim_flutter, @flutter_typeahead]
![Ortssuche mit Autovervollständigung mittels nominatim_flutter und flutter_typeahead](img/Winter/locationSearch.png){width=300px}

#### Routing / Route-Line (OSRM + http)
Wenn zwei geografische Punkte auf einer Karte gegeben sind, besteht häufig die Anforderung, eine dazugehörige Route – beispielsweise für die Autofahrt – zu berechnen. Hierfür kann der Routingdienst **OSRM (Open Source Routing Machine)** verwendet werden. OSRM stellt eine API bereit, über die Routen zwischen Koordinatenpunkten berechnet und als Geodaten zurückgegeben werden.

Für die Kommunikation mit dem Routingdienst kommt in Flutter in der Regel das `http`-Package zum Einsatz. Es ermöglicht das Senden von HTTP-Anfragen an die OSRM-API und das Auswerten der erhaltenen Antworten. Die vom Dienst zurückgelieferten Routendaten können anschließend verarbeitet und als Route-Linie in einer Kartenansicht dargestellt werden. [@http, @osrm_docs]
![Route auf einer Flutter-Map](img/Winter/routeExample.png){width=300px}


### Supabase
Supabase ist eine Plattform für Backend-as-a-Service (BaaS) und stellt Entwicklern eine Vielzahl an Diensten wie Authentifizierung, Datenbank, Storage und Realtime-Funktionen zur Verfügung. Die Plattform orientiert sich funktional an Firebase, setzt jedoch im Gegensatz dazu auf eine relationale PostgreSQL-Datenbank.

Supabase verfolgt einen Low-Code-Ansatz, wodurch viele Backend-Funktionen ohne umfangreiche Programmierkenntnisse genutzt werden können. Neben einem kostenlosen Tarif für kleinere Anwendungen stehen auch kostenpflichtige Pläne für größere Projekte mit erhöhtem Ressourcenbedarf zur Verfügung. [@supabase_tutorial]


#### Supabase Überblick (Auth, Database, Realtime)
Supabase stellt mehrere zentrale Dienste bereit, die in modernen Anwendungen häufig benötigt werden. Dazu zählen insbesondere die Komponenten Auth, Database und Realtime.

Der Dienst **Auth** dient zur Verwaltung von Benutzerkonten und unterstützt Funktionen wie Registrierung, Anmeldung, Passwortzurücksetzung und E-Mail-Bestätigung. Die Passwörter der Benutzer werden dabei nicht im Klartext gespeichert, sondern sicher gehasht. Auth lässt sich direkt in Flutter-Anwendungen integrieren und beispielsweise mit einem Login-System verbinden.

Die Komponente **Database** stellt eine relationale PostgreSQL-Datenbank zur Verfügung. In dieser können Tabellen angelegt, Datensätze erstellt und Abfragen durchgeführt werden. Zusätzlich unterstützt Supabase Datenbankfunktionen, Trigger und Policies zur Zugriffskontrolle.

Mit **Realtime** können Änderungen an Datenbankeinträgen in Echtzeit erkannt und an angebundene Clients weitergegeben werden. Dadurch ist es möglich, Benutzeroberflächen automatisch zu aktualisieren, sobald sich Daten verändern, ohne dass eine manuelle Aktualisierung erforderlich ist. [@supabase_docs]


#### Authentifizierung (supabase_flutter)
Die Authentifizierung in Supabase basiert auf dem Auth-Dienst und lässt sich über das Package `supabase_flutter` direkt in Flutter-Anwendungen integrieren. Nach der Initialisierung des Supabase-Clients können Benutzerkonten angelegt, Anmeldungen durchgeführt und Sitzungen verwaltet werden.

Das folgende Beispiel zeigt die Initialisierung von Supabase in einer Flutter-App sowie die Registrierung eines Benutzers mittels E-Mail und Passwort.

```dart
void main() async {
  WidgetsFlutterBinding.ensureInitialized();

  await Supabase.initialize(
    url: SUPABASE_URL,
    anonKey: SUPABASE_ANON_KEY,
  );

  runApp(MyApp());
}

final supabase = Supabase.instance.client;

// Registrierung mit E-Mail und Passwort
await supabase.auth.signUp(
  email: email,
  password: password,
);
```
[@supabase_flutter]

#### Datenzugriff (CRUD)
Der Zugriff auf Daten in Supabase erfolgt in Flutter über den Supabase-Client. Typische Operationen sind das Erstellen, Lesen, Aktualisieren und Löschen von Datensätzen und werden unter dem Begriff **CRUD** (Create, Read, Update, Delete) zusammengefasst. Abfragen können gefiltert werden und ermöglichen so den gezielten Zugriff auf bestimmte Datensätze, beispielsweise in Abhängigkeit vom aktuell angemeldeten Benutzer.

Das folgende Beispiel zeigt das Auslesen und Einfügen von Datensätzen in einer Tabelle mittels Supabase-Client. Auf erweiterte sicherheitsrelevante Aspekte, wie Row Level Security (RLS), wird in einem späteren Kapitel noch näher eingegangen.

```dart
// Datensätze lesen (SELECT) mit Filtern
final data = await supabase
    .from('cities')
    .select()
    .eq('country_id', 1)   // equals-Filter
    .neq('name', 'The Shire'); // not-equals-Filter

// Neuen Datensatz einfügen (INSERT)
await supabase
    .from('cities')
    .insert({'name': 'The Shire', 'country_id': 554});
```
[@supabase_flutter]

#### Realtime / Subscriptions
Die Realtime-Funktion von Supabase ermöglicht es, Datenbankänderungen in Echtzeit zu verarbeiten. Änderungen an Datensätzen werden unmittelbar an verbundene Clients übermittelt, sodass Benutzeroberflächen ohne manuelle Aktualisierung auf dem aktuellen Stand gehalten werden. Dies ist insbesondere in Anwendungen relevant, in denen Informationen ohne Verzögerung aktualisiert werden müssen, beispielsweise in Chat-, Shop- oder Tracking-Systemen.

Damit Realtime genutzt werden kann, muss die Funktion für die betreffende Tabelle in Supabase aktiviert werden. In Flutter können anschließend sogenannte Subscriptions eingerichtet werden. Dabei „abonniert“ der Client eine Tabelle oder einzelne Ereignisarten (Insert, Update, Delete) und erhält bei Änderungen entsprechende Benachrichtigungen. [@supabase_flutter]

```dart
// Subscription auf eine Supabase-Tabelle
final channel = supabase.channel('public:orders')
  ..onPostgresChanges(
    event: PostgresChangeEvent.all,
    schema: 'public',
    table: 'orders',
    callback: (payload) {
      debugPrint('Event: ${payload.eventType}, data: ${payload.newRecord}');
    },
  )
  ..subscribe();

// Verarbeitung der Änderungen
void handleOrderChange(PostgresChangePayload payload) {
  // neue Daten nach Insert/Update
  final newData = payload.newRecord;

  // alte Daten bei Delete/Update
  final oldData = payload.oldRecord;

  debugPrint('Event: ${payload.eventType}, data: $newData');

  // hier könnte z. B. die UI aktualisiert werden
  // (setState, Provider-Update usw.)
}
```
[@supabase_flutter]

#### Datenmodelle & Mapping (JSON <-> Dart)
Die Kommunikation zwischen Supabase und der Flutter-Anwendung erfolgt im JSON-Format. Die von Supabase empfangenen JSON-Objekte werden in Flutter in der Regel zunächst als `Map<String, dynamic>` verarbeitet und anschließend in passende Dart-Datenmodelle überführt.

Für komplexere Strukturen, wie beispielsweise Benutzersitzungen oder eigene Datenobjekte, wird häufig ein klassisches Mapping über `fromJson`- und `toJson`-Methoden verwendet. Dadurch können JSON-Daten in typsichere Dart-Objekte konvertiert und umgekehrt wieder in JSON übertragen werden.

Diese Datenmodelle lassen sich anschließend in der Benutzeroberfläche weiterverwenden, beispielsweise in Verbindung mit `StreamBuilder` oder State-Management-Lösungen, um Änderungen direkt in der UI darzustellen. [@supabase_flutter]


### Authentifizierung & Sicherheit (RLS/Policies)
Ein wichtiger Aspekt einer Anwendung ist der sichere Umgang mit Benutzeranmeldungen und Zugriffsrechten. Nach einer erfolgreichen Authentifizierung stellt Supabase eine Sitzung (Session) bereit, die unter anderem ein Zugriffstoken enthält. Dieses Token wird bei weiteren Anfragen an das Backend verwendet, um den Benutzer eindeutig zu identifizieren und dessen Berechtigungen zu überprüfen.

Neben der Authentifizierung spielt auch die Zugriffskontrolle auf Daten eine zentrale Rolle. Supabase unterstützt hierfür Row Level Security (RLS). Mithilfe von Policies kann präzise festgelegt werden, welche Datensätze ein angemeldeter Benutzer lesen, einfügen, ändern oder löschen darf. Dadurch ist es möglich, Zugriffsrechte direkt auf Datenbankebene abzusichern und zu verhindern, dass Benutzer auf fremde Daten zugreifen. [@supabase_docs]

#### Session & Token-Grundidee
Nach einer erfolgreichen Anmeldung eines Benutzers erstellt Supabase eine Sitzung (Session), die ein Authentifizierungstoken enthält. Dieses Token wird bei weiteren Anfragen der App an das Backend mitgesendet und dient dazu, den Benutzer eindeutig zu identifizieren.

Anhand des Tokens wird serverseitig überprüft, ob der Benutzer angemeldet ist und welche Berechtigungen ihm zustehen. Sobald eine Sitzung abläuft oder der Benutzer sich abmeldet, verliert das Token seine Gültigkeit und der Zugriff auf geschützte Bereiche ist nicht mehr möglich. [@supabase_docs]

#### Row Level Security (RLS)
Row Level Security (RLS) ist ein Sicherheitsmechanismus von PostgreSQL, der den Zugriff auf Daten auf Zeilenebene steuert. Dadurch kann definiert werden, welche Datensätze ein Benutzer lesen oder verändern darf. Der Zugriff erfolgt somit nicht nur auf Tabellen- oder Spaltenebene, sondern auf einzelne Zeilen.

In Supabase ist RLS für neu erstellte Tabellen standardmäßig aktiviert, sofern diese nicht über die grafische Oberfläche angelegt wurden. Wird eine Tabelle per SQL-Anweisung erstellt, muss RLS gegebenenfalls manuell aktiviert werden. Mithilfe von RLS lassen sich sehr fein abgestufte Sicherheitsregeln definieren, die exakt an die Anforderungen einer Anwendung angepasst werden können. [@supabase_docs]


#### Policies (SELECT/INSERT/UPDATE/DELETE)
Policies werden in Kombination mit Row Level Security (RLS) verwendet und legen fest, auf welche Datensätze einer Tabelle ein Benutzer zugreifen darf. Eine Policy ist immer einer konkreten Tabelle zugeordnet und wird bei jedem Lese- oder Schreibzugriff ausgewertet. Sie wirkt funktional ähnlich wie eine zusätzliche `WHERE`-Bedingung, die automatisch an jede Anfrage an die Tabelle angehängt wird. 

Policies können für alle grundlegenden Datenbankoperationen definiert werden, also für **SELECT** (Lesen), **INSERT** (Einfügen), **UPDATE** (Ändern) und **DELETE** (Löschen).

Policies können entweder direkt in SQL formuliert oder über die grafische Oberfläche von Supabase konfiguriert werden. Im folgenden Beispiel wird eine Policy definiert, die bewirkt, dass Benutzer nur ihre eigenen Datensätze lesen dürfen:


```sql
create policy "Individuals can view their own todos."
on todos
for select
using ( (select auth.uid()) = user_id );
```
Dabei wird geprüft, ob die Benutzer-ID der aktuellen Sitzung (`auth.uid()`) mit der `user_id` der jeweiligen Tabellenzeile übereinstimmt. Nur wenn diese Bedingung erfüllt ist, wird der Datensatz zurückgegeben. Ohne eine entsprechende Policy würde RLS standardmäßig sämtliche Zugriffe blockieren. [@supabase_docs]

#### Datenschutz
Die zuvor beschriebenen Mechanismen wie Authentifizierung, Row Level Security (RLS) und Policies sind zentral für den Schutz personenbezogener Daten. In vielen Anwendungen werden sensible Informationen verarbeitet, beispielsweise Namen, E-Mail-Adressen oder Standortdaten.

Durch die Kombination dieser Sicherheitsmechanismen wird sichergestellt, dass Benutzer nur auf diejenigen Daten zugreifen können, für die sie berechtigt sind. Unbefugtes Auslesen oder Verändern fremder Datensätze wird dadurch unterbunden, was einen wesentlichen Beitrag zur Einhaltung von Datenschutzanforderungen leistet.


### REST APIs und HTTP-Kommunikation
Viele moderne Anwendungen sind auf die Kommunikation mit externen Diensten angewiesen, um beispielsweise Zahlungen zu verarbeiten, E-Mails zu versenden oder Routing-Daten abzurufen. Diese Kommunikation erfolgt in der Regel über REST (Representational State Transfer) APIs unter Verwendung des **HTTP-Protokolls**.

Eine REST API bietet eine standardisierte Schnittstelle, über die ein Client (wie die Flutter-App) Anfragen an einen Server stellen kann. Die Kommunikation erfolgt über HTTP-Methoden wie `GET` (zum Auslesen von Daten), `POST` (zum Erstellen neuer Daten), `PUT` (zum Aktualisieren) und `DELETE` (zum Löschen). Die Antworten werden typischerweise im JSON-Format übermittelt. [@http]

In Flutter können HTTP-Anfragen mit dem Package `http` durchgeführt werden. Ein Beispiel ist die Kommunikation mit der SumUp-API zur Zahlungsverarbeitung: Der Client stellt eine `POST`-Anfrage mit einem `Bearer Token` in den HTTP-Headern und dem Zahlungsdetails im JSON-Body. Der Server antwortet mit einer Bestätigung im JSON-Format, die anschließend ausgewertet wird.

```dart
final response = await http.post(
  Uri.parse('https://api.sumup.com/v0.1/checkouts'),
  headers: {
    'Authorization': 'Bearer token_here',
    'Content-Type': 'application/json',
  },
  body: jsonEncode({'amount': 100.0, 'currency': 'EUR'}),
);
```

Die Implementierung von HTTP-Kommunikation erfordert dabei Sorgfalt bei der Fehlerbehandlung, Timeout-Verwaltung und der sicheren Speicherung von Authentifizierungsdaten wie API-Keys. [@http]


### Responsive Design und Dark Mode
Moderne Anwendungen müssen auf verschiedenen Geräten und unter verschiedenen Bedingungen funktionieren. Dazu zählen unterschiedliche Bildschirmgrößen (Smartphones, Tablets, Laptops) sowie unterschiedliche Anzeigeeinstellungen wie Dark Mode und Light Mode.

**Responsive Design** beschreibt den Ansatz, Benutzeroberflächen so zu gestalten, dass sie sich automatisch an die verfügbare Bildschirmgröße anpassen. In Flutter werden hierfür Widgets wie `MediaQuery` (zur Ermittlung der Bildschirmgröße), `LayoutBuilder` (zur relativen Dimensionierung) und `Flexible`/`Expanded` (zur flexiblen Raumverteilung) verwendet. Dadurch wird ermöglicht, dass eine einzige App-Version auf Smartphones, Tablets und anderen Endgeräten optimal dargestellt wird. [@flutter_docs]

**Dark Mode** ist eine Anzeigeeinstellung, die die Benutzeroberfläche mit dunklen Hintergrundfarben und hellen Texten darstellt. Dies reduziert Blendeffekte bei schwachen Lichtverhältnissen und kann den Stromverbrauch auf OLED-Displays senken. In Flutter wird Dark Mode durch unterschiedliche `ThemeData`-Objekte für Light und Dark Mode realisiert. Ein zentraler Theme-Manager (wie `ThemeProvider` mit `ChangeNotifier`) verwaltet den aktuellen Theme und benachrichtigt die App bei Änderungen. [@flutter_docs] [@provider]


### Testing und Qualitätssicherung
Testen ist ein fundamentaler Bestandteil der Softwareentwicklung und trägt wesentlich zur Qualität und Zuverlässigkeit von Anwendungen bei. In Flutter werden typischerweise drei Testarten unterschieden: **Unit-Tests**, **Integration-Tests** und **Widget-Tests**.

**Unit-Tests** prüfen einzelne Funktionen und Methoden isoliert, ohne Abhängigkeiten zu anderen Komponenten. Sie sind schnell ausführbar und helfen, logische Fehler früh zu erkennen. Typische Beispiele sind Tests von Validierungsfunktionen oder Berechnungslogiken.

**Widget-Tests** (auch UI-Tests genannt) testen die Benutzeroberfläche in isolierter Form, ohne ein echtes Gerät zu benötigen. Sie überprüfen, ob Widgets korrekt rendern und auf Benutzeraktionen reagieren, beispielsweise ob ein Button nach dem Klick eine neue Seite öffnet.

**Integration-Tests** testen das Zusammenspiel mehrerer Komponenten in einem realitätsnahen Szenario, beispielsweise das Durchlaufen eines kompletten Login-Flows vom Eingabefeld bis zur Anmeldung am Backend. Integration-Tests können auf echten Geräten oder Emulatoren durchgeführt werden. [@flutter_docs]

Neben automatisierten Tests ist auch **manuelles Testen** wichtig, besonders für die Überprüfung von Benutzerfreundlichkeit, Performance auf verschiedenen Geräten und Edge Cases, die automatisiert schwer zu testen sind. Die Kombination aller Testformen trägt zu einer zuverlässigen Anwendung bei.


### Lokale Benachrichtigungen und Realtime-Updates

In modernen mobilen Anwendungen ist es essenziell, Benutzer zeitnah über wichtige Ereignisse zu informieren. Besonders in einer Fahrtbörsen-App ist die sofortige Benachrichtigung über Fahrtaktualisierungen, Statusänderungen oder Fahrer-Ankünfte entscheidend für die Benutzerfreundlichkeit. Das Package `flutter_local_notifications` ermöglicht die Darstellung von lokalen Benachrichtigungen auf Android- und iOS-Geräten, ohne dass ein zentrales Push-Notification-System (wie Firebase Cloud Messaging) notwendig ist. [@flutter_notifications]

#### Grundkonzept von flutter_local_notifications

Das Package `flutter_local_notifications` stellt eine plattformübergreifende API zur Verfügung, um lokale Benachrichtigungen zu erstellen und anzuzeigen. Diese Benachrichtigungen werden direkt auf dem Gerät generiert und sind nicht von externen Cloud-Diensten abhängig. Sie sind besonders nützlich für App-spezifische Ereignisse wie:

- Benachrichtigungen bei Datenbank-Updates (via Supabase Realtime)  
- Status-Änderungen (z. B. Fahrt angenommen, Fahrer unterwegs)  
- Timer und zeitgesteuerte Erinnerungen  
- Lokale Notifikationen bei Benutzeraktionen  

Das Package bietet Kontrolle über:
- **Titel und Nachrichtentext** – aussagekräftige Benachrichtigungsinhalte  
- **Sound und Vibration** – Benachrichtigungsfeedback  
- **Symbole und große Bilder** – visuelle Gestaltung  
- **Aktionen und Buttons** – Interaktive Benachrichtigungen  

Durch die Kombination von `flutter_local_notifications` mit Supabase Realtime können Benachrichtigungen automatisch ausgelöst werden, sobald relevante Daten in der Datenbank aktualisiert werden, ohne dass der Benutzer die App manuell aktualisieren muss. [@flutter_local_notifications]

#### Initialisierung und Konfiguration

Die Initialisierung des Notification-Service erfolgt üblicherweise in der `main()` Funktion oder in einem dedizierten Service. Dabei werden plattformspezifische Einstellungen konfiguriert:

```dart
class NotificationService {
  static final FlutterLocalNotificationsPlugin flutterLocalNotificationsPlugin =
      FlutterLocalNotificationsPlugin();

  Future<void> initialize() async {
    const AndroidInitializationSettings androidInitializationSettings =
        AndroidInitializationSettings('@mipmap/ic_launcher');
    
    const DarwinInitializationSettings iosInitializationSettings =
        DarwinInitializationSettings(
      requestAlertPermission: true,
      requestBadgePermission: true,
      requestSoundPermission: true,
    );

    final InitializationSettings initializationSettings =
        InitializationSettings(
      android: androidInitializationSettings,
      iOS: iosInitializationSettings,
    );

    await flutterLocalNotificationsPlugin.initialize(initializationSettings);
  }
}
```
[@flutter_local_notifications]

#### Benachrichtigungen auslösen

Benachrichtigungen können jederzeit im Anwendungsfluss ausgelöst werden. Ein typischer Anwendungsfall ist die Benachrichtigung bei Statusänderungen:

```dart
Future<void> showNotification({
  required String title,
  required String body,
  required int id,
}) async {
  const AndroidNotificationDetails androidNotificationDetails =
      AndroidNotificationDetails(
    'channel_id',
    'Fahrt-Updates',
    channelDescription: 'Benachrichtigungen für Fahrt-Status-Änderungen',
    importance: Importance.max,
    priority: Priority.high,
  );

  const NotificationDetails notificationDetails = NotificationDetails(
    android: androidNotificationDetails,
  );

  await flutterLocalNotificationsPlugin.show(
    id,
    title,
    body,
    notificationDetails,
  );
}
```
[@flutter_local_notifications]

\newpage

## Praktische Arbeit

### Zielplattformen & Technologie-Auswahl

#### Auswahl des Flutter-Frameworks

Für die Entwicklung der Kundenapplikation wurde das **Flutter-Framework** ausgewählt. Diese Entscheidung basierte auf mehreren Faktoren:

**Plattformübergreifende Entwicklung**: Flutter ermöglicht die Entwicklung einer einzigen Codebasis, die sowohl auf **Android als auch auf iOS** ohne wesentliche Anpassungen ausgeführt werden kann. Dies reduziert Entwicklungszeit und Wartungsaufwand erheblich, da nicht zwei separate native Apps programmiert werden müssen.

**Vorkenntnisse aus der Schulausbildung**: Das Framework Flutter wurde bereits während der Schulausbildung intensiv behandelt, weshalb die notwendigen Grundkenntnisse vorhanden waren. Dies beschleunigte die Entwicklung. [@flutter_docs]

#### Auswahl von Supabase als Backend

Für die Backend-Infrastruktur wurde **Supabase** als Backend-as-a-Service (BaaS)-Lösung gewählt. Die Gründe für diese Auswahl sind:

**Einfache Backend-Implementierung**: Supabase bietet eine vollständig verwaltete PostgreSQL-Datenbank, die ohne umfangreiche Datenbankadministration verwendet werden kann. Die grafische Oberfläche ermöglicht das einfache Erstellen von Tabellen und das Verwalten von Daten.

**Integrierte Authentifizierung**: Der Auth-Dienst von Supabase bietet eine produktionsreife Authentifizierungslösung mit Unterstützung für E-Mail/Passwort, Social Login und anderen Authentifizierungsmethoden. Dies erspart die Implementierung komplexer Authentifizierungssysteme von Grund auf.

**Realtime-Fähigkeiten**: Die Realtime-Funktionalität ermöglicht die automatische Benachrichtigung von Clients bei Datenänderungen, ohne dass manuelle Polling-Mechanismen implementiert werden müssen. Dies ist besonders wichtig für eine Fahrtbörsen-App, bei der Änderungen am Fahrstatus sofort allen relevanten Clients mitgeteilt werden müssen.

**Row Level Security (RLS)**: Supabase unterstützt Row Level Security direkt auf Datenbankebene. Dies ermöglicht eine sichere Umsetzung von Zugriffskontrollrichtlinien, bei denen Benutzer nur ihre eigenen Daten abrufen und bearbeiten können.

**Kosteneffizienz für kleine bis mittlere Anwendungen**: Supabase bietet einen großzügigen kostenlosen Tarif, der für die Entwicklung und erste Produktionsdeployments ausreichend ist. Dies reduziert die Einstiegsbarriere für das Projekt. [@supabase_tutorial]

#### Zielplattformen und Anforderungen

Die Anwendung wurde für folgende Zielplattformen entwickelt:

- **Android** (Minimum SDK Level 21, entspricht Android 5.0 und höher)
- **iOS** (Minimum Deployment Target 11.0)

Diese Mindestversionen wurden gewählt, um eine breite Kompatibilität mit verschiedenen Endgeräten zu gewährleisten, während gleichzeitig ausreichend moderne APIs und Funktionen zur Verfügung stehen. [@flutter_docs]


### Einrichtung des Flutter-Projekts

Zu Beginn der praktischen Umsetzung wurde ein neues Flutter-Projekt für die Kunden-Applikation erstellt. Als Entwicklungsumgebung kam **Android Studio** in Kombination mit dem Flutter-Plugin zum Einsatz. Nach der Installation des Flutter-SDKs sowie der Konfiguration der Umgebungsvariablen wurde mit dem folgenden Befehl ein neues Projekt angelegt:

```bash
flutter create kunden_app
```

Anschließend wurde das Projekt in Android Studio geöffnet, wodurch automatisch die standardmäßige Flutter-Ordnerstruktur generiert wurde. Zentrale Verzeichnisse sind dabei:

- `lib/` – enthält den eigentlichen Applikationscode  
- `android/` und `ios/` – plattformspezifische Anpassungen  
- `assets/` – Bilder und weitere statische Ressourcen  
- `pubspec.yaml` – Konfiguration von Abhängigkeiten und Assets  

In der Datei `pubspec.yaml` wurden anschließend alle für das Projekt benötigten Pakete eingetragen. Dazu zählen unter anderem:

- Supabase-Anbindung (`supabase_flutter`)
- State-Management (`provider`)
- Standortbestimmung, Geokodierung und Kartenanzeige (`geolocator`, `flutter_map`, `latlong2`, `flutter_map_location_marker`, `nominatim_flutter`, `flutter_localization`)
- Berechtigungsverwaltung (`permission_handler`)
- PDF-Erstellung und Druckfunktion (`pdf`, `printing`)
- lokale Datenspeicherung (`shared_preferences`)
- Suche und Autovervollständigung (`flutter_typeahead`)
- Kommunikation mit externen Diensten (`http`)
- Formatierung von Datums (`intl`)
- lokale Push-Benachrichtigungen (`flutter_local_notifications`)

```yaml
dependencies:
  flutter:
    sdk: flutter
  supabase_flutter: ^2.0.0
  flutter_map: ^8.2.1
  latlong2: ^0.9.1
  permission_handler: ^12.0.1
  geolocator: ^14.0.2
  flutter_map_location_marker: ^10.1.0
  nominatim_flutter: ^0.0.8
  flutter_typeahead: ^5.2.0
  http: ^1.2.2
  printing: ^5.13.4
  pdf: ^3.11.0
  intl: ^0.20.2
  flutter_localization: ^0.3.3
  provider: ^6.1.1
  shared_preferences: ^2.2.2
  flutter_local_notifications: ^19.5.0
```

Nach der Ausführung von `flutter pub get` wurden sämtliche Abhängigkeiten installiert und in das Projekt eingebunden. Anschließend wurde die Anwendung auf einem Android-Emulator gestartet, um die erfolgreiche Projektinitialisierung sowie die grundlegende Funktionsfähigkeit zu überprüfen.

![Erstmalig gestartete Flutter-App mit Standard-Counter-Demo](img/Winter/appErststart.png){width=300px}

### Strukturierung der App-Architektur

Um eine klare Trennung zwischen Benutzeroberfläche, Geschäftslogik und Datenzugriff sicherzustellen, wurde die Anwendung bereits zu Beginn in mehrere logisch abgegrenzte Schichten gegliedert. Hierzu wurde im Verzeichnis `lib/` eine strukturierte Ordnerhierarchie angelegt:

- `config/` – zentrale Konfigurationen und Theme-Einstellungen (Light-/Dark-Mode)  
- `core/`  
  - `constants/` – globale Konstanten, beispielsweise Farben, Abstände und API-URLs (nur in der Entwicklung)  
  - `services/` – unter anderem Supabase-Service, Location-Service und Routing-Service  
  - `utils/` – Hilfsklassen, beispielsweise für Formatierungen, Validierungen oder Geocoding  
- `models/` – Datenmodelle, etwa `Ride` oder `UserProfile`  
- `providers/` – State-Management-Komponenten auf Basis von `ChangeNotifier`  
- `screens/` – Benutzeroberflächen für einzelne Funktionsbereiche (z. B. Login, Startseite, Kartenansicht, Profil)  
- `widgets/` – wiederverwendbare UI-Komponenten wie Buttons, Formularfelder oder Karten-Widgets  

![Projektordnerstruktur der Kunden-App](img/Winter/projektstruktur.png){width=300px}

Die Umsetzung orientiert sich an einem **Schichtenmodell**. Die UI-Schicht (Screens und Widgets) kommuniziert nicht direkt mit Supabase oder gerätespezifischen Funktionen wie der Standortbestimmung. Stattdessen erfolgt der Zugriff ausschließlich über Services und Provider. Dadurch wird die Benutzeroberfläche weitgehend von Geschäftslogik entkoppelt, was die Wartbarkeit, Testbarkeit und Erweiterbarkeit der Anwendung wesentlich verbessert.

### Implementierung der Datenmodelle

Die Datenmodelle bilden jene Entitäten ab, die sowohl in Supabase als auch in der mobilen Anwendung oft und aktiv verwendet werden. Im Fall der Kunden App ist `Ride`, welche Informationen zu einer Fahrt (Start- und Zieladresse, Preis, Status, Zeitstempel) speichert sehr wichtig.

Die Modelle wurden als Dart-Klassen umgesetzt und mit geeigneten Konstruktoren sowie `fromJson`- und `toJson`-Methoden ausgestattet. Dadurch wird die Konvertierung zwischen den in Supabase gespeicherten JSON-Strukturen und den in der App verwendeten Dart-Objekten erheblich vereinfacht.

```dart
class Ride {
  final String id;
  final String userId;
  final DateTime createdAt;
  final String startAddress;
  final String destinationAddress;
  final double price;
  final String status; // z. B. 'requested', 'accepted', 'finished'

  Ride({
    required this.id,
    required this.userId,
    required this.createdAt,
    required this.startAddress,
    required this.destinationAddress,
    required this.price,
    required this.status,
  });

  factory Ride.fromJson(Map<String, dynamic> json) {
    return Ride(
      id: json['id'] as String,
      userId: json['user_id'] as String,
      createdAt: DateTime.parse(json['created_at'] as String),
      startAddress: json['start_address'] as String,
      destinationAddress: json['destination_address'] as String,
      price: (json['price'] as num).toDouble(),
      status: json['status'] as String,
    );
  }

  Map<String, dynamic> toJson() {
    return {
      'id': id,
      'user_id': userId,
      'created_at': createdAt.toIso8601String(),
      'start_address': startAddress,
      'destination_address': destinationAddress,
      'price': price,
      'status': status,
    };
  }
}
```

![UML-Diagramm der zentralen Datenmodelle](img/Winter/datenmodellUml.png){width=400px}

Durch den Einsatz solcher Modellklassen werden Typfehler reduziert, die Verständlichkeit des Codes erhöht und eine einheitliche Datenbasis für Widgets, Provider und Services geschaffen.
### Navigation und Routing der Anwendung

Die Navigation zwischen den verschiedenen Ansichten der Anwendung wurde mithilfe benannter Routen und eines zentralen Routers realisiert. Zu den zentralen Seiten gehören:

- Login- und Registrierungsseite  
- Startseite mit Kartenansicht  
- Bildschirm zur Fahrtanfrage  
- Übersicht über vergangene Fahrten  
- Profil- und Einstellungsbereich  

In der Datei `main.dart` wurde eine zentrale `MaterialApp` mit einer definierten `onGenerateRoute`-Funktion erstellt, über welche sämtliche Routen an einer Stelle verwaltet werden.

```dart
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Taxi Kunden-App',
      initialRoute: '/splash',
      onGenerateRoute: (settings) {
        switch (settings.name) {
          case '/splash':
            return MaterialPageRoute(builder: (_) => const SplashScreen());
          case '/login':
            return MaterialPageRoute(builder: (_) => const LoginScreen());
          case '/home':
            return MaterialPageRoute(builder: (_) => const HomeScreen());
          case '/rideDetails':
            final ride = settings.arguments as Ride;
            return MaterialPageRoute(
              builder: (_) => RideDetailsScreen(ride: ride),
            );
          default:
            return MaterialPageRoute(builder: (_) => const LoginScreen());
        }
      },
    );
  }
}
```

![Navigationsfluss der Anwendung](img/Winter/navigationsdiagramm.png){width=400px}

![Login-Screen der Kunden-App](img/Winter/loginScreen.png){width=300px}

![Startseite mit Kartenansicht](img/Winter/startseiteKarte.png){width=300px}

Ein zentrales Element stellt das sogenannte **Auth-Gate** dar: Ist ein Benutzer nicht angemeldet, wird er automatisch auf die Login-Seite weitergeleitet. Erst nach erfolgreicher Authentifizierung erhält er Zugriff auf die Hauptbereiche der Anwendung, wie beispielsweise die Kartenansicht oder die Übersicht vergangener Fahrten.

### State-Management mit Provider

Für die Verwaltung des Anwendungszustands wird das Paket `provider` eingesetzt. Der zentrale Zustand, der bei dieser Kunden-App mit dem `provider` verwaltet wird, ist die Anwendungseinstellung Dark-/Light-Mode über den `ThemeProvider`.

Der `ThemeProvider` wird als `ChangeNotifier` implementiert und in der `main.dart` registriert, sodass er in der gesamten Anwendung kontextweit zur Verfügung steht. Im Gegensatz zu einem klassischen `MultiProvider`-Ansatz wird der ThemeProvider bereits vor dem Start der App initialisiert, da seine Einstellungen (z. B. der gewählte Theme-Modus) lokal persistiert sein können.

```dart
Future<void> main() async {
  WidgetsFlutterBinding.ensureInitialized();
  
  // Initialize Supabase
  await Supabase.initialize(
    url: AppConstants.supabaseUrl,
    anonKey: AppConstants.supabaseAnonKey,
  );

  // Initialize Theme Provider with persisted settings
  final themeProvider = ThemeProvider();
  await themeProvider.initialize();

  // Initialize Notification Service
  await NotificationService().initialize();

  runApp(TaxiApp(themeProvider: themeProvider));
}

class TaxiApp extends StatelessWidget {
  final ThemeProvider themeProvider;

  @override
  Widget build(BuildContext context) {
    return ChangeNotifierProvider.value(
      value: themeProvider,
      child: Consumer<ThemeProvider>(
        builder: (context, themeProvider, child) {
          return MaterialApp(
            theme: AppTheme.lightTheme,
            darkTheme: AppTheme.darkTheme,
            themeMode: themeProvider.materialThemeMode,
            home: const AuthGate(),
          );
        },
      ),
    );
  }
}
```

Der ThemeProvider wird mit `ChangeNotifierProvider.value()` registriert. Diese Registrierungsmethode wird verwendet, da die Provider-Instanz bereits initialisiert ist, bevor die App startet. Über den `Consumer<ThemeProvider>` können alle abhängigen Widgets automatisch auf Theme-Änderungen reagieren und werden neu aufgebaut, wenn sich `themeProvider.materialThemeMode` ändert.

![Datenfluss zwischen Providern und UI-Komponenten](img/Winter/providerDatenfluss.png){width=400px}

### Gestaltung der Benutzeroberfläche (UI)

Die Benutzeroberfläche wurde so gestaltet, dass sie sich optisch an moderne Mobilitätsanwendungen anlehnt und gleichzeitig eine hohe Übersichtlichkeit gewährleistet. Farbwerte, Schriftarten und Abstände werden zentral in der Datei `config/theme.dart` verwaltet. Dadurch können Anpassungen am Erscheinungsbild konsistent und an einer einzigen Stelle vorgenommen werden.

Zentrale Designentscheidungen waren:

- eine klare Trennung zwischen primären und sekundären Aktionen (z. B. ein hervorgehobener Button „Fahrt bestellen“)  
- gut lesbare Schriftgrößen  
- ausreichend große Touch-Ziele für interaktive Elemente  
- eine einheitliche Verwendung von Abständen und Kantenradien  

### Wiederverwendbare Widgets in der Kunden-App

Wichtige UI-Komponenten sind in `lib/widgets/` gekapselt und werden mehrfach eingesetzt:

- `CustomInput` / `PasswordInput` – einheitliche Textfelder mit Prefix/Suffix, Validatoren und Passwort-Toggle (widgets/common/custom_input.dart)  
- `GlassCard` / `SectionCard` – strukturierte Karten mit Glassmorphism-Optik (widgets/common/glass_card.dart)  
- `AddressSearchField` – TypeAhead-Adresssuche mit Geocoding-Vorschlägen (widgets/forms/address_search_field.dart)  
- `BookingForm` – komplettes Buchungsformular inkl. Zahlungsmethoden-Chips und Standortwahl (widgets/forms/booking_form.dart)

```dart
class CustomInput extends StatelessWidget {
  const CustomInput({
    super.key,
    required this.controller,
    required this.label,
    this.hint,
    this.prefixIcon,
    this.suffixIcon,
    this.keyboardType,
    this.textInputAction,
    this.obscureText = false,
    this.enabled = true,
    this.maxLines = 1,
    this.validator,
    this.onChanged,
    this.onFieldSubmitted,
    this.focusNode,
    this.autofillHints,
  });

  @override
  Widget build(BuildContext context) {
    return TextFormField(
      controller: controller,
      focusNode: focusNode,
      keyboardType: keyboardType,
      textInputAction: textInputAction,
      obscureText: obscureText,
      enabled: enabled,
      maxLines: maxLines,
      validator: validator,
      onChanged: onChanged,
      onFieldSubmitted: onFieldSubmitted,
      autofillHints: autofillHints,
      decoration: InputDecoration(
        labelText: label,
        hintText: hint,
        prefixIcon: prefixIcon != null ? Icon(prefixIcon) : null,
        suffixIcon: suffixIcon,
      ),
    );
  }
}
```

#### Responsive Design

Die App nutzt responsive Verhaltensweisen vor allem über `MediaQuery` und flexible Layout-Widgets:

- **MediaQuery für dynamische Abstände/Größen**: z. B. das Overlay in der Account-Seite passt seinen Abstand an Tastatur-Insets und Bildschirmhöhe an:
  ```dart
  final viewInsets = MediaQuery.of(context).viewInsets;

  return GlassCard(
    margin: EdgeInsets.only(
      left: 16,
      right: 16,
      bottom: 16 + viewInsets.bottom,
      top: MediaQuery.of(context).size.height * 0.3,
    ),
    child: Form(...),
  );
  ```

#### Dark Mode Implementierung

Die App unterstützt Light-, Dark- und System-Mode. Ein zentraler `ThemeProvider` (mit `AppThemeMode { light, dark, system }`) verwaltet den aktuellen Modus, lädt ihn aus `shared_preferences` und bietet die passenden Flutter-`ThemeMode`-Werte an.

~~~{caption="ThemeProvider (persistenter Theme-Mode)" .dart}
class ThemeProvider extends ChangeNotifier {
  static const String _themeKey = 'app_theme_mode';
  AppThemeMode _themeMode = AppThemeMode.system;
  late SharedPreferences _prefs;

  AppThemeMode get themeMode => _themeMode;

  ThemeMode get materialThemeMode {
    switch (_themeMode) {
      case AppThemeMode.light:
        return ThemeMode.light;
      case AppThemeMode.dark:
        return ThemeMode.dark;
      case AppThemeMode.system:
        return ThemeMode.system;
    }
  }

  Future<void> initialize() async {
    _prefs = await SharedPreferences.getInstance();
    final savedTheme = _prefs.getString(_themeKey);
    if (savedTheme != null) {
      _themeMode = AppThemeMode.values.firstWhere(
        (mode) => mode.name == savedTheme,
        orElse: () => AppThemeMode.system,
      );
    }
    notifyListeners();
  }

  Future<void> setThemeMode(AppThemeMode mode) async {
    if (_themeMode == mode) return;
    _themeMode = mode;
    await _prefs.setString(_themeKey, mode.name);
    notifyListeners();
  }
}
~~~

Die konkreten Theme-Definitionen liegen in `config/theme.dart` als `AppTheme.lightTheme` und `AppTheme.darkTheme` (auf Basis von `ColorScheme.fromSeed`, inkl. Buttons, Inputs, SnackBars etc.).

~~~{caption="Registrierung und Nutzung in main.dart" .dart}
Future<void> main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Supabase.initialize(url: AppConstants.supabaseUrl, anonKey: AppConstants.supabaseAnonKey);

  final themeProvider = ThemeProvider();
  await themeProvider.initialize();          // lädt gespeicherten Modus

  await NotificationService().initialize();

  runApp(TaxiApp(themeProvider: themeProvider));
}

class TaxiApp extends StatelessWidget {
  final ThemeProvider themeProvider;

  @override
  Widget build(BuildContext context) {
    return ChangeNotifierProvider.value(
      value: themeProvider,
      child: Consumer<ThemeProvider>(
        builder: (context, themeProvider, _) {
          return MaterialApp(
            theme: AppTheme.lightTheme,
            darkTheme: AppTheme.darkTheme,
            themeMode: themeProvider.materialThemeMode,
            home: const AuthGate(),
          );
        },
      ),
    );
  }
}
~~~

Die Auswahl (Hell/Dunkel/System) wird persistent gespeichert (`shared_preferences`), sodass der Modus nach App-Neustart erhalten bleibt.

![Startseite im Light-Mode](img/Winter/startseiteKarte.png){width=300px}
![Startseite im Dark-Mode](img/Winter/startseiteDark.png){width=300px}
![Fahrtenliste im Light-Mode](img/Winter/fahrtenlisteLight.png){width=300px}
![Fahrtenliste im Dark-Mode](img/Winter/fahrtenlisteDark.png){width=300px}
![Einstellungsseite im Light-Mode](img/Winter/einstellungenLight.png){width=300px}
![Einstellungsseite im Dark-Mode](img/Winter/einstellungenDark.png){width=300px}

### Implementierung der Authentifizierung

Die Authentifizierung erfolgt über `supabase_flutter` mit E-Mail/Passwort. Zentrale Aufrufe liegen im `SupabaseService`, die UI-Logik in den Auth-Screens (`login_page.dart`, `registration_page.dart`). Ein eigener `AuthProvider` wird nicht verwendet; der `AuthGate` in `main.dart` lauscht direkt auf `Supabase.instance.client.auth.onAuthStateChange`.

```dart
class SupabaseService {
  SupabaseClient get client => Supabase.instance.client;

  Future<AuthResponse> signIn({
    required String email,
    required String password,
  }) async {
    return await client.auth.signInWithPassword(
      email: email.trim(),
      password: password.trim(),
    );
  }

  Future<AuthResponse> signUp({
    required String email,
    required String password,
    Map<String, dynamic>? data,
  }) async {
    return await client.auth.signUp(
      email: email.trim(),
      password: password.trim(),
      data: data,
    );
  }

  Future<void> signOut() async => client.auth.signOut();
}
```

```dart
class _LoginPageState extends State<LoginPage> {
  final _supabaseService = SupabaseService();
  // ...

  Future<void> _handleLogin() async {
    if (!_formKey.currentState!.validate()) return;
    setState(() { _isLoading = true; _errorMessage = null; });

    try {
      final response = await _supabaseService.signIn(
        email: _emailController.text.trim(),
        password: _passwordController.text.trim(),
      );
      if (response.user != null && mounted) {
        ScaffoldMessenger.of(context).showSnackBar(
          const SnackBar(content: Text('Erfolgreich angemeldet!')),
        );
        Navigator.of(context).pushNamedAndRemoveUntil('/main', (route) => false);
      } else {
        _setError('Anmeldung fehlgeschlagen. Bitte erneut versuchen.');
      }
    } on AuthException catch (e) {
      _setError(_mapErrorMessage(e.message));
    } catch (_) {
      _setError('Ein unerwarteter Fehler ist aufgetreten.');
    } finally {
      if (mounted) setState(() => _isLoading = false);
    }
  }
}
```

Der `AuthGate` in `main.dart` wechselt abhängig vom Auth-Stream zwischen Splash, Login und Main Screen:

```dart
return StreamBuilder<AuthState>(
  stream: Supabase.instance.client.auth.onAuthStateChange,
  builder: (context, snapshot) {
    if (snapshot.connectionState == ConnectionState.waiting) {
      return const SplashScreen();
    }
    final session = snapshot.data?.session;
    if (session != null) {
      NotificationService().startRideMonitoring(session.user?.id ?? '');
      return const MainScreen();
    }
    NotificationService().stopRideMonitoring();
    return const LoginPage();
  },
);
```

![Login-Formular der Kunden-App](img/Winter/loginFormular.png){width=300px}

![Registrierungs-Formular](img/Winter/registrierungFormular.png){width=300px}

Nach einer erfolgreichen Anmeldung speichert der `AuthProvider` die aktuelle Sitzung und informiert alle abhängigen Widgets über den geänderten Authentifizierungsstatus. Nicht authentifizierte Benutzer werden automatisch auf die Login-Seite weitergeleitet. Zusätzlich wird mithilfe von `shared_preferences` ein Flag gespeichert, sodass der Login-Status beim nächsten Start der Anwendung wiederhergestellt werden kann (vgl. Abschnitt 4.2.9).

### Anbindung an die Supabase-Datenbank

Die Supabase-Datenbank bildet das Backend der Kundenanwendung. Zentrale Tabellen sind:

- `rides` – Fahrtanfragen mit Status, Zeitstempel und Fahrtdetails  
- `profiles` – Benutzerprofildaten  
- `addresses` – gespeicherte Adressen des Kunden  
- `payments` – Zahlungsinformationen pro Fahrt  

Der Zugriff erfolgt über `SupabaseService`, eine zentrale Service-Schicht, die den Supabase-Client kapselt. Alle Datenbankoperationen laufen über diese Service.

```dart
class SupabaseService {
  SupabaseClient get client => Supabase.instance.client;
  User? get currentUser => client.auth.currentUser;

  // Fahrt anlegen (via RPC-Funktion)
  Future<Map<String, dynamic>> requestRide({
    required int pickupAddressId,
    required int dropoffAddressId,
    required DateTime scheduledAt,
    required VehicleType vehicleType,
    required double estimatedPrice,
    String? notes,
  }) async {
    return await client.rpc('request_ride', params: {
      'p_pickup_address_id': pickupAddressId,
      'p_dropoff_address_id': dropoffAddressId,
      'p_scheduled_at': scheduledAt.toUtc().toIso8601String(),
      'p_vehicle_type': vehicleType.name,
      'p_estimated_price': estimatedPrice,
      'p_notes': notes,
    });
  }

  // Fahrten auslesen (gefiltert nach Benutzer)
  Future<List<Ride>> getRides({
    String? customerId,
    RideStatus? status,
    int? limit,
    bool ascending = false,
  }) async {
    final uid = customerId ?? currentUser?.id;
    if (uid == null) throw Exception('Not authenticated');

    final response = await client
        .from('rides')
        .select('*, pickup:pickup_address_id(*), dropoff:dropoff_address_id(*), payments(*)')
        .eq('customer_id', uid);

    var rides = (response as List<dynamic>)
        .map((json) => Map<String, dynamic>.from(json))
        .toList();

    // Filter & Sortierung in Dart
    if (status != null) {
      rides = rides.where((ride) => ride['status'] == status.name).toList();
    }
    
    rides.sort((a, b) {
      final dateA = DateTime.parse(a['requested_at']);
      final dateB = DateTime.parse(b['requested_at']);
      return ascending ? dateA.compareTo(dateB) : dateB.compareTo(dateA);
    });

    return rides.map<Ride>((json) => Ride.fromJson(json)).toList();
  }

  // Fahrt stornieren
  Future<void> cancelRide(int rideId) async {
    await client
        .from('rides')
        .update({'status': RideStatus.canceled.name})
        .eq('id', rideId);
  }
}
```

![Supabase Tabellenschema](img/Winter/supabaseTablesScheme.png){width=300px}

Sicherheitsrelevante Aspekte wie Row Level Security und Datenbank-Policies werden im Theorieteil „Authentifizierung & Sicherheit (RLS/Policies)" ausführlich behandelt.


### Speicherung lokaler Daten (shared_preferences)

Neben den in Supabase gespeicherten Daten werden bestimmte Informationen lokal auf dem Endgerät gesichert. Dies dient der Verbesserung der Benutzerfreundlichkeit und ermöglicht es, Benutzereinstellungen persistent zu speichern. Zu den lokal gespeicherten Daten zählen insbesondere:

- der aktuelle Theme-Modus (Hell/Dunkel/System)  
- Benutzerpräferenzen für Zahlungsmethoden  
- zuletzt verwendete Adressen  

Hierfür wird das Paket `shared_preferences` eingesetzt, mit dem Schlüssel-Wert-Paare dauerhaft am Gerät gespeichert werden können.

```dart
class ThemeProvider extends ChangeNotifier {
  static const String _themeKey = 'app_theme_mode';
  AppThemeMode _themeMode = AppThemeMode.system;
  late SharedPreferences _prefs;

  Future<void> initialize() async {
    _prefs = await SharedPreferences.getInstance();
    final savedTheme = _prefs.getString(_themeKey);

    if (savedTheme != null) {
      _themeMode = AppThemeMode.values.firstWhere(
        (mode) => mode.name == savedTheme,
        orElse: () => AppThemeMode.system,
      );
    }
    notifyListeners();
  }

  Future<void> setThemeMode(AppThemeMode mode) async {
    if (_themeMode == mode) return;
    _themeMode = mode;
    await _prefs.setString(_themeKey, mode.name);
    notifyListeners();
  }
}
```

![Settings Page mit Dark-Mode Switcher](img/Winter/einstellungenLight.png){width=300px}

Beim Start der Anwendung werden diese Werte wieder ausgelesen und in den entsprechenden Providern hinterlegt. Dadurch bleibt beispielsweise der gewählte Theme-Modus auch nach einem Neustart der App aktiv, ohne dass der Benutzer die Einstellung erneut vornehmen muss.



### Standortabfrage und Berechtigungen

Da die Kundenanwendung Fahrten auf Basis der aktuellen Benutzerposition anbietet, ist der Zugriff auf den Gerätestandort erforderlich. Dieser Zugriff setzt entsprechende Betriebssystemberechtigungen voraus, die mithilfe des Pakets `permission_handler` abgefragt und verwaltet werden.

Die eigentliche Standortbestimmung erfolgt über das Paket `geolocator`. Der `LocationService` bietet zwei Betriebsmodi:

1. **Einmalige Standortabfrage** (`getCurrentPosition`): für einmalige Positionsbestimmung beim Buchen  
2. **Kontinuierliche Updates** (`startLocationUpdates`): für Echtzeit-Tracking während einer Fahrt

Vor jeder Standortoperation wird geprüft, ob:
- die Standortdienste aktiviert sind  
- die erforderliche Berechtigung vorliegt  
- bei dauerhaft verweigerter Berechtigung der Nutzer in die Systemeinstellungen geleitet wird

```dart
class LocationService {
  Stream<LatLng> get locationStream => _locationController.stream;
  
  Future<bool> initialize() async {
    _isLocationServiceEnabled = await Geolocator.isLocationServiceEnabled();
    if (!_isLocationServiceEnabled) return false;
    
    final permissionGranted = await requestLocationPermission();
    if (!permissionGranted) return false;
    
    await getCurrentPosition();
    return true;
  }

  Future<bool> requestLocationPermission() async {
    var status = await Permission.location.status;
    
    if (status.isDenied) {
      status = await Permission.location.request();
    }
    
    if (status.isPermanentlyDenied) {
      await openAppSettings();
      return false;
    }
    
    return status.isGranted;
  }

  Future<LatLng?> getCurrentPosition() async {
    if (!isLocationAvailable) {
      throw LocationServiceException('Location permission not granted');
    }
    
    final position = await Geolocator.getCurrentPosition(
      desiredAccuracy: LocationAccuracy.high,
    );
    
    return LatLng(position.latitude, position.longitude);
  }

  void startLocationUpdates({
    LocationAccuracy accuracy = LocationAccuracy.high,
    int distanceFilter = 10,
  }) {
    final locationSettings = LocationSettings(
      accuracy: accuracy,
      distanceFilter: distanceFilter,
    );
    
    Geolocator.getPositionStream(locationSettings: locationSettings).listen(
      (Position position) {
        final latLng = LatLng(position.latitude, position.longitude);
        _locationController.add(latLng);
      },
    );
  }
}
```

![Dialog bei verweigerter Berechtigung](img/Winter/noPermissionDialogue.png){width=300px}

Fehlende Berechtigungen werden dem Benutzer verständlich erklärt, um Missverständnisse zu vermeiden und gleichzeitig die Sicherheit sowie Transparenz im Umgang mit sensiblen Standortdaten zu gewährleisten.

### Kartenanzeige und Markerfunktion

Für die Darstellung der Karte sowie der relevanten Positionen wird das Paket `flutter_map` in Kombination mit **OpenStreetMap** eingesetzt. Die Karte bildet den zentralen Bestandteil der Startseite und zeigt sowohl den aktuellen Standort des Benutzers (mit blauem Marker und Genauigkeitskreis) als auch Start-/Zielpunkte und Routenlinien.

Das `TaxiMap`-Widget unterstützt:
- **Theme-aware Kartenkacheln** (helles/dunkles Design)  
- **Aktuelle Benutzerposition** mit `CurrentLocationLayer` und automatischem Folgen  
- **Benutzerdefinierte Marker** für Start/Ziel  
- **Route-Polylines** mit Schatten-Effekt  

```dart
class TaxiMap extends StatefulWidget {
  final LatLng? center;
  final double? zoom;
  final List<Marker> markers;
  final List<Polyline> routePolylines;
  final bool showCurrentLocation;
  final bool followCurrentLocation;
  final VoidCallback? onMapReady;
  final void Function(LatLng)? onTap;

  @override
  State<TaxiMap> createState() => _TaxiMapState();
}

class _TaxiMapState extends State<TaxiMap> {
  late MapController _mapController;
  final LocationService _locationService = LocationService();

  @override
  Widget build(BuildContext context) {
    // Theme-aware Kartenkacheln
    final isDarkMode = Theme.of(context).brightness == Brightness.dark;
    final mapTileUrl = AppConstants.getMapTileUrl(isDarkMode);

    return FlutterMap(
      mapController: _mapController,
      options: MapOptions(
        initialCenter: widget.center ?? const LatLng(47.2, 11.4),
        initialZoom: widget.zoom ?? 14,
        onMapReady: widget.onMapReady,
        onTap: (tapPosition, point) => widget.onTap?.call(point),
      ),
      children: [
        // Kartenkacheln (theme-aware)
        TileLayer(
          urlTemplate: mapTileUrl,
          userAgentPackageName: AppConstants.mapUserAgent,
          maxZoom: 19,
        ),

        // Routenlinien (hinter Markern)
        if (widget.routePolylines.isNotEmpty)
          PolylineLayer(polylines: widget.routePolylines),

        // Aktuelle Benutzerposition mit blauem Marker
        if (widget.showCurrentLocation && _locationService.isLocationAvailable)
          CurrentLocationLayer(
            alignPositionOnUpdate: widget.followCurrentLocation
                ? AlignOnUpdate.always
                : AlignOnUpdate.never,
            style: LocationMarkerStyle(
              marker: DefaultLocationMarker(
                color: AppTheme.primary,
                child: const Icon(
                  Icons.person_pin_circle,
                  color: Colors.white,
                  size: 18,
                ),
              ),
              accuracyCircleColor: AppTheme.primary.withOpacity(0.12),
            ),
          ),

        // Benutzerdefinierte Marker (Start/Ziel)
        if (widget.markers.isNotEmpty)
          MarkerLayer(markers: widget.markers),
      ],
    );
  }
}
```

![Map mit aktuellen Standort](img/Winter/mapWithLocation.png){width=300px}

Die Position des Benutzers wird über `CurrentLocationLayer` in Echtzeit aktualisiert, sodass in der Kartenansicht stets eine aktuelle Standortdarstellung gewährleistet ist. Zusätzlich passen sich die Kartenkacheln automatisch an Light/Dark Mode an.

### Routenberechnung und Darstellung

Um dem Benutzer nicht nur die Position, sondern auch die Route zwischen Start- und Zielpunkt anzuzeigen, wird ein externer Routingdienst (**OSRM – Open Source Routing Machine**) verwendet. Die Kommunikation erfolgt über HTTP-Anfragen, die im `RoutingService` gekapselt sind.

Der Service berechnet neben der reinen Route auch:
- **Fahrtdauer** (in Sekunden)  
- **Fahrtentfernung** (in Metern)  
- **ETA (Estimated Time of Arrival)**  
- **Geschätzte Fahrtkosten** basierend auf Entfernung und Dauer  

Die vom Routingdienst zurückgelieferte Route besteht aus einer Folge von Koordinatenpunkten. Diese werden in der App zu einer **Polyline mit Schatten-Effekt** verarbeitet und anschließend in der Karte visualisiert.

```dart
class RoutingService {
  /// Berechnet Route zwischen zwei Punkten
  Future<RouteResult> calculateRoute(
    LatLng from,
    LatLng to, {
    RouteProfile profile = RouteProfile.driving,
  }) async {
    final url = _buildRouteUrl(from, to, profile);
    final response = await http.get(Uri.parse(url));

    if (response.statusCode != 200) {
      throw RoutingException('Routing server error');
    }

    final data = json.decode(response.body) as Map<String, dynamic>;
    if (data['code'] != 'Ok' || (data['routes'] as List).isEmpty) {
      throw RoutingException('No routes found');
    }

    return RouteResult.fromJson(data['routes'].first);
  }

  /// Berechnet ETA (Fahrtdauer + Entfernung)
  Future<EtaResult> calculateEta(LatLng from, LatLng to) async {
    final route = await calculateRoute(from, to);
    return EtaResult(
      durationSeconds: route.durationSeconds,
      distanceMeters: route.distanceMeters,
      estimatedArrival: DateTime.now().add(
        Duration(seconds: route.durationSeconds),
      ),
    );
  }

  /// Geschätzte Fahrtkosten basierend auf Route
  double estimateFare(double distanceKm) {
    if (distanceKm <= 10) {
      return 20.0;
    }
    final extraKm = distanceKm - 10;
    return 20.0 + (extraKm * 2.10);
  }
}
```

```dart
// In TaxiMap:
if (widget.routePolylines.isNotEmpty)
  PolylineLayer(polylines: widget.routePolylines),

// Route-Polylinen mit Schatten werden in RoutePolylines erstellt:
class RoutePolylines {
  static List<Polyline> createMainRoute(List<LatLng> points) {
    return [
      // Schatten (dicker, dunkler)
      Polyline(
        points: points,
        strokeWidth: 8,
        color: Colors.black.withOpacity(0.35),
      ),
      // Hauptroute
      Polyline(
        points: points,
        strokeWidth: 4.5,
        color: AppTheme.primary,
      ),
    ];
  }
}
```

![Map mit eingezeichneter Route](img/Winter/mapWithRoute.png){width=300px}

Die Routenberechnung ermöglicht es dem Benutzer, bereits vor Fahrtantritt die voraussichtliche Strecke, Fahrtdauer und geschätzte Kosten zu sehen. Dies erleichtert die Entscheidungsfindung und unterstützt eine bessere Kommunikation mit dem Fahrer.

### Formularerstellung und Validierung

Für die Eingabe von Benutzerdaten (z. B. E-Mail, Passwort) sowie Fahrtdaten (Start-/Zieladresse, geplante Zeit, Fahrzeugtyp, Notizen) kommen mehrere Formulare zum Einsatz. Die Validierung erfolgt über zentrale `ValidationHelper`-Methoden, und die UI nutzt wiederverwendbare Komponenten wie `CustomInput` und `AddressSearchField`.

Das `BookingForm`-Widget etwa kombiniert:
- **Adresssuche** (`AddressSearchField`) mit TypeAhead-Autovervollständigung  
- **Zahlungsmethoden-Chips** (Bar/Karte)  
- **Zeitpicker** für geplante Fahrten  
- **Fahrzeugtyp-Auswahl**  
- **Notizen-Feld** für zusätzliche Informationen  

Validierungen erfolgen über standardisierte Funktionen:

```dart
class ValidationHelper {
  static String? validateEmail(String? value) {
    if (value == null || value.trim().isEmpty) {
      return 'E-Mail ist erforderlich';
    }
    if (!value.contains('@') || !value.contains('.')) {
      return 'Ungültige E-Mail-Adresse';
    }
    return null;
  }

  static String? validatePassword(String? value) {
    if (value == null || value.isEmpty) {
      return 'Passwort ist erforderlich';
    }
    if (value.length < 6) {
      return 'Mindestens 6 Zeichen erforderlich';
    }
    return null;
  }

  static String? validateStrongPassword(String? value) {
    if (value == null || value.isEmpty) {
      return 'Passwort ist erforderlich';
    }
    if (value.length < 8) return 'Mindestens 8 Zeichen';
    if (!value.contains(RegExp(r'[A-Z]'))) return 'Ein Großbuchstabe erforderlich';
    if (!value.contains(RegExp(r'[0-9]'))) return 'Eine Zahl erforderlich';
    return null;
  }
}
```

```dart
class BookingForm extends StatefulWidget {
  final void Function(BookingData) onSubmit;
  final LatLng? initialPickup;

  @override
  State<BookingForm> createState() => _BookingFormState();
}

class _BookingFormState extends State<BookingForm> {
  final _formKey = GlobalKey<FormState>();
  final _pickupController = TextEditingController();
  final _dropoffController = TextEditingController();
  
  LatLng? _pickupCoordinates;
  LatLng? _dropoffCoordinates;
  PaymentMethod _paymentMethod = PaymentMethod.cash;
  VehicleType _vehicleType = VehicleType.sedan;

  void _handleSubmit() {
    if (_formKey.currentState!.validate()) {
      _formKey.currentState!.save();
      
      if (_pickupCoordinates == null || _dropoffCoordinates == null) {
        ScaffoldMessenger.of(context).showSnackBar(
          const SnackBar(content: Text('Bitte wählen Sie Start- und Zieladresse')),
        );
        return;
      }

      widget.onSubmit(BookingData(
        pickup: _pickupCoordinates!,
        dropoff: _dropoffCoordinates!,
        paymentMethod: _paymentMethod,
        vehicleType: _vehicleType,
      ));
    }
  }

  @override
  Widget build(BuildContext context) {
    return Form(
      key: _formKey,
      child: Column(
        children: [
          // Adresssuche mit TypeAhead
          AddressSearchField(
            controller: _pickupController,
            label: 'Startadresse',
            onSelected: (suggestion) {
              setState(() => _pickupCoordinates = suggestion.coordinates);
            },
          ),
          const SizedBox(height: 16),
          AddressSearchField(
            controller: _dropoffController,
            label: 'Zieladresse',
            onSelected: (suggestion) {
              setState(() => _dropoffCoordinates = suggestion.coordinates);
            },
          ),
          const SizedBox(height: 24),

          // Zahlungsmethoden
          Text('Zahlungsart', style: AppTheme.titleMedium(context)),
          const SizedBox(height: 12),
          Wrap(
            spacing: 12,
            children: [
              ChoiceChip(
                selected: _paymentMethod == PaymentMethod.cash,
                label: const Text('Bar'),
                onSelected: (selected) {
                  if (selected) setState(() => _paymentMethod = PaymentMethod.cash);
                },
              ),
              ChoiceChip(
                selected: _paymentMethod == PaymentMethod.card,
                label: const Text('Karte'),
                onSelected: (selected) {
                  if (selected) setState(() => _paymentMethod = PaymentMethod.card);
                },
              ),
            ],
          ),
          const SizedBox(height: 24),

          FilledButton(
            onPressed: _handleSubmit,
            child: const Text('Fahrt anfragen'),
          ),
        ],
      ),
    );
  }
}
```

![Fahrtanfrage-Formular](img/Winter/fahrtanfrageFormular.png){width=300px}

Fehlerhafte Eingaben werden direkt unter den jeweiligen Feldern angezeigt. Die AddressSearchField bietet Echtzeitvorschläge, wodurch die Bedienung intuitiv wird und Tippfehler bei Adressen minimiert werden.

### Fehlerbehandlung und Nutzerfeedback

Eine stabile Anwendung muss Fehler abfangen und dem Benutzer verständliches Feedback geben. In diesem Projekt werden Fehler an mehreren Stellen behandelt, unter anderem bei:

- Netzwerkfehlern (z. B. fehlende Internetverbindung)  
- fehlenden Berechtigungen (z. B. Standortzugriff)  
- fehlerhaften Eingaben in Formularen  
- Problemen beim Zugriff auf Supabase (z. B. Authentifizierungsfehler)  

Zur Darstellung von Fehlern werden mehrere Mechanismen eingesetzt:

- **Schnelle Rückmeldungen**: SnackBars für kurze Bestätigungen und Fehlermeldungen
- **Error-States**: Vollbild-Fehlerwidgets mit Retry-Optionen für kritische Fehler
- **Inline-Fehler**: Fehlerboxen direkt im Formular (z. B. LoginPage)
- **Dialoge**: Modal-Dialoge für wichtige Benachrichtigungen

Zentrale Fehlermeldungen sind in `AppConstants` als Strings gekapselt, sodass Fehler über die gesamte Anwendung hinweg einheitlich dargestellt werden.

```dart
static const String genericErrorMessage = 'Ein unerwarteter Fehler ist aufgetreten.';
static const String networkErrorMessage = 'Netzwerkfehler. Bitte prüfen Sie Ihre Internetverbindung.';
static const String locationErrorMessage = 'Standortberechtigung erforderlich.';
static const String authErrorMessage = 'Anmeldung erforderlich.';
```

![Fehlermeldung wenn eine Fahrt erst 30 Min vor Abholzeit gebucht wurde.](img/Winter/errorPickupTime.png){width=300px}

#### Error-States und Error-Handling Patterns

**SnackBars für kurze Bestätigungen:**

```dart
ScaffoldMessenger.of(context).showSnackBar(
  SnackBar(
    content: Text(message),
    backgroundColor: isError ? AppTheme.error : AppTheme.success,
    duration: const Duration(seconds: 3),
  ),
);
```

**ErrorState Widget für kritische Fehler:**

```dart
class ErrorState extends StatelessWidget {
  const ErrorState({
    required this.message,
    this.onRetry,
    this.padding = const EdgeInsets.all(24),
  });

  final String message;
  final VoidCallback? onRetry;
  final EdgeInsets padding;

  @override
  Widget build(BuildContext context) {
    return Center(
      child: Padding(
        padding: padding,
        child: Column(
          mainAxisSize: MainAxisSize.min,
          children: [
            Icon(Icons.error_outline, color: AppTheme.error, size: 48),
            const SizedBox(height: 16),
            Text(
              'Fehler aufgetreten',
              style: AppTheme.titleMedium(context).copyWith(color: AppTheme.error),
            ),
            const SizedBox(height: 8),
            Text(
              message,
              style: AppTheme.bodySmall(context),
              textAlign: TextAlign.center,
            ),
            if (onRetry != null) ...[
              const SizedBox(height: 16),
              OutlinedButton.icon(
                onPressed: onRetry,
                icon: const Icon(Icons.refresh),
                label: const Text('Erneut versuchen'),
              ),
            ],
          ],
        ),
      ),
    );
  }
}
```

**Fehlermappung in der LoginPage:**

Die LoginPage zeigt Fehler in einer Fehlerbox direkt im Formular an und mappt Supabase-Fehlermeldungen zu benutzerfreundlichen Texten:

```dart
void _setError(String message) {
  if (!mounted) return;
  
  final mappedMessage = _mapErrorMessage(message);
  
  setState(() {
    _isLoading = false;
    _errorMessage = mappedMessage;
  });
}

String _mapErrorMessage(String message) {
  if (message.contains('invalid') || message.contains('Invalid') || message.contains('credentials')) {
    return 'Falsches Passwort oder E-Mail-Adresse';
  }
  if (message.contains('not confirmed') || message.contains('not verified')) {
    return 'E-Mail-Adresse wurde noch nicht bestätigt';
  }
  if (message.contains('user') || message.contains('not found')) {
    return 'Kein Konto mit dieser E-Mail-Adresse vorhanden';
  }
  return message;
}
```

#### Edge Cases und spezielle Fehlerszenarien

**Null-Sicherheit**: Durch die Verwendung von Null Safety in Dart werden viele Fehler bereits zur Compile-Zeit erkannt. Dennoch werden kritische Abfragen mit null-checks durchgeführt:

```dart
// Sicherer Zugriff auf optionale Werte
final userName = user?.profile?.name ?? 'Gast';
final coordinates = currentLocation?.latitude;
```

**Ungültige oder fehlende Standortdaten**: Falls die Standortbestimmung fehlschlägt oder einen Timeout hat, wird dem Benutzer eine verständliche Meldung angezeigt:

```dart
try {
  position = await Geolocator.getCurrentPosition();
} on TimeoutException {
  _setError('Standortbestimmung timed out. Bitte versuchen Sie es erneut.');
} on LocationServiceException catch (e) {
  _setError('Standortbestimmung nicht möglich: ${e.message}');
} catch (e) {
  _setError('Ein unerwarteter Fehler ist aufgetreten.');
}
```

**Netzwerkfehler und Timeouts**: Alle HTTP-Anfragen und asynchronen Operationen implementieren Timeout-Logik:

```dart
try {
  final route = await calculateRoute(from, to);
  return route;
} on TimeoutException {
  throw RoutingException('Routing request timed out');
} catch (e) {
  if (e is RoutingException) rethrow;
  throw RoutingException('Failed to calculate route: $e');
}
```

**Authentifizierungsabläufe**: Falls die Session während der Nutzung abläuft, wird der Benutzer automatisch zur Login-Seite weitergeleitet. Dies wird durch den `AuthGate` in `main.dart` verwaltet, der mit einem `StreamBuilder` auf Auth-State-Changes lauscht.

**Validierung von Eingabeformularen**: Alle Eingabefelder werden vor dem Absenden validiert. Falls Validierungen fehlschlagen, werden spezifische Fehlermeldungen unter dem jeweiligen Feld angezeigt (mittels `validator`-Callback in TextFormField).

**Überprüfung von Datenbankoperationen**: Nach Datenbankoperationen wird der Erfolg überprüft. Bei Fehlern werden entsprechende Benachrichtigungen angezeigt:

```dart
try {
  await _supabaseService.requestRide(rideData);
  _showSuccess('Fahrtanfrage gesendet!');
} on PostgrestException catch (e) {
  _setError(_supabaseService.getErrorMessage(e));
} catch (e) {
  _setError('Ein unerwarteter Fehler ist aufgetreten.');
}
```

Fehler werden im Debug-Modus zusätzlich über `debugPrint()` protokolliert, um während der Entwicklung Probleme schneller identifizieren und beheben zu können.

### Erstellen und Drucken von PDF-Dokumenten

PDF-Dokumentationen werden bei Fahrten verwendet, um Rechnungen zu exportieren. Diese werden mithilfe der `pdf`-Bibliothek dynamisch erzeugt und können anschließend über das `printing`-Package geteilt oder gedruckt werden. Die Implementierung ist österreich-konform gemäß § 11 UStG (Personenbeförderung).

**Zwei Implementierungen:**

1. **InvoiceWidget** - Die UI-Ansicht der Rechnung im Detail-Screen
2. **PDF-Export** - Die PDF-Generierung für Download/Print

#### Rechnung anzeigen (InvoiceWidget)

Das `InvoiceWidget` zeigt die detaillierte Rechnung direkt im UI:

~~~{caption="InvoiceWidget für Rechnungsanzeige" .dart}
class InvoiceWidget extends StatelessWidget {
  const InvoiceWidget({required this.ride, required this.onExport});

  final Ride ride;
  final VoidCallback onExport;

  String _generateInvoiceNumber() {
    final year = DateTime.now().year;
    final id = ride.id.toString().padLeft(5, '0');
    return '$year-$id';
  }

  double _calculateNet(double gross) {
    return gross / (1 + AppConstants.taxRate); // 20% AT MwSt
  }

  double _calculateTax(double gross) {
    return gross - _calculateNet(gross);
  }

  @override
  Widget build(BuildContext context) {
    final colorScheme = Theme.of(context).colorScheme;
    final grossAmount = ride.finalPrice ?? ride.estimatedPrice ?? 0.0;
    final netAmount = _calculateNet(grossAmount);
    final taxAmount = _calculateTax(grossAmount);
    final invoiceNumber = _generateInvoiceNumber();

    return Container(
      padding: const EdgeInsets.all(16),
      decoration: BoxDecoration(
        color: colorScheme.surface,
        borderRadius: BorderRadius.circular(12),
        border: Border.all(color: colorScheme.outlineVariant, width: 1),
      ),
      child: Column(
        crossAxisAlignment: CrossAxisAlignment.stretch,
        children: [
          // Firmen-Header
          Container(
            padding: const EdgeInsets.all(12),
            decoration: BoxDecoration(
              color: AppTheme.primary.withOpacity(0.1),
              borderRadius: BorderRadius.circular(8),
            ),
            child: Column(
              children: [
                Text(
                  AppConstants.companyName.toUpperCase(),
                  style: AppTheme.titleMedium(context).copyWith(
                    fontWeight: FontWeight.bold,
                    color: AppTheme.primary,
                  ),
                  textAlign: TextAlign.center,
                ),
                Text(
                  'UID: ${AppConstants.companyUid}',
                  style: AppTheme.bodySmall(context),
                ),
              ],
            ),
          ),
          const SizedBox(height: 16),

          // Rechnungsnummer
          Text(
            'Rechnung Nr. ${invoiceNumber}',
            style: AppTheme.labelMedium(context).copyWith(fontWeight: FontWeight.w600),
          ),
          const SizedBox(height: 12),

          // Fahrtdetails
          Text(
            'FAHRTDETAILS',
            style: AppTheme.labelMedium(context).copyWith(fontWeight: FontWeight.w600),
          ),
          const SizedBox(height: 8),
          Container(
            padding: const EdgeInsets.all(12),
            decoration: BoxDecoration(
              color: colorScheme.surface,
              borderRadius: BorderRadius.circular(8),
              border: Border.all(color: colorScheme.outlineVariant),
            ),
            child: Column(
              children: [
                _InfoRow('Fahrt-ID', '#${ride.id}'),
                _InfoRow('Von', ride.pickup.displayAddress),
                _InfoRow('Nach', ride.dropoff.displayAddress),
                _InfoRow('Fahrzeugtyp', ride.vehicleType.label),
              ],
            ),
          ),
          const SizedBox(height: 16),

          // Preisberechnung
          Text(
            'PREISBERECHNUNG',
            style: AppTheme.labelMedium(context).copyWith(fontWeight: FontWeight.w600),
          ),
          const SizedBox(height: 8),
          Container(
            padding: const EdgeInsets.all(12),
            decoration: BoxDecoration(
              color: colorScheme.surface,
              borderRadius: BorderRadius.circular(8),
              border: Border.all(color: colorScheme.outlineVariant),
            ),
            child: Column(
              children: [
                _InvoiceRow(label: 'Grundpreis', value: DateFormatter.formatMoney(ride.estimatedPrice ?? 0)),
                if (ride.surchargeAmount != null && ride.surchargeAmount! > 0)
                  _InvoiceRow(
                    label: 'Zuschlag',
                    value: DateFormatter.formatMoney(ride.surchargeAmount!),
                  ),
                const Divider(),
                _InvoiceRow(
                  label: 'Nettobetrag',
                  value: DateFormatter.formatMoney(netAmount),
                ),
                _InvoiceRow(
                  label: 'MwSt. 20% (AT)',
                  value: DateFormatter.formatMoney(taxAmount),
                ),
                const SizedBox(height: 8),
                _InvoiceRow(
                  label: 'GESAMTBETRAG',
                  value: DateFormatter.formatMoney(grossAmount),
                  isBold: true,
                ),
              ],
            ),
          ),
          const SizedBox(height: 16),

          // Legal Notice
          Container(
            padding: const EdgeInsets.all(8),
            decoration: BoxDecoration(
              color: colorScheme.surface,
              borderRadius: BorderRadius.circular(6),
            ),
            child: Text(
              'Gemäß § 11 UStG • Personenbeförderung • ${AppConstants.companyUid}',
              style: AppTheme.bodySmall(context).copyWith(
                fontSize: 10,
                color: colorScheme.onSurface.withOpacity(0.6),
              ),
              textAlign: TextAlign.center,
            ),
          ),
          const SizedBox(height: 16),

          // Export Button
          FilledButton.icon(
            onPressed: onExport,
            icon: const Icon(Icons.picture_as_pdf),
            label: const Text('Rechnung als PDF herunterladen'),
          ),
        ],
      ),
    );
  }
}
~~~

#### PDF-Export mit `_createInvoicePdf()`

Die PDF-Generierung erfolgt in `ride_detail_page.dart` mit vollständiger Österreich-Konformität:

~~~{caption="PDF-Generierung für Rechnungsexport" .dart}
Future<void> _exportReceiptPdf() async {
  if (_ride == null) return;

  try {
    final doc = await _createInvoicePdf(_ride!);

    // PDF-Layout öffnen (Print/Share Dialog)
    await Printing.layoutPdf(
      onLayout: (format) async => await doc.save(),
      name: 'Rechnung_${_ride!.id}.pdf',
    );
  } catch (e) {
    _showError('PDF-Export fehlgeschlagen: $e');
  }
}

Future<pw.Document> _createInvoicePdf(Ride ride) async {
  final doc = pw.Document();

  // Österreich Unternehmensdaten
  const companyName = AppConstants.companyName;
  const companyAddress = AppConstants.companyAddress;
  const companyUid = AppConstants.companyUid;
  const companyPhone = AppConstants.companyPhone;
  const taxRate = AppConstants.taxRate;

  // Rechnungsnummer (YYYY-XXXXX format)
  final invoiceNumber = '${DateTime.now().year}-${ride.id.toString().padLeft(5, '0')}';

  // Netto/Brutto Berechnung
  final grossAmount = ride.finalPrice ?? ride.estimatedPrice ?? 0.0;
  final netAmount = grossAmount / (1 + taxRate);
  final taxAmount = grossAmount - netAmount;

  doc.addPage(
    pw.Page(
      build: (context) => pw.Column(
        crossAxisAlignment: pw.CrossAxisAlignment.start,
        children: [
          // Firmen-Header
          pw.Container(
            padding: const pw.EdgeInsets.only(bottom: 20),
            decoration: pw.BoxDecoration(
              border: pw.Border(bottom: pw.BorderSide(width: 2)),
            ),
            child: pw.Column(
              crossAxisAlignment: pw.CrossAxisAlignment.start,
              children: [
                pw.Text(
                  companyName,
                  style: pw.TextStyle(fontSize: 20, fontWeight: pw.FontWeight.bold),
                ),
                pw.SizedBox(height: 4),
                pw.Text(companyAddress, style: const pw.TextStyle(fontSize: 10)),
                pw.Text('Tel: $companyPhone', style: const pw.TextStyle(fontSize: 10)),
                pw.Text(
                  'UID: $companyUid',
                  style: pw.TextStyle(fontSize: 10, fontWeight: pw.FontWeight.bold),
                ),
              ],
            ),
          ),

          // Rechnungs-Header
          pw.Row(
            mainAxisAlignment: pw.MainAxisAlignment.spaceBetween,
            children: [
              pw.Text(
                'RECHNUNG',
                style: pw.TextStyle(fontSize: 18, fontWeight: pw.FontWeight.bold),
              ),
              pw.Column(
                crossAxisAlignment: pw.CrossAxisAlignment.end,
                children: [
                  pw.Text('Rechnungsnr.: $invoiceNumber'),
                  pw.Text('Datum: ${DateFormatter.formatDate(DateTime.now())}'),
                ],
              ),
            ],
          ),
          pw.SizedBox(height: 20),

          // Fahrtdetails
          pw.Text('Fahrtdetails', style: pw.TextStyle(fontWeight: pw.FontWeight.bold)),
          pw.SizedBox(height: 8),
          _pdfRow('Fahrt-ID', '#${ride.id}'),
          _pdfRow('Abholung', ride.pickup.displayAddress),
          _pdfRow('Ziel', ride.dropoff.displayAddress),
          _pdfRow('Fahrzeug', ride.vehicleType.label),
          if (ride.startTime != null)
            _pdfRow('Start', DateFormatter.formatDateTime(ride.startTime)),
          if (ride.endTime != null)
            _pdfRow('Ende', DateFormatter.formatDateTime(ride.endTime)),
          pw.SizedBox(height: 20),

          // Preisaufschlüsselung
          pw.Container(
            padding: const pw.EdgeInsets.all(12),
            decoration: pw.BoxDecoration(
              border: pw.Border.all(width: 1),
              borderRadius: const pw.BorderRadius.all(pw.Radius.circular(4)),
            ),
            child: pw.Column(
              crossAxisAlignment: pw.CrossAxisAlignment.start,
              children: [
                if (ride.estimatedPrice != null)
                  _pdfRow('Grundpreis', DateFormatter.formatMoney(ride.estimatedPrice)),
                if (ride.surchargeAmount != null && ride.surchargeAmount! > 0)
                  _pdfRow('Zuschlag', DateFormatter.formatMoney(ride.surchargeAmount)),
                pw.Divider(),
                pw.SizedBox(height: 8),
                _pdfRow('Nettobetrag', DateFormatter.formatMoney(netAmount)),
                _pdfRow('MwSt. 20% (AT)', DateFormatter.formatMoney(taxAmount)),
                pw.SizedBox(height: 8),
                pw.Row(
                  mainAxisAlignment: pw.MainAxisAlignment.spaceBetween,
                  children: [
                    pw.Text('GESAMTBETRAG', style: pw.TextStyle(fontSize: 14, fontWeight: pw.FontWeight.bold)),
                    pw.Text(
                      DateFormatter.formatMoney(grossAmount),
                      style: pw.TextStyle(fontSize: 14, fontWeight: pw.FontWeight.bold),
                    ),
                  ],
                ),
              ],
            ),
          ),
          pw.SizedBox(height: 20),

          // Legal Notice
          pw.Container(
            padding: const pw.EdgeInsets.all(8),
            decoration: pw.BoxDecoration(
              border: pw.Border(
                top: pw.BorderSide(width: 1),
                bottom: pw.BorderSide(width: 1),
              ),
            ),
            child: pw.Text(
              'Gemäß § 11 UStG • Personenbeförderung • ATU12345678',
              style: pw.TextStyle(fontSize: 8, fontStyle: pw.FontStyle.italic),
              textAlign: pw.TextAlign.center,
            ),
          ),
          pw.SizedBox(height: 16),

          // Notizen wenn vorhanden
          if (ride.notes?.isNotEmpty == true) ...[
            pw.Text('Notizen', style: pw.TextStyle(fontWeight: pw.FontWeight.bold)),
            pw.SizedBox(height: 4),
            pw.Text(ride.notes!, style: const pw.TextStyle(fontSize: 9)),
          ],

          pw.Spacer(),

          // Footer
          pw.Divider(),
          pw.Text(
            'Vielen Dank für Ihre Nutzung unseres Services!',
            style: const pw.TextStyle(fontSize: 9),
            textAlign: pw.TextAlign.center,
          ),
        ],
      ),
    ),
  );

  return doc;
}

pw.Widget _pdfRow(String label, String? value) {
  return pw.Padding(
    padding: const pw.EdgeInsets.only(bottom: 4),
    child: pw.Row(
      crossAxisAlignment: pw.CrossAxisAlignment.start,
      children: [
        pw.SizedBox(
          width: 120,
          child: pw.Text(label, style: pw.TextStyle(fontWeight: pw.FontWeight.bold)),
        ),
        pw.Expanded(child: pw.Text(value ?? '-')),
      ],
    ),
  );
}
~~~

![PDF-Rechnung](img/Winter/rechnungPdf.png){width=300px}

Auf diese Weise können Benutzer Fahrtbelege mit vollständiger Preisaufschlüsselung und österreich-konformer Rechnungslegung (inklusive Mehrwertsteuer) exportieren und als PDF herunterladen oder drucken.



### Zahlungssystem mit SumUp Sandbox Integration

Die Anwendung implementiert ein professionelles Zahlungssystem mit Unterstützung für mehrere Zahlungsmethoden: **Barzahlung**, **Kartenzahlung via SumUp Sandbox API**, **Rechnungen** und **PayPal**.

#### Zahlungsarchitektur

Das Zahlungssystem folgt einem strukturierten Ablauf mit drei Phasen:

**Phase 1 – Booking**: Bei der Fahrtbuchung wird die bevorzugte Zahlungsmethode lokal in `SharedPreferences` gespeichert und beim nächsten Buchen wieder vorgeschlagen.

**Phase 2 – Ride Execution**: Nach Fahrtabschluss wird automatisch ein Zahlungseintrag in der Supabase-Datenbank (`payments`-Tabelle) erstellt mit der gewählten Zahlungsart und dem Betrag (Status: `pending` oder direkt `paid` bei Barzahlung).

**Phase 3 – Completion**: Nach Fahrtabschluss wird das `PaymentForm` Widget angezeigt. Hier kann der Benutzer die Zahlungsart wählen und bei Kartenzahlung den Checkout durchführen, bei Barzahlung wird der Fahrer als bestätigt markiert, oder eine Rechnung wird ausgestellt.

#### SumUp Checkout API

Für Kartenzahlungen wird die **SumUp REST API** (Checkouts Endpoint) verwendet. Dies ermöglicht die sichere Verarbeitung von Kartendaten. Der SumUp-Service wurde als Singleton-Klasse implementiert:

```dart
class SumUpService {
  static final SumUpService _instance = SumUpService._internal();
  factory SumUpService() => _instance;
  SumUpService._internal();

  final String _baseUrl = AppConstants.sumupApiUrl;
  final String _privateKey = AppConstants.sumupPrivateKey;
  final String _merchantCode = AppConstants.sumupMerchantCode;

  Future<SumUpPaymentResult> processCardPayment({
    required double amount,
    required String currency,
    required String customerEmail,
    required String description,
  }) async {
    try {
      debugPrint('💳 SumUp: Starting card payment for €$amount');

      // Prepare request body for Checkouts API
      final checkoutRef = 'checkout_${DateTime.now().millisecondsSinceEpoch}';
      final Map<String, dynamic> requestBody = {
        'checkout_reference': checkoutRef,
        'amount': amount,
        'currency': currency,
        'description': description,
        'merchant_code': _merchantCode,
      };

      debugPrint('📤 SumUp Request: $requestBody');

      // Make API request
      final response = await http.post(
        Uri.parse('$_baseUrl/v0.1/checkouts'),
        headers: {
          'Content-Type': 'application/json',
          'Authorization': 'Bearer $_privateKey',
        },
        body: jsonEncode(requestBody),
      ).timeout(
        const Duration(seconds: 15),
        onTimeout: () {
          throw Exception('SumUp API timeout');
        },
      );

      debugPrint('📥 SumUp Response Status: ${response.statusCode}');
      debugPrint('📥 SumUp Response Body: ${response.body}');

      // Parse response
      final Map<String, dynamic> responseData = jsonDecode(response.body);

      if (response.statusCode == 201 || response.statusCode == 200) {
        final transactionId = responseData['id']?.toString() ?? 'txn_unknown';
        final checkoutStatus = responseData['status']?.toString() ?? 'PENDING';

        debugPrint('✅ SumUp Checkout Created: $transactionId (Status: $checkoutStatus)');
        
        // DEMO MODE: Simulate immediate payment success für Diplomarbeit
        // In production: User würde zur Zahlungsseite weitergeleitet oder SDK genutzt
        debugPrint('🎓 DEMO MODE: Simulating successful payment for thesis');

        return SumUpPaymentResult(
          success: true,
          transactionId: transactionId,
          status: 'PAID',
          message: 'Zahlung erfolgreich verarbeitet',
        );
      } else {
        final errorMessage = responseData['message']?.toString() ?? 
            responseData['error_message']?.toString() ?? 
            'Zahlungsfehler';

        debugPrint('❌ SumUp Payment Failed: $errorMessage');

        return SumUpPaymentResult(
          success: false,
          transactionId: null,
          status: 'FAILED',
          message: errorMessage,
        );
      }
    } catch (e) {
      debugPrint('❌ SumUp Exception: $e');
      return SumUpPaymentResult(
        success: false,
        transactionId: null,
        status: 'ERROR',
        message: 'Netzwerkfehler: $e',
      );
    }
  }
}
```

Die API-Anmeldedaten (Private Key, Merchant Code) werden zentral in `lib/core/constants.dart` gespeichert:

```dart
static const bool sumupSandboxMode = true;
static const String sumupPublicKey = 'SUMUPPUBLICKEY';
static const String sumupPrivateKey = 'SUMUPPRIVATEKEY';
static const String sumupMerchantCode = 'MERCHANTCODE';
static const String sumupApiUrl = 'https://api.sumup.com';
```

Der Sandbox-Modus ermöglicht vollständiges Testen ohne echte Transaktionen. Im DEMO-Modus wird jede Zahlung sofort als erfolgreich simuliert.

#### PaymentForm Widget

Das `PaymentForm` Widget verwaltet alle Zahlungsmethoden und wird nach Fahrtabschluss angezeigt:

```dart
class PaymentForm extends StatefulWidget {
  const PaymentForm({super.key, required this.ride, required this.onSaved});

  final Ride ride;
  final VoidCallback onSaved;

  @override
  State<PaymentForm> createState() => _PaymentFormState();
}

class _PaymentFormState extends State<PaymentForm> {
  final _formKey = GlobalKey<FormState>();
  final _amountController = TextEditingController();
  final _supabaseService = SupabaseService();

  PaymentMethod _method = PaymentMethod.cash;
  PaymentStatus _status = PaymentStatus.pending;
  bool _isLoading = false;
  bool _showSuccess = false;
  String? _transactionId;

  @override
  void initState() {
    super.initState();
    _initializeForm();
  }

  void _initializeForm() {
    final existingPayment = widget.ride.payments.isNotEmpty 
        ? widget.ride.payments.first 
        : null;

    if (existingPayment != null) {
      // Load existing payment data
      _method = existingPayment.method;
      _status = existingPayment.status;
      _amountController.text = existingPayment.amount.toStringAsFixed(2);
    } else {
      // Initialize with ride cost
      final defaultAmount = widget.ride.finalPrice ?? widget.ride.estimatedPrice ?? 0.0;
      _amountController.text = defaultAmount.toStringAsFixed(2);

      // Load preferred payment method from SharedPreferences
      _loadPreferredPaymentMethod();

      // Bar = direkt bezahlt, Karte/Rechnung = pending
      _status = _method == PaymentMethod.cash
          ? PaymentStatus.paid
          : PaymentStatus.pending;
    }
  }

  Future<void> _loadPreferredPaymentMethod() async {
    try {
      final prefs = await SharedPreferences.getInstance();
      final preferred = prefs.getString('preferred_payment_method');
      
      if (preferred != null) {
        final method = PaymentMethod.fromString(preferred);
        if (method != null) {
          setState(() => _method = method);
        }
      }
    } catch (e) {
      debugPrint('Error loading preferred payment method: $e');
    }
  }

  Future<void> _processCardPayment(double amount) async {
    debugPrint('💳 Processing card payment via SumUp: €$amount');

    // Show processing dialog
    if (mounted) {
      showDialog(
        context: context,
        barrierDismissible: false,
        builder: (context) => const _PaymentProcessingDialog(),
      );
    }

    try {
      final sumUpService = SumUpService();
      
      final result = await sumUpService.processCardPayment(
        amount: amount,
        currency: 'EUR',
        customerEmail: 'customer@example.com',
        description: 'Fahrt #${widget.ride.id}',
      );

      if (result.success) {
        _transactionId = result.transactionId;
        _status = PaymentStatus.paid;
        debugPrint('✅ SumUp payment successful: $_transactionId');

        if (mounted) {
          Navigator.pop(context); // Close processing dialog
        }
      } else {
        throw Exception('SumUp Zahlung fehlgeschlagen: ${result.message}');
      }
    } catch (e) {
      if (mounted) {
        Navigator.pop(context); // Close processing dialog
      }
      _status = PaymentStatus.failed;
      debugPrint('❌ Card payment error: $e');
      rethrow;
    }
  }

  Future<void> _processInvoicePayment(double amount) async {
    debugPrint('📋 Processing invoice: €$amount');

    // Rechnungen bleiben pending bis Admin bestätigt
    _status = PaymentStatus.pending;
    _transactionId = 'inv_${DateTime.now().millisecondsSinceEpoch}';

    if (mounted) {
      ScaffoldMessenger.of(context).showSnackBar(
        const SnackBar(
          content: Text('Rechnung erstellt. Sie erhalten diese per E-Mail.'),
          duration: Duration(seconds: 3),
        ),
      );
    }
  }
}
```

#### Zahlungsstatus in Supabase

Nach erfolgreicher Verarbeitung wird der Zahlungsstatus in der Datenbank aktualisiert:

```dart
try {
  await _supabaseService.createOrUpdatePayment(
    rideId: widget.ride.id,
    method: _method,
    status: _status,
    amount: amount,
    paymentId: _existingPayment?.id,
  );

  debugPrint('✅ Payment saved successfully to database');

  if (mounted) {
    setState(() => _showSuccess = true);
    widget.onSaved();
  }
} catch (e) {
  _showError('Zahlungsfehler: ${_supabaseService.getErrorMessage(e)}');
}
```

Die `payments`-Tabelle enthält:
- `id` – eindeutige Zahlungs-ID
- `ride_id` – zugehörige Fahrt
- `method` – Zahlungsart (cash/card/invoice/paypal)
- `status` – Status (pending/paid/failed/refunded)
- `amount` – Betrag in EUR
- `created_at` / `updated_at` – Zeitstempel

#### Benutzeroberflächen-Integration

Das PaymentForm zeigt unterschiedliche UI-Zustände:

**Pending State (Karte):**

### Lokale Benachrichtigungen und Echtzeit-Monitoring

Die Anwendung implementiert ein automatisches Notification-System zur Benachrichtigung des Kunden über Fahrt-Status-Änderungen. Dies geschieht durch die Kombination von Supabase Realtime (Datenbankänderungen) und `flutter_local_notifications` (lokale Benachrichtigungen).

#### NotificationService Implementierung

Ein zentraler `NotificationService` wurde als Singleton implementiert, um alle Benachrichtigungsfunktionen zu kapseln. Der Service kombiniert **Supabase Realtime** für Fahrt-Updates mit **flutter_local_notifications** für lokale Sounds und Vibrationen (kein Firebase erforderlich):

```dart
class NotificationService {
  static final NotificationService _instance = NotificationService._internal();
  factory NotificationService() => _instance;
  NotificationService._internal();

  final FlutterLocalNotificationsPlugin _localNotifications =
      FlutterLocalNotificationsPlugin();

  final _supabase = Supabase.instance.client;

  bool _initialized = false;
  RealtimeChannel? _rideSubscription;

  /// Initialisiere Local Notifications (für Sounds/Vibration)
  Future<bool> initialize() async {
    if (_initialized) return true;

    try {
      // Android 13+ Runtime Permission
      if (Platform.isAndroid) {
        final android = _localNotifications
            .resolvePlatformSpecificImplementation<AndroidFlutterLocalNotificationsPlugin>();
        await android?.requestNotificationsPermission();
        debugPrint('✅ NOTIFICATION: Android permission requested');
      }

      // Android Settings
      const androidSettings = AndroidInitializationSettings('@mipmap/ic_launcher');

      // iOS Settings
      const iosSettings = DarwinInitializationSettings(
        requestAlertPermission: true,
        requestBadgePermission: true,
        requestSoundPermission: true,
      );

      const initSettings = InitializationSettings(
        android: androidSettings,
        iOS: iosSettings,
      );

      final initialized = await _localNotifications.initialize(
        initSettings,
        onDidReceiveNotificationResponse: _onNotificationTapped,
      );

      _initialized = initialized ?? false;
      debugPrint('✅ NOTIFICATION: Service initialized: $_initialized');
      return _initialized;
    } catch (e) {
      debugPrint('Failed to initialize notifications: $e');
      return false;
    }
  }

  /// Starte Ride-Monitoring mit Supabase Realtime
  void startRideMonitoring(String userId) {
    debugPrint('🚀 NOTIFICATION SERVICE: Starting ride monitoring for user: $userId');
    
    // Cleanup alte Subscription
    _rideSubscription?.unsubscribe();

    // Neue Subscription für Ride-Updates
    _rideSubscription = _supabase
        .channel('ride_updates_$userId')
        .onPostgresChanges(
          event: PostgresChangeEvent.update,
          schema: 'public',
          table: 'rides',
          filter: PostgresChangeFilter(
            type: PostgresChangeFilterType.eq,
            column: 'customer_id',
            value: userId,
          ),
          callback: (payload) => _handleRideUpdate(payload),
        )
        .subscribe();

    debugPrint('✅ NOTIFICATION SERVICE: Listening for updates on channel: ride_updates_$userId');
  }

  /// Handle Ride Updates von Supabase Realtime
  void _handleRideUpdate(PostgresChangePayload payload) {
    debugPrint('📬 NOTIFICATION: Ride update received!');
    
    final oldRecord = payload.oldRecord;
    final newRecord = payload.newRecord;

    if (oldRecord == null || newRecord == null) {
      debugPrint('❌ NOTIFICATION: Missing record data');
      return;
    }

    final oldStatus = oldRecord['status'] as String?;
    final newStatus = newRecord['status'] as String?;

    debugPrint('📊 NOTIFICATION: Status changed from $oldStatus to $newStatus');

    // Status hat sich geändert -> Notification zeigen!
    if (oldStatus != newStatus) {
      debugPrint('✅ NOTIFICATION: Showing notification for status: $newStatus');
      _showRideStatusNotification(newStatus);
    }
  }

  /// Zeige Notification bei Status-Änderung
  Future<void> _showRideStatusNotification(String? status) async {
    debugPrint('🔔 NOTIFICATION: Preparing notification for status: $status');
    
    String title = 'Fahrt-Update';
    String body = '';

    switch (status?.toLowerCase()) {
      case 'assigned':
        title = '🚕 Fahrer zugewiesen!';
        body = 'Ein Fahrer wurde Ihrer Fahrt zugewiesen';
        break;
      case 'in_progress':
      case 'inprogress':
      case 'unterwegs':
        title = '🚗 Fahrt gestartet!';
        body = 'Die Fahrt hat gestartet';
        break;
      case 'completed':
        title = '✅ Fahrt abgeschlossen';
        body = 'Ihre Fahrt wurde erfolgreich abgeschlossen';
        break;
      default:
        debugPrint('⚠️ NOTIFICATION: Unknown status, skipping: $status');
        return;
    }

    debugPrint('📤 NOTIFICATION: Showing - Title: $title, Body: $body');
    await showNotification(
      title: title,
      body: body,
      payload: 'ride_update',
    );
  }

  /// Zeige allgemeine Notification mit Sound und Vibration
  Future<void> showNotification({
    required String title,
    required String body,
    String? payload,
  }) async {
    const androidDetails = AndroidNotificationDetails(
      'taxi_app_channel',
      'Fahrt-Updates',
      channelDescription: 'Benachrichtigungen über Ihre Fahrten',
      importance: Importance.high,
      priority: Priority.high,
      showWhen: true,
      enableVibration: true,
      playSound: true,
    );

    const iosDetails = DarwinNotificationDetails(
      presentAlert: true,
      presentBadge: true,
      presentSound: true,
    );

    const details = NotificationDetails(
      android: androidDetails,
      iOS: iosDetails,
    );

    await _localNotifications.show(
      DateTime.now().millisecond,
      title,
      body,
      details,
      payload: payload,
    );
  }

  /// Callback wenn User auf Notification tippt
  void _onNotificationTapped(NotificationResponse response) {
    debugPrint('Notification tapped: ${response.payload}');
    final payload = response.payload;

    if (payload == 'ride_update') {
      AppNavigator.navigateTo('/main');
    }
  }

  /// Stoppe Monitoring
  void stopRideMonitoring() {
    _rideSubscription?.unsubscribe();
    _rideSubscription = null;
  }
}
```

#### Integration in den Anwendungsfluss

Der NotificationService wird in der `main.dart` beim App-Start initialisiert:

```dart
Future<void> main() async {
  WidgetsFlutterBinding.ensureInitialized();

  // Initialize Supabase
  await Supabase.initialize(
    url: AppConstants.supabaseUrl,
    anonKey: AppConstants.supabaseAnonKey,
  );

  // Initialize Notification Service
  await NotificationService().initialize();

  runApp(TaxiApp(themeProvider: themeProvider));
}
```

Nach einer erfolgreichen Authentifizierung wird das Fahrt-Monitoring automatisch gestartet. Dies geschieht in der `AuthGate`:

```
class _AuthGateState extends State<AuthGate> {
  @override
  Widget build(BuildContext context) {
    return StreamBuilder<AuthState>(
      stream: Supabase.instance.client.auth.onAuthStateChange,
      builder: (context, snapshot) {
        final session = snapshot.data?.session;

        if (session != null) {
          // Starte Monitoring für diese Benutzer-Session
          final userId = session.user?.id;
          if (userId != null) {
            NotificationService().startRideMonitoring(userId);
          }
          return const MainScreen();
        }

        // User ist nicht angemeldet - stoppe Monitoring
        NotificationService().stopRideMonitoring();
        return const LoginPage();
      },
    );
  }
}
```

#### Supabase Realtime Integration

Die Benachrichtigungen werden über **Supabase Realtime** ausgelöst, wenn sich der Fahrt-Status ändert:

- **old_status != new_status** → Notification wird angezeigt
- **Nur UPDATE-Events** werden monitored (INSERT/DELETE werden ignoriert)
- **Kanäle**: `ride_updates_${userId}` für benutzer-spezifisches Monitoring
- **Filter**: `customer_id = ${userId}` auf Datenbank-Ebene

#### Benutzerfreundlichkeit

Die Benachrichtigungen werden mit benutzerfreundlichen Emojis und Meldungen dargestellt:

- **🚕 Fahrer zugewiesen**: "Ein Fahrer wurde Ihrer Fahrt zugewiesen"
- **🚗 Fahrt gestartet**: "Die Fahrt hat gestartet"
- **✅ Fahrt abgeschlossen**: "Ihre Fahrt wurde erfolgreich abgeschlossen"

Tipp auf eine Notification navigiert automatisch zur Activity-Seite (`/main`), um die Fahrtdetails zu sehen. Sound und Vibration sind für beide Plattformen aktiviert.

### Testen und Debugging der Anwendung

Zur Qualitätssicherung wurden verschiedene Testformen durchgeführt. Das Testen ist ein essenzieller Bestandteil der Softwareentwicklung und trägt wesentlich zur Zuverlässigkeit und Qualität der Anwendung bei. [@flutter_docs]

#### Manuelle Tests

**Funktionales Testen**: Die wichtigsten Funktionen der Anwendung wurden manuell auf verschiedenen Emulatoren und realen Endgeräten getestet, um sicherzustellen, dass sie wie erwartet funktionieren:

- Tests der Authentifizierung (Registrierung, Login, Logout, Passwort zurücksetzen)  
- Tests der Standortfunktionen (mit und ohne Berechtigung, GPS an/aus)  
- Tests der Backend-Anbindung (Erstellen, Laden und Aktualisieren von Fahrten)  
- Tests der Kartendarstellung und Navigation  
- Tests der PDF-Erstellung und Druckfunktion  
- Tests des Zahlungssystems mit verschiedenen Szenarien (erfolgreiche Zahlung, Fehlerfall, Timeout)  
- Tests der Benachrichtigungsfunktion bei Fahrt-Status-Änderungen

**Gerätespezifische Tests**: Die App wurde auf verschiedenen Android-Versionen (API 21+) und Bildschirmgrößen getestet, um Kompatibilität und Responsive Design sicherzustellen.

#### Strukturiertes Debugging mit `debugPrint()`

Statt umfassender Unit-Tests wurde während der Entwicklung ein strukturiertes Debugging-System mit `debugPrint()` implementiert. Dies ermöglichte schnelle Fehleridentifikation und Nachverfolgung des Programmablaufs:

**Beispiele aus der Implementierung:**

```dart
// LocationService
debugPrint('📍 LocationService: Requesting location permission');
debugPrint('✅ Location obtained: ${position.latitude}, ${position.longitude}');

// RoutingService
debugPrint('🗺️ Calculating route from $from to $to');
debugPrint('✅ Route calculated: ${route.distanceKilometers} km, ${route.durationMinutes} min');

// SumUpService
debugPrint('💳 SumUp: Starting card payment for €$amount');
debugPrint('✅ SumUp Checkout Created: $transactionId');
debugPrint('🎓 DEMO MODE: Simulating successful payment for thesis');

// NotificationService
debugPrint('🚀 NOTIFICATION SERVICE: Starting ride monitoring for user: $userId');
debugPrint('📬 NOTIFICATION: Ride update received!');
debugPrint('✅ NOTIFICATION: Showing notification for status: $newStatus');

// PaymentForm
debugPrint('💾 Saving payment to database: status=$_status, amount=$amount');
debugPrint('✅ Payment saved successfully to database');
```

Diese strukturierte Fehlerbehandlung mit Emojis und aussagekräftigen Meldungen half bei der schnellen Lokalisierung von Problemen während der Entwicklung.

#### Automatisierte Tests

Ein grundlegender Widget-Test wurde als Platzhalter implementiert:

```dart
void main() {
  testWidgets('App renders splash screen', (WidgetTester tester) async {
    // Placeholder test - app requires Supabase initialization and auth
    // In a real test, you would mock Supabase and test individual widgets
    expect(true, true);
  });
}
```

**Hinweis**: Für vollständige Unit- und Integration-Tests wären folgende Schritte nötig:
- Mock-Implementierungen von Supabase, LocationService, RoutingService
- Fixture-Daten für Test-Szenarien
- Tests für jeden Service separat
- Integration-Tests für komplexe Workflows (z.B. Login → Booking → Payment)

Dies wurde auf Grund des Umfangs der Diplomarbeit priorisiert, sodass der Fokus auf der Implementierung der Kernfunktionalität lag.

#### Debugging-Techniken

Während der Entwicklung wurden die Debugging-Funktionalitäten von Flutter intensiv genutzt:

- **Hot Reload und Hot Restart**: Ermöglichten schnelles Testen von Codeänderungen ohne vollständigen App-Neustart
- **Breakpoints in Android Studio/VS Code**: Zur Analyse des Programmablaufs und Überprüfung von Variablenwerten während der Entwicklung
- **DevTools**: Zur Analyse der Widget-Hierarchie und Performance-Profiling
- **Strukturiertes `debugPrint()`**: Mit Emojis und aussagekräftigen Meldungen zur Verfolgung des Programmablaufs in allen Services

**Behobene Fehler während der Entwicklung:**

- Fehlerhafte Navigation bei abgelaufener Session (AuthGate StreamBuilder-Logik)
- Unvollständige Validierungen in Formularen (ValidationHelper-Integration)
- Falsche Behandlung von `null`-Werten in optionalen Feldern (Ride-Model)
- Race Conditions bei parallelen asynchronen Operationen (LocationService mit Streams)
- Fehlerhafte Realtime-Subscriptions bei mehrfachem Aufrufen (NotificationService Cleanup)
- Timeout-Probleme bei Location-Requests (AppConstants.locationTimeout)

Durch kontinuierliches Debugging während der Implementierung konnte verhindert werden, dass sich Fehler über längere Zeit im Code ansammeln.

### Datenschutz und DSGVO-Conformance

Die Kundenapplikation verarbeitet sensible personenbezogene Daten wie E-Mail-Adressen, Standortdaten und Fahrtinformationen. Eine korrekte Behandlung dieser Daten ist nicht nur ethisch notwendig, sondern auch gesetzlich vorgeschrieben. [@DSGVO]

#### Datenverschlüsselung

**Transport-Layer Security (TLS/HTTPS)**: Alle Kommunikation zwischen App und Backend erfolgt über verschlüsselte HTTPS-Verbindungen. Dies gilt insbesondere für:

- Authentifizierungsdaten (Passwörter, Session-Tokens)
- Standortdaten während der Übertragung
- Zahlungsdaten bei der Kommunikation mit SumUp

**Datenbank-Verschlüsselung**: Supabase verschlüsselt Daten standardmäßig on-disk. Zusätzlich können sensitive Felder (wie Passwort-Hashes) durch spezielle Datenbankfunktionen geschützt werden.

#### Datenspeicherung

**Lokale Speicherung**: Sensible Daten wie Authentifizierungs-Token werden lokal mit `shared_preferences` gespeichert. Diese sollten in Produktionsumgebungen mit zusätzlicher Verschlüsselung (z.B. `flutter_secure_storage`) geschützt werden.

**Session-Management**: Session-Tokens haben eine begrenzte Gültigkeitsdauer und werden regelmäßig refreshed. Abgelaufene Sessions werden automatisch invalidiert.

#### Zugriffskontrolle mit Row Level Security (RLS)

Wie im Kapitel „Authentifizierung & Sicherheit" beschrieben, wird RLS verwendet, um sicherzustellen, dass Benutzer nur auf ihre eigenen Daten zugreifen können:

```sql
-- Benutzer können nur ihre eigenen Fahrten sehen
create policy "users_can_view_own_rides"
on rides
for select
using (user_id = auth.uid());

-- Benutzer können nur ihre eigenen Profilinformationen ändern
create policy "users_can_update_own_profile"
on profiles
for update
using (id = auth.uid());
```

#### Datensicherung und Löschung

**Automatische Backups**: Supabase führt automatische Backups durch, die bei Datenverlust wiederhergestellt werden können.

**Recht auf Löschung**: Benutzer können ihr Konto löschen, woraufhin alle zugehörigen Daten (Profile, Fahrthistorie) entfernt werden können. Dies erfolgt durch Datenbank-Trigger:

```sql
-- Automatische Löschung zugehöriger Daten
create function delete_user_data()
returns trigger as $$
begin
  delete from rides where user_id = old.id;
  delete from profiles where id = old.id;
  return old;
end;
$$ language plpgsql;

create trigger on_auth_user_deleted
after delete on auth.users
for each row
execute function delete_user_data();
```

#### Benutzereinwilligung und Transparenz

- **Datenschutz-Erklärung**: Die App enthält eine Datenschutzerklärung, die erläutert, welche Daten erfasst werden und wie diese verwendet werden
- **Explizite Genehmigungen**: Für sensitive Funktionen wie Standortzugriff werden explizite Berechtigungen abgefragt
- **Transparente Datennutzung**: Benutzer wissen zu jeder Zeit, wann und warum ihre Daten verwendet werden

#### Compliance-Überprüfung

Die Implementierung wurde überprüft auf:

- Einhaltung der DSGVO-Anforderungen
- Korrekte Implementierung von Authentifizierung und Autorisierung
- Sichere Behandlung von Standortdaten
- Sichere Zahlungsverarbeitung
