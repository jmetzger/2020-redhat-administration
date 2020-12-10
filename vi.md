# vi

## vi aufrufen 

```
vi dateiname # auch für neue Datei  
```

## vi verlassen mit speichern 
```
ESC + : + x + RETURN (Diese 3 Tasten hintereinander drücken) 
```

## Zeilennummer aktivieren 

```
# Interactive 
ESC + : + set number + ENTER # ESC : ENTER 

# immer für den Benutzer root 
cd /root 
echo "set number" >> .vimrc 
ln -s .vimrc .virc ## damit das mit vi und vim funktioniert 
```

## Letzten Befehl rückgängig machen 

```
ESC + u # ESC u 
```

## Zeilen löschen 
```
ESC + dd # eine Zeile löschen 
ESC + 100dd # 100 Zeilen löschen / Achtung Blindflug -> am Ende kommt die Meldung in der letzten Zeile 
```

## Zeichen löschen 
```
ESC # einmalig  
x  # dann jeweils an der gewünschten Stelle 
```

## Visuelles Kopieren (Bereich markieren -> klein v) 
```
ESC + v # ESC v
#Dann Text markieren wie gewünscht
# Dann entweder Kopieren
ESC + y 
# oder Ausschneiden 
ESC + x 

### An anderer wieder einfügen 
ESC  + p 
```

## Visuelles Kopieren (Zeilenweise) 

```
ESC + V # ESC V
#Dann Text markieren wie gewünscht
# Dann entweder Kopieren
ESC + y 
# oder Ausschneiden 
ESC + x 

### An anderer wieder einfügen 
ESC  + p 
```
