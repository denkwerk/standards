# Standards Flash Parameter

Grundsätzlich werden Flash-Dateien mit Hilfe von SWFObject in eine HTML-Seite eingebunden. Dabei wird ein bestimmtes HTML-Element durch die Flash-Datei in Form eines Object-Tags crossbrowserkonform ersetzt.

SWF-Object Webseite: 
[http://code.google.com/p/swfobject/](http://code.google.com/p/swfobject/)

SWF-Object Dokumentation: 
[http://code.google.com/p/swfobject/wiki/documentation](http://code.google.com/p/swfobject/wiki/documentation)


**Ein Beispiel mit gesetzten Standard-Parametern:**

	<script type="text/javascript">
		var flashvars = {};
		flashvars.captchaUrl = escape("<Link zum Captcha-Script>");
		flashvars.formUrl = escape("<Link zum Formular-Script>");
		flashvars.tafUrl = escape("<Link zum Tell-a-Friend-Script>");
		flashvars.ibeUrl = escape("<Link zum IBE-Pfad>");
			
		var params = {};
		params.quality = "best";
		params.allowScriptAccess = "always";
		params.bgcolor = "#FFFFFF";
		params.menu = "false";
		params.allowfullscreen = "true";	

		var attributes = {};
		attributes.id = "condor_nacho_day";
			
		swfobject.embedSWF(
			"assets/swf/nacho_day_loader.swf", 
			"flashContent", "958", "836", "10.3", 
			"assets/swf/expressInstall.swf", 
			flashvars, params, attributes
		);
	</script>


**Was diese Angaben bedeuten:**

*flashvars:*

* Flashvars sind die projektspezifischen Parameter, die an das Flash übergeben werden.
* Standard ist es, diese Variablen in camelCase zu schreiben.
* Sie sollten möglichst knapp beschrieben werden (abgekürzt). Ordner- und Dateipfade enden immer mit dem Zusatz „Url”.
* Werte der Parameter müssen escaped werden, damit Sonderzeichen (z.B. „&“) in Scriptpfaden bei der Einbindung nicht interpretiert werden.

*params:*

* Params sind vordefinierte Einbettungs-Parameter.
* Hier ist Standard, dass man auf den wmode generell verzichtet.
=> In Sonderfällen muss dies mit dem zuständigen Flasher abgestimmt werden.
* Weitere Standard-Einstellungen sind:
	* `params.quality = "best";`
	* `params.allowScriptAccess = "always";`
	* `params.menu = "false";`
	* `params.allowfullscreen = "true";`

*attributes:*

* Diese Parameter sind die Attribute des HTLM-Objekts. Standardmäßig wird eine ID übergeben damit man z. B. per JS das eingebundene Flash-Objekt ansprechen kann.

*embedSWF:*

* Mit dieser Funktion von swfobject wird das Flash in das HTML-DOM eingebunden.
* Standard ist es die expressInstall.swf zu benutzen. Diese SWF muss immer mitgegeben werden. Dadurch wird dem User mit veraltetem Flash-Player eine einfache Möglichkeit gegeben, diesen zu aktualisieren.   

---

### Übergabe aus dem Flash Standard-Formular und dem Taf-Formular (Tell-a-Friend-Formular) an das Backend :   
   
Grundlegende Angaben zum Standard-Formular und TaF-Formular:
* Die Bezeichner sind immer englischsprachig
* Das Flash erwartet ein XML zurück

Parameternamen die aus dem Flash Standard-Formular an das Backend übergeben werden:
* `salutation` = Anrede;
* `firstname` = Vorname
* `lastname` = Nachname
* `street` = Straße
* `zip` = Postleitzahl
* `city` = Stadt
* `email` = E-Mail
* `emailrepeat` = E-Mail wiederholen
* `country` = Land
* `newsletter` = Newsletterbestellung ( Möglich: „“, „html“ oder „text“ )
* `termsandconditions` = Teilnahmebedingungen ( 1 oder 0)

Werte die aus dem Flash TaF-Formular an das Backend übergeben werden:
* `receiverEmail1` = E-Mail Empfänger 1
* `receiverEmail2` = E-Mail Empfänger 2
* `receiverEmail3` = E-Mail Empfänger 3
* `senderName` = Enthält den Vorname und den Nachnamen aus dem Standard-Formular
* `senderEmail` = Enthält die E-Mail aus dem Standard-Formular
