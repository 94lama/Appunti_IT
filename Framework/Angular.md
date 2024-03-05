Angular è un #framework #front-end , sviluppato da Google e basato su [[TypeScript]] ed è dotato di #composition, ovvero la capacità di creare un componente e riutilizzarlo all'interno del progetto.
# Struttura
|- node_modules/
|- src/
|-- app/
|--- nome-componente/
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

# Comandi
## Terminale
Creazione di un componente:
```sh
ng generate component <nome componente>
```
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
Sono preceduti dal simbolo **@**, e sono utilizzati per definire i componenti
# Componenti
```TypeScript
@Component({
	selector: 'app.root',
	standalone: true
})
```

## Pipe
Una Pipe è un metodo di trasformazione da un input ad un risultato
```Typescript
<p>Testo | uppercase </p>
```
