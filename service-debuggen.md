# Service debuggen (Service startet nicht) 

```
# Wir starten den Service und stellen fest erläuft nicht
# systemctl start servicename 
# z.B. 
systemctl start mariadb.service 

# Schritt 1:
# Nach status gucken -> letzte 10 Zeilen sind logfiles 
systemctl status mariadb.service

# Schritt 2: 
# Wenn nicht fündig in Schritt
# nach -u den Servicenamen verwenden 
# z.B. 
journalctl -u mariadb.service

# Schritt 3: 
# a) ins Log-Verzeichnis wechseln 
cd /var/log 
# Sichtprüfung, ob es eine Datei - Verzeichnis gibt, die so ähnlich heisst, wie der Dienst 
# hier: Verzeichnis mariadb
cd mariadb 
# letzte 1000 Zeilen von Log // alle Zeilen davon die error im Text haben 
# Sinnvoll wenn Log-Datei sehr gross 
tail -n 1000 mariadb.log | grep -i error
tail -n 1000 mariadb.log 

# Schritt 4:
# /var/log/messages <- in der allgemeinen Log - Datei suchen 
cd /var/log 
# Eventuell mehr anzeigen, weil alles drin ist. 
tail -n 1000 messages 

