# denkwerk JavaScript Standards

## Inhaltsverzeichnis

 * [Whitespace](#whitespace)
 * [Schöne Syntax](#spacing)
 * [Praktischer Style](#practical)
 * [Bezeichnungen](#naming)
 * [Kommentare](#comments)

------------------------------------------------

## Style Manifest


1. <a name="whitespace">Whitespace</a>
    - Mische niemals Spaces und Tabs
    - Indention Regeln im denkwerk sind
        - 4 Spaces für frontend JavaScript Projekte
        - 2 Spaces für backend JavaScript Projekte

    - Eure Editoren/IDEs sollten so konfiguriert werden, das sie folgende Guides automatisch umsetzen:
        - Löschen von Whitespaces am Ende der Zeile
        - Löschen von leeren "Whitespace Zeilen"
        - Löschen von Leerzeilen am Ende von Dateien

Dadurch werden diffs & commits lesbarer & wir matchen die std. einstellungen
von jshint & jslint


2. <a name="spacing">Ästehtische Syntax</a>

    <b>A. Leerzeichen, geschweifte Klammern und Zeilenumbrüche</b>

    if/else/for/while/try enthalten immer geschweifte Klammern
    und erstrecken sich über mehrere Zeilen.
    Das trägt zur Lesbarkeit bei

    <b>FALSCH</b>

    ```
    if(Bedingung) machWas();

    while(Bedingung) iterieren++;

    for(var i=0;i<100;i++) irgendeineIterativeFunktion();
    ```

    <b>RICHTIG</b>

    ```
    if (Bedingung) {
        // statements
    }

    while (Bedingung) {
        // statements
    }

    for (var i = 0; i < 100; i++) {
        // statements
    }

    if (true) {
        // statements
    } else {
        // statements
    }
    ```


    <b>B. Zuweisungen, Deklarationen, Funktionen (Benamte, Ausdrücke, Kontruktoren)</b>

	<i><u>Variablen:</u></i>

    ```
    var foo = 'bar',
        num = 1,
        undef;
    ```

    <i><u>Literalnotationen:</u></i>

	```
    var array = [],
        object = {};
	```

    <i><u>Variablen werden deklariert wenn sie benötigt werden</u></i>

	<b>Falsch</b>

	```
    var foo = '';
    var bar = '';
    var qux;

    // statements
    qux = null;
    var foobar = 'smthdifferent';
	```

	<b>Richtig</b>

	```
    var foo = '',
        bar = '',
        foobar = 'smthdifferent',
        qux;
	```

	<b>Noch besser</b>

	```
    var foo = '',
        bar = '';

    // staments
    var qux = null;
	```


    <i><u>var block statements sollten immer an den Anfang ihrers respektiven Scopes (Funktion)
    Das gleiche gilt für const und let aus ECMAScript 6</i></u>

	<b>Falsch</b>

	```
    function foo() {
        // irgendwas

        var bar = '',
            qux;
    }

	```

	<b>Richtig</b>

	```
    function foo() {
        var bar = '';
        const MY_CONST = 1;
        let whatever = aWhateverReturner();

        // alle Statements nach der var-Deklaration
    }
    ```


    <i><u>Benannte Funktionsdeklaration (Named function)</u></i>

    ```
    function foo(arg1, argN) {}

    foo(arg1, argN);

    function quadrat(zahl) {
        return zahl * zahl;
    }

   	quadrat( 10 );

    function quadratCb(zahl, callback) {
        callback(zahl * zahl);
    }

    quadratCb( 10, function (square) {
        // callback Statements
    });
    ```

    <i><u>Funktionsausdruck (Function expression)</u></i>


    ```
    var quadrat = function (zahl) {
        // gibt irgendwas zurück
        return zahl * zahl;
    }
    ```

    <i><u>Funktionsausdruck mit bezeichner (Named function expression)</u></i>
    <p>Diese Form hat den Vorteil, das sie sich selbst aufrufen kann
    und der Bezeichner im Stack Trace zufinden ist</p>


    ```
    var factorial = function factorial(zahl) {
        if ( zahl < 2 ) {
            return 1;
        }

        return zahl * factorial(zahl-1);
    };
    ```

    <i><u>Konstruktor deklaration</u></i>


    ```
    function FooBar (options) {
        this.options = options;
    }

    var fooBar = new FooBar({a: 'alpha'});
    console.log(fooBar.options); // {a: 'alpha'}
    ```

    <i><u>Callback argumente</u></i>

    ```
    foo(function() {
    	// callbackish statements
    });

    ```
	<i><u>Allgemeines zu Funktionen</u></i>
	
	<p>Scope möglichst auf 10 Zeilen beschränken</p>
	<p>Nicht mehr als 80 Zeichen pro Zeile</p>
	<p>Tiefe Verschachtelungen vermeiden</p>
	
	
    <b>C. Anführungszeichen</b><br />
	<p>Im Gegensatz zu anderen Programmiersprachen gibt es bei JavaScript keine
	unterschiedung zwischen doppelten und einfach Anführungszeichen.
	Wir benutzen in unseren Projekten immer einfache Anführungszeichen</p>

	<b>Falsch</b>

    ```
 	var foo = "A string";

    ```

	<b>Richtig</b>

    ```
 	var foo = 'A string';

    ```

3. <a name="naming">Bezeichnungen</a>

    Du bist kein Compiler, also versuch nicht einer zu sein.

    Der folgende Code ist ein Beispiel für entsetzlich schlechte Bezeichnungen:

	<b>Falsch</b>

    ```
    function q(s) {
      return document.querySelectorAll(s);
    }
    var i,a=[],els=q("#foo");
    for(i=0;i<els.length;i++){a.push(els[i]);}
    ```

    Hier ist der gleiche Code, nur klarer, durchdachter und mit einer lesbaren Struktur:

	<b>Richtig</b>

    ```
    function query( selector ) {
      return document.querySelectorAll( selector );
    }

    var idx = 0,
        elements = [],
        matches = query("#foo"),
        length = matches.length;

    for(idx; idx < length; idx++){
        elements.push(matches[idx]);
    }

    ```

    <b><i>Ein paar weitere Punkte bezüglich der Bezeichnungen:</b></i>

	<p>Strings</p>

    ```
    `dog` ist ein String
	```

    <p>Arrays</p>

	```
    `dogs` ist ein Array bestehend aus `dog` Strings
	```

    <p>Funktionen, Objekte, Instanzen etc.</p>

	```
    camelCase; Funktions- und var- Deklarationen
	```

    <p>Konstruktoren und Prototypen</p>

	```
    PascalCase; Konstruktorfunktion
	```


    <p>Reguläre Ausdrücke</p>

	```
    rDesc = //;
	```

    <p>Sonstiges</p>

	```
    functionNamesLikeThis;
    variableNamesLikeThis;
    ConstructorNamesLikeThis;
    EnumNamesLikeThis;
    methodNamesLikeThis;
    SYMBOLIC_CONSTANTS_LIKE_THIS;
    ```

4. <a name="comments">Kommentare</a>


5. <a name="misc">Sonstiges</a>

## Testing Frameworks

 * [QUnit](http://github.com/jquery/qunit)
 * [Jasmine](https://github.com/pivotal/jasmine)
 * [Vows](https://github.com/cloudhead/vows)
 * [Mocha](https://github.com/visionmedia/mocha)
 * [Hiro](http://hirojs.com/)
 * [JsTestDriver](https://code.google.com/p/js-test-driver/)
 * [Buster.js](http://busterjs.org/)

Denkwerk standard zur Erstellung von JavaScript Unit Tests ist <b>QUnit</b>.

## Code Quality Tools

 * [JavaScript Plugin](http://docs.codehaus.org/display/SONAR/JavaScript+Plugin) for [Sonar](http://www.sonarsource.org/)
 * [jsPerf](http://jsperf.com/)
 * [jsFiddle](http://jsfiddle.net/)
 * [jsbin](http://jsbin.com/)
 * [JavaScript Lint (JSL)](http://javascriptlint.com/)
 * [jshint](http://jshint.com/)
 * [jslint](http://jslint.org/)

[Leveraging Code Quality Tools by Anton Kovalyov](http://anton.kovalyov.net/slides/gothamjs/)

### JSHint-Konfiguration auf CI-Server
Stand: 15.05.2013, version 1.3
```
{
                 "bitwise"       : true,
                 "browser"       : true,
                 "camelcase"     : true,
                 "curly"         : true,
                 "devel"         : true,
                 "eqeqeq"        : true,
                 "immed"         : true,
                 "jquery"        : true,
                 "maxcomplexity" : 8,
                 "maxdepth"      : 3,
                 "maxlen"        : 160,
                 "maxparams"     : 5,
                 "maxstatements" : 20,
                 "newcap"        : true,
                 "undef"         : true,
                 "unused"        : true,
                 "noarg"         : true,
                 "nonew"         : true,
                 "quotmark"      : "single",
                 "trailing"      : true,
                 "white"         : false,
                 "predef"        : ["_"]
 }
```              

