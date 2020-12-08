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

## Verzeichnis anzeigen 

```
ls -l  # Verzeichnis alphabetisch anzeigen 
ls -ltr # t letzte Modfikation zuerst anzeigen (Modifizierugsdatum) 
        # umdrehen - d.h. genau anders herum 
```

## Hilfe bekommen

```
man pwd # das funktioniert in Centos/Redhat zu 99,9% 
# und bei eingebauten Befehlen (in die bash eingebaut)
help pwd
```

## Dateien / Verzeichnisse löschen 

```
rm training 
# nachfrage löschen mit "y" oder "j" beantworten 
```

## Alias einrichten und verwenden 

```
# In diesem Beispiel geht das nur in der aktuellen Session 
alias zeigmal='ls -la'
zeigmal 
```
