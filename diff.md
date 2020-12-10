# Verzeichnisse und Dateien vergleichen (diff) 

```
cp -a /etc /etc3 
diff -r /etc /etc3 

## Datei vergleichen 
echo "#test" >> /etc3/services 
diff /etc/services /etc3/services 
```
