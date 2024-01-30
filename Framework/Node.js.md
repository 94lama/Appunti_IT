# Introduzione
Node.js è un #framework #backend per [[JavaScript]].
**lts** = long term support.
# npm
#npm è il #package-manager di Node.js
## Librerie
La lista delle librerie richieste è contenuta all'interno del fil **package.json**, mentre quella delle librerie installate (escluse le #cdn) è all'interno del file **package-lock.json**
## Comandi

### Installazione
L'installazione avviene, all'interno del progetto, tramite il comando
```
npm install
```
Mentre, l'installazione di pacchetti successivi, avviene tramite il comando:
```
npm i nomeLibreria
npm i nomeLibreria@latest // installa l'ultima versione della libreria
```
E' possibile #unire tutti i file in versione #minificata, a  progetto finito, tramite  il comando:
```
npm run build
```
mentre, se si vuole avere solo una visualizzazione delle direttive importate, si può eseguire il comando
```
npm run dev //compila i vari file in maniera continua, utilizzata in fase di sviluppo
```
# package.json
```JSON
node: "modules" //permette di utilizzare i metodi "import" ed "export" per gestire i pacchetti
```
# vite.config.js
#vite è un file #JavaScript che permette di rendere un file #minificato (con attributo **.min**, ovvero contenente l'intero codice in una sola riga).
# Librerie
## Express
Express è una libreria che permette di velocizzare la creazione di una struttura #backend in JavaScript.
### Richieste HTML
#### GET
```JavaScript
res = 
res.get(route, middleware_1, middleware_2, ...)
```
### Multer
Libreria che permette di gestire i #middleware per le richieste #http 
## ECMA