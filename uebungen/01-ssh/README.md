# Übung 01

Überprüfen ob man sich mittels ssh auf der Maschine einloggen kann

## Durchführung

```
ssh -o UserKnownHostsFile=/dev/null -i key.pem ubuntu@<hostname>
```

## gewünschtes Ergebnis

Login auf der Maschine
