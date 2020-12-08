# Redhat Administration 

## Als Root arbeiten 

```
# in den root-benutzer 
# passwort des normalen Benutzers eingeben  
sudo su - 

## In welchem Zustand (=target) wird das System hochgefahren ? 

```
# Zeigt den Zustand in den das System, wenn es hochfährt 
[root@centos1 ~ ]#systemctl get-default 
graphical-target 
```

