# AJAX
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
ritorna il primo parametro se è FLASY, altrimenti ritorna il secondo
```Jvascript
<variable_1>?attr && <variable_2> //result: attr se FALSY, altrimenti <variable_2> 
```
Logical OR
Ritorna il primo valore se TRUTY, altrimenti il secondo valore (indipendentemente dalla tipologia del dato)
```Javascript
console.log(false||true) //result: true
consoel.log(false||false) //result: false
```
# Framework
- [[Node.js]] - Framework #back-end 
- [[React]] - Framework #front-end 

# Librerie
- [DOMpurify](https://www.npmjs.com/package/dompurify) - #sanificare  degli input
## [Chaijs](https://www.chaijs.com/)
#chaijs permette di effettuare dei test.
### Metodi
**Apertura di un test** 
```Javascript
var.test("nome", ()  => {
	verifica
})
```
**Ricezione della risposta**
```Javascript
var.response;
```
La **response** sarà un #oggetto con la seguente struttura:
```RESPONSE
|-headers
|--get()
|-status
```
**Tipologie di verifica**
```Javascript
var.expect.to.be.equal(<valore_aspettato>);
var.expect.not.to.be.equal(<valore_non_aspettato>);
var.expect.to.have.length(<lunghezza>);
pm.expect.(<valore>).not.is.undefined;
```

## [Cheerio](https://cheerio.js.org/)
