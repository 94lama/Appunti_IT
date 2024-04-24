# Modelli
**![](https://lh7-us.googleusercontent.com/7K8eehOXd7rTScTou9-5panIKwoF3MDEiA-r7ZV_3d5MIs-lVkXOagof0JQiJ9_FixrNivXjU6dkx-5ocvz8j_-84JGhMAKCgaENCWPja5BunZbwtzt1qGPHRX1okr6rWZuV_1_CuNzdy4erBrG2Pw=s2048)**
## ISO/OSI
La Pila #ISO/OSI rappresenta 7 fasi diverse del processo di comunicazione, tra loro consequenziali (ovvero non è possibile saltare protocolli per il passaggio da un punto iniziale ad un punto finale)
### Livelli
#### Applicazione
E' il momento in cui ci interfacciamo con un applicazione (che sia un software di mailing, un browser o un'app). A questo livello vengono supportati i servizi di rete, come:
- Email
- Trasferimento di file
- Condivisione di database
- Altro
I dati vengono convertiti in #PDU (Protocol Data Unit), ovvero un'unità di informazioni scambiata tra 2 entità in un protocollo di comunicazione a strati.
il #PDU è composto da un #header e da un #body
#### Presentazione
Una volta che i dati vengono convertito in #PDU, quest'ultimo viene standardizzato tramite una serie di processi, tra i quali:
- Crittografia
- Compressione
- Formattazione
Questi processi sono standardizzati, permettendo così di essere letti indipendentemente dalle caratteristiche (tipo #OS) delle due macchine.
#### Sessione
In questo stadio:
- Vengono definite le regole di comunicazione tra il mittente ed il destinatario
- Si effettuano gli scambi di informazione
- Si termina la connessione
#### Trasporto
Si organizza la modalità di trasporto dei dati e si verifica l'effettiva ricezione degli stessi. Ci sono due protocolli di trasporto principali:
- [TCP](<#TCP/IP>) - affidabile
- [UDP](<#UDP>) - non affidabile
Nel caso si utilizzino protocolli affidabili, nel caso un pacchetto non venga ricevuto dal destinatario, esso verrà inviato di nuovo dal mittente
#### Rete
Iniziano le operazioni che consentono la trasmissione del pacchetto attraverso il mezzo fisico. In questo livello vengono aggiunte all' #header le informazioni relative al percorso.
#### Collegamento
Permette lo scambio di pacchetti tra nodi adiacenti della rete, attraverso il livello fisico. Offre un livello di comunicazione affidabile ed efficiente.
Può essere rappresentato dai due #mac-address adiacenti
#### Fisico
I pacchetti vengono trasmessi bit per bit attraverso il mezzo fisico di comunicazione (cavo o wireless). Qua vengono definite forma e voltaggio del segnale, le caratteristiche del mezzo fisico e le caratteristiche elettriche e meccaniche delle #interfacce-di-rete

## TCP-IP
### Introduzione
Il Transmission Control Protocol  #tcp-ip è il protocollo più importante, e funziona tramite suddivisione in pacchetti di piccole dimensioni delle informazioni, che vengono poi spediti separatamente e poi riassemblati dal ricevente, provvede all'instradamento dei pacchetti e controlla la buona riuscita della spedizione.
Un altro parametro da considerare è il mezzo di trasmissione dei pacchetti, che può essere un cavo, cos' come delle onde elettromagnetiche.
E' il modello su cui si basa concettualmente la [[#ISO/OSI]]. Infatti si basa su dei livelli concettualmente simili, ma più compatti
### Livelli
#### Applicazione
Include i livelli Applicazione, Presentazione e Sessione del modello #ISO/OSI
#### Trasporto
E' assimilabile al livello Trasporto della ISO/OSI. Il trasporto può avvenire tramite l'utilizzo di uno tra due protocolli: #tcp e #udp
#### Rete
Noto anche come Livello IP, è assimilabile al livello Rete della ISO/OSI
#### Network
E' assimilabile ai livelli Collegamento e Fisico della ISO/OSI

## SNA
Protocollo definito dalla IBM, è utilizzato prevalentemente in ambito bancario.
# Protocolli
**![](https://lh7-us.googleusercontent.com/wB9im8FVSfk_-eER1aUR7kMBpIB9iKWS7As8LPD4cPvPGd5bE2FjsCHTGGbV_ro_YO59dbyNBeZLgHn2E4x6yQYYo2ZnYDTv9P3Ww2gs-knQ0KniH-5v5FCWnKWUXelUlh2Z6vAaEKTPsALq737qwQ=s2048)**
## Applicazione
### HTTP
Il processo di comunicazione tra macchine, nel caso del web, è gestito tramite #protocollo #HTTP (Hyper-Text Transfer Protocol). Un messaggio HTTP è composto da un #header, che contiene le impostazioni del messaggio e da un #body, che di solito contiene le informazioni.
#### Headers
Ogni #header è sostanzialmente composto da una coppia chiave-valore.
##### Content-Type
Viene utilizzato per indicare la struttura del body. Il valore attribuito segue la struttura del [MIME](https://www.geeksforgeeks.org/http-headers-content-type/)
```HTTP
Content-Type: text/html; charset=utf-8
```
	ESEMPI DI VALORI:
	application/xml
	audio/mp3
	image/jpeg
	multipart/form-data
	text/html
	
#### Status Code
Gli #status-code sono dei codici che riassumono il risultato della query.

| Codice | descrizione                                                                                         |
| ------ | --------------------------------------------------------------------------------------------------- |
| 1xx    | Risposta informativa (di solito relativa a problemi avvenuti durante la trasmissione dei pacchetti) |
| 2xx    | Successo                                                                                            |
| 200    | Ok                                                                                                  |
| 3xx    | Reindirizzamento                                                                                    |
| 4xx    | Client error                                                                                        |
| 400    |                                                                                                     |
| 404    | Not Found                                                                                           |
| 5xx    | Server Error                                                                                        |
| 502    | Termporary unavailable                                                                              |
### HTTPS
Protocollo che consiste nell'evoluzione dell' [[#HTTP]], che include un processo di criptazione dei dati (con protocollo [[#SSL]] o [[#TSL]]) durante la trasmissione degli stessi. 

Questo permette di ottenere:
- Autenticazione del sito web
- Protezione della #privacy 
- Integrità dei dati scambiati
### SMTP
Simple Mail Transfer Protocol, è un protocollo utilizzato per la gestione delle #email (modificato nel 2008 con l'Extended SMTP) per mandare e ricevere messaggi al #server mail.
#### POP3
Simple Mail Transfer Protocol, è un protocollo utilizzato per la gestione delle #email. Copia tutte le informazioni dal server alla macchina locale e le sincronizza lato esterno.

| Pro                        | Contro                       |
| -------------------------- | ---------------------------- |
| Risparmio spazio su server | Non sincronizza le modifiche |
#### IMAP
Simple Mail Transfer Protocol, è un protocollo utilizzato per la gestione delle #email. Sincronizza le mail tramite sincronizzazione online si alato interno che esterno.

| Pro                        | Contro                                        |
| -------------------------- | --------------------------------------------- |
| Risparmio spazio su client | Sincornizza tutto in base ai dati sul #server |

### SMTPS
### E2EE
La End-to-end Encryption permette di crittare i dati non a livello di #server (come avviene nel #https)
## Trasporto
### TCP
Il #tcp, ovvero Transmission Control Protocol è un #protocollo **Orientato alla connessione** e quindi considerato affidabile.
#### Three-way handshake
![[Pasted image 20240219204523.png]]
E' un processo composto da 3 fasi di comunicazione, che viene eseguito ogni volta che avviene uno scambio di pacchetti tramite protocollo #tcp tra due dispositivi. 
#### SYN
Synchronization, ovvero il mittente invia un messaggio al destinatario
#### ACK
Acknowledgement, ovvero il destinatario invia un messaggio al mittente confermando la ricezione del primo messaggio.
Dopodichè un terzo messaggio viene inviato dal mittente al destinatario, contenente il pacchetto di dati.
### UDP
Protocollo simile al [TCP](#TCP), ma senza la presenza del [[#Three-way handshake]]. L'assenza di quel processo permette all' #UDP una maggiore velocità (dovuta all'assenza di fase di riordinamento dei pacchetti), a discapito di una minore affidabilità di scambio. Per questo è spesso utilizzato, ad esempio, per i servizi di #streaming.
### Telnet
Protocollo di comunicazione tra macchine attraverso #shell. E' stato sostituito dal [[#SSH]] per motivi di sicurezza.
### SSH
Secure SHell #ssh è un protocollo cifrato utilizzato da [[Linux]], che sostituisce il precedente telnet, che permette, ad esempio, di accedere ad un altra macchina tramite righe di comando.
Il protocollo consente:
- Connessioni Crittografate
- Verifica d'integrità
- Autenticazione forte
- TCP port forwarding

La comunicazione tra le due macchine avviene tramite #tunneling, ovvero un percorso prestabilito e concordato dalle macchine, attraverso il quale vengono trasmessi i vari pacchetti.
#### Sicurezza
Il protocollo è reso sicuro tramite utilizzo di criptazione tramite #chiave-asimmetrica (ovvero utilizzo di chiave pubblica per criptare il messaggio e chiave privata per decriptarlo).
### RDP
Remote Desktop Protocol, è un protocollo di connessione sicura di [[Windows]], che permette l'accesso diretto alla macchina.
## Rete
### IP
Ovvero Internet Protocol. Si occupa della metodologia di frammentazione de instradamento ( #routing) del pacchetto. La dimensione massima del pacchetto dipende dal materiale su cui viene instradato, ed è indicata dal Maximum Transmission Unit ( #mtu). Questo protocollo è gestito dal #gateway.
#### IPv4
L' #IPv4 si basa su dati di dimensione standard 32 bit, ovvero 4 byte. Ogni byte rappresenta un numero (da 0 a 255) ed è separato dagli altri byte da un punto #dotted-decimal 

	102.54.94.97
Questo indirizzo contiene due tipi principali di informazioni: la prima parte individua la rete fisica in cui il dispositivo è collegato, mentre la seconda identifica il dispositivo stesso.
##### Notazione CIDR
Aggiunge all'indirizzo IPv4 una indicazione relativa alla #subnet. La notazione #cidr collega un numero ad una potenza di 2, partendo da /32 come 2^0.

	102.54.94.97/24
	CIDR:
	In questo caso ci sono 256 indirizzi collegati a questo indirizzo IPv4
Una volta raggiunto il server avente indirizzo #ip desiderato, il [Router](Macchina#Router) si occuperà di smistare i dati tramite l'utilizzo di [tabelle di routing](<Macchina#Tabelle di routing>)
#### IPv6
Evoluzione dell' [[#IPv4]], che consiste in una sequenza alfanumerica di dati.

### SSL
Secure Socket Layer
### TSL
Versione aggiornata di [[#SSL]]
## Network

## Fisico
### FTP
Il File Transfer Protocol (o #FTP) è un protocollo organizzativo per l'utilizzo delle porte. Le porte possono avere 3 stati:
- Aperta
- Chiusa
- #honeypot - ovvero una porta "finta", ovvero riconosciuta come aperta dal sistema, ma atti a bloccare e analizzare i pacchetti ricevuti ([[Cybersecurity]])

Si utilizza questo protocollo per:
- Download/upload di file
- Recupero di trasferimenti interrotti (deve essere impostato dal #provider)
- Rimozione e rinomina di file
- Creazione di #directory 
- Navigazione tra #directory 

#### Lista delle porte standard

| Numero | Protocollo                     |
| ------ | ------------------------------ |
| 20     | FTP (data)                     |
| 21     | FTP (comando)                  |
| 22     | [[#SSH]]                       |
| 25     | [[#SMTP]]                      |
| 53     | [[#DNS]]                       |
| 80     | [[#HTTP]]                      |
| 443    | [[#HTTPS]]                     |
| 1024 + | FTP lato client (porta random) |
| 3389   | [[#RDP]]                       |
| 8080   | [[#HTTP]]                      |
## Altro
### IPCM
L' #IPCM è utilizzato per il monitoraggio delle reti 
### REST
Il #REST, o Representation State Transfer, è un sistema di trasmissione dei dati su  #http, basato su una struttura degli #URL #stateless, ovvero senza il concetto di #sessione. Utilizza 5 metodi di trattamento delle informazioni:
#### GET
Richiede delle informazioni
#### POST
Invia delle informazioni
#### PUT
Modifica un'informazione in maniera integrale
#### PATCH
Modifica un'informazione in maniera parziale
#### DELETE
Cancella un'informazione

### SOAP
Il Simple Object Access Protocol, o #soap un protocollo per lo scambio di messaggi tra componenti software. Comunemente comunica tramite il protocollo #http tramite il #metalinguaggio [[XML]] ed una struttura head-body, dove la head contiene parametri relativi instradamento, sicurezza, transazioni, mentre il body contiene il messaggio (chiamato anche carico utile o #payload).
### DNS
Domain Name System, serve ad attribuire un #dominio a degli indirizzi #IP, in modo tale da rendere più agevole la navigazione degli utenti (es. facebook.com, amazon.it).
Il servizio si basa su dei #server DNS.
# Utilizzo dei protocolli
## Sovraffollamento
il #sovraffollmento è  un eccessivo numero di richieste in un breve arco di tempo, che porta all'impossibilità del serve di rispondere in tempo normale.
### Coda
La #queue è un meccanismo di protezione del server dal #sovraffollmento, che consiste nel conferire un valore numerico alle varie richieste, che definisce l'ordine in cui esse verranno trattate dal server (di solito in ordine temporale). 

