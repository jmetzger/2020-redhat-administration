# Redhat Administration 

1. [Rechte unter Linux](rechte.md) 
1. [Benutzer unter Linux](benutzer.md)
1. [Suche mit Locate](suche-locate.md)
1. [Suche mit Find](find.md)
1. [!!!Recursive Suche mit Grep !!!](grep-recursive.md)
1. [Übung](uebung1.md) 
1. [Übung: Installieren von Diensten](uebung-dienste.md) 
1. [Übung: Find](uebung-find.md) 


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


## Verzeichnis anzeigen / Dateien anzeigen

### Verzeichnis anzeigen
```
ls -l  # Verzeichnis alphabetisch anzeigen 
ls -ltr # t letzte Modfikation zuerst anzeigen (Modifizierugsdatum) 
        # umdrehen - d.h. genau anders herum 
ls -la 
```

### Dateien anzeigen (spezielle) 
```
# um zu überprüfen, ob datei im verzeichnis existiet 
ls -la dateiname 
# oder 
ls -la | grep dateiname 
```

### Verzeichnisse kopieren 

```
# das kopierte VErzeichnis gehört root:root 
# in den root-benutzer wechseln
sudo su 
cp -r fotos fotos.bkup 

# das kopierte Verzeichnis hat die gleichen Rechte wie das Ursprungsverzeichnis 
# in den root-benutzer wechseln 
cp -a fotos fotos.bkup2
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

## Dateien verschieben  

```
mv vonhier nachhier 
# Beispiel 
mv datei ~/.local/bin
# Achtung, wenn verzeichnis existert, wird datei unter diesem namen angelegt
mv datei ~/.local/sbin 
cd ~/.local/bin 
ls -la sbin 
[trainer01@centos8-01 .local]$ ls -la sbin
-rw-rw-r--. 1 trainer01 trainer01 29  9. Dez 09:44 sbin
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
```

## Automatische Indizierung des System für die Suche mit locate aktivieren

  * Das ist auf Centos 8 nicht standardmäßig der Fall 
  * https://bugzilla.redhat.com/show_bug.cgi?id=1697244
  
```
# Fix
# Schritt 1: händisch aktualisieren
updatedb 
# Schrit 2: Timer aktivieren, damit es ab dem nächsten Tag läuft 
# Timer aktivieren, damit dieser nach dem nächsten Reboot automatisch läuft 
systemctl enable mlocate-updatedb.timer
# Timer jetzt gestartet für nächsten Durchlauf (um 24:00 jeden Tag) 
systemctl start mlocate-updatedb.timer
# Status
systemctl status mlocate-updatedb.timer
# Alle Timer von systemd 
systemctl list-timers
# Hier kann ich sehen was im Timer eingertragen (wann läuft dieser)
systemctl cat mlocate-updatedb.timer
# Hier kann ich sehen, welches Programm der Timer startet 
# Warum: *.service und *.timer - Dateien mit gleichem gelten als zusammengehörig  
systemctl cat mlocate-updatedb.service
```
