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

Das folgende Codebeispiel zeigt die Formatierung eines Geldbetrags im österreichischen Zahlenformat. [@intl] [@flutter_docs]

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

#### Datenmodelle & Mapping (JSON $\leftrightarrow$ Dart)
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

\newpage

## Praktische Arbeit















