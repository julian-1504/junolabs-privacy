# junolabs — Rechtsseiten

Die öffentlichen Rechtsseiten der junolabs-Apps, ausgeliefert über GitHub Pages:
<https://julian-1504.github.io/junolabs-privacy/>

Das Repo ist öffentlich, damit die Seiten erreichbar sind — Google Play verlangt eine
Datenschutzerklärung für **jede** App, auch für kostenlose und auch für solche, die keine
Daten erheben, und der OAuth-Zustimmungsbildschirm verlangt dieselbe URL. Der Quellcode der
Apps liegt woanders und ist nicht öffentlich.

## Aufbau

```
_config.yml              Theme und baseurl
index.md                 → /junolabs-privacy/
moodtrackr/
  index.md               → /junolabs-privacy/moodtrackr/
  datenschutz.md         → /junolabs-privacy/moodtrackr/datenschutz.html
```

Eine weitere App bekommt einen weiteren Ordner. Bestehende URLs bleiben dabei, wie sie sind —
das ist der Grund für die Ordnerstruktur: die URL steht in der ausgelieferten App, im
Play-Console-Feld und im OAuth-Bildschirm, und sie zu ändern kostet ein App-Release.

## Zwei Dinge, die hier schiefgehen können

- **Front Matter.** Jede `.md` braucht den `---`-Block. Fehlt er, behandelt Jekyll die Datei
  als statische Datei und liefert rohes Markdown statt einer Seite.
- **Absolute Links.** Ein Link mit führendem `/` zeigt an der Projektseite vorbei. Links
  zwischen den Seiten bleiben relativ (`moodtrackr/datenschutz.html`, zurück `../`).

Veröffentlicht wird aus *Settings → Pages → Branch `main`, Ordner `/` (root)*.

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

Dasselbe gilt für das Data-Safety-Formular in der Play Console: Formular und Seite müssen
dasselbe sagen.
