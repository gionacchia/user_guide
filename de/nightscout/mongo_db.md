
# Einrichten der Mongo-Datenbank



Die [Mongo DB Datenbank](https://de.wikipedia.org/wiki/MongoDB) ist eine Dokumentations - Datenbank. Hier werden die Daten der Nightscout Website gespeichert. Es handelt sich um eine Cloud - Datenbank in Rechenzentren der USA und Europa. 
Mongo DB gibt es als **kostenlose** Sandbox - Variante.

Bevor wir mit der Konfiguration loslegen, ist es wichtig, das [Arbeitsblatt](../nightscout/datenblatt.md) auszudrucken
und auszufüllen.


Es ist für weitere Konfigurationen wichtig, dieses Datenblatt sicher aufzubewahren.

Die URL Adresse zum Start gibt es hier: https://mlab.com

Wir starten mit der Einrichtung der Benutzer - Konten auf der mlab - Startseite:


**SIGN UP:**
![mongodb signin up](../images/mongodb/mlab_sign_up.jpg)

Weiter gehts mit dem **Anlegen** der benötigten **Konten:** zur Verwaltung

![mongo db create account](../images/mongodb/mongo_db_create_account.jpg)

**Passwörter**

Der Einfachheit halber kann man denselben Benutzernamen (Account name) für die Verwaltung von mongolab als auch für den Datenbanknutzer (Username) nutzen, muss es aber nicht. Hauptsache: **Alles notieren**. Auch sind eigene Passwörter nur für mlab und Nightscout sinnvoll, es sollten auf keinen Fall bereits bekannte Passwörter, welche man für andere Anlässe wie Online-Banking nutzt, verwendet werden.

**Überprüfung Email:**
![verifyemail](../images/mongodb/verifyemail.jpg)

Nachdem der Benutzer - Account eingerichtet wurde, bitte einmal im Postfach der angegebenen Email - Adresse die Bestätigungs - Email suchen. Durch Klick auf den Link wird man auf die Seite zur Einrichtung einer Datenbank geleitet.

**Anlegen einer Datenbank:**

Wir starten mit dem Klick auf "Create New":

![create_db](../images/mongodb/create_db.jpg)

Alle gelb markierten Punkte sind auszufüllen, der Datenbankname ist frei wählbar:

![mongodb_details](../images/mongodb/mongodb_details.jpg)


Wichtig ist er Eintrag FREE, damit wird die Datenbank kostenlos betrieben.
Nachdem der Button **Create new MongoDB deployment** geklickt wurde, erscheint eine Erfolgsmeldung:

![mongodb_create_success](../images/mongodb/mongodb_create_success.jpg)

Durch Doppelklick auf den Namen, hier: **ds040888/nscgmdatabase** fügt man u.a. den Datenbankbenutzer ein. Das ist derjenige, welcher in Azure oder xdrip konfiguriert wird,
um auf die mongodb zuzugreifen:

**Datenbankbenutzer hinzufügen:**

![mongodb_create_dbuser](../images/mongodb/mongodb_createdbuser.jpg)

..und die vorher notierten Daten eingeben:


![mongodb_dbuser_details](../images/mongodb/mongodb_dbuser_details.jpg)


**Hinzufügen einer "Collection":**

Unter Collections auf "add collection" gehen, einen Namen wie z.B. "entries" eintragen und auf "create" tippen. Dieser Name wird später bei azure unter Anwendungseinstellungen als mongo collection eingefügt.

**WICHTIG:**

Am Ende bitte unbedingt die MongoDB [URI](https://de.wikipedia.org/wiki/Uniform_Resource_Identifier) notieren..Diese wird benötigt, um auf die Daten über das Internet zugreifen zu können.

**Die URI Syntax:**

Zum besseren Verständnis ausführlich erklärt:

**mongodb://dbuser:dbpassword@ds040888.mlab.com:40888/nscgmdatabase**

**dbuser:** ist der vorher eingerichtete Datenbankbenutzer

**dbpassword:** ist das eingerichtete Passwort für den Datenbankbenutzer

**@:** ist ein Verbindungszeichen, muss angegeben werden

**ds040888.mlab.com:** ist ein einzigartiger Name, über den die mongodb angesprochen wird

**:** ist ein Verbindungszeichen, muss angegeben werden

**40888:** ist ein sogenannter [Kommunikationsport](https://de.wikipedia.org/wiki/Port_%28Protokoll%29), der für den Zugriff benötigt wird

**nscgmdatabase:** Name der mongodb

Diese Daten bitte unbedingt im Datenblatt notieren. Bei evtl. Verbindungsproblemen ist eine der häufigsten Ursachen ein falsche URI, es kommt hier auf Details, auf jedes Zeichen an!

Es gibt **optionale** Komponenten zum Management der MongoDB im nächsten Kapitel, diese sind nicht Bestandteil der Implementierung.

Ansonsten geht es jetzt weiter mit der Einrichtung von [GitHub](../nightscout/github.md)
