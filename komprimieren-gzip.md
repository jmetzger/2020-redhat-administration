# Komprimieren mit gzip 

```
cp -a /etc/services /root/services 
cd /root
# Variante 1: ausgabe und bearbeitung über pipe und dann umleiten in file 
cat services | gzip -k > services.gz 
# Variante 2: -k für keep (behält Originaldateien) 
gzip -k services  # entstellt automatisch die Datei services.gz 

```

