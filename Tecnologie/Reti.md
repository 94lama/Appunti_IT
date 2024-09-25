# Introduzione
Internet è la più grande rete al mondo, composta da nodi, attraverso i quali transitano dei dati. Al fine di far avvenire questo scambio di dati, si utilizza il metodo della **commutazione di pacchetto**.
Questo metodo è composto da una serie di processi, che permettono di standardizzare i dati da inviare ed il metodo di spedizione, chiamati [[Protocolli di comunicazione]].
## [Subnetting](https://www.itimarconi.ct.it/sezioni/didatticaonline/informatica/lezionidisistemi/quinta/subnetting.htm)
Il subnetting consiste nel raggruppare i dispositivi connessi alla rete (creando appunto delle sottoreti) per facilitare l'applicazione di Policy di sicurezza e ridurre il peso delle chiamate [broadcast](./Networking#Broadcast) tra dispositivi. La definizione delle sottoreti avviene tramite [maschera di sottorete](<#Subnet mask>).
### Subnet mask
Una [maschera di sottorete](https://it.wikipedia.org/wiki/Maschera_di_sottorete) è un parametro di configurazione utilizzato per identificare la rete alla quale l'host è connesso. Si basa su 4 blocchi numerici da 32 byte (256 bit) ciascuno, attraverso i quali è possibile identificare l'[indirizzo IP](./Protocolli#IPv4) della sottorete utilizzata, tramite [moltiplicazione booleana](<./Operatori#Moltiplicazione booleana>). 

```
Nel caso degli indirizzi IP questoprocesso si applica per ogni blocco, comparandolo alla maschera di sottorete, ad esempio:
192 = 11000000
255 = 11111111    La moltiplicazione permette di avere:
______________
	  11000000    ovvero 192, la cifra corretta del blocco analizzato.

Complicando il discorso, questo permette di identificare l'IP nella sottorete di un dispositivo tramite indirizzo IP pubblico e maschera di sottorete:

IPv4 =   192.168.0.10
Subnet = 255.255.255.245

Questo porterà ad identicifare l'indirizzo della sottorete:
192.168.0
Mentre l'indirizzo della sottorete si calcola tramite moltiplicazione:

245 = 00001111
10  = 11110101
___________________
      00000101 = 5

IPv4 della sottorete: 192.168.0.5
```

#### NAT
Utilizzando l'algoritmo delle maschere di sottorete, è possibile suddividere in maniera efficiente una rete. Per convenzione, gli indirizzi privati sono stati suddivisi in 3 categorie, ognuna delle quali ha delle maschere di sottorete preimpostate, al fine di suddividere le reti in base alla loro capienza: 
```
Per le reti di grandi dimensioni, in quanto permette di contenere più di 16 milioni di dispositivi (256 * 256 * 255), si usa: 
10.0.0.0    -> 255.0.0.0

Per le reti di medie dimensioni, in quanto permette di ospitare più di 65.000 dispositivi, si usa:
172.16.0.0  -> 255.255.0.0

Mentre, per le reti piccole (come quelle domestiche), è sufficiente ospitare fino a 255 dispositivi:
192.168.0.0 -> 255.255.255.0
```
	Si ricorda che il valore 255 significa che il valore dello slot corrispondente non può essere modificato all'interno della sottorete. Quindi, ad esempio, la rete con primo blocco uguakle a 72, può contenere tutti gli indirizzi IP che vanno da 172.16.0.1 a 172.16.255.255 e così via.

Questo processo prende il nome di Network Address Translation (Traduzione degli indirizzi di rete), o NAT.
# Architettura
## Domain controller
E' un server specifico addetto alla gestione delle richieste degli utenti, compreso lo smistamento dei collegamenti e la verifica degli accessi degli utenti, il loro ruolo e l'utilizzo delle risorse di rete.
Di solito i Domain controllers sono organizzati per #cluster  (definiti dall'amministratore di sistema) di computer.
Alcuni dei compiti principali di un Domain Controller sono:
- #autenticazione degli utenti
- #backup
- Definizione delle #policy di accesso
- Gestione dei #database 
Nativo dei sistemi [[Windows]], di recente il suo utilizzo si è diffuso anche per sistemi [[Linux]].
- Il domain controller di [[AWS]] è il servizio [IAM](<AWS#IAM>)
## Active Directory
Active Directory Directory Service è un sistema server centralizzato, composto da un insieme di servizi di rete ( #directory-service, ovvero hardware e account di utenti), adottati dai sistemi operativi [[Windows]], gestito centralmente da server detti "controllori di dominio", utilizzato per gestire e monitorare tutti i dispositivi (e l'accesso alle risorse) tramite l'utilizzo delle #policy.
L'insieme dei servizi di rete dell'active directory (in particolare il servizio di autenticazione [Kerberos](<Protocolli di comunicazione#Kerberos>)), realizzano un'altra delle caratteristiche più importanti, ovvero il [[#Single Sign-On]].
### Single Sign-On
E' un meccanismo tramite il quale un utente, una volta effettuato il login, ha accesso alle risorse disponibili in rete senza dover effettuare nuovamente l'autenticazione per un determinato periodo di tempo.
## Utenti
L'utente è un elemento caratterizzato da
- Nome utente
- Password
- Gruppo
- Tipo

### Password
E' consigliabile effettuare un cambio periodico delle password, anche in base al ruolo occupato nel #dominio:

| Tipologia di utente        | Periodo di cambio password         |
| -------------------------- | ---------------------------------- |
| Livello alto (admin, root) | 30 giorni                          |
| Livello medio (utente)     |                                    |
| Livello basso (guest)      | Singolo accesso (nessuna password) |

### Gruppo
Entità che contiene un determinato numero di utenti, in base a caratteristiche comuni (es. sede lavorativa o settore). 
### Tipo
- Amministratore: ha  il controllo completo del dominio
- Standard: può utilizzare i servizi stabiliti dall'amministratore e modificare le impostazioni di sistema che non influiscono sugli altri utenti
- Guest: account speciale, utilizzato per fornire un accesso limitato e temporaneo alle risorse (spesso specifiche) del #dominio ad utenti terzi. Di solito ha **nome utente** Guest e nessuna **password**
## Directory Service
Programma (o insieme di programmi) avente lo scopo di organizzare, gestire e memorizzare informazioni e risorse centralizzate e condivise all'interno di [[Reti]] di computer, rese disponibili agli utenti. Alcuni concetti fondamentali durante la creazione di un #directory-service sono:
- Prestazioni
- Sicurezza
- Facilità di utilizzo
- Disponibilità
Di solito i dati vengono salvati su più #server per due motivi principali: La **sicurezza** relativa la perdita degli stessi e la **disponibilità** degli stessi (ovvero la velocità di accesso agli stessi indipendentemente dall'area geografica dalla quale vengono richiesti e dal numero di richieste ricevute).
Per aumentare le prestazioni, di solito vengono create applicazioni per facilitare l'accesso a specifici elementi del #dominio agli utenti (es. viene rimossa la necessità di inserire il percorso di accesso allo specifico dato/elemento).
## Commutatori
### Switch
### Hub
## Domain client
# LAN
Local Area Network ( #LAN) è il sinonimo di Rete Locale. Nel caso due dispositivi si trovino nella stessa LAN, la rete di comunicazione è diretta.
Una rete locale consiste in una serie di dispositivi collegati tra loro. I principali sono:
- Switch: permette di connettere tra loro più dispositivi;
- Router: permette di connettersi alla [rete pubblica](<#Rete pubblica>) se ha anche funzionalità di [gateway](#Gateway) ([vedi differenze](https://community.fs.com/it/article/router-vs-gateway-what-is-the-similarity-and-difference.html)) o ad altre LAN;
- Dispositivi [endpoint](./Networking#Endpoint).
Nel caso di reti LAN aziendali, spesso esse vengono suddivise in [sottoreti](#Subnetting) tramite router, per facilitare i controlli di sicurezza, evitare il sovraffollamento o raggruppare i nodi secondo categorie (es. localizzazione geografica dei nodi, mansione lavorativa dei dipendenti, ecc.).
# Rete pubblica
Nota anche come Wide Area Network ( #WAN). Nel caso due dispositivi vogliano comunicare tramite WAN, la comunicazione passa dal #gateway, ovvero un macchinario fornito da un #provider, che permette l'instradamento dei pacchetti all'interno di una rete, che dirige le comunicazioni con i dispositivi connessi alla rete pubblica.
# Gateway
E' il dispositivo che collega e gestisce i processi di comunicazione dalla rete privata a quella pubblica ( #WAN) i norma è identificato con il #router.
Di solito è rappresentato nella WAN con l'indirizzo
```
192.168.1.1
```
	I rimi due byte dipendono dal gestore ed eventualmente dalle impostazioni della rete.
# DNS
Il #DNS, o Domain Name System, è un algoritmo che associa un [IP](Protocolli%20di%20comunicazione.md#IP di comunicazione#IP>) ad un #URL
# Roba da smistare
## MAC
Un #mac-addresss (dove MAC sta per _[Media Access Control](https://it.wikipedia.org/wiki/Media_Access_Control "Media Access Control")_), detto anche "indirizzo fisico" o "indirizzo Ethernet", è un codice di 48 [bit](https://it.wikipedia.org/wiki/Bit "Bit") associato ad ogni [dispositivo di rete](https://it.wikipedia.org/wiki/Scheda_di_rete "Scheda di rete") che implementa lo standard [Ethernet](https://it.wikipedia.org/wiki/Ethernet "Ethernet"). Il suo scopo principale è quello di attribuire un'identità univoca a ciascuno dei nodi collegati ad uno stesso segmento di rete, consentendo quindi comunicazioni locali di tipo [unicast](https://it.wikipedia.org/wiki/Unicast "Unicast").
## Comandi da shell
### ping
Serve a verificare la velocità di comunicazione tra due dispositivi
```sh
ping <indirizzo_ip>
```
	Risposta da 142.250.180.164: byte=32 durata=8ms TTL=114
	nel caso il proprietario della macchina abbia più server, l'ip potrebbe
	esere diverso di volta in volta
Questo comando viene ripetuto all'infinito su [[Linux]] e [[iOs]], mentre solo 4 volte su [[Windows]]
### trace route
Ritorna gli indirizzi dei server ( #gateway) in versione #IPv4, attraverso i quali passa la trasmissione. Per Linux o iOS.
```sh
traceroute <indirizzo_ip>
```
	 Traccia instradamento verso www.google.it [142.251.209.3]
	su un massimo di 30 punti di passaggio:
	
	  1     2 ms     1 ms     1 ms  192.168.1.1
	  2     6 ms     6 ms     6 ms  net-93-71-88-1.cust.vodafonedsl.it [93.71.88.1]
	  3     *        *        *     Richiesta scaduta.
	  4     *        *        *     Richiesta scaduta.
	  5     8 ms     7 ms     7 ms  185.210.48.38
	  6    10 ms     7 ms     7 ms  185.210.48.39
	  7     8 ms     7 ms     7 ms  185.210.48.3
	  8    80 ms     8 ms    25 ms  72.14.239.144
	  9    12 ms    41 ms     7 ms  142.251.235.175
	 10     9 ms     6 ms     7 ms  mil04s50-in-f3.1e100.net [142.251.209.3]
	
	Traccia completata.
Per Windows
```sh
tracert <indirizzo_ip>
```
E' possibile negare la risposta al comando. Nel caso il nodo non viene stampato nel terminale.
# Software
## CISCO Packet Tracer
