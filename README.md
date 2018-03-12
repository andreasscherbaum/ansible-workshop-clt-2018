# ansible-workshop-clt-2018

Ansible Workshop für die Chemnitzer Linux-Tage 2018

## Inhalt

Dieses Repository enthält die Slides und Übungen für einen [Ansible](https://www.ansible.com/) Workshop während der Chemnitzer Linux-Tage 2018.

## Vortragende

* Jens Kubieziel (Spezialist für IT-Sicherheit und Datenschutzbeauftragter, [Octopi.Consulting](https://torservers.net/)) / [Homepage](https://kubieziel.de/)
* Andreas Scherbaum (Principal Software Engineer) / [Homepage](http://andreas.scherbaum.la/)
* Andreas Krause (Senior Specialist, Zero.One.Data, DB Systel GmbH)

## Anmeldung

https://chemnitzer.linux-tage.de/2018/en/programm/beitrag/145

## Vorkenntnisse

* Grundlagen in der Administration eines Linux-Systems sowie in der Benutzung von SSH
* Umgang mit einem Texteditor

## Voraussetzungen

* Laptop mit gängiger, aktueller Linux-Distribution (z.B. Ubuntu >= 16.04, Debian >= stretch)
* Installiertes Ansible >= 2.1
* Git
* SSH client

## Vorbereitungen

* Clone des Git Repos:
    ```console
    git clone https://github.com/andreasscherbaum/ansible-workshop-clt-2018
    ```
* Wechsel in das Repo:
    ```console
    cd ansible-workshop-clt-2018
    ```
* Speichern der drei Dateien `ansible.cfg`, `inventory` und `key.pem` aus der Email mit den Zugangsdaten in das Verzeichnis `ansible-workshop-clt-2018`
* Anpassen der Permissions für `key.pem`:
    ```console
    chmod 0600 key.pem
    ```
* Setzen der Umgebungsvariable `ANSIBLE_CONFIG`:
    ```console
    export ANSIBLE_CONFIG=$(pwd)
    ```

## Nach den Chemnitzer Linux-Tagen 2018

Die Übungen in diesem Workshop kann man auch unabhängig vom CLT 2018 in Chemnitz nutzen. Allerdings muss man dafür seine eigene Umgebung mit zwei Servern (zum Beispiel virtuellen Maschinen) aufsetzen. Auf beiden Maschinen wird Debian oder Ubuntu vorausgesetzt, außerdem muss der verwendete Unix-User "sudo"-Rechte haben. Folgende Dateien werden benötigt:

### `ansible.cfg`

Diese Datei wird im ausgecheckten Hauptverzeichnis abgelegt. Beispielinhalt:

```ini
[defaults]
inventory = $ANSIBLE_CONFIG/inventory
private_key_file = $ANSIBLE_CONFIG/key.pem
remote_user = ubuntu
host_key_checking = False
```

Der `remote_user` muss an den Nutzer angepasst werden, der sich später in die virtuellen Maschinen einloggen wird. Die Datei in `private_key_file` wird verwendet, um sich mit dem darin enthaltenen privaten Schlüssel auf den VMs anzumelden. Ist der Zugang bereits über ssh-keyless Login gewährleistet, kann diese Zeile entfernt werden.

### `inventory`

Diese Datei enthält Informationen über die virtuellen Maschinen. Diese Datei wird ebenfalls im ausgecheckten Verzeichnis abgelegt. Beispielinhalt:

```ini
[all]
host1 ansible_host=<IP VM 1>
host2 ansible_host=<IP VM 2>

[dbservers]
host1 ansible_host=<IP VM 1>

[webservers]
host2 ansible_host=<IP VM 2>
```

### `key.pm`

Diese Datei enthält den privaten Schlüssel, um sich auf den VMs anzumelden.
