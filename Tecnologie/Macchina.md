# Locazione di memoria
I dati possono essere di diverse tipologie:
## Primitivi

#interi

	 1

#decimali

	1.45

#booleani

	true

#stringhe
	
	"stringa" o 'stringa' (insieme di caratteri alfanumerici) 

#string_interpolation: "elemento $variabile elemento"
		Linguaggi che usano la string interpolation: [[Php]] 

## Non primitivi
#array	 
	
	[1, "sdf", true, 2]

- Se un array contiene lo stesso tipo di variabili al suo interno, si definisce #omogenea
- Se un array è formato da coppie chiave-valore, si definisce #associativo

#oggetti
	
	{"chiave":"valore", "chiave2":"valore2"}


# Cablaggio
Insieme di collegamenti e impianti fisici, che permettono l'interconnessione tipicamente nell'ambito di un edificio (o gruppo di edifici) per la realizzazione di una rete.
## Cavo di rame
Mezzo di trasporto di impulsi elettrici. In quanto tale è suscettibile a:
- Interferenza elettromagnetica o di onde radio
- Crosstalk (ovvero un disturbo del campo elettrico causato da altri cavi vicini)
### Cavo coassiale
Cavo ormai quasi del tutto sostituito dall'[UTP](#UTP), è composto da un filo spesso di rame, avvolto da uno strato spesso di isolante plastico, a sua volta avvolto da una rete metallica a da uno strato protettivo finale per i danni fisici.
Ci sono 4 tipi principali di connettori per il cavo coassiale:
- Bayonet Neill-Concelman (BNC)
- Tipo N
- TIpo F

Il cavo coassiale è ancora utilizzato durante:
- L'installazione di reti wireless per collegare l'antenna all'equipaggiamento radio
- Installazione di internet tramite cavo per trasportare il segnale dalla centralina all'interno delle abitazioni private (in sostituzione con il cavo in fibra)

### UTP
Gli Unshielded Twisted-Pair noti anche come doppini) sono composti da quattro coppie di cavi, ognuna delle quali intrecciata un numero diverso di volte su se stessa, avvolte da uno strato di materiale isolante (tipo plastica). Ogni coppia è identificabile dal colore dell'isolante. I cavi vengono intrecciati in coppia per ridurre il Crosstalk.
Ci sono 4 categorie di UTP:
- 3 - Usata originariamente per la trasmissione di dati sonori, in seguito utilizzata per la trasmissione di dati. Si riconosce perchè i cavi non sono intrecciati per formare la coppiaò
- 5 - Usata per la trasmissione dei dati
	- 5 - Bandwidth 100Mbps
	- 5E - Bandwidth 1000Mbps
- 6 - Viene aggiunto un separatore tra le coppie di cavi rispetto al modello 5 e supporta un traffico fino a 10Gbps
- 7 - Simile al 6
- 8 - Supporta un traffico fino a 80 Gbps

#### Terminazioni
I cavi UTP hanno diverse terminazioni, tra le quali le più importanti sono:
- RJ-45 UTP, ovvero la classica terminazione per la porta Ethernet del computer
- RJ-45 UTP Socket, ovvero la controparte femmina della terminazione, installata sui pc

Le coppie di cavi vengono collegate alle terminazioni in base a degli standard, tra i quali i più importanti sono:
![[./../Immagini/Pasted image 20241011131951.png]]

