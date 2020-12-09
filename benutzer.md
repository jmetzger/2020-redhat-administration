# Benutzer unter Linux 

## Alle Gruppen anzeigen in den ein Benutzer Mitglied ist 

```
# als root reinwechseln 
sudo su 
groups trainer01 

```

## Neuen Benutzer anlegen (Centos 8)  

```
useradd benutzer 
passwd benutzer 

# Wenn er sudo-Rechte (root) haben sein soll,
# dann 
usermod -aG wheel benutzer
```

## Besitz- und Gruppenrechte ändern 

```
# User und Gruppe ändern 
chown trainer01:trainer01 testdatei22 
# User ändern 
chown root testdatei22 
# Gruppe ändern 
chown :root testdatei 22 
```
