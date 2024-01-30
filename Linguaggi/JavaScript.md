## AJAX
#ajax è un metodo per effettuare richieste al server senza la necessità di ricaricare la pagina da cui è stata inviata
# Oggetti
Tutti gli oggetti di Javascript derivano da un modello base di oggetto, richiamabile tramite:
```Javascript
{}
new Object()
```
## Metodi
### Oggetto base
```Javascript
__proto__ //prototipo su cui si basa l'oggetto
hasOwn(proprietà) //verifica se l'oggetto bersaglio possiede la proprietà indicata
```
## Destructuring
Permette di creare rapidamente un oggetto contenente i vari dati inseriti nelle parentesi graffe. 
```Javascript
cons {data1, data2} = data; //Crea un oggetto data = {data1="data1", data2:"data2"}
```
# DOM
Il #DOM è una rappresentazione dell'intero file .html.
## Valori
| Valore | Descrizione |
| ---- | ---- |
| DOMContentLoaded | Valore che diventa automaticamente true quando l'intera pagine #HTML viene caricata dal #browser |
|  |  |
## Manipolazione del DOM
| Metodo | Descrizione |
| ---- | ---- |
| addEventListener(event, function) | Aggiunge un #listener che attiva la funzione ogni volta che si verifica l'evento dichiarato (es. submit) |
|  |  |
# Operatori logici
[Logical AND](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND)
```Jvascript
<variable_1>?attr && <variable_2> //ritorna il prima parametro (<variabile_1>.attr) se è FLASY, altrimenti ritorna il secondo
```
# Framework
- [[Node.js]] - Framework #backend 
- [[React]] - Framework #front-end 

# Librerie
- [DOMpurify](https://www.npmjs.com/package/dompurify) - Sanificare gli input