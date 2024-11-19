# Struttura
La CLI di CISCO permette di accedere, visualizzare informazioni e configurare i componenti hardware di una rete.

I comandi seguono sempre la struttura:
```
[Propmpt][modalita' di esecuzione][comando] [parole chiave] [argomenti (opzionali)]
```
	ESEMPIO: Switch>ping 192.168.0.1

## CLI
La CLI ha due modalità di utilizzo (differenziate in base alla quantità di comandi abilitati):
- EXEC User: ovvero la modalità base (comunemente chiamata modalità di visualizzazione)
- EXEC Privilegiata: permette di inviare tutti i comandi disponibili sull'IOS

## Switch
Gli [switch](./../Tecnologie/Macchina#switch) sono elementi utilizzabili per collegare vari dispositivi tra loro all’interno della stessa LAN. Per configurare uno switch Cisco, basta collegare un computer (che sia fornito di software per comunicare con la switch, ad esempio Tera Term) alla porta di configurazione dello switch ([UTP](./../Tecnologie/Macchina#utp)) (situata sopra la porta dello storage). Per configurare lo switch connettere i cavi prima di avviare lo switch nel caso si voglia configurare in modalità out-of-band (senza che il computer sia connesso allo switch, evitando quindi problemi di connessione o di lentezza della rete al costo di doversi collegare direttamente allo switch fisicamente).

Una volta avviato lo switch, Verranno letti automaticamente l’OS (sistema operativo, salvato nella memoria flash) e lo startup config (salvato nella NVRAM), che permetterà di caricare le configurazioni dello switch (running config).

## Router
Dotato di:
- Sistema operativo (OS)
- Central processing unit (CPU)
- Random-access memory (RAM)
- Read-only memory (ROM)
- Nonvolatile random-access memory (NVRAM)

É un dispositivo che permette di direzionare il flusso di dati tra porte. Pertanto é composto da:
- **Porte di console** - Permettono l’accesso diretto al dispositivo per la configurazione
- **Interfacce LAN** - Possono essere GigabitLan o EthernetLan e permettono di collegare altri dispositivi al router
- **Network Interface Modules (NIMs)** - Slot di espansione delle interfacce del router.

I router della CISCO sono anche dotati di meccanismo di controllo bassato su [HMAC](../cybersecurity#hmac) per i messaggi LSU (Link Separate Update)

### Configurazione
L’accesso all’area di configurazione può essere effettuata tramite connessione fisica diretta (porte di console) o remota tramite interfaccia WAN, utilizzando il protocollo SSH o la porta aux (nel caso di uso della rete telefonica e modem).

Durante l’avvio lo switch avvierà la POST per trovare il file bootstrap.

## CISCO Cognitive Intelligence
Software [antimalware](../Cybersecurity#Antimalware) cloud-based che utilizza dati di tipo statistico per cercare attività sospetta all'interno di una rete.

# Comandi

Avere la lista dei comandi disponibili
```cisco
?
```
	N.B. il comando può essere utilizzato anche a seguito di un altro comand, per avere la lista degli argomenti utilizzabili con il comando stesso o dopo i primi caratteri di un comando (o una serie di comandi) per ottenere la lsita di comandi che iniziano con quella stringa di caratteri

Attivare la modalità EXEC Privilegiata
```cisco
enable
```
	N.B. Quando la modalità EXEC privilegiata è attiva, apparirà il simbolo '#' dopo il nome del dispositivo che si sta utilizzando (es. Router#)

Mostrare dei dati di sistema
```cisco
show
```
	PAROLE CHIAVE:
		aaa
		arp | mostra la tabella ARP
		cdp neighbors detail | Per convalida layer 1 e 2, mostra i dispositivi Cisco collegati
		clock
		dhcp
		hosts
		interfaces | Verifica lo stato delle interfacce e vede se ci sono messaggi di errore
		ip
		ip interface [brief]
		ipv6 interface [brief] | Mostra gil indirizzo IPv6 dei dispositivi collegati e utilizza il loro MAC per creare gli indirizzzi LLA. Dopodichè mostra gli indirizzi IPv6 privati e pubblici dei dispositivi, o l'indicazione che la porta è libera.
		ip route | Verifica le informazioni di routing del livello 3
		ipv6 route | Mostra gli indirizzi IPv6 dei dispositivi collegati con indicazione se il dispositivo è collegato in locale (L) o con IP pubblico (C)
		mac
		mac-address-table
		port
		protocols | Vede quali protocolli siano attivi
		running-config | mostra le configurazioni dell'host
		switch
		tech-support | mostra una serie di show, utili nel caso di inoltro di un ticket
		version | Verifica la memoria, le interfacce e le licenze del dispositivo

## EXEC Privilegiata
I seguenti comandi son disponibili unicamente per la modalità EXEC Privilegiata.

Fornite notifiche legali
```cisco
banner motd [delimitatore] [messaggio] [delimitatore]
```

Entrare nella modalità di configurazione del terminale
```cisco
configure terminal
```
	E' possibile utilizzare anche la chortcut "configure t"
	
	N.B. Una volta richiamato il comando, il terminale mostrerà la scritta "config" tra parentesi dopo il nmome del dispositivo che si sta configurando

Salvare la configurazione attuale (renderla attiva sin dall'avvio della macchina)
```cisco
copy running-config startup-config
```

Disattivare la modalità EXEC Privilegiata ed entrare in quella EXEC User
```cisco
disable
```

Uscire dalla modalità di modifica interfaccia
```cisco
end
```

Uscire dalla modalità di configurazione del terminale
```cisco
exit
```
	N.B. E' possibile uscire anche premendo Ctrl + Z

### Configurazione
Questa modalità permette di configurare il dispositivo. E' segnalata sulla CLI nell'area della **modalità di esecuzione**:
```cisco
S1(config)#
```

Impostare una password di accesso
```cisco
enable secret [password]
```

Assegnare un nome al dispositivo
```cisco
hostname [nome]
```

Per entrare nella modalità di modifica di un'interfaccia
```cisco
interface <tipo_connessione> <numero_porta>
```
	ESEMPIO: interface ethernet 0/1
	E' anche possibile abbreviare il comando in: "int e 0/1" 
	
	TIPI DI CONNESSIONE:
	- ethernet
	- vlan
	- 
	
	N.B. E' possibile passare da un'interfaccia ad un'altra tramite questo comando.

Per entrare nelle configurazione di una sottozona
```cisco
line <tipologia> <numero_porta>
```
	ESEMPIO: line console 0
	N.B. Una volta richiamato il comando, il terminale mostrerà la scritta "config-line" tra parentesi dopo il nmome del dispositivo che si sta configurando
	
	TIPOLOGIE:
	- console 0
	- vty 0 5 (per connessioni SSH o Telnet)

Criptare tutte le password salvate sulla configurazione attuale
```cisco
service password-encryption
```

#### Interfaccia
L'interfaccia è segnalata sulla CLI nell'area della **modalità di esecuzione**:
```cisco
S1(config-if)#
```

Uscire dall'interfaccia e tornare alla modalità configurazione
```cisco
exit
```

Assegnare un indirizzo IPv4
```cisco
ip address [indirizzo ip] [maschera di sottorete]
```

Assegnare un indirizzo IPv6 LLA
```cisco
ipv6 address [indirizzo ip]/[cidr]
```
	OPZIONI:
	Nel caso si voglia usare un indirizzo privato, utilizzare l'argomento "link-local"

Registrare l'indirizzo IP del gateway di default
```cisco
ip degault-gateway [indirizzo ip]
```

Attiva l'interfaccia
```cisco
no shutdown
```
#### Sottozona
La sottozona è segnalata sulla CLI nell'area della **modalità di esecuzione**:
```cisco
S1(config-line)#
```

Uscire dalla sottozona e tornare alla modalità configurazione
```cisco
exit
```

Effettuare il login
```cisco
login
```

Impostare una password
```cisco
password [password]
```

Assegnare un protocollo di accesso alla rete
```cisco
transport input
```
	ARGOMENTI:
		ssh
		telnet
		none
		all

## Shortcut

| Combinazione     | Descrizione                                                                                                                                                    |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Ctrl + A         | Sposta il cursore all'inizio della **linea di comando**                                                                                                        |
| Ctrl + C         | Esce dalla modalità configurazione e torna nella **modalità EXEC privilegiata**. Se in modalità Setup, termina la modalità e ritorna al **prompt dei comandi** |
| Ctrl + E         | Sposta il cursore alla fine della **linea di comando**                                                                                                         |
| Ctrl + I         | Mostra il prompt di sistema e la linea di comando dopo che viene mostrato un messaggio                                                                         |
| Ctrl + L         | Mostra il prompt di sistema e la linea di comando dopo che viene mostrato un messaggio                                                                         |
| Ctrl + R         | Mostra il prompt di sistema e la linea di comando dopo che viene mostrato un messaggio                                                                         |
| Ctrl + W         | Cancella la parola a sinistra del cursore                                                                                                                      |
| Ctrl + X         | Azzera i caratteri della **riga di comando**                                                                                                                   |
| Ctrl + Z         | Esce dalla modalità configurazione e torna nella **modalità EXEC privilegiata**.                                                                               |
| Ctrl + Shift + 6 | Termina la sequenza in atto (usato per **interrrompere processi** come il **DNS lookup**, **traceroute**, **ping** ecc.)                                       |
| Esc + D          | Cancella tutti i caratteri a destra del cursore fino alla fine della parola                                                                                    |
