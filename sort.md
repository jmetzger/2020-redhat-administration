# Sort-Befehl - Beispiele 

```
# Numerisch sortieren 
cat /etc/services | grep -v '^#' | grep tcp | tr -s ' ' | cut -d ' ' -f 2 | sort -n

# Numerisch absteigend 
cat /etc/services | grep -v '^#' | grep tcp | tr -s ' ' | cut -d ' ' -f 2 | sort -nr 

```
