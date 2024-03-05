# Modelli
## ISO/OSI
La Pila #ISO/OSI rappresenta 7 fasi diverse del processo di comunicazione:
### Livelli
#### Applicazione
E' il momento in cui ci interfacciamo con un applicaizone (che sia un software di mailing, un browser o un'app). A questo livello vengono supportati i servizi di rete, come:
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
Il  #tcp-ip è il protocollo più importante, e funziona tramite suddivisione in pacchetti di piccole dimensioni delle informazioni, che vengono poi spediti separatamente e poi riassemblati dal ricevente, provvede all'instradamento dei pacchetti e controlla la buona riuscita della spedizione.
Un altro parametro da considerare è il mezzo di trasmissione dei pacchetti, che può essere un cavo, cos' come delle onde elettromagnetiche.
E' il modello su cui si basa concettualmente la [[#ISO/OSI]]. Infatti si basa su dei livelli concettualmente simili
### Livelli
#### Applicazione
Include i livelli Applicazione, Presentazione e Sessione del modello #ISO/OSI
#### Trasporto
E' assimilabile al livello Trasporto della ISO/OSI. Il trasporto può avvenire tramite l'utilizzo di uno tra due protocolli: #tcp e #udp
#### Rete
Noto anche come Livello IP, è assimilabile al livello Rete della ISO/OSI
#### Network
E' assimilabile ai livelli Collegamento e Fisico della ISO/OSI

# Protocolli
## Applicazione
### HTTP
Il processo di comunicazione tra macchine, nel caso del web, è gestito tramite #protocollo #HTTP (Hyper-Text Transfer Protocol)
### HTTPS
## Trasporto
### TCP
Ovvero Transmission Control Protocol è un #protocollo **Orientato alla connessione** e quindi considerato affidabile.
#### Three-way handshake
![[Pasted image 20240219204523.png]]
E' un processo composto da 3 fasi di comunicazione, che viene eseguito ogni volta che avviene uno scambio di pacchetti tramite protocollo #tcp tra due dispositivi. 
#### SYN
Synchronization, ovvero il mittente invia un messaggio al destinatario
#### ACK
Acknowledgement, ovvero il destinatario invia un messaggio al mittente confermando la ricezione del primo messaggio.
Dopodichè un terzo messaggio viene inviato dal mittente al destinatario, contenente il pacchetto di dati.
### UDP
Protocollo simile al [TCP](#TCP), ma senza la presenza del [[#Three-way handshake]]. L'assenza di quel processo permette all' #UDP una maggiore velocità, a discapito di una minore affidabilità di scambio. Per questo di norma è utilizzato per i servizi di #streaming
## Rete
### IP
Ovvero Internet Protocol. Si occupa della metodologia di frammentazione de instradamento ( #routing) del pacchetto. La dimensione massima del pacchetto dipende dal materiale su cui viene instradato, ed è indicata dal Maximum Transmission Unit ( #mtu). Questo protocollo è gestito dal #gateway.

## Network

# Altro
### SSH
Secure SHell #ssh è un protocollo cifrato, che sostituisce il precedente telnet, che permette di accedere ad un altra macchina tramite righe di comando.
Di default la #porte dedicata al protocollo SSH è la 22, sia per le comunicazioni #tcp che #udp.

### IPv4
L' #IPv4 si basa su dati di dimensione standard 32 bit, ovvero 4 byte. Ogni byte rappresenta un numero (da 0 a 255) ed è separato dagli altri byte da un punto #dotted-decimal 

	102.54.94.97
Questo indirizzo contiene due tipi principali di informazioni: la prima parte individua la rete fisica in cui il dispositivo è collegato, mentre la seconda identifica il dispositivo stesso.
#### Notazione cdir
Aggiunge all'indirizzo IPv4 una indicazione relativa alla #subnet

	102.54.94.97/24
### IPv6
### IPCM
L' #IPCM è utilizzato per il monitoraggio delle reti 
### REST
Il #REST, o Representation State Transfer, è un sistema di trasmissione dei dati su  #http, basato su una struttura degli #URL #stateless, ovvero senza il concetto di #sessione. Utilizza 5 metodi di trattamento delle informazioni:
### GET
Richiede delle informazioni
### POST
Invia delle informazioni
### PUT
Modifica un'informazione in maniera integrale
### PATCH
Modifica un'informazione in maniera parziale
### DELETE
Cancella un'informazione

### SOAP
Il Simple Object Access Protocol, o #soap un protocollo per lo scambio di messaggi tra componenti software. Comunemente comunica tramite il protocollo #http tramite il #metalinguaggio [[XML]] ed una struttura head-body, dove la head contiene parametri relativi instradamento, sicurezza, transazioni, mentre il body contiene il messaggio (chiamato anche carico utile o #payload).
### SMTP
### DNS
Domain Name System, serve ad attribuire un #dominio a degli indirizzi #IP, in modo tale da rendere più agevole la navigazione degli utenti (es. facebook.com, amazon.it).
Il servizio si basa su dei #server DNS.
# Porte standard
22 - [[#SSH]]
53 - [[#DNS]]
80 - 
443 - [[#HTTPS]]