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

# End point
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

# Protocollo internet
## IPv4
[Vedi IPv4](informatica/Tecnologie/Protocolli.md#IPv4)
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

### Indirizzi IPv4 speciali
Alcuni indirizzi IP sono dedicati a funzionalità specifiche, come il broadcast di messaggi e gli indirizzi di rete e non possono essere assegnati agli **host**.

#### Loopback
Gli indirizzi loopbacksono utilizzati da un host per attrarre il traffico su se stesso (ad esempio per effettuare il **ping**)
```
127.0.0.0/8
127.0.0.1
127.255.255.254
```
#### Link-local
Gli indirizzi link local sono usati per l'assegnazione automatica degli indirizzi IP (Automatic Private IP Addressing, o APIPA). Sono utilizzati dai client Windows per l'autoconfigurazione nel caso gli altri metodi di configurazione non abbiano avuto successo. Possono anche essere usati per il peer-to-peer (connessione paritaria tra due dispositivi, ovvero nella quale entrambi siano sia client che server, ovvero equivalenti).
### Subnet mask
Una [maschera di sottorete](https://it.wikipedia.org/wiki/Maschera_di_sottorete) è un parametro di configurazione utilizzato per identificare la rete alla quale l'host è connesso. 
### Indirizzamento Legacy Classful
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

## IPv6
E' un'evoluzione dell'IPv4, ideata per risolvere il problema della carenza di disponibilità di nuovi indirizzi. L'IPv6 è un codice di lunghezza pari a 128bit (rispetto ai 32 dell'IPv4), consistente in 8 blocchi di codice esadecimale da 64 bit l'uno: ogni blocco ha un valore minimo di 0000 ad un massimo di ffff.
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
- Se uno o più blocchi hanno valore vuoto, vengono saltati e rappresentati semplicemente con ```::```.
Quindi il blocco può essere rappresentato anche in forma compressa
```
Forma estesa:
2001:0db8:acad:a088:0000:0000:0000:0123

Forma compressa:
2001:db8:acad:a088::123
```
### Migrazione da IPv4
La migrazione da IPv4 a IPv6 è stata programmata per avvenite nell'arco di anni, nei quali i tecnici potranno aggiornare le reti tramite 3 tecnologie principali:
#### Router dual stack
Permettono di utilizzare contemporaneamente sia l'IPv4 che l'IPv6 per la stessa rete. 
#### Tunneling
Permette di tradurre un indirizzo IPv6 in una rete con IPv4 tramite #incapsulamento
#### Traduzione
Il NAT64 (Network Address Translation 64) permette ai dispositivi abilitati all'IPv6 di comunicare con i dispositivi IPv4 tramite una tecnologia simile al NAT per IPv4, effettuando una traduzione dell'intero pacchetto.

### DHCP
IL DHCP, o Dynamic Host Control Protocol (Protocollo di controllo dinamico degli host), è un protocollo di assegnazione automatica degli indirizzi IP agli host, che può essere utilizzato in alternativa all'assegnazione statica degli indirizzi, dove l'operatore assegna manualmente gli indirizzi IP ai vari dispositivi connessi.

Mentre la configurazione statica permette di avere un maggior controllo della rete, il protocollo DHCP permette di avere una maggiore adattabilità, rendendo possibile effettuare il cambio di porta di accesso per il dispositivo e maggiore velocità di realizzazione (anche solo perché si evita di inserire gli indirizzi IP statici in ogni dispositivo e tenerne traccia).
[Come attivare il DHCP su Windows](https://support.microsoft.com/it-it/windows/modificare-le-impostazioni-tcp-ip-bd0a07af-15f5-cd6a-363f-ca2b6f391ace)

## Network segmentation
Il router non propaga le richieste di Broadcast o richieste indirizzate a indirizzi IPv4 privati (Dominio di 2 livello di Broadcast). Per trovare gli indirizzi MAC di tutte le macchine a cui inviare un messaggio, si usa il Protocollo di Risoluzione degli Indirizzi ([ARP](./Protocolli#ARP)), che permette di inviare una richiesta [Boradcast](#broadcast) a tutti gli indirizzi IP della rete locale. Per trovare gli indirizzi IPv4 invece, di solito si utilizza il [DHCP](./protocolli#dhcp), ovvero Dynamic Host Configuration Protocol (protocollo di configurazione dinamica degli host).
Nel caso di reti di grosse dimensioni, inviare messaggi in broadcast porta a rallentamenti della rete. Per questo di solito si segmenta la rete in sottoreti per permettere di inviare messaggi in broadcast ad una quantità limitata di utenti e non intasare la rete.
Criteri di segmentazione di una rete possono essere:
- Localizzazione
- Gruppo o funzionalità
- Tipo di dispositivo

Le comunicazioni sono suddivise anche in base al numero di dispositivi che devono ricevere i messaggi:
### Unicast
Avviene quando un dispositivo invia un messaggio a solo un destinatario.
```
192.172.0.1 = Mittente
192.172.0.20 = Destinatario
```
	Gli indirizzi IPv4 destinati alla ricezione di messaggi Unicast hanno una maschera di sottorete inclusa tra 1.1.1.1 e 223.255.255.255, con alcuni indirizzi utilizzati per specifici scopi.
### Broadcast
Avviene quando un dispositivo invia un messaggio a tutti i dispositivi presenti nel network
Esempio:
```
192.172.0.1 = Mittente
255.255.255.255 = Destinatario
```
	In questo caso 255.255.255.255 è un indirizzo standardizzato per indicare tutti i dispositivi

### Multicast
Avviene quando un dispositivo invia un messaggio a specifici dispositivi (più di uno). L'indirizzo IPv4 destinato alle comunicazioni **multicast** è nel range tra 224.0.0.0 e 239.255.255.255.
Esempio:
```
192.172.0.1 = Mittente
235.255.255.255 = Destinatario
```

Solo alcuni protocolli (come l'OSPF, che avviene tramite il canale 224.0.0.5) sono abilitati alla gestione di multicasting. I dispositivi che non supportano il protocollo scelto per la comunicazione, ignoreranno automaticamente i pacchetti ricevuti.