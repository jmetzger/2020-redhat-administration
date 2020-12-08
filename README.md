# Redhat Administration 

## Als Root arbeiten 

```
# in den root-benutzer 
# passwort des normalen Benutzers eingeben  
sudo su - 
```
## In welchem Zustand (=target) wird das System hochgefahren ? 

```
## Zeigt den Zustand in den das System, wenn es hochfährt 
[root@centos1 ~ ]#systemctl get-default 
graphical-target 
```

## Wie finde ich heraus in welchem Verzeichnis 

```
echo ~
pwd # print working directory 
# - Zeichen leiten Kommentare ein 
```

## Befehl parken und Befehl zurück holen

```
# 1. vor den Befehl # schreiben
# z.B. 
# rm -r verzeichnis # und enter - Taste drücken 

# 2. Befehl zurückholen 
# Pfeil Taste nach oben drücken 
```
