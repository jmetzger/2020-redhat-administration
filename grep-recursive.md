# Mit grep recursive in Ordnern suchen 

```
# Suche nach dem Vorkkommen in einer Datei von 'documentroot'
# !! im gesamten /etc - Verzeichnis 
# !! Egal ob groß- oder kleingeschrieben 
grep -inr 'documentroot' /etc

# über mehrere verzeichnisse
grep -inr 'documentroot' /etc /var 

```
