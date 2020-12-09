# Rechte

## Allgemein 
```
- | rw- |

     u  => eigentümer (owner)

r = Leserechte 
w = Schreibrechte 
x = Ausführungsrecht 


Schritt 1:
- Linux Kernel findet heraus wer ich bin
  und konzentriert sich nur auf diese Rechte


Beispiel:
trainer01 will auf datei zugreifen:
(und gehört der Gruppe trainer01 an) 

--w-rw-r--. 1 trainer01 trainer01 20  9. Dez 10:02 testdatei

-> Du bist trainer01, dann bist du der Eigentümer
der Datei testdatei und ich kümmere mich nur 
um die --w (ganz ehrlich: Der Rest ist mir egal!) 


## Schreibrechte für Eigentümer enziehen, Leserechte vergeben 

chmod u=r testdatei # genau die folgenden Rechte, egal was vorher dort stand 
chmod u+r,u-w testdatei


```

## Verzeichnis 

```
mkdir testdir
# Alle Berechtigungen für User entzogen 
chmod u= testdir
# wir können nicht reinwechseln 
# permission denied
cd testdir
# Ausführungsrechte gegeben fürs aktuelle Verzeichnis = testdir 
# wir können zwar reinwechseln aber nix lesen und schreiben 
chmod u+x . 
# Schreibrechte hinzufügen, jetzt können dateien erstellen, d.h. in das Verzeichnis schreiben 
# Aber nicht das Verzeichnis lesen, ausser wir kennen dateinamen 
chmod u+w .
echo "test" > testdatei2
# geht nicht ! lesen nicht erlaubt 
ls -la
# geht, lesen zwar nicht erlaubt, aber wir kennen den Dateinamen 
ls -la testdatei2
# jetzt dürfen wir wieder alles = rwx 
chmod u+r .

```

## Spezielles Verhalten von vi bei w! (overwrite) 

  * https://unix.stackexchange.com/questions/502826/how-vim-overwrites-readonly-mode
