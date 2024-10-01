# Tipologie di reti
Le reti sono categorizzate in base alla loro dimensione e complessità. Si dividono in:
## Reti domestiche
Sono reti composte da pochi dispositivi, connesse ad internet.
## Piccole reti aziendali e uffici (SOHO)
Rispetto alle reti domestiche può aumentare il numero di macchine collegate alla rete. Di solito sono presenti risorse condivise, disponibili solo all'interno della rete stessa.
## Reti di medie dimensioni
Sono reti estese, che possono contenere migliaia di utenti (un esempio è una rete scolastica).
## Reti globali
Un esempio è [Internet](./Internet).

# Endpoint
Gli endpoint sono i dispositivi che funzionano da tramite tra l'utente e la rete. Possono essere divisi in base alla tipologia di dispositivo e al suo utilizzo in:
- Dispositivi portativi;
- Dispositivi casalinghi connessi alla rete (Smart home);
- Dispositivi smart collegati ad altro tipo di rete.
Ogni dispositivo può essere un Client (riceve il dato) o un Server (invia il dato). Nel caso un dispositivo funga sia da **client** che da **server** in una **rete**, la rete assume il nome di **peer-to-peer** (P2P).
## Portatili
- Smartphone
- Tablet
- Smartwatch
- Smart glasses
## Smart home
- Sistemi di sicurezza
- Elettrodomestici
- Smart TV
- Console di gioco
## Altri dispositivi
- Automobili
- Tag RFID
- Sensori ed attuatori
- Dispositivi medici

