# Übung 01

Erreichbarkeit der Maschine überprüfen

## Durchführung

```
ansible all -m ping --inventory-file=hosts.cfg
```

## gewünschtes Ergebnis

```
hostname.domain.tld | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
```
