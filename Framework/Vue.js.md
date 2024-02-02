# Introduzione
Vue è un #framework di [[JavaScript]]. E' stato realizzato per creare siti dinamici in single-web-page application, grazie alle rotte lato browser. Lavora lato #front-end in maniera iterativa, tramite [Virtual DOM]( #virtual-dom).
- Option API
- Composition
# Componenti
## Tag
- template permette di definire un template standard per l'app
### Attributi
Tutti gli attributi sono richiamabili tramite attributo v-funzione:nomeEvento (es. v-on:click o v:if**), o tramite @nome_evento. Le funzioni devono essere incluse in un oggetto chiamato methods, da includere all'interno del componente.

|attributo|descrizione|
|-|-|
|@click|onclick|
|scoped|rende lo styling del componente valido unicamente per se stesso|

** **v-if={false}** crea un tag commentato. **v.if={true}**, invece, permette di omettere eventuali elementi duplicati (es. 2 tag **h1**)
- v-on: esegue l'istruzione a seguito dell'attivazione di un evento
- v-if: mostra l'elemento se il valore è vero
- v-for: esegue un ciclo for
```
<li v-for(element in array) :key='key'>{variabile}</li>
```
- v-bind: permette di leggere link da fonti esterne all'interno del file 
## Variabili
E' possibile leggere e manipolare dati tramite #string_interpolation 
```
<template>
	<h1>{{title}}</h1>
</template>
```
Il file del componente deve contenere un tag *script*, per  ed un *template*
## Creazione di un componente

### Lazy loading
```
component: () import ('componentPath')
```
# Metodi
## useRoute
Permette di utilizzare il #routing 
```Vue
const route = useRoute() //inizializzo il routing

<img :src="post.image" class="img.thumbnail" v-bind=route.query />
```
# Attributi
## v-bind
Collega i valori attribuiti al tag
```Vue
<img :src="post.image" class="img.thumbnail" v-bind=route.query />
```
L'utilizzo di questo attributo può essere soggetto a problemi di #sicurezza, poiché permette l'inserimento di codice [[JavaScript]] all'interno del #tag ( #insecure-design  #cross-site-scripting ).
# Composition API
# [[Cybersecurity]]
## #cross-site-scripting 
### v-bind
```Vue
<h1 v-bind:immerHTML={window.location.search}></h1>
```
Questo tag permette l'esecuzione arbitraria di script tramite #URI

