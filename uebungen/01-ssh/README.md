# Übung 01

Überprüfen ob man sich mittels ssh auf der Maschine einloggen kann

## Durchführung

```
ssh -o UserKnownHostsFile=/dev/null -i key.pem ubuntu@<IP Adresse>
```

Die IP-Adresse(n) der Maschine(n) sind in der Datei _inventory_ zu finden.


## gewünschtes Ergebnis

Login auf der Maschine
