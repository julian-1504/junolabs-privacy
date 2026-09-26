# junolabs — Rechtsseiten

Die öffentlichen Rechtsseiten der junolabs-Apps, ausgeliefert über GitHub Pages:
<https://julian-1504.github.io/junolabs-privacy/>

Das Repo ist öffentlich, damit die Seiten erreichbar sind — Google Play verlangt eine
Datenschutzerklärung für **jede** App, auch für kostenlose und auch für solche, die keine
Daten erheben, und der OAuth-Zustimmungsbildschirm verlangt dieselbe URL. Der Quellcode der
Apps liegt woanders und ist nicht öffentlich.

## Aufbau

```
_config.yml              baseurl, Titel, Sprache
_layouts/default.html    das Seitengerüst
assets/style.css         eine Spalte, Systemschriften, Hell und Dunkel
index.md                 → /junolabs-privacy/
moodtrackr/
  index.md               → /junolabs-privacy/moodtrackr/
  datenschutz.md         → /junolabs-privacy/moodtrackr/datenschutz.html
voctrainr/
  index.md               → /junolabs-privacy/voctrainr/
  datenschutz.md         → /junolabs-privacy/voctrainr/datenschutz.html
```

**Kein Jekyll-Theme.** Das Layout gehört uns. Ein fremdes Theme setzt englischen Text um
den deutschen Rechtstext — „This project is maintained by …", „Hosted on GitHub Pages" —
und kann das Gerüst beim nächsten Update unangekündigt ändern. Auf einer Seite, die eine
verantwortliche Person benennt, ist beides unerwünscht.

Eine weitere App bekommt einen weiteren Ordner. Bestehende URLs bleiben dabei, wie sie sind —
das ist der Grund für die Ordnerstruktur: die URL steht in der ausgelieferten App, im
Play-Console-Feld und im OAuth-Bildschirm, und sie zu ändern kostet ein App-Release.

## Zwei Dinge, die hier schiefgehen können

- **Front Matter.** Jede `.md` braucht den `---`-Block. Fehlt er, behandelt Jekyll die Datei
  als statische Datei und liefert rohes Markdown statt einer Seite.
- **Absolute Links.** Ein Link mit führendem `/` zeigt an der Projektseite vorbei. Links
  zwischen den Seiten bleiben relativ (`moodtrackr/datenschutz.html`, zurück `../`), und
  im Layout geht alles durch `relative_url` — sonst lädt das Stylesheet nicht, und die
  Seite erscheint als unformatierter Text.

Veröffentlicht wird aus *Settings → Pages → Branch `main`, Ordner `/` (root)*.

## Sprache: deutsch, und das mit Absicht

Die Apps sind deutschsprachig, also sind es diese Seiten auch. Google Play schreibt für die
Datenschutzerklärung **keine** Sprache vor — verlangt ist nur eine erreichbare, nicht
geoblockte, unveränderliche URL —, und das Feld in der Play Console nimmt ohnehin nur eine
einzige URL, nicht eine pro Sprachvariante des Eintrags.

Eine englische Fassung kommt, wenn eine App lokalisiert wird, und dann geschlossen:
Oberfläche, Store-Eintrag und Rechtsseite zusammen. Sie kommt als **zusätzliche Datei unter
einem neuen Pfad** — vorgesehen `moodtrackr/privacy.html` neben `datenschutz.html`, mit
gegenseitigen Sprachlinks. Die bestehende URL bewegt sich dabei nie: sie steht in der
ausgelieferten App, im Play-Console-Feld und im OAuth-Zustimmungsbildschirm, und sie zu
ändern kostet ein App-Release.

## Diese Texte sind die einzige Fassung

Es gibt keine Kopie in den App-Repos. Eine zweite Fassung würde driften, und bei einem
Rechtstext ist „veraltet" der Fehlermodus, der zählt.

Umgekehrt heißt das: Einige Aussagen hängen an Code, der hier nicht liegt. Ändert sich dort
etwas, muss es hier nachgezogen werden. Für MoodTrackr (`mood-trackr`) sind das:

| Aussage auf der Seite | Hängt an |
|---|---|
| Höchstens drei Sicherungsgenerationen in Drive | `BackupRepository.kt` — `GENERATIONS_TO_KEEP` |
| Ausschließlich der Scope `drive.appdata` | `GoogleAuthorization.kt` — `SCOPE` |
| Die Konto-Mailadresse liegt nur auf dem Gerät | `BackupStore.kt` — `backup_account_email` |
| Android-Cloud-Backup ist abgeschaltet | `AndroidManifest.xml` — `allowBackup="false"` |
| Der Schlüssel liegt im Android Keystore | `BackupStore.kt`, `data/crypto/` |

Für VocTrainr (`julian-1504/voc-trainr`, privat):

| Aussage auf der Seite | Hängt an |
|---|---|
| Android-Sicherung an, nur Datenbank und Einstellungen, kein Cache | `AndroidManifest.xml` — `allowBackup="true"`; `res/xml/backup_rules.xml`, `data_extraction_rules.xml` |
| Fotos landen nicht in den App-Daten | `data/db/*Entity.kt` — keine Bild-URI; der Scanner schreibt nur in den Cache |
| Scanner und einige Schriftmodelle kommen über Play | `ui/scan/ScanScreen.kt` — `ModuleInstall`; `libs.versions.toml` — `play-services-mlkit-*` |
| Teilen nur über eine Cache-Datei | `transfer/VocabFileStore.kt` — `shareable`; `res/xml/file_paths.xml` |
| Optionaler Name nur lokal, nicht im Export | `data/SettingsRepository.kt` — `USER_NAME`; `transfer/VocabFile.kt` — kein Namensfeld |
| Erinnerung lokal, ohne Push-Dienst | `reminder/ReminderScheduler.kt`, `ReminderWorker.kt` |
| Keine Analyse- oder Werbe-SDKs | `app/build.gradle.kts` — `dependencies` |
| Welche Diagnosedaten ML Kit an Google sendet | Googles Seite *ML Kit – Data disclosure* und die ML-Kit-Module in `libs.versions.toml` (neues Modul → Seite erneut prüfen) |

Dasselbe gilt für das Data-Safety-Formular in der Play Console: Formular und Seite müssen
dasselbe sagen.
