# Locazione di memoria
I dati possono essere di diverse tipologie:

[primitivi]

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

[non primitivi]
#array	 
	
	[1, "sdf", true, 2]

- Se un array contiene lo stesso tipo di variabili al suo interno, si definisce #omogenea
- Se un array è formato da coppie chiave-valore, si definisce #associativo

#oggetti
	
	{"chiave":"valore", "chiave2":"valore2"}


# Cablaggio
Insieme di collegamenti e impianti fisici, che permettono l'interconnessione tipicamente nell'ambito di un edificio (o gruppo di edifici) per la realizzazione di una rete.
## Cavo coassiale
Cavo per TV
## Doppino
I doppini UTP sono classificati in categorie
## Fibra ottica
### FTTC
### FTTH
# NIC
Nota anche come [Scheda di rete](https://it.wikipedia.org/wiki/Scheda_di_rete), permette il collegamento alla rete e la trasmissione dei dati. E' composta da:
- Ingresso - doppino
# Porte
Sono dispositivi che permettono il collegamento della macchina con periferiche esterne. Le porte possono essere fisiche o di rete.
## Porte di rete
Sono porte adibite alla comunicazione tra dispositivi tramite [Rete](./Reti) e sono rappresentate da un sistema di numerazione a 16 bit (65.536 porte in totale). Queste sono raggruppate in base all'uso in base a convenzioni.

| Porte       | Destinazione                                                                             |
| ----------- | ---------------------------------------------------------------------------------------- |
| 0-1023      | Porte destinate allo IANA e utilizzate a livello di sistema operativo (Well-known ports) |
| 1024-49151  | Utilizzate come riferimento tra applicazioni                                             |
| 59152-65535 | Liberamente utilizzabili                                                                 |

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
| 22    | Login tramite [SSH](./Protocolli#SSH)        |
| 23    | Login tramite [Telnet](./Protocolli#Telnet)  |
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

L'unico compito dello switch è quello di leggere gli indirizzo [MAC](./Protocolli#MAC) del pacchetto di dati (non legge, ad esempio, gli indirizzi IP dei dispositivi). Questi indirizzi MAC sono poi comparati ai dati presenti nella Tabella degli Indirizzi MAC (nota anche come Content Addressable Table, o CAM), al fine di verificare quali porte collegare.
## Modem
Il #modem è un dispositivo di ricetrasmissione che ha funzionalità logiche di modulazione/demodulazione in trasmissioni analogiche e digitali.
## Router
Sono strumenti più intelligenti dei [[#Modem]], in quanto permettono di trovare automaticamente percorsi alternativi per la trasmissione di pacchetti qualora si riscontrassero problemi di rallentamento o blocco del traffico nel percorso predefinito.
Utilizza #protocollo [IP](Protocolli di comunicazione#IP), [IPX](Protocolli di comunicazione#IPX), ed [Apple talk](Protocolli di comunicazione#Apple talk).
### Tabelle di routing