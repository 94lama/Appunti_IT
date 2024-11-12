# Modelli
![](https://www.aiutocomputerhelp.it/wp-content/uploads/layer-logico-tcp-ip.jpg)
## ISO/OSI
La Pila #ISO/OSI rappresenta 7 fasi diverse del processo di comunicazione, tra loro consequenziali (ovvero non è possibile saltare protocolli per il passaggio da un punto iniziale ad un punto finale)
### Livelli
Il modello rappresenta il flusso di dati suddiviso in 7 categorie (chiamate livelli), attraverso le quali il pacchetto viene analizzato e trattato per permetterne il trasporto. 
![[./../Immagini/Pasted image 20240930152150.png]]
#### 7 - Applicazione
E' il momento in cui ci interfacciamo con un applicazione (che sia un software di mailing, un browser o un'app). A questo livello vengono supportati i servizi di rete, come:
- Email
- Trasferimento di file
- Condivisione di database
- Altro
I dati vengono convertiti in #PDU (Protocol Data Unit), ovvero un'unità di informazioni scambiata tra 2 entità in un protocollo di comunicazione a strati.
il #PDU è composto da un #header e da un #body
#### 6 - Presentazione
Una volta che i dati vengono convertiti in #PDU, quest'ultimo viene standardizzato tramite una serie di processi, tra i quali:
- Crittografia
- Compressione
- Formattazione
Questi processi sono standardizzati, permettendo così di essere letti indipendentemente dalle caratteristiche (tipo #OS) delle due macchine.
#### 5 - Sessione
In questo stadio:
- Vengono definite le regole di comunicazione tra il mittente ed il destinatario
- Si effettuano gli scambi di informazione
- Si termina la connessione
#### 4 - Trasporto
Si organizza la modalità di trasporto dei **pacchetti** di dati e si verifica l'effettiva ricezione degli stessi. Ci sono due protocolli di trasporto principali:
- [TCP](<#TCP/IP>) - affidabile
- [UDP](<#UDP>) - non affidabile
Nel caso si utilizzino protocolli affidabili, nel caso un pacchetto non venga ricevuto dal destinatario, esso verrà inviato di nuovo dal mittente
#### 3 - Rete
Iniziano le operazioni che consentono la trasmissione del **pacchetto** attraverso il mezzo fisico. In questo livello vengono aggiunte all' #header le informazioni relative al percorso.
#### 2 - Collegamento
I protocolli inerenti il Data Link permettono lo scambio di **frame** di dati tra nodi adiacenti della rete, attraverso il livello fisico. Offre un livello di comunicazione affidabile ed efficiente.
#### 1 - Fisico
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
## Applicazione
![](https://lh7-us.googleusercontent.com/wB9im8FVSfk_-eER1aUR7kMBpIB9iKWS7As8LPD4cPvPGd5bE2FjsCHTGGbV_ro_YO59dbyNBeZLgHn2E4x6yQYYo2ZnYDTv9P3Ww2gs-knQ0KniH-5v5FCWnKWUXelUlh2Z6vAaEKTPsALq737qwQ=s2048)
![](https://lh7-us.googleusercontent.com/wB9im8FVSfk_-eER1aUR7kMBpIB9iKWS7As8LPD4cPvPGd5bE2FjsCHTGGbV_ro_YO59dbyNBeZLgHn2E4x6yQYYo2ZnYDTv9P3Ww2gs-knQ0KniH-5v5FCWnKWUXelUlh2Z6vAaEKTPsALq737qwQ=s2048)
### Email
#### SMTP
Simple Mail Transfer Protocol, è un protocollo utilizzato per la gestione delle #email (modificato nel 2008 con l'Extended SMTP) per mandare e ricevere messaggi al #server mail.
#### SMTPS
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

### File
#### VoIP
Il Voice over IP é un protocollo utilizzato per l'invio di dati di tipo audio, utilizzati spesso per gestire le chiamate vocali tra dispositivi. Di solito la connessione viene gestita con protocollo [UDP](#UDP).
### Web
#### HTTP
Il processo di comunicazione tra macchine, nel caso del web, è gestito tramite #protocollo #HTTP (Hyper-Text Transfer Protocol). Un messaggio HTTP è composto da un #header, che contiene le impostazioni del messaggio e da un #body, che di solito contiene le informazioni.
##### Headers
Ogni #header è sostanzialmente composto da una coppia chiave-valore.
###### Content-Type
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
	
##### Status Code
Gli #status-code sono dei codici che riassumono il risultato della query.

| Codice | descrizione                                                                                         |
| ------ | --------------------------------------------------------------------------------------------------- |
| 1xx    | Risposta informativa (di solito relativa a problemi avvenuti durante la trasmissione dei pacchetti) |
| 2xx    | Successo                                                                                            |
| 200    | Ok                                                                                                  |
| 3xx    | Reindirizzamento                                                                                    |
| 302    | Found                                                                                               |
| 4xx    | Client error                                                                                        |
| 400    |                                                                                                     |
| 404    | Not Found                                                                                           |
| 5xx    | Server Error                                                                                        |
| 502    | Termporary unavailable                                                                              |
#### HTTPS
Protocollo che consiste nell'evoluzione dell' [[#HTTP]], che include un processo di criptazione dei dati (con protocollo [[#SSL]] o [TLS](#TLS) durante la trasmissione degli stessi. 

Questo permette di ottenere:
- Autenticazione del sito web
- Protezione della #privacy 
- Integrità dei dati scambiati

### Altro
#### E2EE
La End-to-end Encryption permette di crittare i dati non a livello di #server (come avviene nel #https)

#### NTP
Il Protocollo Temporale della Rete viene utilizzato nel caso ci sia la necessità di sincronizzare il tempo tra più dispositivi (come alternativa al dettaglio manuale dello stesso).
Il protocollo permette ai Router di connettersi ad un Server NTP e sincronizzare l’orario, per poi inviare il dato temporale a tutti i dispositivi della rete a cascata. Per praticità i dispositivi della rete vengono catalogati in base alla vicinanza che hanno con il Server NTP:
-  Stratum 0: Sono i dispositivi appositi che forniscono il dato temporale
- Stratum 1: Dispositivi collegati direttamente ai dispotivi che forniscono il dato
- Stratum 2+: Dispositivi che ricevono il dato dallo Stratum 1. Possono anche agire come Server NTP per i livelli inferiori.
Il numero massimo di livelli ammissibile è 16.

### SNMP
Il Protocollo di Gestione Semplice della Rete è utilizzato dagli amministratori per gestire dispositivi come Router, Switch, Server, Workstation e dispositivi di sicurezza all’interno di una rete basata su protocollo IP.
Un sistema SNMP è formato da due elementi:
- Gestore SNMP: Dispositivo che avvia il software di geetione
- Agente SMNP: Nodi che sono monitorati dal software. I vari agenti sono registrati all’interno del MIB (Base di Informazioni Gestionali), assieme ai loro dati operativi.

I messaggi sono di 3 tipi:
- GET: inviati dal gestore per richiedere informazioni
- SET: inviati dal gestore per modificare impostazioni
- TRAP: inviati dal nodo per inviare informazioni

## Presentazione

### SSL
Secure Socket Layer

### TLS
Il [Transport Layer Security](https://it.wikipedia.org/wiki/Transport_Layer_Security) (Livello di Sicurezza del Trasporto) è l'evoluzione del [SSL](#ssl), ed è utilizzato per offrire una rete di comunicazione sicura su reti TCP/IP, grazie a servizi di autenticazione, integrità dei dati e confidenzialità

## Sessione

## Trasporto
I protocolli del livello 4 (trasporto) determinano la metodologia di trasmissione dei dati al livello di [internet](<./Reti#Rete pubblica>), l'ordinamento dei dati e il controllo di flusso (ovvero la velocità di invio e eventualmente il controllo della avvenuta ricezione dei dati).
Durante la sessione, entrambi i dispositivi mantengono aperte delle [porte](<./Macchina#Porte di rete>) prestabilite (identificate in coppia **origine - destinazione**) per permettere l'invio e l'ascolto costante di messaggi di risposta. Le porte vengono inserite nel pacchetto di dati da inviare tramite coppia di [socket](./Macchina#Socket).
### TCP
Il #tcp, ovvero [Transmission Control Protocol](https://datatracker.ietf.org/doc/html/rfc793) è un #protocollo **Orientato alla connessione** e quindi considerato affidabile. La connessione è garantita dal three-way handshake, che assicura la connessione reciproca dei due dispositivi per tutta la sessione (durante la quale si potranno trasferire un numero variabile di pacchetti di dati, in base alla tipologia di connessione scelta), che verrà chiusa automaticamente una volta conclusa l'operazione desiderata.
#### Header
![[./../Immagini/Pasted image 20241009100107.png]]

#### Three-way handshake
E' un processo composto da 3 fasi di comunicazione, che viene eseguito ogni volta che avviene uno scambio di pacchetti tramite protocollo #tcp tra due dispositivi. I dati utilizzati per il controllo del Three-way handshake sono inclusi nel campo [Control Bits](<#Control bits>). 

![[Pasted image 20240219204523.png]]
#### Control Bits
Campo dati di lunghezza pari a 6-bit, che definisce il tipo di messaggio di controllo dello stato della comunicazione. Ogni bit rappresenta uno stato della comunicazione o una richiesta: 
##### URG
Urgent pointer.
##### ACK
Acknowledgement, ovvero il destinatario invia un messaggio al mittente confermando la ricezione del primo messaggio.
Dopodichè un terzo messaggio viene inviato dal mittente al destinatario, contenente il pacchetto di dati.
##### PSH
Push function.
##### RST
Reset the connection (utilizzato in caso di errori di conenssione)
##### SYN
Synchronization, ovvero il mittente invia un messaggio al destinatario
##### FIN
Messaggio utilizzato per terminare la connessione TCP tra due dispositivi. I messaggi inviati sono:
1. L'Host manda un FIN al Server
2. Il Server invia un ACK all'Host
3. Il Server invia un FIN all'Host
4. L'Host invia un ACK al Server

#### Sequence number
Valore numerico progressivo (32-bit) che, partendo da un **ISN** (Initial Sqeuence Number, o numero di inizio sequenza), definisce l'ordine d'invio dei pacchetti, in modo tale da permetterne il corretto riassemblamento una volta ricevuti dall'host.

Nel caso alcuni segmenti del messaggio vengano ricevuti, l'Host invia un messaggio ACK relativo al primo segmento non ricevuto, ed il Server provvederà ad inviare nuovamente tutti i messaggi partendo da quello indicato.
Nel caso l'Host abbia ricevuto correttamente tutti i segmenti, invia un messaggio ACK con valore parti all'ISN sommato al numero di pacchetti ricevuti.

##### SACK
E' possibile impostare un messaggio SACK (Selective ACKnowledgement) che permette di indicare il range di pacchetti ricevuti con successo a seguito di un errore di ricezione:

| Segmento | Stato        |
| -------- | ------------ |
| 1        | Ricevuto     |
| 2        | Non ricevuto |
| 3        | Non ricevuto |
| 4        | Ricevuto     |
| 5        | Ricevuto     |
| 6        | Ricevuto     |
 Considerando questo caso, l'Host può inviare un messaggio SACK con valori 4-6. In questo modo il Server invierà unicamente i pacchetti 2, 3 e dal 7 in poi (se presenti).
#### Window
Indica il numero massimo di dati ricevibili dall'Host affinché possano essere elaborati in maniera affidabile e la dimensione massima di ogni segmento (Maximum Segment Size, o **MSS**), ricevibile prima di inviare un messaggio ACK. Per i protocolli IPv4 di solito il MSS è pari a 1460-b.
Nel caso il dispositivo dell'Host sia abilitato all'uso dello Sliding Window Protocol, questo campo è modificabile anche durante la sessione. Questo permette di velocizzare l'invio di dati di grosse dimensioni (e non doversi interrompere nel caso venga raggiunta la dimensione massima della Window).
### UDP
L'User Datagram Protocol è un protocollo paragonabile al [TCP](#TCP), ma senza la presenza del [[#Three-way handshake]]. L'assenza di quel processo permette all' #UDP una maggiore velocità (dovuta all'assenza di fase di riordinamento dei pacchetti), a discapito di una minore affidabilità di scambio. Per questo è spesso utilizzato, ad esempio, per i servizi di #streaming.
#### Header
![[./../Immagini/Pasted image 20241009100537.png]]

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

## Network
### Descrizione
Gestisce l'indirizzamento a livello logico e l'instradamento dei **pacchetti** e deve assicurare il corretto espletamento delle seguenti funzioni:
- Tolleranza dei fallimenti (ovvero il processo di networking non deve interrompersi nel caso incontri un errore). Di solito avviene tramite cancellazione del messaggio errato e nella prosecuzione della coda di messaggi successivi e la ridondanza di connessioni tra i vari dispositivi;
- Scalabilità, ovvero capacità di aumentare o ridurre considerevolmente il numero di periferiche connesse e in poco tempo;
- Qualità del servizio, ovvero la capacità di mantenere un flusso di dati costante nel tempo, evitando rallentamenti o colli di bottglia. L'importante è tenere in considerazione il tipo di messaggio da trasportare e prioritizzare il traffico sensibile al passare del tempo;
- Sicurezza, ovvero il controllo dei processi che avvengono nella rete, il blocco degli accessi in base a criteri di autorizzazione. I criteri si applicano secondo principi di **confidenzialità**, **integrità** e **disponibilità** dei dati.

Confidenzialità: i dati devono essere accessibili solo agli utenti predefiniti.
Disponibilità: i dati devono essere sempre accessibili in maniera affidabile.
Integrità: il trasporto dei dati deve avvenire senza perdite o corruzione degli stessi.

Il [router](./Macchina#Router) è un dispositivo che si occupa della gestione dei dati a livello 3 - Network.

A livello di Rete, i messaggi vengono smistati in base agli indirizzi MAC dei dispositivi in comunicazione.
![[Pasted image 20240924110817.png]]
Lo schema sopra mostra i dati utilizzati per smistare un messaggio in [internet](<./Reti#Rete pubblica>): gli indirizzi utilizzati sono i MAC di origine e destinazione, mentre il destinatario è identificato tramite IPv4. Il messaggio (già contenente i dati del destinatario) viene incapsulato e "decapsulato" più volte:
1. LAN - Incapsulamento per l'inserimento degli indirizzi MAC della [LAN](./Reti#LAN) (aa-aa-aa, bb-bb-bb)
2. LAN - Ricezione del messaggio da parte del router (bb-bb-bb), con successivo aggiornamento degli indirizzi MAC (bb-bb-bb, cc-cc-cc)
3. WAN - Ricezione del messaggio da parte del router della rete del destinatario, con successivo aggiornamento degli indirizzi MAC (cc-cc-cc, dd-dd-dd)
4. LAN - RIcezione del messaggio da parte del destinatario (ee-ee-ee, 55-55-55)

L'associazione del flusso degli indirizzi MAC agli IP del messaggio è effettuata tramite:
- [ARP](./Protocolli#ARP) (Address Resolution Protocol) nel caso di IPv4;
- [ND](./Protocolli#ND) (Neighbor Discovery) nel caso di IPv6.

### ARP
Il protocollo ARP, o [Addresses Resolution Protocol](https://it.wikipedia.org/wiki/Address_Resolution_Protocol) (Protocollo di risoluzione degli indirizzi) serve ad identificare l'indirizzo MAC di un dispositivo collegato ad una [LAN](./Reti#LAN) tramite l'indirizzo IP dello stesso dispositivo. Consiste in un invio di una request in [broadcast](./Networking#Broadcast), contenente l'indirizzo [IPv4](#IPv4) del destinatario. Il dispositivo il cui indirizzo IPv4 combacia con quello desiderato, invierà un messaggio di risposta, contenente il proprio indirizzo MAC al mittente. Nel caso l'IP sia esterno alla [rete](./Reti#LAN), il MAC di risposta corrisponderà a quello del router.

Il protocollo ARP è identificata con il codice 0x806.

Un ARP request contiene:
1. Ethernet header
	- Indirizzo MAC [broadcast](./Reti#Broadcast) **ffff.ffff.ffff**
	- Indirizzo MAC del mittente
3. Pacchetto IP
	- Indirizzo MAC del mittente
	- Indirizzo IP del mittente

#### ARP reply
La ARP reply è il messaggio (UNICAST) di risposta che un computer invia, dopo aver ricevuto una richiesta ARP avente il proprio indirizzo IP come destinatario.
Il mesaggio viene inviato solo dopo aver registrato nella propria [tabella degli indirizzi ARP](<#ARP table>) l'indirizzo IP e l'indirizzo MAC del mittente della ARP request.

Un ARP reply contiene:
1. Ethernet header
	- Indirizzo MAC del destinatario
	- Indirizzo MAC del mittente (della ARP reply)
3. Pacchetto IP
	- Indirizzo MAC del mittente (della reply)
	- Indirizzo IP del mittente (della reply)

#### ARP table
Per identificare un indirizzo MAC partendo da un IP, il computer è dotato di una tabella degli indirizzi ARP (o Cache ARP), memorizzata nella [RAM](./Macchina#RAM). Ogni riga della tabella che non viene utilizzato per un determinato arco di tempo (di solito tra i 15 e i 45 secondi), viene rimosso.

Se si invia il comando ```arp -a``` su [Windows](<Windows.md>), sarà possibile vedere la [Tabella degli indirizzi ARP](<#ARP table>) del dispositivo

| Internet address | Physical address | Type    |
| ---------------- | ---------------- | ------- |
| 192.168.10.1     | a0e0.af0d.e140   | dynamic |
| 209.165.200.255  | a30d.6fe1.9d91   | dynamic |

#### Problematiche
- Nelle reti di grandi dimensioni, accendere molti dispositivi contemporaneamente potrebbe portare a rallentamenti alla rete stessa, dovuti alla moltitudine di richieste ARP da gestire.
- Possibile [spoofing](./../Cybersecurity#Spoofing) degli indirizzi IPv4 (portando ad attacchi di tipo [ARP poisoning](<./../Cybersecurity#ARP Poisoning>))

### DHCP
Il DHCP, o Dynamic Host Control Protocol (Protocollo di controllo dinamico degli host), è un protocollo di assegnazione automatica degli indirizzi IP agli host, che può essere utilizzato in alternativa all'assegnazione statica degli indirizzi, dove l'operatore assegna manualmente gli indirizzi IP ai vari dispositivi connessi, che vengono mantenuti per un periodo di tempo definito dall'operatore.

Mentre la configurazione statica permette di avere un maggior controllo della rete, il protocollo DHCP permette di avere una maggiore adattabilità, rendendo possibile effettuare il cambio di porta di accesso per il dispositivo e maggiore velocità di realizzazione (anche solo perché si evita di inserire gli indirizzi IP statici in ogni dispositivo e tenerne traccia).
Nel caso di rete wireless, il Router lavora sia da DHCP client (in quanto elabora i messaggi da inviare all'ISP) che DHCP server (in quanto gestisce gli indirizzi IP dei dispositivi connessi alla rete).
#### Configurare una rete con DHCP
[Come attivare il DHCP su Windows](https://support.microsoft.com/it-it/windows/modificare-le-impostazioni-tcp-ip-bd0a07af-15f5-cd6a-363f-ca2b6f391ace)
1. Il client invia in [#Broadcast] un pacchetto (chiamato **DHCPDISCOVER**), contenente l'indirizzo MAC al Server DHCP.
2. Il Server riceve il messaggio ed invia un **DHCPOFFER, contenente l'indirizzo IP assegnato, una [[#Gateway mask]] e l'Indirizzo [Gateway] di default.
3. L'Host riceve il messaggio, invia una **DHCPREQUEST** di accettazione dell'offerta e aggiorna le proprie impostazioni IP
4. Il Server aggiorna la Tabella degli indirizzi IP ed invia un messaggio di accettazione (Acknowledgement, che può essere **DHCPACK** in caso di risposta positiva, o **DHCPNACK** in caso di risposta negativa).

Nel caso di IPv6, il protocollo cambia i nomi delle richieste (mantenendone la ratio):
1.  **SOLICIT** (DHCPDISCOVER)
2. **ADVERTISE** (DHCPOFFER)
3. **INFORMATION** (DHCPINFORM o DHCPREQUEST)
4. **REQUEST** (DHCPREQUEST)
5. **REPLY** (DHCPACK o DHCPNACK)

### DNS
Domain Name System, serve ad attribuire un Fully Qualified Domain Name ( #dominio) a degli indirizzi #IP, in modo tale da rendere più agevole la navigazione degli utenti (es. facebook.com, amazon.it).
Il servizio si basa su dei #server DNS.
E' il primo step per la navigazione su internet odierna, in quanto permette di semplificare il reindirizzamento al server corretto, grazie all'utilizzo di parole piuttosto che indirizzi IP.

Permette di identificare l'IP dall'URL inviato e inviare come risposta l'indirizzo IP corretto del server.

#### Pacchetto
Un messaggio DNS per essere ricevuto ed elaborato correttamente dal **Server DNS**, che verifica all'interno delle sue risorse se il dato richiesto è registrato o meno. I dati contenuti sul server fanno riferimento a:
- A - Indirizzo IPv4 del dispositivo di riferimento
- NS - Nome del Server
- AAAA - Indirizzo IPv6 del dispositivo di riferimento
- MX - registro di scambio email

Nel caso il Server DNS non abbia al suo interno il dato richiesto, effettua una richiesta agli altri Server DNS alla ricerca del dato (ogni computer ha una propria tabella di indirizzi DNS nella [cache](./Macchina#Cache) in cui effettuare una prima ricerca)

Ogni richiesta DNS contiene:
- Domanda
- Risposta
- Authority
- Altre informazioni

#### Gerarchia
Il protocollo DNS usa un sistema gerarchico per creare un database, bassato sui nomi di **dominio**. I principali sono:

| Dominio | Proprietario              |
| ------- | ------------------------- |
| .com    | Aziende o business        |
| .org    | Organizzazioni non-profit |
| .au     | Australia                 |
| .co     | Colombia                  |
| .it     | Italia                    |
![[./../Immagini/Pasted image 20241002001123.png]]
#### URI
Lo Uniform Resource Identifier Indica il segnaposto del server con cui stabilire una connessione 
```
https://it.wikipedia.org/wiki/Uniform_Resource_Identifier#Relazione_fra_URI,_URL_e_URN
```
Rappresenta l'unione di URL e Fragment.
#### URL
Lo Uniform Resource Locator rappresenta la parte dell'URI adibita ad identificare lo specifico file visualizzato ed il protocollo utilizzato per la connessione
```
https://it.wikipedia.org/wiki/Uniform_Resource_Identifier
```
#### URN
Lo Uniform Resource Name rappresenta unicamente il server con cui avviene la comunicazione ed il file richiesto
```
it.wikipedia.org/wiki/Uniform_Resource_Identifier
```
#### Fragment
Identifica eventuali parametri utilizzati durante la chiamata all'interno dell'URI come, ad esempio, l'[anchor](./../Linguaggi/HTML#a) di riferimento o la query richiesta
```
#Relazione_fra_URI,_URL_e_URN
```

### EUI-64
Protocollo definito dalla IEEE per generare indirizzo IPv6 [GUA](#ipv6#gua), che utilizza l'indirizzo [MAC](#MAC) di un client (48-bit), gli aggiunge altri 16-bit tra i due blocchi (codice produttore (OUI) e numero dispositivo). Questi 16 bit sono a loro volta scomponibili in:
1. Primo ottetto dell'OUI
2. Primo ottetto dell'OUI avente come ultima cifra:
	1. 0 - Nel caso di indirizzo statico
	2. 1 - Nel caso di dispositivo collegato alla rete

### ICMP
#### Descrizione
L'Internet Control Message Protocol è un protocollo *stateless* utilizzato per inviare messaggi informativi relativi allo stato delle sessioni IP (disponibile sia per IPv4 che per IPv6). I messaggi si possono dividere in categorie, in base alla loro funzione:

#### Raggiungibilità
Sono utilizzati per testare la connessione tra due dispositivi (un classico esempio di utilizzo è il **ping**). Forniscono dettagli sulla connessione tramite 2 principali tipologie di messaggi:

##### Destinazione o servizio non raggiungibili
Sono rappresentati da dei codici presenti all'interno del messaggio, e sono:

| Codice | IPv4                       | IPv6                                                           |
| ------ | -------------------------- | -------------------------------------------------------------- |
| 0      | Rete irraggiungibile       | Rete assente                                                   |
| 1      | Host non raggiungibile     | La comunicazione con l'host è stata proibita (es. da firewall) |
| 2      | Protocollo irraggiungibile | Oltre il raggio di disponibilità dell'indirizzo di partenza    |
| 3      | Porta irraggiungibile      | Indirizzo non ragiungibile                                     |
| 4      |                            | Porta non raggiungibile                                        |

##### Tempo limite scaduto
Viene utilizzato dai Router per indicare che il [TTL](#IP#Header) (Time to Live per IPv4) o lo [Hop Limit](#IP#Header) (per l'IPv6) ha raggiunto il valore 0. Questo messaggio è usato nel comando ```traceroute``` per identificare i router presenti nel percorso.

#### ICMPv6
Alcuni messaggi sono stati inclusi unicamente nella versione per IPv6 del protocollo e possono essere categorizzati in:
- Router
- Network (o rete)

###### Router
Sono di due tipi: Advertisement (RA) e Solicitation (RS).
- RA - Il router invia ogni 200 secondi un messaggio a tutti gli host abilitati a IPv6, contenente informazioni utili, come:
	- Indirizzo [DNS](#DNS)
	- Nome del dominio
	- Prefisso
	Se l'host sta usando la [SLAAC](#SLAAC), aggiornerà automaticamente l'indirizzo del Gateway di deafult.
- RS - L'host invia un messaggio di richiesta per in indirizzo IPv6 al router e rimane in attesa di un messaggio RA che permetta di creare automaticamente un indirizzo IPv6 tramite protocollo SLAAC.

##### Network
Sono i messaggi inviati alla rete locale in generale ([Local-Link](#IPv6) scope) e sono di due tipi: Advertisement (NA) e Solicitation (NS)
- NS - è utilizzato per effettuare un [DAD](#DAD) a seguito di una auto-assegnazione di indirizzo IPv6 tramite SLAAC. E' un messaggio inviato in [multicast](./Reti#Multicast) (Segnalato nell'indirizzo [MAC](#MAC) di destinazione)
- NA - utilizzato per l'invio di messaggi [unicast](./Reti#Unicast) ad altri dispositivi. Viene usato, ad esempio, per rispondere ad un NS nel caso l'indirizzo IP risulti duplicato.

##### ND
Il protocollo ND, o Neighbor Discovery Protocol (letteralmente protocollo di scoperta dei vicini). Si utilizza per fornire 3 servizi:
- Risoluzione degli indirizzi
- Fornire servizi di redirezione
- Router discovery
E' un protocollo che si basa sull'utilizzo di messaggi ICMP per costruire la propria tabella degli indirizzi MAC, avendo come base gli indirizzo IPv6 dei dispositivi connessi alla [rete](,.Reti#LAN). Il protocollo si compone di 5 passaggi:
1. Messaggi NS (Network Solicitation) per fornire una risoluzione di indirizzo (?)
2. Ricezione dei messaggi NA per supportare l'allocazione degli indirizzi e la SLAAC
3. Messaggio RS, per migliorare il parametro [Hop limit](#IP#Header)
4. Ricezione del messaggio RA (Router advertisement)
5. Redirezione del messaggio (?)

### IP
#### Descrizione
Ovvero ***Internet Protocol***. Si occupa della metodologia di frammentazione de instradamento ( #routing) del pacchetto. La dimensione massima del pacchetto dipende dal materiale su cui viene instradato, ed è indicata dal Maximum Transmission Unit ( #mtu). Questo protocollo è gestito dal #gateway.
Il protocollo IP ha 3 caratteristiche principali:
- **Connectionless**: Non c'è nessun tipo di connessione con il destinatario prima dell'dell'invio dei dati;
- **Best effort**: L'indirizzo IP è inaffidabile(in quanto non garantisce la ricezione del messaggio)
- **Media indipendent**: Non dipende dal mezzo di comunicazione utilizzato per trasportare il dato.

Ci sono 2 protocolli principali: IPv4 e IPv6, dove il primo rappresenta attualmente quello più utilizzato ed il secondo un protocollo ideato per risolvere la progressiva scarsezza degli indirizzi IPv4 rispetto alla richiesta mondiale.
Il protocollo IP ha 3 caratteristiche principali:
- **Connectionless**: Non c'è nessun tipo di connessione con il destinatario prima dell'dell'invio dei dati;
- **Best effort**: L'indirizzo IP è inaffidabile(in quanto non garantisce la ricezione del messaggio)
- **Media indipendent**: Non dipende dal mezzo di comunicazione utilizzato per trasportare il dato.

Ci sono 2 protocolli principali: IPv4 e IPv6, dove il primo rappresenta attualmente quello più utilizzato ed il secondo un protocollo ideato per risolvere la progressiva scarsezza degli indirizzi IPv4 rispetto alla richiesta mondiale.

##### Header
![[./../Immagini/Pasted image 20240930154031.png]]
L'intestazione (o header) di un pacchetto IP è un dati avente lunghezza fissa pari a 20B, che contiene le informazioni utili per il trasporto e la lettura dello stesso da parte del destinatario. L'header è composto da:
- **Version** (4-bit): versione del protocollo IP utilizzata (in binario)
- **Differntiated Servides** (8-bit): Noto anche come DiffServ o DS, specifica la priorità di ogni pacchetto. Può essere diviso in:
	- DSCP (DiffServ Code Point)
	- Explicit Congestion Notification (ECN)
- **Time To Live** (8-bit): valore impostato dall'host che invia il pacchetto e che decrementa di 1 ogni volta che arriva ad un nuovo router. QUando raggiunge lo 0, il router scarta il pacchetto ed invia un messaggio [ICMP](#ICMP) (Internet Control Message Protocol) di tipo Time Exceeded (tempo scaduto) al mittente
- **Protocol** (8-bit): Identifica il prossimo protocollo da utilizzare. Valori comuni sono:
	- 1: ICMP
	- 6: [TCP](#TCP)
	- 17: [UDP](#UDP)
- **Header checksum** (16-bit): slot utilizzata per identificare corruzioni dell'header IPv4
- **Indirizzo IP mittente** (32-bit)
- **Indirizzo IP Destinatario** (32-bit)

Nel caso di utilizzo di IPv6, alcuni moduli dell'header variano. In particolare:
![[./../Immagini/Pasted image 20240930193334.png]]
Questa modifica dell'intestazione permette di ridurre lo spazio dell'header a 40-Byte nel caso di chiamata IPv6:
![[./../Immagini/Pasted image 20240930193612.png]]

#### IPv4
L' #IPv4 è un indirizzo, assegnato ad una rete [LAN](./Reti#LAN), che
si basa su dati di dimensione standard 32 bit, ovvero 4 byte. Ogni byte rappresenta un numero (da 0 a 255) ed è separato dagli altri byte da un punto #dotted-decimal 

	102.54.94.97

##### Struttura
Questo indirizzo contiene due tipi principali di informazioni: la prima parte individua la rete fisica in cui il dispositivo è collegato, mentre la seconda identifica il dispositivo stesso.

	102.54.94 = Network locale
	102.54.94 = Network locale
	97 = Host

Gli indirizzi IPv4 possono essere privati (indicati anche come indirizzi privati RFC1918) o pubblici. Nel primo caso appartengono ad un range specifico di IP:
```
10.0.0.0 - 10.255.255.255
172.16.0.0 - 172.31.255.255
192.168.0.0 - 192.168.255.255
```
	Questi IP privati sono relativi al network in cui si trovano (intranet), quindi non sono univoci per la rete pubblica: due reti diverse possono avere gli stessi IP privati.

La traduzione da IP privato a pubblico avviene tramite [NAT], ovvero Network Address Translation (di solito la funzione è svolta dal [Router](./Macchina#Router)). Un'altra funzione svolta dal router è la frammentazione:
Nel caso di pacchetti aventi dimensioni troppo elevate, infatti, il protocollo include un processo di divisione del pacchetto in più pacchetti per agevolarne il trasporto. Questo processo prende il nome di **Fragmentation** (processo che tuttavia, causa latenza nella connessione.

##### Routing
La traduzione da IP privato a pubblico avviene tramite [NAT], ovvero Network Address Translation (di solito la funzione è svolta dal [Router](./Macchina#Router)). Un'altra funzione svolta dal router è la frammentazione:
Nel caso di pacchetti aventi dimensioni troppo elevate, infatti, il protocollo include un processo di divisione del pacchetto in più pacchetti per agevolarne il trasporto. Questo processo prende il nome di **Fragmentation** (processo che tuttavia, causa latenza nella connessione.

Una volta raggiunto il server avente indirizzo #ip desiderato, il [Router](Macchina.md#Router) si occuperà di smistare i dati tramite l'utilizzo di [tabelle di routing](Macchina.md#Tabelle%20di%20routing di routing>).
Ovvero Internet Protocol versione 4. Si occupa della metodologia di frammentazione de instradamento ( #routing) del pacchetto.
L' #IPv4 è un indirizzo, assegnato ad una rete [LAN](./Reti#LAN), che si basa su dati di dimensione standard da 32 bit (ovvero 4 byte). Ogni byte rappresenta un numero (da 0 a 255) ed è separato dagli altri byte da un punto.

	102.54.94.97

Questo indirizzo contiene due tipi principali di informazioni: la prima parte individua la rete fisica in cui il dispositivo è collegato, mentre la seconda identifica il dispositivo stesso.

	102.54.94 = Rete
	97 = Dispositivo o host

Se un dispositivo ha un indirizzo IP diverso da quello della rete a cui è collegato, non avrà accesso alla rete stessa. Due reti separate possono comunicare tra loro tramite Routing.

Gli indirizzi IPv4 possono essere privati (indicati anche come indirizzi privati RFC1918) o pubblici. Nel primo caso appartengono ad un range specifico di IP:
```
10.0.0.0 - 10.255.255.255
172.16.0.0 - 172.31.255.255
192.168.0.0 - 192.168.255.255
```
	Questi IP privati sono relativi al network in cui si trovano (intranet), quindi non sono univoci per la rete pubblica: due reti diverse possono avere gli stessi IP privati.

La traduzione da IP privato a pubblico avviene tramite [NAT], ovvero Network Address Translation (di solito la funzione è svolta dal [Router])

##### Indirizzi IPv4 speciali
Alcuni indirizzi IP sono dedicati a funzionalità specifiche, come il [broadcast]() di messaggi e gli indirizzi di rete e non possono essere assegnati agli **host**.
Alcuni indirizzi IP sono dedicati a funzionalità specifiche, come il [broadcast]() di messaggi e gli indirizzi di rete e non possono essere assegnati agli **host**.

###### Loopback
Gli indirizzi loopbacksono utilizzati da un host per attrarre il traffico su se stesso (ad esempio per effettuare il **ping**)
```
127.0.0.0/8
127.0.0.1
127.255.255.254
```
###### Link-local
Gli indirizzi link local sono usati per l'assegnazione automatica degli indirizzi IP (Automatic Private IP Addressing, o APIPA). Sono utilizzati dai client Windows per l'autoconfigurazione nel caso gli altri metodi di configurazione non abbiano avuto successo. Possono anche essere usati per il peer-to-peer (connessione paritaria tra due dispositivi, ovvero nella quale entrambi siano sia client che server, ovvero equivalenti).

##### Indirizzamento Legacy Classful
Ideato nel 1981, consisteva nella classificazione degli indirizzi in 5 categorie, in base alla numerazione dell'IP
- Classe A (0.0.0.0/8 - 191.255.0.0/16), per le reti di grandi dimensioni (più di 16 milioni di hosts)
- Classe B (128.0.0.0/16 - 191.255.0.0/6), per le reti medio-grandi (in media 65.000 hosts)
- Classe C (192.0.0.0/24 - 233.255.255.0/24) per supportare reti di piccole dimensioni, con massimo 254 hosts
- Classe D (224.0.0.0 - 239.0.0.0), dedicata al [multicast](#multicast)
- Classe E (240.0.0.0 - 255.0.0.0), sperimentale.
Questa classificazione è diventata antiquata a metà degli anni 90, con l'introduzione del World Wide Web, che ha portato un'evoluzione ad un raggruppamento senza classificazione, basato sull'allocazione degli indirizzi IP in base al numero di indirizzi che possono essere giustificati. La gestione degli stessi è affidata allo IANA (Autorità per l'Assegnazione dei Numeri in Internet), che smista gli indirizzi in base al RIR (Registro Internet Regionale) di riferimento, che gestisce i vari ISP (Internet Service Provider) locali:
- **AfriNIC** (African Network Information Centre) - Africa Region
- **APNIC** (Asia Pacific Network Information Centre) - Asia/Pacific Region
- **ARIN** (American Registry for Internet Numbers) - North America Region
- **LACNIC** (Regional Latin-American and Caribbean IP Address Registry) - Latin America and some Caribbean Islands
- **RIPE NCC** (Réseaux IP Européens Network Coordination Centre) - Europe, the Middle East, and Central Asia

#### IPv6
##### Descrizione
E' un'evoluzione dell'[IPv4](#IPv4), ideata per risolvere il problema della carenza di disponibilità di nuovi indirizzi. L'IPv6 è un codice di lunghezza pari a 128bit (rispetto ai 32 dell'IPv4), consistente in 8 blocchi di codice esadecimale da 64 bit l'uno: ogni blocco ha un valore minimo di **0000** ad un massimo di **ffff**.
```
2001:0db8:acad:a088:0000:0000:0000:0123 = 128 bit
0db8 = 16 bit
0 = 0000 (4bit)
d = 1101 (4bit)
b = 1011 (4bit)
8 = 1000 (4bit)
```

Come nel caso dell'IPv4, anche l'IPv6 può essere **pubblico** o **privato** (anche il funzionamento è simile). Nel primo caso si parla di [GUA](#GUA) (Global Unicast Address), mentre nel secondo di [LLA](#LLA) (Link-Local Address). 
##### Struttura
Può essere diviso in Prefisso e ID dell'interfaccia. Assieme questi due dati (aventi come somma delle lunghezze 128 bit), permettono di identificare con precisione il dispositivo di destinazione e la sottorete di riferimento:
```IPv6
[Prefisso]            [ID dell'interfaccia]
2001:0db8:000a:0000 + 0000:0000:0000:0000
```

E' possibile rappresentare l'ID dell'interfaccia tramite [notazione CIDR](#CIDR), indicando la lunghezza dell'ID al termine del Prefisso (separati da uno "/"):
```IPv6
2001:0db8:000a::/64
```

**N.B.** E' consigliato utilizzare sempre un CIDR di 64, poiché il protocollo [SLAAC](#SLAAC) usa questo numero come predefinito per l'ID dell'interfaccia e quindi facilita la creazione e la gestione delle sottoreti.

Anche in questo caso, ci sono dei metodi predefiniti di comunicazione all'interno della stessa [LAN](./Reti#LAN):
- [Unicast](./Reti#Unicast)
- [Multicast](./Reti#Multicast)
- Anycast, simile alla [boradcast](./Reti#Broadcast).

Gli indirizzi Anycast si presentano quando più dispositivi condividono ko stesso IPv6.

**N.B.** Il metodo Broadcast è accessibile tramite comunicazione multicast aperta a tutti i dispositivi.
##### Convenzioni
Si usano delle convenzioni per descrivere un indirizzo IPv6:
- Si omettono gli zeri a sinistra del blocco (es. 00b2 diventa b2)
- Due blocchi si separano dai due punti ```:```
- Se uno o più blocchi consecutivi hanno valore vuoto, vengono saltati e rappresentati semplicemente con ```::```.
- La regola precedente può essere utilizzata solo una volta
Quindi il blocco può essere rappresentato anche in forma compressa
```
Forma estesa:
2001:0db8:acad:0000:a088:0000:0000:0123

Forma compressa:
2001:db8:acad:0:a088::123
```

Il protocollo IPv6, a differenza del suo [predecessore](#IPv4), non permette la frammentazione dei dati da parte del [router](./Macchina#Router).
##### GUA
Deve esser unico a livello globale, come nel caso degli indirizzi pubblici in [IPv4](#IPv4) e può essere scomposto in 3 parti:
- [Prefisso](#ipv6#struttura) globale di routing;
- ID di sottorete;
- ID dell'interfaccia.

E' possibile ottenere un GUA in 3 modi:
- **SLAAC**: metodo **stateless** (ovvero non necessita che le informazioni vengano salvate da nessuna dispositivo) che prevede l'autoassegnazione di un IPv6 e la successiva comunicazione agli altri router;
- **SLAAC** e **stateless DHCPv6 Server**: Dopo aver creato il proprio indirizzo GUA, il dispositivo invia dati relativi indirizzo del **server DNS** e **nome del dominio** al server DHCP
- **Stateful DHCP**: Dopo un ciclo RA/RS con il router, il dispositivo invia un [DHCP solicit](<#DHCP#Configurare una rete con DHCP>) ad Server DHCP per ottenere un indirizzo IPv6 a registrare i propri dati sul server.
In ognuno dei tre casi, il dispositivo potrà effettuare una chiamata [DAD](#DAD) per verificare che l'indirizzo sia effettivamente libero.

**N.B.** Nel terzo caso l'IP verrà assegnato tramite protocollo [EUI-64](#eui-64) e non tramite [SLAAC](#slaac), quindi non sarà generato randomicamente dal dispositivo, ma avrà dal server (che conferirà di default un [CIDR](#cidr) di /64)

L'IAAA ha assegnato agli indirizzi pubblici i seguenti prefissi globali di routing:
- 001
- 2000::/3
Il GUA è composto da 3 parti:
- Prefisso globale di routing
- ID di sottorete
- ID dell'interfaccia
##### LLA
Comparabile ad un indirizzo [IPv4](#IPv4) privato. E' identificabile dall'indirizzo riantrante nel range **fe80::/10** (ovvero tutti gli indirizzi inclusi tra fe80:: e febf::).

Come nel caso degli IPv4 privati, anche un IPv6 privato può essere assegnato in maniera statica o dinamica (di solito tramite il metodo [EUI](#EUI), ovvero Extended Unique Identifier).
##### Migrazione da IPv4 a IPv6
La migrazione da IPv4 a IPv6 è stata programmata per avvenite nell'arco di anni, nei quali i tecnici potranno aggiornare le reti tramite 3 tecnologie principali:
###### Router dual stack
Permettono di utilizzare contemporaneamente sia l'IPv4 che l'IPv6 per la stessa rete. 
###### Tunneling
Permette di tradurre un indirizzo IPv6 in una rete con IPv4 tramite #incapsulamento
###### Traduzione
Il NAT64 (Network Address Translation 64) permette ai dispositivi abilitati all'IPv6 di comunicare con i dispositivi IPv4 tramite una tecnologia simile al NAT per IPv4, effettuando una traduzione dell'intero pacchetto.

##### ULA
Gli Unique Local Addresses, o indirizzi locali unici (leggi predefiniti) sono:

| Indirizzo     | Utilizzo                             |
| ------------- | ------------------------------------ |
| 001           | GUA                                  |
| 2000::/3      | GUA                                  |
| 2001:db8::/32 | Documentazione                       |
| fe80::/10     | IP privati                           |
| ff02::1       | Multicast a tutti i nodi della LAN   |
| ff02::2       | Multicast a tutti i router della LAN |
#### CIDR
Aggiunge all'indirizzo IPv4 (o IPv6) una indicazione relativa alla [maschera di sottorete](<./Reti#Subnet mask>). La notazione #cidr consiste nell'accoppiare l'indirizzo IPv4 ad un secondo numero (di solito una potenza di 2), fino ad un massimo di 31 ed indica il numero di bit identificativi alla rete principale (permettendo di identificare il numero massimo di macchine  collegabili alla sottorete di riferimento).
Il numero (anticipato sempre dal simbolo **/**), identifica il numero di bit riservati alla [maschera di sottorete](<./Reti#Subnet mask>). Per identificare l'IP della sottorete di riferimento basta effettuare un [AND logico](<./Operatori#Moltiplicazione booleana>) tra indirizzo IP e maschera di sottorete:

```
11000000.10101000.00100000.01100001 AND      (IP: 192.168.032.097/27)
11111111.11111111.11111111.11100000 =        (Subnet mask 255.255.255.224)
-------------------------------------
11000000.10101000.00100000.01100000          (Subnet 192.168.032.096)
```
	Indica una sottorete all'indirizzo 192.168.032.096, che contiene 31 dispositivi (255 - 224) al suo interno.

	102.54.94.97/24
	CIDR:
	In questo caso ci sono un massimo di 256 indirizzi collegati a questo indirizzo IPv4, considerando quello del router stesso.

Sempre tramite notazione CIDR, è possibile identificare il primo e l'ultimo host utilizzabile, assieme all'indirizzo per trasmissioni in [broadcast](./Reti#Broadcast): 
- Primo indirizzo IP per host disponibile: sarà il primo ip immediatamente successivo rispetto all'indirizzo di sottorete
- Indirizzo di broadcast: l'ultimo indirizzo disponibile della sottorete
- Ultimo indirizzo IP per host: il penultimo indirizzo disponibile della sottorete

```
IPv4 =        192.168.  2. 38/24
Subnet mask = 255.255.255.  0 (derivata dalla notazione cidr)
Sottorete =   192.168.  2.  0

Primo host =  192.168.  2.  1
ultimo host = 192.168.  2.254
broadcast =   192.168.  2.255
```

Ovvero:
![[./../Immagini/Pasted image 20241001184553.png]]

### WPA
Wi-fi Protected Access è un'evoluzione del WEP, che utilizza un metodo di crittazione [TKIP](#tkip) (Protocollo di Integrità Temporale della Chiave) per crittare la chiave (256-bit) in maniera dinamica (cambia ad ogni pacchetto inviato).
La versione personal richiede l'immissione di una password per ottenere l'accesso alla rete. 

Tra le funzionalità offerte ci sono:
- Controlli dell'integrità dei messaggi
- implementazione del TKIP

### WPA2
Evoluzione del WPA, utilizza crittazione obbligatoria tramite [AES] (Standard di Crittazione Avanzato) e la sostituzione del protocollo TKIP con il [CCMP](#ccmp). Come il WPA, richiede l'immissione di una password preimpostata per ottenere l'accesso nella versione Personal. E' possibile sfruttare due diversi meccanismi di autenticazione:
- Personale: ovvero l'autenticazione avviene tramite l'uso di una chiave condivisa (utilizzato per le reti domestiche e le reti piccole)
- Aziendale: avviene tramite RADIUS (Remote Authentication Dial-In User Service), attraverso il quale ogni utente possiede una password privata con cui autenticarsi

### WPA3
E' attualmente il metodo di protezione delle reti wireless più avanzato. Implementa gli ultimi metodi di sicurezza e impedisce l'uso dei metodi Legacy (datati). Non tutti i dispositivi sono abilitati all'uso di questo protocollo.
Rispetto al WPA2, questo protocollo protegge anche dall'ascolto della comunicazione durante la fase di handshake dei dispositivi e del successivo uso del brute-force per identificare la chiave PSK.
Questa casistica si evita grazie all'uso dell'Autenticazione Simultanea tra Eguali (SAE).

Questo protocollo agevola anche la comunicazione con i dispositivi IoT tramite protocollo [DDP] (Protocollo di Approvvigionamento del Dispositivo), che permette a dispositivi *headless* (senza interfaccia grafica per cambiare le impostazioni) una connessione agevole e sicura alla rete.
Per le reti aperte, la WPA3 permette di crittare il traffico, aggiungendo un livello di sicurezza per attacchi di tipo sniffing.

### WEP
Versione datata di comunicazione per connessioni wireless tramite protocollo [RC4]. Ormai sostituita dai protocollo WPA. E' uno dei protocolli ammessi nel frame di controllo dello standard 802.11 ed il primo utilizzato per mettere in sicurezza le comunicazioni tramite chiave statica.

### WPS
Il Wifi Protected Setup viene utilizzato per impostare una rete wireless casalinga sicura. Richiede l'utilizzo di un PIN per connettersi alla rete (meccanismo al giorno d'oggi attaccabile tramite [brute-force](../cybersecurity#Brute-force), motivo per il quale è considerato superato e non più sicuro)

### SAE
L'Autenticazione Simultanea tra Uguali è un protocollo utilizzato da [WPA3](#wpa3) e da 802.11-2016 per evitare l'esposizione della Chiave Pre-Condivisa (PSK).

## Data link
Gestisce l'instradamento dei **frame** a livello Fisico. Lo [switch](./Macchina#Switch) è un esempio di dispositivo che si occupa della gestione dei protocolli in questo livello. A differenza degli altri protocolli, questo livello aggiunge sia un header che un trailer al PDU. 
### LLC
E' un sottolivello del livello Data Link, corrispondente al protocollo IEEE 802.2, si occupa della comunicazione tra i livelli [2 (Data Link)](<#Data link>) e [3 (Network)](#Network). Si occupa di inserire informazioni relative al protocollo Network si sta utilizzando (ad esempio, permette làutilizzo di protocolli IPv4 e IPv6 allàinterno della stessa rete)
### MAC
Il Media Access Control (traducibile come Controllo dell'accesso al dispositivo) è un protocollo utilizzato dal [NIC](./Macchina#NIC), che assegna un codice composto da sei blocchi da due cifre esadecimali ciascuno, **univoco** e non modificabile al dispositivo su cui è installata la [Scheda di rete o NIC](./Macchina#NIC).
```
FF-FF-FF-FF-FF-FF
```
Si occupa dell'incapsulamento dei dati e del controllo all'accesso ai media, gestendone il flusso tramite controllo dei messaggi per fare in modo da processare sempre solo un messaggio per volta ed inserire gli altri messaggi in attesa, tramite algoritmi di retromarcia e ritrasmissione. Gestisce i processi tra il livello Data Link e il livello Fisico del modello ISO/OSI.

Di solito il MAC si compone di due parti:
1. Codice del produttore (OUI) (24-bit)
2. Identificativo del prodotto (24-bit)

### Ethernet
Anche noto come  protocollo **IEEE 802.3**, Ethernet è un protocollo utilizzato per gestire le comunicazioni tra due macchine collegate alla stessa rete.
Un messaggio che utilizza questo protocollo ha una lunghezza standardizzata che varia da 64 a 1518 bytes, dei quali d 46 a 1500 sono dedicati ai dati da trasmettere, mentre i rimanenti vengono utilizzati per inserire i dati necessari alla trasmissione dello stesso, ovvero:
1. Preambolo (7byte)
2. Delimitatore di inizio frame (1 byte)
3. Indirizzo MAC di destinazione (6 byte)
4. Indirizzo MAC di provenienza (6 byte)
5. Tipo di lunghezza (2 byte)
6. Dati  (46-1500 byte)
7. Frame di controllo della sequenza (4 byte)

Se l'host che invia il messaggio non possiede l'indirizzo MAC del destinatario:
- Se appartiene alla stessa [LAN](./Reti#LAN), invierà una richiesta ARP per ottenere l'indirizzo MAC e aggiornare la tabella di routing;
- Se appartiene ad una rete diversa, inserirà l'indirizzo MAC del [Default gateway](./Reti#Gateway).
Una volta inviato il messaggio, se la macchina ha l'indirizzo MAC corrispondente al destinatario, accetterà ed elaborerà il messaggio, altrimenti effettuerà il drop (il messaggio viene scartato).

Il protocollo lavora anche a livello 1 [Fisico](#Fisico) del modello ISO/OSI (protocollo IEEE 802.3), istituendo degli standard a supporto delle seguenti larghezze di banda:
- 10Mbps
- 100 Mbps
- 1000 Mbps
- 10.000 Mbps
- 40.000 Mbps
- 100.000 Mbps
## Fisico
### Descrizione
Gestisce il trasporto dei **frame** a livello materiale, ovvero come i dati vengono rappresentati materialmente. I mezzi di trasporto di dati più utilizzati sono la luce e l'elettricità per i **collegamenti tramite cavo** e il **collegamento wireless**. I protocolli in questo livello sono gestiti da:
- [ISO]
- [ANSI/TIA]
- [ITU-T]
- [ANSI]
- [IEEE]

Gli standard possono essere categorizzati per area di interesse in:
- Componenti fisici
- Codifica
- Segnalazione

#### Codifica
Permette di definire le modalità di conversione dei **frame** (dati) da un formato binario ad uno utilizzabile nei supporti fisici. Un esempio è lil modello di codifica Manchester (utilizzata per la codifica nel protocollo [10Mbps Ethernet](#Ethernet)), che stabilisce l'utilizzo di:
- Alto voltaggio per rappresentare il valore 1
- Basso voltaggio per il valore 0

#### Segnalazione
Si occupa di gestire la modalità di generazione e propagazione del segnale in base alla modalità di [codifica](#Codifica) scelta.

#### Misure
##### Bandwidth
La larghezza di banda rappresenta il numero massimo di dati trasportabile da una rete. Si misura valutando la quantità di dati trasportata (di solito bit, Megabit o Gigabit) nell'unità di tempo (di solito un secondo).

##### Latenza
Rappresenta la quantità di tempo necessaria affinché un **frame** inviato da un dispositivo, raggiunga il dispositivo di destinazione. Si utilizza spesso per verificare la presenza di eventuali **colli di bottiglia** (bottleneck), ovvero punti in cui i dati vengono trasmessi più lentamente.

##### Throughput
Indica la quantità effettiva di dati che attraversa un mezzo in un determinato arco di tempo. Si differenzia dalla [Lunghezza di banda](#Bandwidth) a causa di elementi esterni quali:
- Quantità di traffico presente nel mezzo
- Tipo di traffico
- Latenza creata dal numero di dispositivi che propagano il messaggio nella rete

##### Goodput
Indica la quantità di dati utilizzabili trasferibili. Si calcola sottraendo al [throughput](#Throughput) il tempo necessario per:
- Stabilire una sessione
- Risolvere i vari Aknowledgments
- Effettuare gli incapsulamenti
- Effettuare la ritrasmissione dei dati

### Componenti fisici
#### Descrizione
Sono tutti quei componenti come cavi, NIC ed interfacce, che permettono il trasporto fisico dei dati.


[Vedi qua](./Macchina#Cablaggio)
# Altri protocolli
## Autenticazione
### 802.1x
Un organizzazione gestisce l'autenticazione della tua identità, effettuata in base a delle credenziali o un certificato che viene validato dal Server RADIUS, e autorizza l'accesso alla rete.

### CHAP
Il Challenge Handshake Authentication Protocol (protocollo di autenticazione tramite sfida della stretta di mano) si basa sull'invio da parte dell'utente di una password hashata, che viene successivamente comparata dal server con una sua versione id password (anch'essa sottoposta ad hashing). Se i valori corrispondono, la trasmissione continua.

### EAP
L'Extensible Authentication Protocol (protocollo di autenticazione estensibile) è un set di protocolli basato sull'utilizzo di una password, che viene inserita dall'utente, cifrata ed inviata al server, che provvede a confrontarla con un certificato contenuto nella usa memoria.

#### EAP-TLS

#### PEAP

#### EAP-TTLS

#### EAP-FAST

### Kerberos
Utilizza meccanismi di cifratura forti per richiedere all'utente di dimostrare la sua autenticazione, tramite richiesta di autenticazione da parte del server verso il client.
Il server Kerberos contiene tutti gli id e le password degli utenti registrati (che hanno accesso ai servizi) e le chiavi segrete  condivise con gli altri server a cui ha fornito un ticket di accesso.

L'elemento di base per l'autenticazione è il ticket, che viene utilizzato per un processo di autenticazione in due fasi:
1. Il server Kerberos fornisce all'utente che si vuole autenticare un ticket di fornitura ticket
2. Il client invia il ticket ricevuto, assieme ad un messaggio contenente i servizi che vuole utilizzare al server

Grazie alla cifratura delle comunicazioni, questo protocollo rende superfluo l'utilizzo di password, che potrebbero essere intercettate da utenti terzi.

I ticket hanno una durata temporale prima della scadenza.

### PAP
Il Password Authentication Protocol si basa sull'invio di una coppia di valori (nome utente e password), inviati al server come testo semplice.

### RADIUS
Il [Remote Authentication Dial-In User Service](https://it.wikipedia.org/wiki/RADIUS) è un protocollo di autenticazione utilizzato in applicazioni di accesso reti o di mobilità IP. Viene effettuato tramite immissione di nome utente e password.
La password viene cifrata ed entrambi i dati vengono spediti dal client RADIUS al server RADIUS, che risponde con il nome utente, responsabilità e servizi autorizzati in chiaro. Questo implica la necessità di ulteriori misure di protezione da attacchi di [replay](../cybersecurity#replay) con l'utilizzo di questo protocollo.

### TACACS+
Sfrutta il protocollo TCP per inviare i dati cifrati (nome utente, password, servizi disponibili e responsabilità) tra client e server. Dato che l'amministratore di rete gestisce le ACL, i filtri ed i privilegi utente, è di solito la scelta migliore in ambito aziendale.

- Permette di separare i processi di autenticazione, autorizzazione e responsabilità
- Offre un buon livello di confidenzialità grazie alla cifratura del body dei messaggi
- Utilizza il [CHAP](#chap) per stabilire la comunicazione

## Cifratura
### AES
Lo Standard Avanzato di Crittazione utilizza il protocollo CCMP (Protocollo per il Codice di Autenticazione Anti-Cifratura con Messaggio di Autenticazione tramite Block Chain), che incorpora un meccanismo di Controllo di Integrità del Messaggio (**MIC**), che permette di verificare se la parte crittata o quella non crittata del messaggio sono state alterate.

### CCMP
Il Counter Cipher Mode with Block Chaining Message (Modalità di contro cifratura con blocco della catena dei messaggi) è un protocollo di cifratura dei dati.

### TKIP
Temporal Key Integrity Protocol è il metodo di crittazione utilizzato dal protocollo [WPA](#wpa), che permette di crittare i payload di [livello 2](<#2 - Collegamento>)

### PSK
Chiave Pre Condivisa.


## Collegamento

### Router redundancy protocol
Protocollo utilizzato per assicurare una duplica connessione tra LAN e rete esterna. tramite la biforcazione della connessione in due edge-router, che permette una connessione costante tra le due reti anche nel caso di guasto di uno dei due edge-router.

### Spanning tree
Utilizzato per aumentare la ridondanza di una rete ed evitare i loop quando più switch vengono collegati tra loro. Si occupa di gestire le connessioni, in modo tale che, nel caso ci sia un loop di connessioni tra dispositivi a causa di biforcazioni delle connessioni, solo un percorso venga utilizzato, lasciando il secondo spento ed attivabile in caso di malfunzionamenti.
![[Pasted image 20241109164039.png]]

## Manipolazione e consegna dei dati
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


## Da smistare

### IPCM
L' #IPCM è utilizzato per il monitoraggio delle reti 

### DAD
Il Duplicate Address Detection è un protocollo utilizzato da un dispositivo per verificare che l'indirizzo [IPv6](#IPv6) da lui generato non abbia duplicati all'interno della [LAN](./Reti#LAN).
Il dispositivo invia un messaggio [Broadcast](./Reti#Broadcast) alla rete, contenente il proprio indirizzo IPv6. Nel caso un altro dispositivo abbia lo stesso indirizzo IPv6, invierà un messaggio di risposta ([NS](#ICMPv6#Network)) al primo host, contenente il proprio indirizzo [MAC](#MAC).

### SLAAC
La Stateless Address Autoconfiguration permette ad un dispositivo di autoassegnarsi un indirizzo [IPv6](#IPv6) in base a dei parametri di partenza (come l'indirizzo del Gateway di default e la maschera di sottorete). E' il protocollo utilizzato nelle reti [LAN](./Reti#LAN) per configurare un dispositivo abilitato ad IPv6 e fornirgli un proprio indirizzo IPv6 tramite protocollo [ICMPv6](#ICMPv6).


# Well-known ports
Le [Well-known ports](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers) sono un'indicizzazione (elaborata dallo [IANA](macchina#iana)) del numero di porta consigliato per la ricezione di chiamate in base al protocollo utilizzato.

| Porta | Destinazione                                 |
| ----- | -------------------------------------------- |
| 20    | [TCP](./Protocolli#TCP) - Data               |
| 21    | TCP - Control                                |
| 22    | [SSH](./Protocolli#SSH)                      |
| 23    | [Telnet](./Protocolli#Telnet)                |
| 25    | [SMTP](./Protocolli#SMTP)                    |
| 37    | Time (anche UDP)                             |
| 49    | [TACACS+](#tacacs+)                          |
| 53    | [DNS](./Protocolli#DNS) (anche UDP)          |
| 67    | [DCHP](./Protocolli0#DCHP) Server (solo UDP) |
| 68    | [DCHP](./Protocolli0#DCHP) Client (solo UDP) |
| 69    | [TFTP](./Protofolli#TFTP)                    |
| 80    | [HTTP](./Protocolli#HTTP)                    |
| 109   | [POP](#POP)                                  |
| 110   | [POP](#POP)                                  |
| 139   | Login tramite [NetBIOS]()                    |
| 143   | [IMAP](./Protocolli#IMAP)                    |
| 161   | [SNMP](#SNMP) (solo UDP)                     |
| 443   | [HTTPS](#https)                              |
| 1645  | Contabilità RADIUS                           |
| 1646  | Contabilità RADIUS                           |
| 1812  | Autenticazione RADIUS                        |
| 1813  | Contabilità RADIUS                           |

# Possibili problematiche
## Sovraffollamento
il #sovraffollmento è  un eccessivo numero di richieste in un breve arco di tempo, che porta all'impossibilità del serve di rispondere in tempo normale.
### Coda
La #queue è un meccanismo di protezione del server dal #sovraffollmento, che consiste nel conferire un valore numerico alle varie richieste, che definisce l'ordine in cui esse verranno trattate dal server (di solito in ordine temporale). 

