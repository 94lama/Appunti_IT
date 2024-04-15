[Angular](https://angular.dev/) è un #framework #front-end , sviluppato da Google e basato su [[TypeScript]] ed è dotato di #composition, ovvero la capacità di creare un componente e riutilizzarlo all'interno del progetto.
# Installazione
Angular si può installare tramite npm
```sh
npm install @angular/cli
```
	OPZIONI:
	-g # globale. Installa Angular nella directory principale del pc
Oppure tramite npx
```sh
npx --package=@angular/cli
```
	OPZIONI:
	-p # package
Nel caso non lo si avesse già, è necessario installare anche [Typescript](TypeScript#Installazione)

Per iniziare un nuovo progetto
```sh
ng new -S -s -t
```
	OPZIONI:
	-S # skip test
	-s # style inline
	-t # template inline
# Struttura
|- node_modules/
|- src/
|-- app/
|--- nome_componente/
|--- app.component.css
|--- app.component.js
|--- app.component.spec.js
|--- app.component.ts
|--- app.config.js
|--- app.routes.js
|--- post.service.spec.ts
|--- post.service.ts
|-- assets/
|-- favicon.ico
|-- index.html
|-- main.ts
|-- styles.css
|- .editorconfig
|- .gitignore
|- angular
|- package.json
|- package-lock.json
|- README.md
|- tsconfig.app.json
|- tsconfig.json
|- tsconfig.spec.json

## src
### app
#### app.config.ts
File che contiene le configurazioni dell'app
```app.config.ts

export default {

}
```
## tailwind.config.js
Contiene la lista dei moduli da utilizzare
```tailwind.config.js
@type {import('tailwindcss)}
module.exports=[
daisyui
]
```

# Comandi
## Terminale
Creazione di un componente:
```sh
ng g c sahred/<nome componente>
```
	Per convenzione i componenti vengono creati in una cartella nominata /shared
	OPZIONI:
	
Creazione di un servizio:
```Bash
ng generate service <nome servizio>
```
Avvio 
```Bash
npm start
```
Avvio il server
```bash
ng serve
```

## Decoratori
Sono preceduti dal simbolo **@**, e sono utilizzati per definire i componenti (dalla versione 17 hanno sostituito gli attributi ```ng<comando>```)
### Cicli
```Angular
@if
```
```Angular
@else
```
```Angular
@for
```
```Angular
@empty
```
```Angular
@defer
```

## Metodi
Iniettare un servizio all'interno di una variabile
```Angular
<nomeVariabile> = inject(<NomeServizio>)
```
Salvare lo stato di un elemento ( #signal). Il funzionamento è simile allo useState() di [[React]]. 
```Angular
<nomeVariavile> = signal(<valore>)
```
Effettuare una callback
```Angular
<metodo>
.subscribe((<response>) => {<operazioni>})
```
Aggiornare un #signal 
```Angular
<nomeVariabile>.set(<valore>)
```
Per effettuare operazioni in base alle modifiche apportate ad un #signal  
```Angular
<nomeVariabile> = computed(() => <elaboro la variabile signal()>)
```
# Componenti
I componenti sono composti da 3 sezioni:
- Importazione
- Definizione del componente stesso
- 
```TypeScript
///[Import]
import {Component} from '@angular/core';

///[Componente]
@Component({
	selector: 'app.root', // rappresenta il tag da utilizzare per richiamare il componente
	standalone: true
	template: `
		<div>
		</div>
	`,
	styles: [],
})

///{Export}
export class AppComponent {
	titlke: '<nome_componente>'
}
```
	standalone: rende i lcomponente utilizzabile anche separatamente dal progetto originale
	Questa versione di componente Angular è creato in ambiente con style e template inline. Nel caso non si utilizzi l'opzione inline, al posto di template e style verranno utilizzati templateUrl e styleUrl, che conterranno il collegamento ai rispettivi file 
## Pipe
Una Pipe è un metodo di trasformazione da un input ad un risultato
```Typescript
<p>Testo | uppercase </p>
```