### STP
Gli Shielded Twisted-Pair sono una diretta evoluzione degli [UTP](#UTP), che provvede ad aumentarne la robustezza e la protezione da interferenze esterne tramite avvolgimento delle 4 coppie di cavi all'interno di un foglio metallico prima ed una rete metallica successivamente.
## Fibra ottica
Composta da numerosi cavi in fibra di vetro. Si utilizza di norme per:
- Collegamenti internet
- Reti aziendali
- Reti a lunga distanza
- Cavi di rete sottomarini
### Cavi
Ci sono due modelli di cavi in fibra, che si differenziano sia per la dimensione, che per il metodo di trasporto del fascio:
- SMF e MMF

Mentre i cavi più vecchi permettono il trasporto unidirezionale dei fasci di luce (era quindi necessario installarli in coppie), quelli più recenti permettono uno scambio bidirezionale.
#### SMF
Il Single-Mode Fiber è un cavo composto da:
- Un nucleo di vetro, nel quale passa il fascio di luce (diametro 9 micron)
- Uno strato di rivestimento in vetro (diametro 125 micron)
- Una copertura polimerica di colore giallo
Trasporta il fascio di luce in maniera retta tramite laser e permette di coprire distanze fino a 100 km
## MMF
Il Multi-Mode Fiber è un cavo composto da:
- Un nucleo di vetro, nel quale passa il fascio di luce (diametro 50-62.5 micron)
- Uno strato di rivestimento in vetro (diametro 125 micron)
- Una copertura polimerica di colore aranciuone
Trasporta il fascio di luce (prodotto da un LED) tramite riflessione nelle varie superfici interne e permette di coprire distanze fino a 2 km
### FTTC
Fiber-to-the-Cabin
### FTTH
Fiber-to-the-House
# Cache

# NIC
Nota anche come [Scheda di rete](https://it.wikipedia.org/wiki/Scheda_di_rete), permette il collegamento alla rete e la trasmissione dei **frame** (dati)). La NIC può essere di tipo fisico o wireless (di solito un dispositivo moderno ha entrambe le modalità installate).

## Fisica
E' composta da:
- Ingresso - doppino

## Wireless

# Porte
Sono dispositivi che permettono il collegamento della macchina con periferiche esterne. Le porte possono essere fisiche o di rete.
## Porte di rete
Sono porte adibite alla comunicazione tra dispositivi tramite [Rete](./Reti) e sono rappresentate da un sistema di numerazione a 16 bit (65.536 porte in totale). Queste sono raggruppate in base all'uso in base a convenzioni.

| Porte       | Destinazione                                                                             |
| ----------- | ---------------------------------------------------------------------------------------- |
| 0-1023      | Porte destinate allo IANA e utilizzate a livello di sistema operativo (Well-known ports) |
| 1024-49151  | Utilizzate come riferimento tra applicazioni                                             |
| 59152-65535 | Liberamente utilizzabili                                                                 |

E' possibile controllare le porte ad uso comune libere di una macchina tramite il comando ```netstat```.
### Socket
L'utilizzo delle porte di rete è rappresentato aggiungendo alla fine dell'[IPv4](./Protocolli#IPv4) due punti e il numero della porta di riferimento.

```192.168.0.1:80```
	In questo caso sto indicando che la porta da utilizzare è la numero 80

Questa rappresentazione delle porte prende il nome di socket.
### IANA
La [Internet Assigned Number Authority](https://www.iana.org/) è un organismo che ha la responsabilità di assegnare gli [indirizzi IP](./Protocolli#IP) e mantenere un registro dei protocolli utilizzati su [internet](<./Reti#Rete pubblica>).
Le porte più utilizzate tramite protocollo [TCP](./Protcolli#TCP) o [UDP](./Protoclli#UDP) (dove segnalato) sono:

| Porta | Destinazione                                 |
| ----- | -------------------------------------------- |
| 20    | [TCP](./Protocolli#TCP) - Data               |
| 21    | TCP - Control                                |
| 22    | [SSH](./Protocolli#SSH)                      |
| 23    | [Telnet](./Protocolli#Telnet)                |
| 25    | [SMTP](./Protocolli#SMTP)                    |
| 37    | Time (anche UDP)                             |
| 53    | [DNS](./Protocolli#DNS) (anche UDP)          |
| 67    | [DCHP](./Protocolli0#DCHP) Server (solo UDP) |
| 68    | [DCHP](./Protocolli0#DCHP) Client (solo UDP) |
| 69    | [TFTP](./Protofolli#TFTP)                    |
| 80    | [HTTP](./Protocolli#HTTP)                    |
| 109   | [POP](./Protocolli#POP)                      |
| 110   | [POP](./Protocolli#POP)                      |
| 139   | Login tramite [NetBIOS]()                    |
| 143   | [IMAP](./Protocolli#IMAP)                    |
| 161   | [SNMP](./Protocolli#SNMP) (solo UDP)         |
| 443   | [SSL](./Protocolli#SSL)                      |
| 1645  | Contabilità RADIUS                           |
| 1646  | Contabilità RADIUS                           |
| 1812  | Autenticazione RADIUS                        |
| 1813  | Contabilità RADIUS                           |

# RAM
Random Access Memory.

# Particolari tipologie di macchine
## HUB
Gli #hub, o ripetitori, sono dispositivi che collegano fra loro gli utenti, smistando i vari pacchetti da una macchina all'altra. Gli hub lavorano tramite banda condivisa.

| Pro       | Contro |
| --------- | ------ |
| Economico | Lento  |
| Versatile |        |
## Switch
Lo #switch è  un'evoluzione dell'[[#HUB]] in termini di performance. Permettono di isolare le porte comunicanti tra loro dal resto, per velocizzare la comunicazione.

| Pro                         | Contro  |
| --------------------------- | ------- |
| Veloce                      | Costoso |
| Maggiore lunghezza di banda |         |

L'unico compito dello switch è quello di leggere gli indirizzo [MAC](./Protocolli#MAC) del pacchetto di dati (non legge, ad esempio, gli indirizzi IP dei dispositivi). Questi indirizzi MAC sono poi comparati ai dati presenti nella **Tabella degli Indirizzi MAC** (nota anche come **Content Addressable Table**, o **CAM**), al fine di verificare quali porte collegare.

Durante la scelta di uno switch, sono da considerare diversi parametri:
- Velocità (dipende dal tipo di cavi accettati e se sono half o full-duplex)
- Numero di porte disponibili
- Scalabilità (se é ampliabile o meno con altri moduli)
- Manutenibilitá

**N.B.** Nel caso di connessione tra full-duplex e half-duplex di solito avviene un conflitto con conseguente blocco delle comunicazioni. Alcuni switch hanno incorporato un meccanismo di auto negoziazione per evitare che il conflitto avvenga.

### CAM
La tabella include tutti gli indirizzi MAC da cui lo switch ha ricevuto un messaggio, correlati alla porta a cui sono collegati. Nel caso si ricevano più messaggi da una stessa porta (ad esempio se la porta è connessa ad un altro switch), la CAM viene popolata con tutti gli indirizzi MAC che riceve.

### Inoltro dati
L’inoltro dei dati tramite switch può avvenire secondo due metodologie diverse:
- Store-and-forward switching (memorizza e inoltra), dove lo switch riceve l’intero frame, verifica eventuali corruzioni e, in caso di loro assenza, inoltra il dato;
- cut-forward switching (taglia e inoltra), dove lo switch inoltra le parti di frame che riceve, prima che completino il frame. L’unico dato necessario (completo prima che inizi la procedura) é l’indirizzo MAC di destinazione. Questo processo si divide in altre 2 categorie:
	- fast-forward, dove i bit ricevuti vengono direttamente inoltrati
	- Fragment-free, dove vengono memorizzati e analizzati i primi 64 Bytes del frammento (che sono quelli dove é più frequente incontrare un errore).

Il primo metodo favorisce il controllo dei dati durante il processo, mentre il secondo la velocità di inoltro.

#### Cavi
Di solito si utilizzano cavi Crossover per connettere uno switch con un altro switch e cavi Straight-through negli altri casi, sebbene molti switch moderni utilizzino lo MDIX per adattare il cavo crossover a tutte le casistiche.

### Buffering
Traducibile come Tamponamento, consiste nel memorizzare i frame ricevuti. Lo si può utilizzare per lo store-and-forward switching, o perché la porta di destinazione risulta temporaneamente non disponibile. I dati possono essere salvati in 2 modi:
- Su una compartimentazione della memoria dedicata alla specifica porta. In questo caso si crea una coda di trasmissione dal dato più vecchio al più recente e si inoltrano seguendo l’ordine 
- Si crea un compartimento temporaneo e dinamico su cui allocare il dato, collegando il blocco alla porta di destinazione (ma dando la possibilità di modificarla)

## Modem
Il #modem è un dispositivo di ricetrasmissione che ha funzionalità logiche di modulazione/demodulazione in trasmissioni analogiche e digitali.
## Router
Sono strumenti più intelligenti dei [[#Modem]], in quanto permettono di trovare automaticamente percorsi alternativi per la trasmissione di pacchetti qualora si riscontrassero problemi di rallentamento o blocco del traffico nel percorso predefinito.
Utilizza #protocollo [IP](Protocolli di comunicazione#IP), [IPX](Protocolli di comunicazione#IPX), ed [Apple talk](Protocolli di comunicazione#Apple talk).

### Tabella di routing
La tabella di routing è un insieme di dati che serve a velocizzare la comunicazione tra macchine, grazie al salvataggio dei dati relativi all'indirizzo del destinatario del messaggio. La tabella di routing è utilizzata sia nel PC, che nei Router, è visualizzabile tramite il comando ```show ip route```, e offre prima una legenda informativa con la spiegazione dei vari acronimi utilizzati (nel caso di tabella memorrizzata su un Router), e poi la lista degli indirizzi memorizzati dalla macchina.

| Codice | Descrizione           |
| ------ | --------------------- |
| L      | Connesso alla LAN     |
| C      | Connessa direttamente |
| B      | BGP                   |
| M      | Mobile                |
| U      | User static route     |
| O      | OSPF                  |
| D      | EIGRP                 |
| S      | Route statica         |

Esempio di tabella di routing IPv4 memorizzata su un dispositivo:

| Destinazione    | Maschera di rete | Gateway      | Interfaccia   | Metriche | Descrizione   |
| --------------- | ---------------- | ------------ | ------------- | -------- | ------------- |
| 0.0.0.0         | 0.0.0.0          | 192.168.10.1 | 192.168.10.10 | 25       | IPv4 Computer |
| 127.0.0.1       | 255.0.0.0        | On-link      | 127.0.0.1     | 306      | Main gateway  |
| 127.255.255.255 | 255.255.255.255  | On-link      | 127.0.0.1     | 306      | Broadcast     |
| 192.168.10.0    | 255.255.255.0    | On-link      | 192.168.10.10 | 306      |               |

## Server
Dispositivi utilizzati prevalentemente per memorizzare dati a lungo termine.

### AAA Server
Vengono utilizzati per memorizzare dati relativi a:
- Autenticazione
- Autorizzazione
- Contabilità (accounting)
I server AAA devono essere impostati per accettare unicamente messaggi tramite protocolli [RADIUS](./protocolli#radius) o [TACACS+] (uno dei due, da decidere in base alle necessità della rete, tenendo conto che il RADIUS non effettua cifratura del nome utente e dei dati contabili).