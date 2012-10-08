# PHP Code Convention
Dieses Dokument legt Regeln f�r die Formatierung von PHP Code fest. Falls die Einhaltung einer Regel nicht m�glich ist, muss dies begr�ndet werden.

## Dateiformatierung
### Allgemein
Eine PHP Datei muss UTF-8 kodiert sein und folgt dem Unix-Style.

Die Wahl der Sprache f�r die Vergabe von Dokumentennamen und bei der Programmierung (Namen von Klassen, Variablen, �) ist stets Englisch. Lediglich Kommentare d�rfen in Deutsch formuliert werden. Der Dateiname ist anhand seiner Funktion zu benennen. Z.B. user.class.php

### Einr�cken
Ein Einzug besteht aus 4 Leerzeichen. Der Tabulator kann �blicherweise in jeder IDE (z.B. Netbeans) konfiguriert werden.

## Code Stil und Namensgebung
### Schl�sselw�rter
Schl�sselw�rter (`class, for, if, else,  �`) werden stets kleingeschrieben, weitere Schl�sselw�rter sind unter <http://php.net/manual/de/reserved.keywords.php> zu finden.

### Typsichere Pr�fung
Bei Vergleichsoperatoren ist nach M�glichkeit die typischere Variante zu w�hlen 
(z.B. === statt ==).

Des Weiteren sollte vor der Nutzung einer Variablen gepr�ft werden, ob sie den erwarteten Datentypen hat. Hierf�r liefert PHP einige Methoden wie `is_int()`, siehe <http://de3.php.net/manual/de/ref.var.php>.

Dar�ber hinaus wird empfohlen sogenannte `Type Hints` zu verwenden, welche es Funktionssignaturen erm�glichen den Typ erwarteter Objekte festzulegen.

```php
function typeHint($skalarVar, array $arr, AnyClass $obj) {
    �
}

oder
$int = (int) $_GET['id'];
oder
$int = max(0, intval($_GET['id']));
```

### PHP Code Abgrenzung
Wird PHP Code in anderen Sprachen eingebettet (z.B. HTML), dann muss der PHP Block mit der kompletten Form des Standard-PHP Tags umgeben sein:

```php
<?php 
    � 
?>
// html code
```

Das kurze Tag `<?` ist nicht gestattet. Wenn eine Datei mit PHP Code endet, wird das schlie�ende Tag nicht angegeben.

### Strings
#### String Literale
Wenn ein String keine Variablen enth�lt, ist das einfache Anf�hrungszeichen zu verwenden.

```php
$string = 'I am a string';
```

#### String Literale die ein einfaches Anf�hrungszeichen enthalten
Falls ein String einfache Anf�hrungszeichen enth�lt, ist es gestattet den String mit doppelten Anf�hrungszeichen abzugrenzen. Das ist insbesondere f�r SQL Anweisungen hilfreich.

```php
$sql = "SELECT 'column' from 'table'";
```

#### String enth�lt Variablen
Ein String, der Variablen enth�lt, muss diese mit dem Concat-Operator (`.`) trennen. Dabei steht jeweils ein Leerzeichen vor und nach dem Concat-Operator

```php
$string = 'Content of the variable: ' . $variable;
```

#### Variablen
Variablennamen bestehen aus den Zeichen a-z, A-Z und 0-9. Sie folgen der `lowerCamelCase` Schreibweise. Bei der Vergabe von Namen f�r eine Variable soll ersichtlich werden, welche Daten der Entwickler in ihr speichern m�chte.

```php
$variableName;
```

Eine Z�hlvariable hei�t �blicherweise `$i`. Bei der Verschachtelung von Z�hlvariablen ist die Namensgebung fortlaufend (`$i, $j, �`).

```php
for ($i = 0; $i < $n; $i++) {
    for ($j = 0; $j < $n; $j++) {
        �
    }
}
```

Vor dem Zugriff auf eine eventuell nicht vorhandene Variable muss diese mit `isset()` auf Existenz gepr�ft werden. 

### Konstanten
Konstanten folgen der `UPPERCASE` Schreibweise. Mehrere W�rter werden durch einen Unterstrich miteinander verbunden.

```php
CONSTANT_NAME
```

### Arrays
Vor dem Zugriff auf ein eventuell nicht vorhandenes Element eines Arrays sollte dies mit `array_key_exists()` auf seine Existenz gepr�ft werden.

Wenn die Definition eines Arrays sehr lang ist, bietet es sich an das Array umzubrechen. Dabei beginnt das erste Element in einer neuen Zeile um einen Einr�ckungslevel einger�ckt. Alle folgenden Zeilen haben denselben Einr�ckungslevel. Der schlie�ende Teil steht in einer neuen Zeile auf demselben Einr�ckungslevel wie die Array Deklaration.

Nummerisch indizierte Arrays

```php
$sampleArray = array(
    1, 2, 3, 'Zend', 'Studio',
    $a, $b, $c,
    56.44, $d, 500
);
```

Assoziative Arrays

```php
$sampleArray = array(
    'firstKey'  => 'firstValue',
    'secondKey' => 'secondValue'
);
```

