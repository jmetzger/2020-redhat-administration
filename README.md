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

## Wie finde ich heraus in welchem Verzeichnis ich bin ?

```
echo ~
pwd # print working directory 
# - Zeichen leiten Kommentare ein 
```

## Wie wechsle ich in Verzeichnis 

```
# in meiner Heimatzverzeichnis
cd ~
# noch einfacher
cd 

# absolute in ein Verzeichnis reinwechseln 
cd 
pwd 
# aus dem Heimatverzeichnis direkt ins etc vezeichnis 
cd /etc
```

## Befehl parken und Befehl zurück holen

```
# 1. vor den Befehl # schreiben
# z.B. 
# rm -r verzeichnis # und enter - Taste drücken 

# 2. Befehl zurückholen 
# Pfeil Taste nach oben drücken 
```
## Verzeichnis anlegen
```
cd /home/teilnehmer01/.local
mkdir bin
cd bin 
pwd

# verzeichnisse recursiv anlegen   
mkdir -p daten/baustelle/gewerk



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

## Wo sucht Linux nach Programmen / auch das eigene Shell-Script

```
# in 
echo $PATH # und zwar in alle Pfaden, die dort ":" - separiert angegeben sind. 
# wenn er es dort nicht findet, kann er es nicht ausführen
# Beispiel 
echo "#!/bin/bash" > /home/teilnehmer03/test.sh 
echo "echo hallo du" >> /home/teilnehmer03/test.sh

cd /home/teilnehmer03 
# das geht nicht
test.sh  # weil es nicht in seinem Pfad ist in $PATH
# das geht
./test.sh 
```

## Umgebungsvariablen anzeigen

```
env
# eine spezielle z.B PATH
echo $PATH
echo $USER
```

## Verzeichnis anlegen und Rechte 

```
# Neue Dateien und Verzeichnisse
# haben die Besitz-Rechte des Benutzers,
# der sie anlegt, d.h.  Benutzername und seine Hauptgruppe
# z.B. trainer01 gehört der Hauptgruppe trainer01 an.
cd # wechselt in das Heimatverzeichnis 
mkdir testordner

# mit id können wir sehen, wer wir sind und welcher Hautpgruppe wir angehören 
id 
```

## Datei anlegen mit Umleitung 

```
cd /home/trainer01/.local
mkdir bin
cd bin 
echo '#!/bin/bash' > test2.sh
echo 'echo sonnenschein' >> test2.sh
chmod u+x test2.sh
cat test2.sh
```

## Prozesse anzeigen 

```
ps aux
# bestimmte prozesse
ps aux | grep ssh
top 

# alle zielen mit bestimmter und nachranging aus diesen Zeile nur die mit ssh
cat /run/ssh.pid 
ps aux | grep 928 | grep ssh
# oder anzahl
ps aux | grep 928 | grep -c ssh 

```

## In less/man suchen

```
# suche 
# / eingeben und nach was ihr sucht, z.B. unix + Return 
# nächstes Ergebnis: n - Taste drücken 
# letztes Ergebnis: N - Taste drücken 
```


## Nach paket suchen und installieren 

```
yum search apache | grep httpd 
sudo yum install httpd
# Alle Fragen mit "j" beantworten 

# wie heisst der dienst 
systemctl list-unit-files -t service | grep httpd 

# dienst aktivieren 
systemctl enable httpd
systemctl start httpd 
echo $? # Zeigt Rückgabewert des letzten Befehl -> wenn 0 -> erfolgreich 

```

## Grafische Oberfläche abschalten 

```
# alle targets anzeigen 
systemctl list-unit-files -t target 

# has to be AllowIsolate in target definition 
systemctl cat multi-user.target 
systemctl isolate multi-user.target 
systemctl set-default multi-user.target

