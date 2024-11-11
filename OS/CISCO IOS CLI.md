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

## Router

### ACL

#### Configurazione

Creazione: effettuabile nella modalità configurazione del router:
ACL numerata
```cisco
access-list <access-list-number> {deny | permit | remark <text>} <source> [<source wildcard>] [log]
```
	[] = opzionale
	{a | b | c} = inserire un parametro tra a, b o c

ACL nominale
```cisco
<protocollo> access-list standard <access-list-name>
```
	In questo caso si procede configurandele ACE

ESEMPIO:
```Cisco
config <nome terminale> # entro nella modalità di configurazione

ip access-list standard NO_ACCESS # crea la ACL NO_ACCESS per i lprotocollo di livello 3 ip
deny host 192.168.0.10 # blocco le comunicazioni con l'host 192.168.0.10
permit any
exit

interface g0/0 # seleziono l'interfaccia g0/0
ip access-group <nome lista> out # assegno la ACL alle chiamate in uscita
```

Eliminare una ACL
```cisco

```

Applicare un IPv6 ACL ad un'interfaccia router
```cisco
ipv6 traffic-filter
```

#### Blocco protocollo

Bloccare comunicazioni con protocollo SNMP
```cisco
no snmp-server
```

# Comandi

Avere la lista dei comandi disponibili
```cisco
?
```
	N.B. il comando può essere utilizzato anche a seguito di un altro comand, per avere la lista degli argomenti utilizzabili con il comando stesso o dopo i primi caratteri di un comando (o una serie di comandi) per ottenere la lsita di comandi che iniziano con quella stringa di caratteri

Crea una [ACL](../cybersecurity#acl)
```cisco
<protocollo da verificare> access-list <tipo (opzionale, extended di default)> <nome> <parametri>
```
	PROTOCOLLI ACCETTATI:
	ahp # Authentication Header Protocol
	dvmrp
	eigrp # protocollo nativo di routing della Cisco
	esp # Encapsulation Security Protocol
	gre # tunneling della Cisco
	icmp # Internet Control Message Protocol
	igmp # Internet Gateway Message Protocol
	ip
	ipinip # IP in IP tunneling
	nos
	object-group # Service object group
	ospf
	pcp # Payload Compression Protocol
	pim # Prorocol Independent Multicast
	tcp # Transmission Control Protocol
	udp # User Datagram Protocol
	
	CONTROLLO DELLE PORTE:
	0-65535 # numero della porta
	bgp # Border Gateway Protocol (179)
	chargen # generatore di caratteri (19)
	cmd # comandi da remoto (514)
	daytime # daytime (13)
	discard # scarta (0)
	domain # DNS (53)
	echo # Echo (7)
	exec # Exec (512)
	finger # Finger (70)
	ftp # FTP (21)
	ftp-data # FTP data (20)
	gopher # Gopher (70)
	hostname # server dei NIC degli hostname (101)
	ident # protocollo Ident (113)
	irc
	klogin
	kshell
	login
	lpd
	msrcp
	nntp
	onep-plain
	onep-tls
	pim-auto-rp
	pop2
	pop3
	smtp
	sunrpc
	syslog
	tacacs
	talk
	telnet
	time
	uucp
	whois
	www
Se in modalità configurazione del dispositivo. Una volta inviato il comando si entrerà in modalità di configurazione della ACL, quindi sarà possibile inserire o modificare delle ACE

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
		access-lists # mostra le ACL impostate
		arp
		clock
		dhcp
		hosts
		interfaces | Verifica lo stato delle interfacce e vede se ci sono messaggi di errore
		ip
		ip interface
		ip route | Vwerifica le informazioni di routing del livello 3
		mac
		mac-address-table
		protocols | Vede quali protocolli siano attivi
		running-config | mostra le configurazioni dell'host
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

Assegnare un indirizzo IP
```cisco
ip address [indirizzo ip] [maschera di sottorete]
```

Registrare l'indirizzo IP del gateway di default
```cisco
ip degault-gateway [indirizzo ip]
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
