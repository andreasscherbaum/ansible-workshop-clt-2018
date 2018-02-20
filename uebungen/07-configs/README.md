# Übung 07

Webserver und Datenbank konfigurieren, Dienste neu starten

## Details

Diese Übung konfiguriert den Webserver (genauer gesagt das PHP) und die Datenbank, und startet bei Änderungen die Dienste mittels eines Triggers neu.

Im Folgenden wollen wir

* Das Error Logging und weitere Einstellungen in PHP anpassen
* Die Datenbank auf allen Netzwerk Devices aktivieren
* Einen neuen Datenbank Nutzer erstellen
* Eine neue Datenbank erstellen

Das Passwort für den Datenbank Nutzer wird dynamisch erstellt, und in einer Datei _db-account-test.txt_ im Hauptverzeichnis gespeichert.


## Durchführung

```
ansible-playbook site.yml
```

## gewünschtes Ergebnis

```

```
