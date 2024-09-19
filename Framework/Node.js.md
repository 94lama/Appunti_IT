# Introduzione
Node.js è un #framework #back-end per [[JavaScript]].
**lts** = long term support.
# npm
#npm è il #package-manager di Node.js
## Librerie
La lista delle librerie richieste è contenuta all'interno del fil **package.json**, mentre quella delle librerie installate (escluse le #cdn) è all'interno del file **package-lock.json**
## Installazione
L'installazione avviene, all'interno del progetto, tramite il comando
``` bash
npm install
```
Mentre, l'installazione di pacchetti successivi, avviene tramite il comando:
``` bash
npm i nomeLibreria
npm i nomeLibreria@latest // installa l'ultima versione della libreria
```
E' possibile #unire tutti i file in versione #minificata, a  progetto finito, tramite  il comando:
```Bash
npm run build
```
mentre, se si vuole avere solo una visualizzazione delle direttive importate, si può eseguire il comando
```Bash
npm run dev //compila i vari file in maniera continua, utilizzata in fase di sviluppo
```
## Comandi
Eseguire una scansione del codice
``` bash
npm audit
```
Esegue l'analisi del codice ed effettua gli aggiornamenti delle #dependency vulnerabili (scartando quelle con l'etichetta **no fix available**, il quale fix potrebbe causare malfunzionamenti all'applicazione)
``` bash
npm audit fix
```
	--force # effettua il fix di tutte le dipendenze vulnerabili
# package.json
```JSON
node: "modules" //permette di utilizzare i metodi "import" ed "export" per gestire i pacchetti
```
# Moduli
## fs
Oggetto che permette di visualizzare e/o leggere file all'interno della macchina
```Struttura
└ writeFileSync(<percorso><nome_file>) //Permette di creare un file
```
## JSON Server
Permette di creare un prototipo di database in JSON, da utilizzare in fase di #testing
```sh
npm install json-server
```
per utilizzarlo, una volta installato, bisognerà creare un file json (di solito di chiama ```db.json```), tramite il comando
```sh
npz json-server <percorso_file>/<nome_file>
```

# vite.config.js
#vite è un file #JavaScript che permette di rendere un file #minificato (con attributo **.min**, ovvero contenente l'intero codice in una sola riga).
# Librerie
## Express
Express è una libreria che permette di velocizzare la creazione di una struttura #back-end in JavaScript.
### Richieste HTML
#### GET
```JavaScript
res = 
res.get(route, middleware_1, middleware_2, ...)
```
### Multer
Libreria che permette di gestire i #middleware per le richieste #http 
## ECMA
## child-process
Permette di inserire script nello #shell
### cheerio.js
Simile a jQuery
```Javascript
const $ = cheerio.load(pm.response.text())
const links = $('a') //seleziono i tag anchor

if (links.length > 0) {
	for (const link of Array.from(links)) {
		let var = link.attribs.rel //prelevo tutti gli attributi "rel" di link
	}
}
```
### jQuery