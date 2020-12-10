# Komprimieren mit bzip2 

```
cp -a /etc/services /root/services 
cd /root
# Variante 1: ausgabe und bearbeitung über pipe und dann umleiten in file 
cat services | bzip2 -k > services.bz2 
# Variante 2: -k für keep (behält Originaldateien) 
bzip2 -k services  # entstellt automatisch die Datei services.gz 

```
