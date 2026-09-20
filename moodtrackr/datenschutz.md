---
layout: default
title: Datenschutzerklärung
---

# Datenschutzerklärung für MoodTrackr

Stand: 20. September 2026

## Wer verantwortlich ist

Julian Alt

E-Mail: junolabs@julian-alt.de

Unter dieser Adresse erreichst du den Anbieter mit allen Fragen zum Datenschutz.

## Die kurze Fassung

MoodTrackr speichert alles auf deinem Gerät. Es gibt keinen Server des Anbieters, kein
Nutzerkonto und keine Anmeldung. Der Anbieter erhält keine deiner Einträge — weder deine
Stimmungen noch deine Kommentare noch deine Fragen. Die App enthält keine Werbung, keine
Analyse-Werkzeuge und keine Tracking-Bibliotheken.

## Welche Daten die App verarbeitet

Alles, was du einträgst — Stimmung, Energielevel, Kommentare, Fragen und die dazugehörigen
Zeitstempel — wird ausschließlich in einer Datenbank auf deinem Gerät gespeichert. Diese
Daten verlassen dein Gerät nur in den beiden unten beschriebenen Fällen, und beide löst du
selbst aus. Androids eigenes Cloud-Backup ist für diese App abgeschaltet
(`allowBackup="false"`), damit deine Einträge nicht auf einem Weg abfließen, den die App
nicht kontrolliert.

Die abendliche Erinnerung wird vollständig auf deinem Gerät geplant und ausgelöst; es ist
kein Push-Dienst beteiligt und es werden dafür keine Daten übertragen.

## Verschlüsselte Sicherung in Google Drive (optional)

Wenn du die Sicherung einschaltest, legt die App eine verschlüsselte Kopie deiner Daten in
einem versteckten Ordner deines eigenen Google Drive ab (`appDataFolder`). Dazu:

- Die Verschlüsselung passiert **auf deinem Gerät**, bevor irgendetwas übertragen wird. Der
  Schlüssel wird aus deiner Passphrase abgeleitet, und die Passphrase verlässt dein Gerät
  nie. Google speichert eine Datei, die Google nicht lesen kann. Der Anbieter ebenfalls
  nicht.
- Die App fragt genau eine Berechtigung an: `https://www.googleapis.com/auth/drive.appdata`.
  Das ist ein versteckter, app-eigener Ordner. Auf deine übrigen Dateien in Google Drive hat
  die App keinerlei Zugriff.
- Die Mailadresse des Google-Kontos, das du auswählst, speichert die App **auf deinem
  Gerät**, damit du siehst, welches Konto verbunden ist. Sie wird nicht an den Anbieter
  übertragen und beim Abschalten der Sicherung gelöscht.
- Die Daten liegen in **deinem** Google-Konto, nicht beim Anbieter. Für die Verarbeitung
  durch Google gilt die Datenschutzerklärung von Google.
- Du kannst die Sicherung jederzeit abschalten und die abgelegten Dateien dabei löschen
  lassen. Ist Drive in diesem Moment nicht erreichbar, schaltet die App die Sicherung
  trotzdem ab — die Dateien bleiben dann liegen und lassen sich in deinem Google-Konto
  selbst entfernen.

Rechtsgrundlage: deine Einwilligung (Art. 6 Abs. 1 lit. a DSGVO), die du durch das
Einschalten der Funktion erteilst und durch das Abschalten widerrufst.

## Export deiner Daten

Über *Einstellungen → Deine Daten mitnehmen* schreibt die App alle Einträge in eine
unverschlüsselte JSON-Datei an einen Ort, den du selbst auswählst. Weil sie unverschlüsselt
ist, solltest du sie entsprechend ablegen; sie verlässt dein Gerät nicht, außer du
verschiebst sie selbst.

## Wie die Daten geschützt sind

Die Datenbank liegt im privaten Speicherbereich der App. Andere Apps auf dem Gerät können
sie nicht lesen. Der Schlüssel, mit dem die automatische nächtliche Sicherung arbeitet, wird
im Android Keystore verwahrt, also in dem dafür vorgesehenen, hardwaregestützten
Schlüsselspeicher des Systems, und nicht als Datei daneben. Die Übertragung nach Google
Drive läuft ausschließlich über TLS.

## Wie lange die Daten bleiben

Deine Einträge auf dem Gerät bleiben so lange, bis du sie löschst oder die App
deinstallierst. Eine automatische Löschung nach Zeit gibt es nicht — es sind deine
Aufzeichnungen, und wann sie weg sollen, entscheidest du.

In Google Drive liegen höchstens **drei Sicherungen**. Bei jeder neuen Sicherung löscht die
App die älteste. Schaltest du die Sicherung ab, werden alle Dateien gelöscht und der lokale
Schlüssel entfernt.

## Was die App nicht tut

- Keine Werbung und keine Werbe-SDKs
- Keine Analyse, kein Crash-Reporting, keine Nutzungsstatistik
- Keine Werbe-ID (Advertising ID) und kein Geräte-Fingerprinting
- Keine Weitergabe von Daten an Dritte

## Deine Rechte

Dir stehen nach DSGVO die Rechte auf Auskunft, Berichtigung, Löschung, Einschränkung,
Datenübertragbarkeit und Widerspruch zu. In der Praxis brauchst du dafür niemanden zu
fragen: Der Anbieter hat deine Daten nicht.

- **Auskunft und Übertragbarkeit:** die Export-Funktion in der App.
- **Löschung:** Einträge in der App löschen, die Sicherung abschalten (dabei die Kopie in
  Drive löschen lassen) oder die App deinstallieren.

Wenn du dennoch eine Frage hast, erreichst du den Anbieter unter junolabs@julian-alt.de. Du
hast außerdem das Recht, dich bei einer Datenschutz-Aufsichtsbehörde zu beschweren.

## Alter

MoodTrackr richtet sich an Jugendliche ab 13 Jahren. Die App fragt weder nach dem Namen noch
nach dem Alter noch nach einer E-Mail-Adresse und legt kein Nutzerkonto an.

## Änderungen

Wird diese Erklärung geändert, steht das neue Datum oben. Wesentliche Änderungen werden
zusätzlich in den Release-Notes der App genannt.
