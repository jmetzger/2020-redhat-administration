# Redhat Administration 

## Cheatsheet 

  * https://www2.icp.uni-stuttgart.de/~icp/mediawiki/images/b/bd/Sim_Meth_I_T0_cheat_sheet_10_11.pdf

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
ls -la 
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

## Wie kann ich herausfinden, ob ein Dienst auf dem System existiert und läuft ? 

```
# Dienst existiert 
systemctl list-unit-files -t service | grep -i ssh # grep zeigt alle Zeilen an, in den in der Ausgabe von systemctl das "ssh" oder "SSH" vorkommt   
# Hiermit herausfinden, ob der Dienst läuft 
systemctl status sshd  # wenn wir keine .service dahinter schreiben, geht systemctl davon aus, dass wir einen service meinen 
systemctl status sshd.service 

# lauscht der dienst nach draussen
lsof -i | grep ssh 
# welcher port ist ssh, d.h. welche zahl 
cat /etc/services | grep ssh 
```

## Wo wird festgelegt, welches Repo (Webseite oder FTP) für die Installation von Paketen verwendet wird 

```
/etc/yum/repos.d 
# und dort alle *.repo dateien 
```

## Einen Befehl aus der Historie ausführen ? 

```
history 
# nr. herausfinden, befehl 50 ausführen 
!50 # und return bzw. enter eingeben 
```

## Where bin ich ? (mein Benutzername) 

```
echo $USER 
# oder 
whoami 
```
