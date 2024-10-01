# Modelli
![](https://www.aiutocomputerhelp.it/wp-content/uploads/layer-logico-tcp-ip.jpg)
## ISO/OSI
La Pila #ISO/OSI rappresenta 7 fasi diverse del processo di comunicazione, tra loro consequenziali (ovvero non è possibile saltare protocolli per il passaggio da un punto iniziale ad un punto finale)
### Livelli
Il modello rappresenta il flusso di dati suddiviso in 7 categorie (chiamate livelli), attraverso le quali il pacchetto viene analizzato e trattato per permetterne il trasporto
![[./../Immagini/Pasted image 20240930152150.png]]
#### Applicazione
E' il momento in cui ci interfacciamo con un applicazione (che sia un software di mailing, un browser o un'app). A questo livello vengono supportati i servizi di rete, come:
- Email
- Trasferimento di file
- Condivisione di database
- Altro
I dati vengono convertiti in #PDU (Protocol Data Unit), ovvero un'unità di informazioni scambiata tra 2 entità in un protocollo di comunicazione a strati.
il #PDU è composto da un #header e da un #body
#### Presentazione
Una volta che i dati vengono convertiti in #PDU, quest'ultimo viene standardizzato tramite una serie di processi, tra i quali:
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
I protocolli inerenti il Data Link permettono lo scambio di pacchetti tra nodi adiacenti della rete, attraverso il livello fisico. Offre un livello di comunicazione affidabile ed efficiente.
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
## Applicazione
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
### Web
#### DNS
Domain Name System, serve ad attribuire un #dominio a degli indirizzi #IP, in modo tale da rendere più agevole la navigazione degli utenti (es. facebook.com, amazon.it).
Il servizio si basa su dei #server DNS.
E' il primo step per la navigazione su internet odierna, in quanto permette di semplificare il reindirizzamento al server corretto, grazie all'utilizzo di parole piuttosto che indirizzi IP.