# Dati
## Unità di misura
L'unità di misura standard per rappresentare la dimensione dei dati è il **bit**, ovvero un elemento binario (vero o falso) che rappresenta lo stato dell'elemento.
Una seconda unità di misura molto utilizzata è il **byte**, ovvero 8 bit. Il byte rappresenta il minimo numero di bit impiegati per rappresentare un carattere tramite codifica [ASCII](/Codifiche.md#ASCII).
Multipli del bit sono:

```
bit (b) = 1/0
byte (B) = 8b
kilobit (kb) = 1.000b
megabit (Mb) = 1.000.000b
gigabit (Gb) = 1.000.000.000b
terabit (Tb) = 1.000.000.000.000b

megabyte (kB) = 1.000 B = 8.000 b
```
Altre unità di misura collegate al bit sono:
```
bit  per secondo (bps): Numero di bit elaborati in un secondo
kilobit per secondo (kbps)
megabit per secondo (Mbps)
ecc.

Latenza (s): Secondi necessari affinchè un dato viaggi tra du epunti della rete
```
Quantità di dati inviati, assieme alla latenza e alla tipologia di dati trasmessi, permette di calcolare la capacità di produzione di un sistema (*throughtput*).

## Trasmissione
I dati possono essere trasmessi in qualunque metodo che permetta di stabilire un flusso parzializzabile e rappresentabile tramite codice binario. I mezzi (media) più utilizzati sono:
- Impulsi elettrici
- Impulsi luminosi
- Onde radio
## Lunghezza di banda

# Layer di accesso
## Incapsulamento e l'Ethernet Frame
Si basa sul protocollo [Ethernet](./Protocolli.md#Ethernet)
Consiste in un gruppo di 7 blocchi :
1. Preambolo
2. Delimitatore di inizio frame
3. Indirizzo MAC di destinazione
4. Indirizzo MAC di provenienza
5. Tipo di lunghezza
6. Dati
7. Frame di controllo della sequenza
### Switch Ethernet
Le intestazioni di un pacchetto Ethernet, utilizza delle tabelle di indirizzi MAC per permettere di stabilire le voci 3 e 4 dell'Ethernet Frame. Lo [Switch] ha il compito di: 
- Verificare (ed in caso aggiornare) l'indirizzo MAC del mittente ed il codice della rispettiva porta; 
- Leggere gli indirizzi MAC di destinazione del pacchetto ricevuto ed indirizzarlo all'uscita corretta (comparandolo a tutti gli indirizzi e rifiutando la connessione nel caso non combacino).
1. Verifica se l'indirizzo MAC di origine è incluso nella tabella e in caso non lo sia lo aggiunge alla porta di ricezione
2. Verifica se il destinatario è incluso nella tabella degli indirizzi MAC
3. Invia il messaggio alla porta registrata, altrimenti lo inoltra a tutte le porte, esclusa quella di ricezione.
Il processo si ripete per il messaggio di risposta, aggiornando la tabella anche per il secondo indirizzo MAC
### Tabella di indirizzi MAC
Una tabella di indirizzi MAC contiene una lista di indirizzi MAC, collegati alle varie porte, a cui possono venire collegati i vari dispositivi (o **host**. Ogni dispositivo ha un proprio indirizzo MAC).

# [Protocollo internet](./Protocolli#IP)

### DHCP

IL DHCP, o Dynamic Host Control Protocol (Protocollo di controllo dinamico degli host), è un protocollo di assegnazione automatica degli indirizzi IP agli host, che può essere utilizzato in alternativa all'assegnazione statica degli indirizzi, dove l'operatore assegna manualmente gli indirizzi IP ai vari dispositivi connessi.

Mentre la configurazione statica permette di avere un maggior controllo della rete, il protocollo DHCP permette di avere una maggiore adattabilità, rendendo possibile effettuare il cambio di porta di accesso per il dispositivo e maggiore velocità di realizzazione (anche solo perché si evita di inserire gli indirizzi IP statici in ogni dispositivo e tenerne traccia).
Nel caso di rete wireless, il Router lavora sia da DHCP client (in quanto elabora i messaggi da inviare all'ISP) che DHCP server (in quanto gestisce gli indirizzi IP dei dispositivi connessi alla rete).
#### Configurare una rete con DHCP
[Come attivare il DHCP su Windows](https://support.microsoft.com/it-it/windows/modificare-le-impostazioni-tcp-ip-bd0a07af-15f5-cd6a-363f-ca2b6f391ace)
1. Il client invia in [#Broadcast] un pacchetto (chiamato **DHCP Discover**), contenente l'indirizzo MAC al Server DHCP.
2. Il Server riceve il messaggio ed invia un **DHCP Offer**, contenente l'indirizzo IP assegnato, una [[#Gateway mask]] e l'Indirizzo [Gateway] di default.
3. L'Host riceve il messaggio, invia una DHCP request di accettazione dell'offerta e aggiorna le proprie impostazioni IP
4. Il Server aggiorna la Tabella degli indirizzi IP ed invia un messaggio di accettazione (Acknowledgement).
## Network segmentation
Il router non propaga le richieste di Broadcast o richieste indirizzate a indirizzi IPv4 privati (Dominio di 2 livello di Broadcast). Per trovare gli indirizzi MAC di tutte le macchine a cui inviare un messaggio, si usa il Protocollo di Risoluzione degli Indirizzi ([ARP](./Protocolli#ARP)), che permette di inviare una richiesta [Boradcast](#broadcast) a tutti gli indirizzi IP della rete locale. Per trovare gli indirizzi IPv4 invece, di solito si utilizza il [DHCP](./protocolli#dhcp), ovvero Dynamic Host Configuration Protocol (protocollo di configurazione dinamica degli host).
Nel caso di reti di grosse dimensioni, inviare messaggi in broadcast porta a rallentamenti della rete. Per questo di solito si segmenta la rete in sottoreti per permettere di inviare messaggi in broadcast ad una quantità limitata di utenti e non intasare la rete.
Criteri di segmentazione di una rete possono essere:
- Localizzazione
- Gruppo o funzionalità
- Tipo di dispositivo

Questi criteri sono anche alla base del modello [Hierarchical Network Design](./Reti#HND).

Le comunicazioni sono suddivise anche in base al numero di dispositivi che devono ricevere i messaggi:
### Unicast
Avviene quando un dispositivo invia un messaggio a solo un destinatario.
```
192.172.0.1 = Mittente
192.172.0.20 = Destinatario
```
	Gli indirizzi IPv4 destinati alla ricezione di messaggi Unicast hanno una maschera di sottorete inclusa tra 1.1.1.1 e 223.255.255.255, con alcuni indirizzi utilizzati per specifici scopi.
### Broadcast
Avviene quando un dispositivo invia un messaggio a tutti i dispositivi presenti nel network. Esempio:
```
192.172.0.1 = Mittente
255.255.255.255 = Destinatario
```
	In questo caso 255.255.255.255 è un indirizzo standardizzato per indicare tutti i dispositivi

Un messaggio broadcast è utilizzato per essere ricevuto da tutti i dispositivi della rete (il router on inoltra il messaggio al di fuori della sottorete [LAN](./Reti#LAN) del dispositivo emittente).
### Multicast
Avviene quando un dispositivo invia un messaggio a specifici dispositivi (più di uno). L'indirizzo IPv4 destinato alle comunicazioni **[multicast](#Multicast)** è nel range tra 224.0.0.0 e 239.255.255.255.
Esempio:
```
192.172.0.1 = Mittente
235.255.255.255 = Destinatario
```

Solo alcuni protocolli (come l'OSPF, che avviene tramite il canale 224.0.0.5) sono abilitati alla gestione di multicasting. I dispositivi che non supportano il protocollo scelto per la comunicazione, ignoreranno automaticamente i pacchetti ricevuti.
Dato che di solito i dispositivi conoscono solo l'indirizzo IP del destinatario, ma non il MAC, viene utilizzato il protocollo [ARP](./Protocolli#ARP) per ritrovare l'indirizzo MAC corretto. Il protocollo ARP è un esempio di messaggio [Broadcast](#Broadcast)
## Gateway
Il Gateway è un dispositivo che permette di inoltrare messaggi tra [LAN](./Reti#LAN) diverse (ognuna delle quali imposta un indirizzo IPv4 tramite DHCP o manualmente e inoltra lo stesso, assieme alla [sottomaschera di rete](<./Reti#Subnet mask>) ai dispositivi collegati.
### Router
Spesso (specialmente per le LAN domestiche) il ruolo di gateway viene svolto dal [Router]. In questo caso, essendo questo anche l'elemento di connessione tra la  tra [LAN](./Reti#LAN) e la [rete pubblica](<./Reti#Rete pubblica>), si è soliti utilizzare degli [IPv4](./Protocolli#IPv4) privati per i dispositivi collegati piuttosto che degli indirizzi pubblici, per separarli dalla rete pubblica.

L'ISP (Internet Service Provider), di solito assegna, al router un indirizzo IP pubblico, da utilizzare per le comunicazione con la rete pubblica tramite protocollo [DHCP](./Protocolli#DHCP), rendendo così il router il dispositivo che gestisce gli scambi tra [LAN](./Reti#LAN) e [Internet](<./Reti#Rete pubblica>) e traduce gli indirizzi IP tramite le [maschere di sottorete](<./Reti#Subnet mask>).
- [NAT](./Reti#NAT)
