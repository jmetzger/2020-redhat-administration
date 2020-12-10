# Beispiele grep 

## Beispiel 1

```
Alle Zeilen ohne Kommentar am Anfang und davon 
Alle Zeilen mit Zahl und danach /tcp 

cat /etc/services | grep -v '^#' | grep '[[:digit:]]/tcp' 
```
