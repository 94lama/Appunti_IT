# Introduzione
React è una libreria (non un framework) in [[JavaScript]] a codice dichiarativo (si descrive l'azione tramite codice) e component-based, che fornisce un'insieme di funzionalità, che può essere trasformato in un framework.
A differenza di [[Angular]] e [[Vue]], offre una grande libertà di manovra durante la programmazione.

Alcuni #framework di React sono: 
- Next (full-stack, versatile, ottima gestione delle routes),
- Remix (full-stack con gestione delle route innestate), 
- Gatsby,
- Expo (ottimo per il mobile perchè permette di tradurre il linguaggio in Kotlin e Swift automaticamente)
(la documentazione ufficiale consiglia di partire con uno di questi 4).
# Gestione REST
#REST (REpresentational State Transfer), è un tipo di comunicazione standardizzato (basato su HTTP), scalabile, basato sulla struttura client-server (request-response), stateless, che comunica tramite #JSON.

------- Bitrock: davide.filippi@bitrock.it, luigi.cerrato@bitrock.it, giulia.migliore@bitrock.it, chiara.schivo@bitrock.it

# Installazione
1. Assicurarsi di aver installato npm e node
2. Lanciare il comando per creare un'app di React (versione vecchia)
```
npm i node
npx create-react-app nome-app //preferibilmente in kebab case
```
# Metodologia
- React si sta sviluppando con una tipologia di programmazione funzionale
- I componenti vanno indicati con la lettera maiuscola
- si possono usare #props automatiche chiamate #children
- sempre meglio usare map, filter e reduce per trattare le array perchè creano delle copie da manipolare ed evitare così danni permanenti ai dati
# Metodi
## useEffect
Si evoca quando si vogliono utilizzare particolari metodi built-in di [[JavaScript]] che richiedono l'utilizzo di 
```Javascript
import {useEffect} from 'react'

useEffect(() => {
	metodo stateful da applicare es. fetch(), 
}, [<dependencies>]);
```
## useState
Si utilizza per definire lo stato iniziale di un componente
```JavaScript
import {useState} from 'react'

const [var setVar] = useState(<valoreIniziale>);
```
	Per modificare il valore di var, si utilizza il metodo setVar()
# Componente
Il componente si deve creare solo dopo aver stabilito tutti i dati da inserire al suo interno. Un componente è rappresentato da una funzione, il quale valore di **return** è un tag [[HTML]].
```App.jsx
import 'app.js'

function App(){
	return (
		<>
			<h1>Testo</h1>
		</>
	)
}
```
	<> è un cosidetto #fragment, ovvero un tag simbolico, utilizzato per raggruppare i diversi tag di un return, senza che si vada a creare un generico elemento div

## Componenti predefiniti
### React.StrictMode
Attivo di default, può causare una doppia esecuzione di alcuni comandi (es. console.log())
# REST
React ha delle funzioni native per accedere alle REST. Una di queste è #Axios
# Librerie
## #Axios 
### Metodi
|Metodo|descrizione|
|-|-|
|get()|Accetta un #endpoint come valore
|.then() |Metodo delle #request (-----), che  si attiva solo dopo aver ricevuto la risposta|
## react-router-redux
Permette di effettuare il #routing tra le varie pagine.
```Javascript
navigate(<URL>)
```
```Javascript
dispatch(push({}))
```
# Framework

# [[Cybersecurity]]
## #insecure-design 
### a
React non controlla l'attributo **href** del tag **a**. Nel caso seguente il browser attiverà l' **alert**
```Javascript
<a href={javascript:alert(value_1)}>
	<img href"{linkValue}">
</a>
```
### Generale
L'attributo **dangerousltSetInnerHTML** permette di forzare l'immissione di codice HTML all'interno del componente. Questo sorpassa tutti i controlli preventivi che React effettua per sanificare gli input.