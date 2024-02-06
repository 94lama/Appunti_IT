E' un software per effettuare il #regression-test. Il software è dotato di una console e 4 ambienti (Collections, Environments, History e Configura Sidebar), posizionati nella Sidebar a sinistra della schermata.
# Collections
## Messaggio
Contiene l'indirizzo a cui inviare il messaggio ed il tipo di messaggio da inviare (GET, POST, PUT...)
```Postman
Params | Authorization | Headers (<numero>) |  
```
### Params
Contiene i parametri  necessari per effettuare la chiaata in formato chiave | valore. Nel caso di parametri inseriti nell' #URL, Postman li inserisce automaticamente in questa sezione
### Authorization
### Headers
Si usa per includere gli Headers al messaggio
### Body
Si usa per descrivere il Body del messaggio. Può essere rappresentato in:
- none
- form-data
- x-www-form-urlencoded
- raw
- binary
- GraphQL
### Pre-request Script
### Tests
Permette di scrivere i test in [[JavaScript]], fornendo un oggetto ausiliario **pm**, che si occuperà di gestire le richieste #http:
```pm
|- test((<nome_test>) => { <funzione> })
|- expect()
|-- to. // o not.to, si posiziona dopo l'expect(<valore>)
|--- be. 
|---- equal()
|---- undefined
|--- contain()
|--- include()
|- response
|-- code
|-- responseTime
```
Permette di scrivere i test da effettuare in [[JavaScript]], utilizzando delle variabili predefinite e l'ausilio di Chaijs per la verifica dei #test 
```Javascript
pm.test("<nome_test>", () => {
	// Verifico se lo status della risposta è 200
	pm.expect(pm.response.status).to.be.equal(<stato_aspettato>);
})
```
I test hanno valore **PASS** o **FAIL**. Nel caso di più test (sempre all'iterno dello stesso metodo **test()**) #chaijs utilizza la logica dell'**AND** (test1 && test2).

E' utile salvare i vari test per poterli riutilizzare anche dopo aver chiuso l'app 
### Settings
## Response
```Postman
Body | Cookies | Headers(<numero>) | Test Results (<successi>/<totale>)
```
### Body
### Cookies
### Headers
### Test results
Contiene una lista di tutti i test effettuati ed il loro relativo risultato (**PASS** o **FAIL**), rappresentati anche in forma compressa accanto al titolo della sezione

# Environments
Permette di importare gli #environment da utilizzare.
E' possibile collegare vari dati tramite l'utilizzo di #variabile **{{<nome_variabile>}}**
# History
# Librerie incluse
- Cheerio
- Chaijs