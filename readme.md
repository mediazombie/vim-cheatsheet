<!-- markdownlint-disable MD013 -->
# Vim Cheatsheet

## Willkommen in der Welt von Vim – Dein Einstieg in den legendären Editor

**Vim (und seine Geschwister Vi und Neovim)** gehört zu den mächtigsten Werkzeugen, die die Softwarewelt je hervorgebracht hat. Während normale Texteditoren wie Notizblock-Programme funktionieren, ist Vim eher wie ein Präzisionswerkzeug für Programmierer, Systemsadministratoren und Text-Enthusiasten. Wer Vim beherrscht, tippt nicht nur Text, sondern "spricht" mit dem Editor. Du kannst damit Text blitzschnell manipulieren, durch riesige Dateien springen und Aufgaben automatisieren, für die man sonst minutenlang mit der Maus klicken müsste.

**Warum haben so viele Menschen Respekt oder sogar Angst vor Vim?**  
Vim hat einen berühmt-berüchtigten Ruf: Seine Lernkurve ist steil. Der Grund dafür ist einfach: Vim nutzt keine Menüleisten oder typischen Mausklicks. Wenn man Vim das erste Mal öffnet, tippt man oft blind darauf los – und nichts passiert. Schlimmer noch: Viele wissen nicht einmal, wie man das Programm wieder schliesst (kleiner Spoiler: `:q` gefolgt von `Enter` ist dein Freund!). Diese anfängliche Orientierungslosigkeit schreckt viele ab.

**Terminal oder Grafikoberfläche?**  
Es gibt zwar inzwischen moderne Versionen für Windows, macOS und Linux, die in einem eigenen Fenster mit grafischer Oberfläche laufen. Der eigentliche Einsatzzweck und der grösste Vorteil von Vim liegen jedoch direkt im Terminal (der Kommandozeile). Hier verbraucht Vim so gut wie keine Systemressourcen, läuft selbst auf den ältesten Computern oder über langsame Internetverbindungen reibungslos und hält deine Hände genau dort, wo sie am produktivsten sind: auf der Tastatur.

**Dein Weg zum Vim-Profi**  
Lass dich von den ersten Hürden nicht abschrecken! Niemand lernt Vim an einem Tag. Dieses Cheatsheet soll dir als digitaler Spickzettel und Orientierungshilfe dienen, um die wichtigsten Befehle immer griffbereit zu haben.

* Der beste Start: Wenn du direkt loslegen und spielerisch lernen willst, öffne dein Terminal und tippe einfach den Befehl vimtutor ein. Es startet ein interaktives, ca. 30-minütiges Lernprogramm, das dich sicher durch die allerersten Schritte führt.

Hab etwas Geduld mit dir – sobald sich das "Muskelgedächtnis" erst einmal an Vim gewöhnt hat, wirst du nie wieder einen anderen Editor nutzen wollen!

Hier sind noch 2 weitere Quellen (Englisch) zum lernen von Vim:

