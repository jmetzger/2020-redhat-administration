# sed und awk

## Beispiele awk 

```
# Alle Zeilen anzeigen in denen tcp vorkommt. 
cat /etc/services | awk '/tcp/' 

# Aus jeder Zeile in der tcp vorkommt, nur die Spalte 1 anzeigen
cat /etc/services | awk '/tcp/ { print $2 }'

# Zeilen mit mehr als 18 Zeichen anzeigen
awk 'length($0) > 18' /etc/services 

```

## Beispiele sed 

```
cp -a /etc/services /etc/sedtest
# Text in jeder Zeile ersetzen 
sed 's/tcp/suppe/' /etc/sedtest  

# Alle Vorkommen in der Zeile ersetzen 
sed 's/tcp/suppe/g' /etc/sedtest

# Nur in Zeile ersetzen 
sed '3 s/tcp/suppe/g' /etc/sedtest 

# Letzte Zeile löschen 
sed '$d' /etc/sedtest 

# Zeile 12 bis zur letzten Zeile löschen  
sed '12,$d' /etc/sedtest 
```

## Direkt in file wieder reinschreiben 

```
sed -i '12,$d' /etc/sedtest
``` 


