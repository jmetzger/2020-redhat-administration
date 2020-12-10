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

## Fehler bei falschem Pfad ("/" am Anfang) 

```
tar tvf etc.201212101537.tar.gz 
-rw-r--r-- root/root      1412 2020-12-10 09:24 var/lib/dnf/modulefailsafe/perl-DBD-MySQL:4.046:x86_64.yaml
-rw-r--r-- root/root    442368 2020-12-10 15:04 var/lib/dnf/history.sqlite
-rw-r--r-- root/root   5203592 2020-12-10 09:24 var/lib/dnf/history.sqlite-wal

# Das geht nicht, weil der Pfad so nicht im Archiv steht (hier wurden automatisch alle führenden "/" entfernt
tar xzvf etc.202012101537.tar.gz /var/log/messages 

# so ist es richtig / ohne slash am Anfang
tar xzvf etc.202012101537.tar.gz var/log/messages 
```


```
