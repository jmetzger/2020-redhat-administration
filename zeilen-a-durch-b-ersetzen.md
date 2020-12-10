# Bestimmte Zeilen -> Worta durch Wortb ersetzen 

```
# Alle Zeilen die gefunden werden -> tcp durch noe ersetzt 
cat /etc/services | grep -v '^#' | grep tcp | tr 'tcp' 'noe'
```
