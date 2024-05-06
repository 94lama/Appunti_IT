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
# Scheda di rete
Permettono il collegamento alla rete. Sono composte da
- Ingresso - doppino
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
## Modem
Il #modem è un dispositivo di ricetrasmissione che ha funzionalità logiche di modulazione/demodulazione in trasmissioni analogiche e digitali.
## Router
Sono strumenti più intelligenti dei [[#Modem]], in quanto permettono di trovare automaticamente percorsi alternativi per la trasmissione di pacchetti qualora si riscontrassero problemi di rallentamento o blocco del traffico nel percorso predefinito.
Utilizza #protocollo [IP](Protocolli di comunicazione#IP), [IPX](Protocolli di comunicazione#IPX), ed [Apple talk](Protocolli di comunicazione#Apple talk).
### Tabelle di routing