Permette di identificare l'IP dall'URL inviato e inviare come risposta l'indirizzo IP corretto del server.
##### URI
Lo Uniform Resource Identifier Indica il segnaposto del server con cui stabilire una connessione 
```
https://it.wikipedia.org/wiki/Uniform_Resource_Identifier#Relazione_fra_URI,_URL_e_URN
```
Rappresenta l'unione di URL e Fragment.
##### URL
Lo Uniform Resource Locator rappresenta la parte dell'URI adibita ad identificare lo specifico file visualizzato ed il protocollo utilizzato per la connessione
```
https://it.wikipedia.org/wiki/Uniform_Resource_Identifier
```
##### URN
Lo Uniform Resource Name rappresenta unicamente il server con cui avviene la comunicazione ed il file richiesto
```
it.wikipedia.org/wiki/Uniform_Resource_Identifier
```
##### Fragment
Identifica eventuali parametri utilizzati durante la chiamata all'interno dell'URI come, ad esempio, l'[anchor](./../Linguaggi/HTML#a) di riferimento o la query richiesta
```
#Relazione_fra_URI,_URL_e_URN
```
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
| 4xx    | Client error                                                                                        |
| 400    |                                                                                                     |
| 404    | Not Found                                                                                           |
| 5xx    | Server Error                                                                                        |
| 502    | Termporary unavailable                                                                              |
#### HTTPS
Protocollo che consiste nell'evoluzione dell' [[#HTTP]], che include un processo di criptazione dei dati (con protocollo [[#SSL]] o [[#TSL]]) durante la trasmissione degli stessi. 

Questo permette di ottenere:
- Autenticazione del sito web
- Protezione della #privacy 
- Integrità dei dati scambiati
### Altro
#### E2EE
La End-to-end Encryption permette di crittare i dati non a livello di #server (come avviene nel #https)
## Presentazione
## Sessione
## Trasporto
I protocolli del livello 4 (trasporto) determinano la metodologia di trasmissione dei dati al livello di [internet](<./Reti#Rete pubblica>), l'ordinamento dei dati e il controllo di flusso (ovvero la velocità di invio e eventualmente il controllo della avvenuta ricezione dei dati).
Durante la sessione, entrambi i dispositivi mantengono aperte delle [porte](<./Macchina#Porte di rete>) prestabilite (identificate in coppia **origine - destinazione**) per permettere l'invio e l'ascolto costante di messaggi di risposta. Le porte vengono inserite nel pacchetto di dati da inviare tramite coppia di [socket](./Macchina#Socket).
### TCP
Il #tcp, ovvero Transmission Control Protocol è un #protocollo **Orientato alla connessione** e quindi considerato affidabile. La connessione è garantita dal three-way handshake, che assicura la connessione reciproca dei due dispositivi per tutta la sessione (durante la quale si potranno trasferire un numero variabile di pacchetti di dati, in base alla tipologia di connessione scelta), che verrà chiusa automaticamente una volta conclusa l'operazione desiderata.
#### Three-way handshake
![[Pasted image 20240219204523.png]]
E' un processo composto da 3 fasi di comunicazione, che viene eseguito ogni volta che avviene uno scambio di pacchetti tramite protocollo #tcp tra due dispositivi. 
#### SYN
Synchronization, ovvero il mittente invia un messaggio al destinatario
#### ACK
Acknowledgement, ovvero il destinatario invia un messaggio al mittente confermando la ricezione del primo messaggio.
Dopodichè un terzo messaggio viene inviato dal mittente al destinatario, contenente il pacchetto di dati.
### UDP
L'User Datagram Protocol è un protocollo paragonabile al [TCP](#TCP), ma senza la presenza del [[#Three-way handshake]]. L'assenza di quel processo permette all' #UDP una maggiore velocità (dovuta all'assenza di fase di riordinamento dei pacchetti), a discapito di una minore affidabilità di scambio. Per questo è spesso utilizzato, ad esempio, per i servizi di #streaming.
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

## Network
### Descrizione
Gestisce l'indirizzamento a livello logico e l'instradamento dei pacchetti e deve assicurare il corretto espletamento delle seguenti funzioni:
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
### IP
Ovvero ***Internet Protocol***. Si occupa della metodologia di frammentazione de instradamento ( #routing) del pacchetto. La dimensione massima del pacchetto dipende dal materiale su cui viene instradato, ed è indicata dal Maximum Transmission Unit ( #mtu). Questo protocollo è gestito dal #gateway.
Il protocollo IP ha 3 caratteristiche principali:
- **Connectionless**: Non c'è nessun tipo di connessione con il destinatario prima dell'dell'invio dei dati;
- **Best effort**: L'indirizzo IP è inaffidabile(in quanto non garantisce la ricezione del messaggio)
- **Media indipendent**: Non dipende dal mezzo di comunicazione utilizzato per trasportare il dato.

Ci sono 2 protocolli principali: IPv4 e IPv6, dove il primo rappresenta attualmente quello più utilizzato ed il secondo un protocollo ideato per risolvere la progressiva scarsezza degli indirizzi IPv4 rispetto alla richiesta mondiale.
#### IPv4
L' #IPv4 è un indirizzo, assegnato ad una rete [LAN](./Reti#LAN), che
si basa su dati di dimensione standard 32 bit, ovvero 4 byte. Ogni byte rappresenta un numero (da 0 a 255) ed è separato dagli altri byte da un punto #dotted-decimal 

	102.54.94.97

Questo indirizzo contiene due tipi principali di informazioni: la prima parte individua la rete fisica in cui il dispositivo è collegato, mentre la seconda identifica il dispositivo stesso.

	102.54.94 = Network locale
	97 = Host

Gli indirizzi IPv4 possono essere privati (indicati anche come indirizzi privati RFC1918) o pubblici. Nel primo caso appartengono ad un range specifico di IP:
```
10.0.0.0 - 10.255.255.255
172.16.0.0 - 172.31.255.255
192.168.0.0 - 192.168.255.255
```
	Questi IP privati sono relativi al network in cui si trovano (intranet), quindi non sono univoci per la rete pubblica: due reti diverse possono avere gli stessi IP privati.

La traduzione da IP privato a pubblico avviene tramite [NAT], ovvero Network Address Translation (di solito la funzione è svolta dal [Router]). Un'altra funzione svolta dal router è la frammentazione:
Nel caso di pacchetti aventi dimensioni troppo elevate, infatti, il protocollo include un processo di divisione del pacchetto in più pacchetti per agevolarne il trasporto. Questo processo prende il nome di **Fragmentation** (processo che tuttavia, causa latenza nella connessione.

##### Notazione CIDR
Aggiunge all'indirizzo IPv4 una indicazione relativa alla [maschera di sottorete](<./Reti#Subnet mask>). La notazione #cidr collega un numero ad una potenza di 2, partendo da /32 come 2^0 e permette di stabilire quante macchine sono potenzialmente collegate alla sottorete di riferimento.

```
11000000.10101000.00100000.01100001 AND      (IP: 192.168.032.097)
11111111.11111111.11111111.11100000 =        (Subnet mask 255.255.255.224)
-------------------------------------
11000000.10101000.00100000.01100000          (Subnet 192.168.032.096)
```
	Indica una sottorete all'indirizzo 192.168.032.096, che contiene 31 dispositivi (255 - 224) al suo interno.

	102.54.94.97/24
	CIDR:
	In questo caso ci sono 256 indirizzi collegati a questo indirizzo IPv4

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
E' un'evoluzione dell'[IPv4](#IPv4), ideata per risolvere il problema della carenza di disponibilità di nuovi indirizzi. L'IPv6 è un codice di lunghezza pari a 128bit (rispetto ai 32 dell'IPv4), consistente in 8 blocchi di codice esadecimale da 64 bit l'uno: ogni blocco ha un valore minimo di 0000 ad un massimo di ffff.
```
2001:0db8:acad:a088:0000:0000:0000:0123 = 128 bit
0db8 = 16 bit
0 = 0000 (4bit)
d = 1101 (4bit)
b = 1011 (4bit)
8 = 1000 (4bit)
```

**ATTENZIONE**
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
##### Migrazione da IPv4
La migrazione da IPv4 a IPv6 è stata programmata per avvenite nell'arco di anni, nei quali i tecnici potranno aggiornare le reti tramite 3 tecnologie principali:
###### Router dual stack
Permettono di utilizzare contemporaneamente sia l'IPv4 che l'IPv6 per la stessa rete. 
###### Tunneling
Permette di tradurre un indirizzo IPv6 in una rete con IPv4 tramite #incapsulamento
###### Traduzione
Il NAT64 (Network Address Translation 64) permette ai dispositivi abilitati all'IPv6 di comunicare con i dispositivi IPv4 tramite una tecnologia simile al NAT per IPv4, effettuando una traduzione dell'intero pacchetto.

#### Header
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

### SSL
Secure Socket Layer
### TSL
Versione aggiornata di [[#SSL]]

### ARP
Il protocollo ARP, o [Addresses Resolution Protocol](https://it.wikipedia.org/wiki/Address_Resolution_Protocol) (Protocollo di risoluzione degli indirizzi) serve ad identificare l'indirizzo MAC di un dispositivo collegato ad una [LAN](./Reti#LAN). Consiste in un invio di una request in [broadcast](./Networking#Broadcast), contenente l'indirizzo [IPv4](#IPv4) del destinatario. Il dispositivo il cui indirizzo IPv4 combacia con quello desiderato, invierà un messaggio di risposta, contenente il proprio indirizzo MAC al mittente. 
### DHCP
Il DHCP, o Dynamic Host Control Protocol (Protocollo di controllo dinamico degli host), è un protocollo di assegnazione automatica degli indirizzi IP agli host, che può essere utilizzato in alternativa all'assegnazione statica degli indirizzi, dove l'operatore assegna manualmente gli indirizzi IP ai vari dispositivi connessi.

Mentre la configurazione statica permette di avere un maggior controllo della rete, il protocollo DHCP permette di avere una maggiore adattabilità, rendendo possibile effettuare il cambio di porta di accesso per il dispositivo e maggiore velocità di realizzazione (anche solo perché si evita di inserire gli indirizzi IP statici in ogni dispositivo e tenerne traccia).
Nel caso di rete wireless, il Router lavora sia da DHCP client (in quanto elabora i messaggi da inviare all'ISP) che DHCP server (in quanto gestisce gli indirizzi IP dei dispositivi connessi alla rete).
#### Configurare una rete con DHCP
[Come attivare il DHCP su Windows](https://support.microsoft.com/it-it/windows/modificare-le-impostazioni-tcp-ip-bd0a07af-15f5-cd6a-363f-ca2b6f391ace)
1. Il client invia in [#Broadcast] un pacchetto (chiamato **DHCP Discover**), contenente l'indirizzo MAC al Server DHCP.
2. Il Server riceve il messaggio ed invia un **DHCP Offer**, contenente l'indirizzo IP assegnato, una [[#Gateway mask]] e l'Indirizzo [Gateway] di default.
3. L'Host riceve il messaggio, invia una **DHCP request** di accettazione dell'offerta e aggiorna le proprie impostazioni IP
4. Il Server aggiorna la Tabella degli indirizzi IP ed invia un messaggio di accettazione (Acknowledgement).

## Data link
Gestisce l'instradamento a livello Fisico. Lo [switch](./Macchina#Switch) si occupa della gestione di questo livello.
### LLC
E' un sottolivello del livello Data Link, corrispondente al protocollo IEEE 802.2, si occupa della comunicazione tra i livelli [2 (Data Link)](<#Data link>) e [3 (Network)](#Network). Si occupa di inserire informazioni relative al protocollo Network si sta utilizzando (ad esempio, permette làutilizzo di protocolli IPv4 e IPv6 allàinterno della stessa rete)
### MAC
Il Media Access Control (traducibile come Controllo dell'accesso al dispositivo) è un protocollo utilizzato dal [NIC](./Macchina#NIC), che assegna un codice composto da sei blocchi da due cifre esadecimali ciascuno, **univoco** e non modificabile al dispositivo su cui è installata la [Scheda di rete o NIC](./Macchina#NIC).
```
FF-FF-FF-FF-FF-FF
```
Si occupa dell'incapsulamento dei dati e del controllo all'accesso ai media, gestendone il flusso tramite controllo dei messaggi per fare in modo da processare sempre solo un messaggio per volta ed inserire gli altri messaggi in attesa, tramite algoritmi di retromarcia e ritrasmissione. Gestisce i processi tra il livello Data Link e il livello Fisico del modello ISO/OSI.

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
Gestisce il trasporto dei dati a livello materiale, ovvero come i dati vengono rappresentati materialmente. I mezzi di trasporto di dati più utilizzati sono la luce e l'elettricità. 
# Altri protocolli
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

# Possibili problematiche
## Sovraffollamento
il #sovraffollmento è  un eccessivo numero di richieste in un breve arco di tempo, che porta all'impossibilità del serve di rispondere in tempo normale.
### Coda
La #queue è un meccanismo di protezione del server dal #sovraffollmento, che consiste nel conferire un valore numerico alle varie richieste, che definisce l'ordine in cui esse verranno trattate dal server (di solito in ordine temporale). 

