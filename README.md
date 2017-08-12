# #NRW17 Visualisierung

**Beschreibung**

*#NRW17 Visualisierung* ist eine Visualisierung der Ergebnisse der 26. österreichischen Nationalratswahl am 15. Oktober 2017. Ziel ist es, eine spannende und informative Aufbereitung der Informationen für sämtliche BesucherInnen anzubieten. Dabei handelt es sich um eine gemeinsam entwickelte Web-App, welche die Daten am Wahltag vom Bundesinnenministerium um 17 Uhr holt, in eine Datenbank speichert und mittels verschiedenen Visualisierungen online für alle online verfügbar macht.

![Offene Wahlen](https://github.com/OKFNat/offenewahlen-at/blob/master/images/logos/ow-at.png)

Die Visualisierung wird am 15. Oktober kurz nach 17:00 Uhr unter **[nrw17.offenewahlen.at](https://nrw17.offenewahlen.at)** online gehen.


*#NRW17 Visualisierung* ist ein Teil von dem Projekt [Offene Wahlen Österreich](https://offenwahlen.at), koordiniert vom Verein [Open Knowledge Österreich](https://okfn.at).


Wir möchten uns herzlich beim Bundesministerium für Inneres für den unkomplizierten Zugang zu den Ergebnissen am Wahltag bedanken! 

**Technisches**

Es handelt sich um eine [Django](https://www.djangoproject.com/)-App (Python Web-Framework) mit einer [PostgreSQL](https://www.postgresql.org/)-Datenbank, die auf [Heroku](https://heroku.com) läuft. Am Frontend wird [D3.js](https://d3js.org/) mit [jQuery](http://jquery.com/) und [Bootstrap](http://getbootstrap.com) verwendet. Es wird nur Open Source Software verwendet, und auch der selbst entwickelte Code steht unter der [MIT](https://opensource.org/licenses/MIT)-Lizenz frei zur verfügung.

**Das Repository**

In diesem GitHub-Repository wird gemeinsam der Code entwickelt, die Dokumentation verwaltet sowie das Projektmanagement via dem [Wiki](https://github.com/OKFNat/offenewahlen-nrw17/wiki), den [Milestones](https://github.com/OKFNat/offenewahlen-nrw17/milestones?direction=asc&sort=due_date&state=open) und dem [Board](https://github.com/OKFNat/offenewahlen-nrw17/milestones#boards?repos=96933110) abgewickelt.

**Ressourcen**

Über die folgenden Ressourcen findest du alle relevanten Informationen zu dem Projekt:
* [Wiki](https://github.com/OKFNat/offenewahlen-nrw17/wiki): Wiki von diesem Repository. Dient zur Verwaltung des Wissens und zur Dokumentation. Erster Anlaufpunkt, wenn man mehr über das Projekt erfahren möchte.
* [Milestones](https://github.com/OKFNat/offenewahlen-nrw17/milestones?direction=asc&sort=due_date&state=open): Hier werden die Projekt-Milestones verwaltet. Gute Übersicht zum Projektstand.
* [Board](https://github.com/OKFNat/offenewahlen-nrw17/milestones#boards?repos=96933110): Hier werden die Projekt-Aktivitäten mit Hilfe von Milesontes und Issues verwaltet. Hier sieht man, wer was bis wann macht und wie man sich einbringen kann.
* [OKFNat/offenewahlen-at](https://github.com/OKFNat/offenewahlen-at): Repository zum Projekt Offene Wahlen Österreich. Das dazugehörige [Wiki](https://github.com/OKFNat/offenewahlen-at/wiki) ist eine umfassende Sammlung von Wissen rund um Wahlen und Open Data - von Wahlforschung über Wahlrecht bis hin zu Visualisierungen und Tools.
* [OKFNat/offenewahlen-wikidata](https://github.com/OKFNat/offenewahlen-wikidata): Repository rund um Wahlen und Wikidata.
- [offenewahlen.at](http://offenewahlen.at/): Website des Projektes Offene Wahlen Österreich. Dort findest du Infos zu weiteren Aktivitäten.

## INSTALL

Die Django-App läuft auf MacOS, Win und Linux.

Um die App lokal auf deinem Rechner laufen zu lassen, benötigst du:
* Python 3 ([hier](https://www.python.org/downloads/))
* pip ([hier](https://pip.pypa.io/en/stable/), falls nötig)
* virtualenv ([hier](https://virtualenv.pypa.io/en/stable/) oder [hier](http://docs.python-guide.org/en/latest/dev/virtualenvs/))
* PostgreSQL ([hier](https://www.postgresql.org/))

Nach erfolgreicher Installation: Öffne deine Shell und gehe in den Ordner, in dem du die App haben möchtest. Dort musst du das GitHub-Repository hinein klonen.

```bash
git clone https://github.com/OKFNat/offenewahlen-nrw17.git
ls
```

Jetzt solltest du das runtergeladene Repository in deinem Ordner sehen. Geh jetzt in den Root-Ordner rein und erstelle das Virtual Environment.

```bash
cd offenewahlen-nrw17/
virtualenv venv
```

Das Virtual Environment kann nun aktiviert werden.

```bash
source venv/bin/activate
```

Nun kannst du in das Virtual Environment die benötigten Python Packages aus der `requirements.txt` Datei installieren. Der Vorteil: Die Packages werden dadurch nur im Virtual Environment installiert und nicht auf deinem Betriebssystem.

```bash
pip install -U -r requirements.txt
```

Die App ist an sich jetzt schon funktionsfähig, es muss aber noch die Datenbank initalisiert werden. Dazu in den `src/`-Ordner gehen, welcher der Root-Folder der Django-App ist.

```bash
python manage.py migrate
```

Nun sollten die Tabellen in der PostgreSQL-Datenbank angelegt sein. Mit [pgAdmin](https://www.pgadmin.org/), einem PostgreSQL-GUI, kannst du dies z. B. ansehen.

Wenn du `python manage.py` aufrufst, siehst du eine Liste an Befehlen, die die die Django-App zur Verfügung stellt. Um den Server lokal zu starten, benötigst du den Befehl `runserver`. Beachte: du musst immer im `src/` Ordner sein, um `manage.py` ausführen zu können.

```bash
python manage.py runserver
```

Wenn soweit alles gepasst hat, solltest du nun die App im Browser unter [http://localhost:8000](http://localhost:8000) sehen können.

## DEVELOPMENT

### Ordner-Struktur

* `src/`
  * `offenewahlen_nrw17/`: Hauptordner der Django-App.
  * `viz/`: Name des Django-Projektes. Wurde von uns einfach so gewählt.
    * `management/commands/`: enthält die Python-Scripts, welche man mittels `python manage.py` aufrufen kann.
	* `static/`: enthält die gesammelten Files des Projektes.
	  * `css/app.css` enthält das gesamte CSS.
	  * `js/app.js` enthält das gesamte JavaScript.
	  * `img/`: Logos, etc.
	* `templates/`: 
	  * `viz/`: Unterordner für Projekt. Enthält die Template-Files.
	    * `includes/`: enthält verschiedenste Include-Files für die Templates.
	* `tests/`: enthält die Test-Scripts.
  * `static/`: enthält die gesammelten Files aus allen Projekten (in unserem Fall ja nur ein Projekt). Wird von Python automatisch erstellt.
  * `locale/`: Ordner für die Übersetzungen. Je ein Unterordner für jede Sprache. Beispiel Deutsch: `de/LC_MESSAGES/` enthält `django.mo` (Binary-File) und `django.po` (File mit den Übersetzungen).
  * `migrations/`: Ordner und Inhalt werden bei einer Datenbank-Migrationen automatisch erstellt.
* `data/`: enthält die Daten von uns.
  * `setup/`: alle Daten, die für das Setup der App notwendig sind.
  * `test/`: alle Daten, die für die Tests notwendig sind.
* `venv/`: ist der Ordner für das Virtual Environment. Wird zu Beginn erstellt, siehe [Install](#install).

### Mehrsprachigkeit

Die Sprachfiles erstellen.
```bash
cd src/
python manage.py compilemessages
```

### Daten importieren

XML-Testergebnisse von lokalem Pfad importieren
```bash
python manage.py importxml --local_path ../data/test/example_1.xml
```

### Tests durchführen

```bash
python manage.py test
```

### Unser Development-Workflow

Um beim Entwickeln der App mitzumachen, empfiehlt es sich zuerst mal den Stand zu den [Milestones](https://github.com/OKFNat/offenewahlen-nrw17/milestones?direction=asc&sort=due_date&state=open) und das [Board](https://github.com/OKFNat/offenewahlen-nrw17/milestones#boards?repos=96933110) mit den Issues anzusen. Mit den Milestones koordinieren wir die großen Projekt-Abschnitte, welche sich aus vielen kleineren Issues zusammen setzen, und ist der beste Startpunkt zum Verstehen des Entwicklungs-Standes. Das Board ermöglicht einfaches verwalten der Issues und ist somit die zentrale Übersicht für die Tasks.

Die Entwicklung wird in drei Entwicklungs-Phasen unterteilt:
1. **Alpha**: Die Kernfunktionen der einzelne Prozess-Schritte. Es soll ein Teil nach dem anderen Lauffähig werden, damit möglichst bald an allen drei Teilen parallel gearbeitet werden kann.
2. **Beta**: Die Beta-Phase wird sowohl für den internen Test wie auch der Test-Wahl mit dem BMI verwendet, und muss somit alle am Wahltag benötigten Funktionen implementiert haben.
3. **Final**: Die finale Version 1 der App, mit welcher am Wahltag online gegangen wird.

Unterteilt ist die Reihenfolge je Entwicklungs-Phase immer in:
1. **Datenimport**: Zuerst müssen die notwendigen Daten in die Datenbank importiert werden.
2. **Datenauslieferung**: Die Datenbank liefert die benötigten Daten an das Frontend aus.
3. **Frontend**: Enthält die Visualisierungen und die Statistik-Seite und alles sonstige, was via Browser zugänglich ist.
4. Deployment: Wenn die drei Datenverarbeitungs-Prozesse abgeschlossen ist, wird die App deployed und die nächste Entwicklungs-Phase kann beginnen.

### Selber coden

Lies zuerst den Absatz davor (Unser Workflow). Dann *forke* dieses Repo und *clone* es auf deinen Rechner um die App lokal zum Laufen bringen (siehe [Install](#install)). Dann such dir am besten ein Issue aus dem [Board](https://github.com/OKFNat/offenewahlen-nrw17/milestones#boards?repos=96933110) und versuch es zu lösen. Wenn du Fragen hast, kannst du dich jederzeit via Email (info@offenewahlen.at) oder unter [Kontakt](http://offenewahlen.at/kontakt) melden. Nachdem du das Issue erledigt hast, musst du die Änderungen mittels Pull Request an dieses GitHub Repository hochladen. 

Eine Person vom Team (vermutlich Stefan oder Christopher), werden dann den Pull Request reviewen. Wenn es Probleme gibt, werden wir dies im Pull Request kommentieren, wenn nicht werden wir *mergen*.

**Ressourcen zum Lernen**

- Python: [Kurs @ Udacity](https://de.udacity.com/course/programming-foundations-with-python--ud036/), [The Hitchhiker's Guide to Python](http://docs.python-guide.org/en/latest/)
- Django: [Tutorial](https://docs.djangoproject.com/en/1.11/intro/tutorial01/), [The Django Book](https://djangobook.com/)
- JavaScript: [Kurs @ Udacity](https://de.udacity.com/course/javascript-basics--ud804/)
- jQuery: [Kurs @ Udacity](https://de.udacity.com/course/intro-to-jquery--ud245/)
- D3.js: [Kurs @ Udacity](https://de.udacity.com/course/data-visualization-and-d3js--ud507/)

## DOKUMENTATION

Die Dokumentation findet in diesem Repository in den Files [README.md](README.md) und [DATA.md](DATA.md) sowie dem dazugehörigen [GitHub Wiki](https://github.com/OKFNat/offenewahlen-nrw17/wiki) statt. Das Wiki ist eine frei zugängliche Wissens-Sammlung rund um die App und für alle offen zum Verwenden und Verändern. 

## MITMACHEN

Dies ist ein Open Source Projekt, daher lebt das Projekt von vielen helfenden Händen. 

Wenn du das Projekt gerne ehrenamtlich unterstützen möchtest, melde dich einfach [direkt bei uns](http://offenewahlen.at/kontakt). Jeder noch so kleiner Beitrag ist wichtig und hilfreich. 

Anbei eine paar Ideen, wie man sich bei dem Team einbringen kann:
- **Fehler melden**: Wenn du einen Fehler gefunden hast, erstelle bitte ein [Issue](https://github.com/OKFNat/offenewahlen-nrw17/issues/new) dazu. Immer am besten mit Screenshot und möglichst exakter Fehlerbeschreibung.
- **Fehler beheben**: Sieh dir die [Issues](https://github.com/OKFNat/offenewahlen-nrw17/issues) an und schließe eines. Nähere Infos unter **[Development](#development)**.
- **Web-Design / Grafik**: mach bei der Daten-Visualisierung am Frontend mit. Auch GrafikerInnen für Logos etc. sind gesucht.
- **Web-Entwicklung, UX/UI**: alles was mit klassicher Website-Entwicklung zu tun hat - vor allem Frontend UX/UI. Von HTML5 über CSS3 bis hin zu JavaScript (jQuery, Bootstrap, D3).
- **Django EntwicklerIn**: die App ist mit dem Web-Framework Django umgesetzt. Daher ist hier Know-How sehr gesucht.
- **Wahlen**: Fachwissen rund um Wahlen ist natürlich essentiell. Wenn dich Wahlen interessieren, gibt es eine Vielzahl von Möglichkeiten dich einzubringen und zu lernen. Egal ob bei der Visualisierung, bei der Kommunikation oder der Dokumentation.
- **Übersetzen**: die App ist mehrsprachig. Aktuell ist geplant, in die österr. Minderheitensprachen zu übersetzen, aber es sind keine Grenzen gesetzt.
- **Dokumentation**: Die Dokumentation zur App wird für verschiedene User-Gruppen passend aufbereitet bzw. kann sie auch in Englisch übersetzt werden.
- **[Newsletter](http://offenewahlen.at/newsletter)**: abonniere den Newsletter und bleib am Laufenden.
- **Funding**: Wir suchen passende Funding-Möglichkeiten, um das Projekt kontinuierlich weiter wachsen zu lassen und zu verbessern. Wenn du eine Idee hast, wie man zu Förderungen kommt oder mit uns gemeinsam einreichen möchtest, meld dich bitte.
- **[Spenden](http://offenewahlen.at/spenden)**: Du kannst uns auch finanziell unterstützen, indem du eine kleine Spende da lässt. Das Geld wird Projekt-bezogen verwendet und dient zum Verbessern der verschiedenen Aktivitäten von Offene Wahlen Österreich - von der #NRW17-App über den Datenstandard bis hin zum Abhalten von Coding-Workshops.

Wenn du Fragen hast, kannst du dich jederzeit via Email (info@offenewahlen.at) oder unter [Kontakt](http://offenewahlen.at/kontakt) melden.

## DATEN

Für die App werden verschiedene Daten als Grundlage verwendet. Einige werden von anderen übernommen, andere von uns selber zusammen getragen. Beachte: Wir erheben keinen Anspruch auf Vollständigkeit oder Korrektheit, die Qualität der vorhandenen Daten sollte aber recht gut sein. Unser Ziel ist es, erst mal alle notwendigen Daten für die *#NRW17 Visualisierung* zusammen zu tragen. Danach sollen diese Schritt für Schritt erweitert werden. Wir freuen uns sehr über jede Unterstützung dabei. Wenn du einen Fehler findest, oder selber spannende Daten besitzt - **meld dich bitte!** 


Die Basis-Daten dienen zum Setup der App und als Datengrundlage, um die Ergebnisse passend visualisieren zu können. Die Test-Daten werden zum Testen der einzelnen Prozess-Schritte verwendet. Dies ermöglicht ein verifizieren der App auf seine verschiedenen Funktionen - vom Datenimport bis hin zu Visualisierung.


Die so gesammelten und kuratierten Daten werden kontinuierlich in **Wikidata** importiert, um dies als primäres Repository für Unique-Identifiers rund um Wahlen aufzubauen. Dazu gibt es mit [OKFNat/offenewahlen-wikidata](https://github.com/OKFNat/offenewahlen-wikidata) ein eigenes Repository mit weiteren Infos.


Nähere Infos zu den einzelnen Daten findest du unter **[DATA.md](DATA.md)**.


## COPYRIGHT

Sämtlicher von uns entwickelter Quellcode steht unter der [MIT](https://opensource.org/licenses/MIT)-Lizenz frei zur verfügung.

Alle Materialien wie Texte, Bilder und Folien die im Rahmen dieses Projektes erstellt werden, stehen unter CC BY 4.0, soweit nicht explizit anders erwähnt.

