# Suche mit Locate 

```
# Alle Ergebnisse stammen aus einer Datenbank
# Dieser wird, wenn timer aktiviert (s. Doku) 
# täglich 1x nachts aktualisiert.

# Zeige nur Ergebnisse an, die auch im Filesystem
locate -e file1 

# Problem ist, dass hier nach pattern gesucht, wird, d.h. ganz viele Ergebnisse, wenn ich z.B. nach "file" suche
locate -e file 
# Anzahl der Ergebnisse
locate -e -c file 

# Suche einschränken, nur Ergebnisse wo file im Dateiname, nicht im Pfad
locate -e --basename -c file 

# Lösung mit regex suchen - Variante1: nur Dateien, wo am Anfang des Filenamens "file" drin steht. 
locate -e --basename --regex "^file" 

# Variante filename soll exact so heissen 
locate -e --basename --regex "^file$"
```
