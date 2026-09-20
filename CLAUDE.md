# junolabs — Rechtsseiten

Die öffentlichen Rechtsseiten der junolabs-Apps, ausgeliefert über GitHub Pages.
**Kein App-Code.** Der Aufbau und die Begründungen stehen in `README.md`.

## Die URLs bewegen sich nicht

Jede veröffentlichte URL steht in einer **ausgelieferten App**, im **Play-Console-Feld** und
im **OAuth-Zustimmungsbildschirm**. Eine Datei umzubenennen oder zu verschieben bricht alle
drei und kostet ein App-Release. Neue Seiten kommen daneben, nie an die Stelle einer
bestehenden.

## Der Text beschreibt fremden Code

Die Aussagen über eine App — wie viele Sicherungen aufbewahrt werden, welcher OAuth-Scope
angefragt wird, was auf dem Gerät gespeichert wird — hängen an Code, der in einem anderen
Repo liegt (MoodTrackr: `julian-1504/mood-trackr`, privat). Welche Aussage woran hängt,
steht in `README.md` als Tabelle. Bei jeder inhaltlichen Änderung dort nachsehen, und im
Zweifel gegen den echten Code prüfen statt zu raten: Ein Rechtstext, der etwas Falsches
behauptet, ist schlimmer als einer, der etwas weglässt.

Dasselbe gilt in die andere Richtung — das **Data-Safety-Formular** in der Play Console
muss dasselbe sagen wie diese Seiten.

## Deutsch, mit Absicht

Play schreibt für eine Datenschutzerklärung keine Sprache vor, und das Console-Feld nimmt
ohnehin nur **eine** URL, nicht eine pro Sprachvariante des Eintrags. Die Seiten sind
deutsch, weil die Apps deutsch sind. Eine englische Fassung kommt erst mit der
Lokalisierung der zugehörigen App, und dann als zusätzliche Datei unter einem neuen Pfad.
Begründung und der vorgesehene Pfad stehen in `README.md`.

## Kein Jekyll-Theme

`_layouts/default.html` und `assets/style.css` gehören uns. Ein fremdes Theme setzt
englischen Text um einen deutschen Rechtstext („This project is maintained by …", „Hosted on
GitHub Pages") und kann das Gerüst beim nächsten Update unangekündigt ändern. Beides ist auf
einer Seite, die eine verantwortliche Person benennt, unerwünscht.

## Die zwei Fallen

- **Front Matter.** Jede `.md` braucht den `---`-Block. Fehlt er, liefert Jekyll rohes
  Markdown statt einer Seite.
- **`relative_url`.** Pfade im Layout gehen durch `relative_url`, Links im Inhalt bleiben
  relativ. Ein führender `/` zeigt an der Projektseite vorbei — beim Stylesheet genauso wie
  bei einem Link.

## Prüfen heißt abrufen

Nach einer Änderung die **veröffentlichte** Seite abrufen, nicht die Quelldatei ansehen.
Der Pages-Build braucht einen Moment; sein Status steht unter
`gh api repos/julian-1504/junolabs-privacy/pages/builds/latest`.
