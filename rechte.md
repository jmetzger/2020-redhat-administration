# Rechte
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



## Spezielles Verhalten von vi bei w! (overwrite) 

  * https://unix.stackexchange.com/questions/502826/how-vim-overwrites-readonly-mode
