# Find 

## Aufbau 

```
find [wo suche ich ?] [welche/welche Tests sollen erfüllt werden] [welche Aktion?]
find [WO ?] [Test ?] [Aktion ?]
 
# Wenn ich nichts angebe für den Ort sucht find im aktuellen Verzeichnis 
find 
# das gleiche 
find . 
# oder z.B. 
find /etc 
```

## Nach Verzeichnissen in einem Verzeichnis suchen 

```
# nach Verzeichnissen suchen 
find /etc -type d 

# nach allen Verzeichnissen suchen, die dem Benutzer sssd gehören 
find / -type d -user sssd 

# alle Verzeichnisse, eigentümer sssd, name exact "conf" 
find / -type -d -user sssd -name 'conf' 

# alle Verzeichnisse, eigentümer sssd, in name soll "conf" vorkommen 
find / -type -d user sssd -name '*conf*' 

# gleich wie vorher nur case insensitive (egal ob klein oder groß-geschrieben, es wird gefunden)  
find / -type d -user sssd -iname '*CONF*'

# Zusätzlich nach bestimmten rechten suchen 
find / -type d -user sssd  -perm 700

```

## Aktion nach/bei Suche ausführen 

```
# für alle Verzeichnisse, die gefunden werden ein ls -la machen 
find / -type d -user sssd  -perm 700 -exec ls -la {} ';'
# andere Schreibweise 
find / -type d -user sssd  -perm 700 -exec ls -la {} \;
```
