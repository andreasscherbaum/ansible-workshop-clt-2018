# Übung 03

Ein Playbook verstehen und ausführen

## Details

Playbooks sind die Beschreibung des Sollzustandes, den die Konfiguration einer Maschine haben soll. Im Folgenden wollen wir

* NTP auf all unseren Maschinen installieren und
* Sicherstellen, dass der NTP daemon läuft

Führen wir das Playbook ein zweites Mal aus (der Sollzustand besteht also bereits), wird die Ausgabe von Ansible zeigen, dass keine weiteren Änderungen durchgeführt wurden (Idempotenz).

## Durchführung

```
ansible-playbook install-ntp.yml

ansible-playbook install-ntp.yml
```

## gewünschtes Ergebnis

* erstes Mal
```

PLAY [Install NTP and set timezone] ********************************************

TASK [setup] *******************************************************************
ok: [host1]
ok: [host2]

TASK [install NTP package] *****************************************************
changed: [host1]
changed: [host2]

TASK [ensure ntp is running] ***************************************************
ok: [host1]
ok: [host2]

PLAY RECAP *********************************************************************
host1                      : ok=3    changed=1    unreachable=0    failed=0   
host2                      : ok=3    changed=1    unreachable=0    failed=0   

```


* zweites Mal
```

PLAY [Install NTP and set timezone] ********************************************

TASK [setup] *******************************************************************
ok: [host1]
ok: [host2]

TASK [install NTP package] *****************************************************
ok: [host1]
ok: [host2]

TASK [ensure ntp is running] ***************************************************
ok: [host1]
ok: [host2]

PLAY RECAP *********************************************************************
host1                      : ok=3    changed=0    unreachable=0    failed=0   
host2                      : ok=3    changed=0    unreachable=0    failed=0   

```