### Funktionen, Klassen, Kontrollanweisungen, Methoden und Schleifen
Bei Funktionen, Klassen, Kontrollanweisungen (`if, switch`), Methoden und Schleifen (`for, while`) steht (in der Regel) die �ffnende geschweifte Klammer als letztes Zeichen in derselben Zeile mit dem Schl�sselwort (`function, class, �`). Vor der Klammer steht in diesem Fall immer ein Leerzeichen, siehe Beispiele in den folgenden Abschnitten.

### Klassen
Klassennamen bestehen aus den Zeichen a-z, A-Z und 0-9. Sie werden in `UpperCamelCase` geschrieben.

```php
class ClassName {
    // Content is indented by 4 spaces
}
```

Jede Klasse sollte einen Dokumentationsblock haben, der dem PHPDocumentor Standard entspricht. In jeder PHP-Datei darf nur eine Klasse definiert werden.

Klassenvariablen werden zu Beginn einer Klasse aufgelistet. Sie definieren Ihre Sichtbarkeit durch `private, protected` oder `public` Modifikatoren.

```php
/``
` Dokumentationsblock
`/
class ClassName extends FooAbstract {
    private $firstname;
    private $lastname;
    �
}
```

### Funktionen und Methoden
Funktionen stehen au�erhalb von Klassen und Methoden innerhalb von Klassen. Bis auf die Sichtbarkeit gelten alle Regeln f�r beide Arten.

Funktionsnamen bestehen aus den Zeichen a-z, A-Z und nur im Sonderfall aus 0-9. Sie folgen der `lowerCamelCase` Schreibweise. Der Name der Funktion ist so zu w�hlen, dass der Zweck und das Verhalten der Funktion aus diesem ableitbar sind. Weitere Anmerkungen sollten in einem Kommentar festgehalten werden.

```php
function doSomething() {
    �
}
```

Methoden innerhalb einer Klasse m�ssen ihre Sichtbarkeit durch `private, protected` oder `public` Modifikatoren definieren. 

Die Parameter werden durch Komma und mit einem Leerzeichen nach diesem getrennt. 

Der R�ckgabewert steht nicht in Klammern, da dies die Lesbarkeit des Codes beeinflussen kann.

Funktionen und Methoden sollten einen kurzen Dokumentationsblock haben, welcher die Funktion kurz beschreibt, sowie den Autor und die erwarteten Typen von Parametern und R�ckgabewerten festh�lt.

```php
class ClassName {
    /``
    ` Documentation block
    `/
    public function bar($arg1, $arg2, $arg3) {
        // content
        return $value;
    }
}
```

### Kontrollanweisungen
#### if/else/elseif
Innerhalb der bedingten Anweisung, d.h. in den runden Klammern, werden die Operationen durch Leerzeichen getrennt sowie Bedingungen geklammert, um die Lesbarkeit zu erh�hen.

```php
if ($a === $b && ($b === $c || $b === $e)) {
    $a = $d;
} elseif ($a !== $b) {
    $a = $c;
} else {
    $a = $b;
}
```

Die Kurzschreibweise ist gestattet, wenn diese leicht zu verstehen ist und m�ssen grunds�tzlich eingeklammert werden.

```php
$gender = (($isMale) ? 'male' : 'female');
```

#### Switch
Jeder Inhalt unter `switch` wird um vier Leerzeichen einger�ckt (`case, break` und `default`). Jeder Inhalt unter `case` und `default` wird um vier weitere Leerzeichen einger�ckt.

```php
switch ($num) {
    case 1:
        // do something
    break;
    default:
        // do something
    break;
}
```

### Inline Dokumentation
Alle Dokumentationsbl�cke m�ssen mit dem phpDocumentor Format kompatibel sein (siehe <http://phpdoc.org/>). Dateien, Klassen und Funktionen sollten kommentiert werden.

## Abweichungen f�r Templates
### Alternative Syntax f�r Kontrollstrukturen  
Zur Verbesserung der Lesbarkeit verwenden wir, sobald es zur Vermischung von PHP und HTML kommt, die alternative Schreibweise von Kontrollstrukturen. Dies sollte in inline-Schreibweise erfolgen (<http://www.php.net/manual/de/control-structures.alternative-syntax.php>). 

```php
<ul>

<?php foreach ($elements as $element): ?>

    <li><?= $element ?></li>

<?php endforeach; ?>

</ul>
```

### Zuweisungen in PHP
Enth�lt ein PHP-Block allerdings Zuweisungen, so sollten die PHP-Tags von Diesen in Form von Zeilenumbr�chen getrennt werden.

```php
<?php
    $foo = $bar % 2;
?>
```

### Kurzschreibweise PHP Tags
In Templates ist die Nutzung in Form von `Short-Echo-Tags` erlaubt. Bis PHP 5.3 muss dazu die Option `short_open_tag` aktiviert sein. Ab PHP Version 5.4 steht dieses Tag immer zur Verf�gung (<http://php.net/manual/en/function.echo.php>).

```php
<?= $variable; ?>
```
