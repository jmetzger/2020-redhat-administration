# tar 

## Archiv erstellen 

```
tar cvfz etc.202012101537.tar.gz /var
```

## Files in/aus archiv anzeigen 
```
# t = listing 
tar tvf etc.202012101537.tar.gz 
# Rückgabewert mus 0 sein 
echo $? 
```

## Archiv entpacken 

```
# Achtung entpackt alles im Verzeichnis in dem ich bin 
# bei test, erst testverzeichnis erstellen 
mkdir /root/testdir
cp -a etc.202012101537.tar.gz /root/testdir
cd /root/testdir 
tar xzvf etc.202012101537.tar.gz 
```

## Einzelne Dateien entpacken 

```
cd /root/testdir 
rm -fR var 
# es wird nur var/log/messages entpackt 
tar xzvf etc.202012101537.tar.gz var/log/messages 
```
