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
Test, test, test, test, test, *test*, *test*, *test*.

| Eingabe | Funktion |
| :---: | :--- |
| `G` | An das Ende des Dokuments springen |
| `gg` | An den Anfang des Dokuments springen |
| `ge` | Ans Ende des vorhergehenden Wortes springen |
| `0` | An den Anfang einer Zeile (Absatzes) springen |
| `$` | An das Ende einer Zeile (Absatzes) springen |
| `476G` | Direkt auf Zeile 476 springen |
| `Ctrl-f` | Entspricht PageDown |
| `Ctrl-b` | Entspricht PageUp |
| `Ctrl-d` | Scrollt eine halbe Seite nach unten |
| `Ctrl-u` | Scrollte eine halbe Seite nach oben |
| `H` | An den obersten Bildschirmpunkt springen |
| `M` | An den mittleren Bildschirmpunkt springen |
| `L` | An den untersten Bildschirmpunkt springen |

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
--> Zeile 557!
