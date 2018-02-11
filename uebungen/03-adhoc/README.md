# Übung 03

Ad-Hoc Befehle auf der Maschine ausführen

## Details

Manche Befehle muss man nur einmal auf einem Host ausführen, und benötigt dafür kein Playbook. Zu diesem Zweck werden wir in dieser Übung die folgenden Schritte durchführen:

* Uptime des Hosts herausfinden
* Hostname des Hosts herausfinden
* Betriebssystem des Hosts (Linux) herausfinden
* NTP installieren

## Durchführung

```
ansible all --inventory-file=hosts.cfg -m shell -a "uptime"
ansible all --inventory-file=hosts.cfg -m shell -a "hostname"
ansible all --inventory-file=hosts.cfg -m shell -a "lsb_release -a"
ansible all --inventory-file=hosts.cfg -m shell -a "apt-get install -y ntp"
```

## gewünschtes Ergebnis

Abhängig vom jeweiligen Befehl sollte das Ergebnis in etwa wie folgt aussehen:

* uptime
```
hostname123 | SUCCESS | rc=0 >>
 14:07:07 up 2 days, 57 min,  1 user,  load average: 0,02, 0,08, 0,08
```

* hostname
```
hostname123 | SUCCESS | rc=0 >>
hostname123

```

* lsb_release -a
```
hostname123 | SUCCESS | rc=0 >>
Distributor ID: Ubuntu
Description:    Ubuntu 17.10
Release:        17.10
Codename:       artfulNo LSB modules are available.
```

* NTP installieren
```
 [WARNING]: Consider using apt module rather than running apt-get

hostname123 | SUCCESS | rc=0 >>
Reading package lists...
Building dependency tree...
Reading state information...
The following additional packages will be installed:
  libopts25 sntp
Suggested packages:
  ntp-doc
The following NEW packages will be installed:
  libopts25 ntp sntp
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 786 kB of archives.
After this operation, 2.395 kB of additional disk space will be used.
Get:1 http://mirror.ubuntu.net/ubuntu artful/main amd64 libopts25 amd64 1:5.18.12-3 [57,0 kB]
Get:2 http://mirror.ubuntu.net/ubuntu artful-updates/main amd64 ntp amd64 1:4.2.8p10+dfsg-5ubuntu3.1 [642 kB]
Get:3 http://mirror.ubuntu.net/ubuntu artful-updates/main amd64 sntp amd64 1:4.2.8p10+dfsg-5ubuntu3.1 [87,3 kB]
Fetched 786 kB in 0s (2.696 kB/s)
Selecting previously unselected package libopts25:amd64.
(Reading database ... 189376 files and directories currently installed.)
Preparing to unpack .../libopts25_1%3a5.18.12-3_amd64.deb ...
Unpacking libopts25:amd64 (1:5.18.12-3) ...
Selecting previously unselected package ntp.
Preparing to unpack .../ntp_1%3a4.2.8p10+dfsg-5ubuntu3.1_amd64.deb ...
Unpacking ntp (1:4.2.8p10+dfsg-5ubuntu3.1) ...
Selecting previously unselected package sntp.
Preparing to unpack .../sntp_1%3a4.2.8p10+dfsg-5ubuntu3.1_amd64.deb ...
Unpacking sntp (1:4.2.8p10+dfsg-5ubuntu3.1) ...
Processing triggers for ureadahead (0.100.0-20) ...
Processing triggers for libc-bin (2.26-0ubuntu2.1) ...
Processing triggers for systemd (234-2ubuntu12.1) ...
Setting up libopts25:amd64 (1:5.18.12-3) ...
Processing triggers for man-db (2.7.6.1-2) ...
Setting up sntp (1:4.2.8p10+dfsg-5ubuntu3.1) ...
Setting up ntp (1:4.2.8p10+dfsg-5ubuntu3.1) ...
Created symlink /etc/systemd/system/network-pre.target.wants/ntp-systemd-netif.path → /lib/systemd/system/ntp-systemd-netif.path.
Created symlink /etc/systemd/system/multi-user.target.wants/ntp.service → /lib/systemd/system/ntp.service.
ntp-systemd-netif.service is a disabled or a static unit, not starting it.
Processing triggers for libc-bin (2.26-0ubuntu2.1) ...
Processing triggers for systemd (234-2ubuntu12.1) ...
Processing triggers for ureadahead (0.100.0-20) ...
```