* [Vim School](https://vimschool.netlify.app/)
* [Getting started with Vim](https://opensource.com/article/19/3/getting-started-vim)

## Die Modi von Vim

Hier sind die wichtigsten Modi von Vim:

* Normal-Modus `Esc`: Der Standardmodus für effiziente Navigation, Löschen und Textmanipulation.
* Insert-Modus `i`: Modus zum direkten Schreiben und Einfügen von neuem Text.
* Visual-Modus `v`: Erlaubt das zeichen- (`v`), zeilen- (`Shift-v`) oder blockweise (`Ctrl-v`) Auswählen von Textpassagen.
* Comand-Line-Modus: Eingabe von Befehlen wie z.B. Speichern (`:w`) oder Suchen (`/`).

> [!NOTE]
> Im Visual-Modus kann mittels `o` zwischen dem Anfang der Markierung und dem Ende hin und her gesprungen werden. Dies kann hilfreich sein, wenn man oberhalb oder unterhalb der Markierung noch was in die Markierung einschliessen möchte.

## Bewegen des Cursors

Um den Cursor zu bewegen, nutze die Tasten `h, j, k und l`

| Taste | Funktion |
| :---: | :--- |
| `h` | Cursor nach links bewegen |
| `j` | Cursor nach unten bewegen |
| `k` | Cursor nach oben bewegen |
| `l` | Cursor nach rechts bewegen |

## Vim Beenden

Da es sich nachfolgend um einen Befehl handelt, der nur im `Normal`-Modus funktioniert, stelle zuerst sicher, dass du dich in diesem befindest indem du die Taste `Esc` drückst!

| Eingabe | Funktion |
| :---: | :--- |
| `:q!` | Vim ohne speichern oder Nachfrage schliessen |

## Text editieren

Um Text in Vim zu editieren, muss in den `Insert`-Modus gewechselt werden. Die gebräuchlichste Möglichkeit dazu ist, die Taste `i` zu drücken.

| Taste | Funktion |
| :---: | :--- |
| `i` | Text vor der Cursor-Position einfügen |
| `a` | Text hinter der Cursor-Position einfügen |
| `Shift-i` | Springt zum ersten sichtbaren (Nicht-Leerzeichen-)Zeichen der Zeile und startet dort den Insert-Modus |
| `Shift-a` | Springt hinter das letzte Zeichen der Zeile und startet dort sofort den Insert-Modus (Anhängen) |
| `x` | Zeichen unter dem Cursor löschen |
| `r` | Zeichen unter dem Cursor ändern |

## Löschkommandos

Auch hier ist darauf zu achten, dass man sich im `Normal`-Modus befindet.
Zur Sicherheit zuvor jeweils die `Esc`-Taste drücken.

| Eingabe | Funktion |
| :---: | :--- |
| `dw` | Wort löschen - Cursor muss auf dem ersten Zeichen des Wortes stehen |
| `diw` | Wort löschen - Cursor kann irgendwo im Wort stehen |
| `d$` | Bis ans Ende der Zeile, ab Corsor-Position, löschen |

## Operatoren und Bewegungsfunktionen

Mittels Operatoren können Bewegungsfunktionen bis zu einem definierten Punkt oder mittels Zähler mehrfach nacheinander ausgeführt werden.
Zum Beispiel `d` als Löschoperator gefolgt gefolgt von einer Bewegung (z.B. `w` für Wort):

| Eingabe | Funktion |
| :---: | :--- |
| `dw` | Löschoperator ab aktueller Cursorposition bis Beginn des nächsten Wortes OHNE dessen erstes Zeichen |
| `de` | Löschoperator ab aktueller Cursorposition bis Ende des aktuellen Wortes MIT dessen letztem Zeichen |
| `d$` | Löschoperator ab aktueller Cursorposition bis Ende der Zeile MIT dem letzten Zeichen |

>[!NOTE]
> Durch die Eingabe im Normal-Modus von `w`, `e`, bzw. `b` oder `ge` kann man sich auch ohne Funktionsoperator durch Wörter bewegen. Dabei gilt, `w` und `e` bewegen den Cursor Wortweise vorwärts und `b` bzw. `ge` bewegen den Cursor Wortweise rückwärts.
> Auch hier können mit vorangestellter Zahl mehrere entsprechende Bewegungsschritte ausgeführt werden (z.B. springt `17b` um 17 Wörter zurück)

### Verwendung eines Zählers mit einer Bewegung

Gibt man vor einer Bewegungsfunktion eine Zahl ein, wird die Bewegung entsprechend oft wiederholt. Zum Beispiel wird der Cursor bei Eingabe von `12w` um 12 Wörter vorwärts bewegt.
Dies lässt sich auch mit Richtungsfunktionen `h, j, k, l` verwenden um z. B. um 128 Zeilen nach unten zu springen, gibt man einfach `128j` ein.

### Verwendung eines Zählers für mehrere Operatoren

Da man in Vim vieles miteinander kombinieren kann, ist es beispielsweise auch möglich mit einer Eingabe mehrere Zeilen zu löschen.
Gibt man zum Beispiel im Normal-Modus `d2w` ein, werden die nächsten beiden Wörter gelöscht wobei bei Eingabe von `dw` nur das aktuelle Wort gelöscht wird.
Gleiches funktioniert auch zum löschen von mehr als einer Zeile `dd` (löscht die aktuelle Zeile), wobei `5dd` die nächsten 5 Zeilen löscht.

### Spezielle Bewegungsfunktionen

Es gibt zudem noch einige spezielle Bewegungsfunktionen um sich noch schneller bzw. komfortabler durch ein Dokument zu bewegen (siehe nachfolgende Tabelle):

#### Vertikale Bewegung

| Eingabe | Funktion |
| :---: | :--- |
| `G` | An das Ende des Dokuments springen |
| `gg` | An den Anfang des Dokuments springen |
| `25-gg` | Genau auf Zeile Nummer 25 im Dokument springen |
| `476-G` | Direkt auf Zeile 476 springen |
| `Ctrl-f` | Entspricht PageDown |
| `Ctrl-b` | Entspricht PageUp |
| `Ctrl-d` | Scrollt eine halbe Seite nach unten (`d` für Down) |
| `Ctrl-u` | Scrollte eine halbe Seite nach oben (`u` für Up) |
| `Ctrl-i` | Zur nächsten Sprungmarke springen (Sprungliste = es werden grössere Positionswechsel gespeichert z.B. `42G`, `gg` oder `G`, nicht jedoch "normale" Bewegungen mittels `j`, `k` oder `Ctrl-u`/`Ctrl-d`) |
| `Ctrl-o` | Zur vorherigen Sprungmarke springen (wie bei `Ctrl-i` nur in die andere Richtung) |
| `M` | An den mittleren Bildschirmpunkt springen |
| `zz` | Aktuelle Zeile im Editor zentrieren |
| `%` | Zwischen öffnenden und schliessenden Klammerpaaren den Cursor hin und her bewegen. Dies funktioniert mit allen möglichen Klammerpaaren (z.B. `(`-`)`, `[`-`]` und `{`-`}`) |

> [!NOTE]
> Mittels `Shift-(` oder `Shift-)` kann man sich Blockweise durch einen Text bzw. Code bewegen. Dadurch wird jeweils ein Codeblock hoch oder runter gesprungen.

#### Horizontale Bewegung

| Eingabe | Funktion |
| :---: | :--- |
| `ge` | Ans Ende des vorhergehenden Wortes springen |
| `W` | Ein Wort nach vorne springen aber Zeichen wie `,` usw. ignorieren |
| `B` | Ein Wort zurück springen aber Zeichen wie `,` usw. ignorieren |
| `f-Zeichen` | Springt bis zum eingegeben `Zeichen`, mit `;` wird zum nächsten, mit `,` zum vorherigen Vorkommen von `Zeichen` gesprungen |
| `vi-Zeichen` | Springt bis zum eingegeben `Zeichen` (z.B. `"`) und markiert den Text dazwischen im Visual-Mode (ändern eines Textes zwischen 2 `"`-Zeichen) |
| `va-Zeichen` | Springt bis zum eingegeben `Zeichen` (z.B. `"`) und markiert den Text inkl. dem `Zeichen` im Visual-Mode |
| `vib` | Wählt den nächsten Block innerhalb von runden Klammern `()` aus (der Cursor muss sich auf der entsprechenden Zeile befinden aber nicht zwingend im `()`-Block) |
| `viB` | Wählt den Text innerhalb von geschweiften Klammern `{}` aus (der Cursor muss sich hierzu im gewünschten Block befinden) |
| `yi-Zeichen` | Springt bis zum eingegeben `Zeichen` (z.B. `"`) und yankt (kopiert) den Text dazwischen im Visual-Mode (kopieren eines Textes zwischen 2 `"`-Zeichen) |
| `ya-Zeichen` | Springt bis zum eingegeben `Zeichen` (z.B. `"`) und yankt (kopiert) den Text inkl. der `"`-Zeichen im Visual-Mode (kopieren eines Textes inkl. der 2 `"`-Zeichen) |
| `0` | An den Anfang einer Zeile springen (immer auf Spalte 1), bleibt im Normal-Modus |
| `$` | An das Ende einer Zeile springen (letztes Zeichen), bleibt im Normal-Modus |
| `*` | Benutzt man `*` (`Shift-3`) auf einem Wort unter dem Cursor, wird dieses als Suchbegriff definiert und direkt zum nächsten Vorkommen dessen gesprungen, man kann sich nun mittels `n` in der Suche vorwärts oder mit `N` in der Suche Rückwärts bewegen |

> [!TIP]
> Um einen Block inkl. der entsprechenden Klammern zu markieren, verwendet man `vab` (für runde `()` Klammern), bzw. `vaB` (für geschweifte `{}` Klammern).  
> Um einen Block mit eckigen Klammern zu markieren, verwendet man die Eingabe `vi[`, bzw. `va[` - dies funktioniert natürlich auch mit anderen Zeichen und auch anstelle von `vib` (`vi(`) oder `viB` (`vi{`). Ebenso funktioniert dies auch mit den `va...`-Alternativen (für die Auswahl inkl. der Klammern).

#### Marker

| Eingabe | Funktion |
| :---: | :--- |
| `ma` | Markierung setzen - dabei ist `a` variabel und kann durch jeden möglichen Buchstaben ersetzt werden |
| `'a` | Zur gespeicherten Markierung (`a`) an den Anfang der Zeile springen |
| `` `a `` | Zur gespeicherten Markierung (`a`) springen und zwar exakt zur Zeile und Spalte wo `a` gespeichert wurde |

Da es sowohl Lokale als auch Globale Markierungen gibt, ist folgendes zu beachten:

| Typ | Buchstabe | Reichweite & Verhalten |
| :--- | :---: | :--- |
| Lokale Marker | `a` bis `z` | Gilt nur innerhalb der aktuellen Datei. Du kannst `ma` in Datei X und `ma` in Datei Y unabhängig voneinander nutzen. |
| Globale Marker | `A` bis `Z` | Gilt dateiübergreifend. Wenn du in Datei X `mA` drückst, später Datei Y bearbeitest und `'A` drückst, öffnet Vim automatisch wieder Datei X und springt zur Position. |

**Integrierte Marker:**
Vim setzt viele nützliche Marker ganz automatisch, ohne dass man diese zuerst speichern muss.

* `''` (Zwei Apostrophe): Springt zurück zur letzten Position, an der du vor dem aktuellen Sprung warst (perfekt nach `G` oder `gg`).
* `'.` (Apostroph + Punkt): Springt zur letzten bearbeiteten Zeile.
* `'^` (Apostroph + Caret): Springt zur letzten Einfügeposition (wichtig, wenn du im Insert-Modus warst).
* `'[.` und `']:`: Springen zum Anfang bzw. Ende des zuletzt veränderten oder eingefügten Textes.

**Übersicht behalten:**  
Wenn du mal vergessen hast, welche Marker du gesetzt hast, hilft der Befehl `:marks` weiter.

> [!TIP]
> Drückt man an einer betimmten Position im Dokument (wo man gerade was am bearbeiten ist) die Tastenkombination `Ctrl-G`, werden Informationen zur Datei und die Zeile auf der der Cursor aktuell steht unten am Bildschirm angezeigt.
> Merkt man sich hier die Zeilennummer, kann man sich durch das Dokument bewegen, um was nachzusehen und später durch Eingabe von `Zeilennummer-G` wieder zur Position zurück kehren.

## Rückgängig machen (Undo)

Natürlich ist es auch in Vim möglich, Aktionen (Befehle) rückgängig zu machen. Allerdings NICHT mittels der in GUI-Anwendungen gebräuchlichen Tastenkombination `Ctrl + Z`, sondern durch Eingabe von `u` um das letzte Komando Schritt-für-Schritt rückgängig zu machen oder `U` um eine ganze Zeile wiederherzustellen.

## Wiederherstellen (Redo)

Auch Wiederherstellen, mittels `Ctrl + R`, funktioniert in Vim. Dadurch wird jeweils das letzte rückgängig gemachte Kommando (durch `u`) quasi rückgängig gemacht. Die Besonderheit hier ist, dass dies auch im Insert-Modus funktioniert.

**Beispiel:**  
Ich möchte in einem Text, auf einer Zeile bzw. in einem Absatz, ein Wort z.B. **Fett** schreiben. Dann kannst du den Cursor irgendwo in diesem Wort positionieren, den Befehl `viwc**<Ctrl + R>"**<ESC>` eingeben und schon hast du das Wort **Fett** geschrieben.

**Was ist nun passiert?**

1. `viw` markiert das ganze Wort.
2. `c` schneidet das Wort aus und wechselt in den Insert-Modus.
3. `**` die .md-Formatierungszeichen für **Fett** eingeben.
4. `Ctrl + R + "` fügt das Wort aus dem Zwischenspeicher `"` wieder ein.
5. `**` die abschliessenden .md-Formatierungszeichen eingeben.
6. `<ESC>` drücken um wieder in den Normal-Modus zu gelangen.
7. Um die Formatierung auf weitere Wörter anzuwenden, mittels `w` zum nächsten Wort springen und `.` tippen (lässt sich mehrfach wiederholen) - Fertig!

## Einfügen, Ersetzen und Ändern

### Einfügen (Put)

Vim besitzt einen sehr mächtigen Zwischenspeicher (auch Register genannt). Kleiner Tipp hierzu: Gibt man im Normal-Modus `:reg` ein, werden einem alle Register mit den aktuell darin gespeicherten Werten angezeigt. Solange dieses "Register"-Fenster aktiv ist, lässt es sich mittels `q` wieder schliessen.

| Eingabe | Funktion |
| :---: | :--- |
| `p` | Zuletzt in den Zwischenspeicher (Register) gespeicherten `y` Inhalt auf der nächsten Zeile einfügen |
| `"3p` | Inhalt aus Zwischenspeicher (Register) 3 einfügen |

> [!NOTE]
> Mittels `"` wird der Zugriff auf ein spezifisches Register, gefolgt von einer Nummer oder einem Zeichen, eingeleitet und mittels `...p` dann schliesslich eingefügt.
> Es gibt noch spezielle Register wie `+` und `*` die je nach Betriebssytem auf den Zwischenspeicher des Betriebssystems zugreifen können und somit in Vim gespeicherte Inhalte in allen anderen Programmen mittels `Ctrl + V` einfügen können.

### Ändern (Change)

Mit dem Change-Befehl `c` in Kombination mit einer Bewegungsfunktion (z.B. `ce`) können mehrere Zeichen schnell und einfach geändert werden.

| Eingabe | Funktion |
| :---: | :--- |
| `ce` | Ändern ab Cursor-Position bis zum Ende des aktuellen Wortes |
| `c$` | Ändern ab Cursor-Position bis zum Ende der Zeile (Absatzes) |
| `ciw` | Egal an welcher Stelle in einem Wort sich der Cursor gerade befindet, es wird das ganze Wort (**C**hange**I**nner**W**ord) geändert |

## Suchen und Ersetzen

### Suchen

Auch hier wieder darauf achten, dass man sich im `Normal`-Modus befindet!
Nun tippe auf der Tastatur `/` direkt gefolgt vom Suchbegriff ein, zum Beispiel `/Woort`. Das ist das Wort oder (in diesem Fall) der Fehler nach dem du suchen willst.
Um nach demselben Ausdruck weiterzusuchen, tippe `n` für Next. Um nach demselben Ausdruck in der Gegenrichtung zu suchen, tippe `N`.
Um direkt rückwärts statt vorwärts zu suchen, tippe `?` statt `/`.

> [!TIP]
> Wenn du mittels Suche an der Stelle angekommen bist, an der du bearbeiten möchtest, aber danach wieder in der Historie zurück kehren möchtest, tippe `Ctrl-O`. Möchtest du stattdessen in der Historie vorwärts springen, tippe `Ctrl-I`.
> Diese Tastenkombinationen sind vergleichbar mit dem Zurück- und Vorwärts-Button in einem Webbrowser. Dies funktioniert auch, wenn du zum Beispiel mittels `gg` oder `G` an den Anfang oder das Ende deines Dokuments springst und danach wieder an die letzte Position zurück willst.

### Spezial - Passende Klammern finden

Durch tippen von `%` während der Cursor auf einer Klammer `(`, `[` oder `{` steht, bewegt sich der Cursor immer zur passenden gegenüberliegenden Klammer. Dies funktioniert in beide Richtungen, je nachdem, ob der Cursor auf der Öffnenden oder Schliessenden Klammer steht.

> [!NOTE]
> Diese Funktionalität kann vor allem beim bearbeiten von Programmcode sehr hilfreich und nützlich sein, um fehlende Klammern zu finden.

### Ersetzen (Substitute)

Hier, wie bei den meisten Befehlen, ebenfalls darauf achten, dass man sich im `Normal`-Modus befindet.  
Wenn du `:s/alt/neu/g` tippst, wird auf der aktuellen Zeile nach dem Begriff `alt` gesucht und dieser durch `neu` ersetzt. Das `/g` am Ende der Eingabe bedeutet, dass die ganze aktuelle Zeile bzw. der Absatz durchsucht und jeder gefundene Begriff `alt` direkt durch `neu` ersetzt wird.  
Um das ganze Dokument nach einem Begriff (z.B. Variablenname) zu durchsuchen und zu ersetzen, tippst du `:%s/alt/neu/g`. Um nicht direkt alles zu ersetzen, sondern mittels Abfrage zu jedem gefunden Begriff zu ersetzen, tippst du `%s/alt/neu/gc`. Dadurch wirst du bei jedem gefundenen Begriff, mittels Abfragedialog, gefragt, ob dieser ersetzt werden soll oder nicht.  
Es können auch nur Suchbegriffe auf mehreren, spezifischen und aufeinader folgenden Zeilen ersetzt werden. Hierfür tippst du einfach `:#,#s/alt/neu/g`, wobei `#,#` die Zeilennummern des Bereichs sind. Auch hier kannst du stattdessen `:#,#s/alt/neu/gc` eingeben, damit bei jedem Treffer ein Abfragedialog angezeigt wird.

| Eingabe | Funktion |
| :---: | :--- |
| `:s/alt/neu/g` | In aktueller Zeile nach dem Begriff `alt` suchen und jeden Treffer (`/g`) durch `neu` ersetzen |
| `:%s/alt/neu/gc` | Im aktuellen Dokument nach dem Begriff `alt` suchen und diesen mittels Abfragedialog durch `neu` ersetzen - `../gc` bedeutet `g`=Global (alle Treffer je Zeile, nicht nur den Ersten) und `c` mittels Abfragedialog |
| `:#,#s/alt/neu/g` | In aufeinander folgenden Zeilen `#,#`, wobei `#,#` für die einzuschliessenden Zeilennummern steht, `alt` durch `neu` ersetzen und `/g` dabei alle Treffer berücksichtigen (nicht nur den Ersten) |

## Sortieren

Auch die alphabetische Sortierung kann Vim bzw. Neovim!  
Möchte man beispielsweise die folgende Liste mit Wörtern sortieren, setzt man den Cursor an die Position des Ersten oder Letzten Wortes der Liste und markiert die ganze Liste mit dem Visual-Line-Modus `Shift-v`, wechselt in den Comand-Line-Modus indem man `:sort` eingibt.  
  
Hier eine Beispielliste zum testen:

```text
apples
bananas
watermelons
oranges
grapes
cigarettes
kiwis
raspberrys
```

| Eingabe | Funktion |
| :---: | :--- |
| `:sort i` | Gross-/Kleinschreibung ignorieren (Standardmässig kommen Grossbuchstaben zuerst) |
| `:sort u` | Duplikate entfernen (sortiert die Liste und löscht doppelte Einträge raus) |
| `:sort n` | Nummerisch sortieren (sinnvoll wenn Zeilen mit Zahlen beginnen) |

> [!TIP]
> Um die Liste aus dem Beispiel oben nun sortiert auf einer Zeile mit `,` getrennt auszugeben, kann man die ganze Liste mittels `vip` (den ganzen Absatz-Block markieren) auswählen und anschliessend mittels `:sort` alphabetisch sortieren, mittels `gv` die zuvor markierte Auswahl erneut auswählen und mit `:s/\n/, /` auf einer Zeile ausgeben.
> Ein etwas einfacherer Weg aber ohne `,` geht mittels `J`. Das heisst, zuerst wieder alles markieren mittels `vip`, sortieren `:sort`, vorherige Markierung erneut auswählen `gv` und mittels `J` auf einer Zeile getrennt durch ein Leerzeichen ausgeben.

## Arbeiten mit Zahlen

Auch mit Zahlen kann Vim bzw. Neovim erstaunliches anstellen.  
Angenommen man hat das nachfolgende Szenario und möchte die Zahlen der Reihe nach durchnummeriert haben, markiert man alle Zahlen, die geändert werden sollen (erste Null nicht, die soll so bleiben) mittels dem Visual-Block-Modus `Ctrl-v` oder mittels dem Visual-Line-Modus `Shift-v`. Danach den Befehl `g Ctrl-a` verwenden und die Zahlen werden automatisch korrekt durchnummeriert.

```text
0
0
0
0
0
0
0
0
0
0
0
```

>[!TIP]
> Um sich direkt eine sortierte Liste von aufeinanderfolgenden Zahlen auszugeben, den Befehl `:put =range(0,6)` eingeben und man erhällt eine vertikale Liste mit den Zahlen `0 - 6`. Um diese ggf. hintereinander, durch Leerzeichen getrennt, auszugeben, den Befehl `vip` gefolgt von `J` eingeben.

## Spezielle Befehle (Vertiefung)

### Umgang mit Buffers und Fenstern

| Eingabe | Funktion |
| :---: | :--- |
| `:vsplit Datei` | Vim kann auch geteilte Fenster! Öffnet die `Datei` in der rechten Fensterhälfte |
| `:hsplit Datei` | Öffnet die `Datei` in der unteren Fensterhälfte |
| `Ctrl-h` | In das linke Fenster (Fensterhälfte) wechseln - funktioniert mit allen Bewegungstasten `h, j, k, l` (teilweise, je nach Konfiguration muss `Ctrl-w-h` oder ähnlich verwendet werden) |
| `Shift-h` | Durch Tabs/Buffer schalten - vorheriger Buffer |
| `Shift-l` | Durch Tabs/Buffer schalten - nächster Buffer |
| `:b#` | Wechselt direkt zum zuletzt genutzten Buffer |
| `Space-f-b` | Durchsuchbare Liste mit allen offenen Buffern anzeigen - funktioniert nur mit LazyVim |

> [!NOTE]
> Mit Buffer sind geöffnete Dateien in der aktuellen Vim-Sitzung gemeint!
> Man kann in Vim mehrere Dateien gleichzeitig geöffnet haben und dann mit den entsprechenden Befehlen zwischen diesen hin und her wechseln, auch wenn diese ggf. nicht direkt sichtbar sind.

### Bearbeiten, Speichern und Schliessen

| Eingabe | Funktion |
| :---: | :--- |
| `:e pfad/datei` | Wenn Vim bereits geöffnet ist, eine Datei im aktuellen Verzeichnis oder aus einem anderen Verzeichnis zum bearbeiten öffnen |
| `:w` | Aktuelle Datei (Buffer) die auf dem Bildschirm sichtbar bzw. aktiv ist speichern |
| `:q` | Aktuell am Bildschirm sichtbares bzw. aktives Fenster schliessen - enthält dieses nicht gespeicherte Änderungen, wird eine entsprechende Meldung ausgegeben (Datei ist jedoch nach wie vor im Buffer) |
| `:bd` | Aktuellen Buffer schliessen (Datei ist anschliessend nicht mehr im Speicher) |
| `:bd #` | Buffer mit Nummer `#` schliessen |

### Konsole öffnen

Um hier ein Konsolenfenster zu öffnen, stehen folgende Befehle zur Verfügung:

* `Space-f-t`: Öffnet ein Terminal im aktuellen Verzeichnis (nur Neovim mit LazyVim).
* `Space-f-T`: Öffnet ein Terminal im Root-Verzeichnis des Projekts (nur Neovim mit LazyVim).
* `:term`: Öffnet das Terminal im aktuellen Fenster.
* `:split | term`: Öffnet das Terminal in einem horizontalen Split-Fenster.
* `:vsplit | term`: Öffnet das Terminal in einem vertikalen Split-Fenster.

### Rechtschreibprüfung deaktivieren (nur Neovim mit LazyVim)

> [!NOTE]
> Neovim ist hystorisch gesehen die umfangreichste und aktuellste Version, die aus Vi bzw. Vim abgeleteitet wurde.
> LazyVim hingegen ist eine sehr mächtige Erweiterung zu Neovim, wodurch Neovim noch mächtiger und quasi zu einer vollwertigen IDE (Entwicklungsumgebung) wird.

| Eingabe | Funktion |
| :---: | :--- |
| `Space-u-s` | Rechtschreibprüfung deaktivieren |
