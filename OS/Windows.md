# MS-DOS
Il Sistema di Disco Operativo è un software che permette alle locazioni di memoria di leggere, modificare i file e memorizzarli in maniera organizzata (cartelle) al loro interno. MS-DOS è stato utilizzato nelle prime versioni di Windows, assieme all'interfaccia grafica di Windows stesso, per gestire l'intero sistema operativo del computer. Attualmente è stato sostituito da [Windows NT](#NT), o da nuove funzionalità della GUI (Interfaccia Grafica dell'Utente) (anche se ancora utilizzabile tramite [terminale](#terminale)).

# NT
Acronimo di Windows New Technologies, è 

# Terminale
## Introduzione
Rappresenta la CLI di Windows e può esser utilizzato per impartire comandi al computer (è utilizzabile tramite il tool **cmd.exe**.
- Non è case sensitive per i nomi dei file e per i percorsi
- Le lettere dei dischi sono seguite dal simbolo ```\``` per simboleggiare il ruolo di **root**
- Per richiamare le opzioni aggiuntive (dove presenti), si deve interporre il simbolo ```/``` tra il comando e l'opzione
- Il tasto Tab completa automaticamente la scrittura del comando
- Per cambiare root directory basta digitare la lettera della directory su destinazione, seguita da ","

Il terminale non può eseguire comandi in concerto con la GUI o con il nucleo di Windows. Per queste funzionalità si deve usare la [shell](#shell)

## Lista comandi

Cambiare cartella
```Terminal
cd <percorso>
```
	OPZIONI:
	- E' possibile utilizzare sia i percorsi relativi (che iniziano con il carattere ".") che assoluti
	- .. # Permette di tornare nella sovracartella rispetto a quella attuale
	- \ # Porta alla cartella di root (di solito C)

Copiare un file
```Terminal
copy <file da copiare> <percorso su cui copiare il file>
```

Eliminare un file
```Terminal
del <nome file>
```

Visualizzare la lista dei file nella cartella (directory) corrente
```Terminal
dir
```
	OPZIONI:
	/r # Permette di visualizzare anche i file :ADS correlati ai file inclusi nella directory

Trovare ila stringa di testo all'interno dei file
```Terminal
find
```

Stampare la lista di comandi utilizzabile
```Terminal
help
```
	OPZIONI:
	- E' possibile inserire un comando per cui richiedere le modalità di utilizzo

Trovare l'indirizzo [IP](./../Tecnologie/protocolli#ip) (o crearne/richiederne uno nuovo nel caso non sia impostato) e le configurazioni della [scheda di rete](./../Tecnologie/Macchina#NIC) della macchina su cui si opera
```Terminal
ipconfig
```
	OPZIONI:
	/all - Stapa una lista completa
	/relase - Rilascia gli attuali settaggli DHCP
	/renew - Rilascia le impostaioni attuali ed effettua una nuova 	chiamata DHCP per crearne di nuove
	/displaydns - Mostra tutti i dati DNS nella cache

Verifica il throughput tra client e server (scaricabile)
```Terminal
iperf3 <url>
```

Crea una nuova cartella
```Terminal
mkdir <percorso/nome cartella>
```

Per effettuare la manutenzione della rete
```Terminal
net
```
	OPZIONI:
	accounts # imposta password e requisiti per il logon degli utenti
	session # ritorna una lista o disconnette le sessioni tra un computer e gli altri computer della rete
	share # crea, rimuove o gestisce risorse condivise
	start # avvia un servizio di rete o elenca i servizi di rete attivi
	stop # termina un servizio di rete
	use # si connette, disconnette e visualizza informazioni relative alle risorse di rete
	view # visualizza la lista dei computer e dei dispositivi di rete connessi alla rete

Controlla e mostra i [socket](./../Tecnologie/Macchina#Socket) aperti per le comunicazioni in [TCP](./../Tecnologie/Protocolli#TCP)
```Terminal
netstat
```
	OPZIONI
	-n # Mostra gli indirizzi IP e il numero della porta in forma numerica
	-abno # solo per admin, mostra le connessioni aperte e i relativi processi che le stanno utilizzando

Aprire un [socket](./../TEcnologia/Macchina#Socket) per l'invio di richieste [DNS](./../Tecnologia/Protocolli#DNS) nel server locale. Una volta lanciato il comando si riceveranno informazioni riguardo il server locale, poi sarà possibile effettuare altre ricerche.
```Terminal
nslookup
```
	N.B. Dopo il comando sarà possibile cercare un sito web tramite indirizzo URL.
	Il comando exit permetterà di uscire dalla funzione
	OUTPUT: (alla ricerca di www.cisco.com)
		Server:  UnKnown
		Address:  10.10.10.1
		Non-authoritative answer:
		Name:    e2867.dsca.akamaiedge.net
		Addresses:  2600:1404:a:395::b33
		          2600:1404:a:38e::b33
		          172.230.155.162
		Aliases:  www.cisco.com
		          www.cisco.com.akadns.net
		          wwwds.cisco.com.edgekey.net
		          wwwds.cisco.com.edgekey.net.globalredir.akadns.net

Verificare la velocità della connessione con un altra macchina
```Terminal
ping <indirizzo_ip>
```

Rinominare un file
```Terminal
ren <file> <nuovo nome>
```

Verificare le #porte aperte su un indirizzo #IP 
```Terminal
telnet <indirizzo_ip>
```

Ricevere informazioni relative al percorso effettuato dal pacchetto per raggiungere destinazione
```Terminal
tracert
```
# Shell
La shell permette di eseguire i file in formato .ps1 richiamandoli per nome.
## Lista dei comandi

Eseguire un azione e ritornare il risultato al prossimo comando da eseguire
```Shell
cmdlets
```

Richiedere informazioni relative ad un determinato comando
```Shell
get-help <comando>
```
	OPZIONI:
	-examples # mostra un aiuto base pe ril comando con esempi
	-detailed # mostra un aiuto dettagliato per il comando con esempi
	-full mostra tutte le informazioni relative al comando con esempi approfonditi

# Hyper-V
#hypervisor default di Windows. Serve a gestire la [[Virtualizzazione]].
# Server
## Server manager

## System manager

# Scheda di rete
## Accesso
Avviene tramite **Pannello di Controllo**, nella categoria **Rete e Internet**. Per visualizzarne lo stato attuale, basta cliccare sulla voce **Visualizza attività e stato della rete**.

Per vedere le proprietà della connessione wireless, ad esempio, si deve andare su ```Pannello di Controlle/Reti internet/Connessione di rete```,
fare click col tasto destro del mouse su Wireless Network Connection e selezionare Proprietà, da dove sarà possibile, ad esempio, visualizzare l'[IP](./../Tecnologie/Protocolli#IP) del dispositivo e scegliere se assegnarlo in maniera statica o tramite [DHCP](./../Tecnologie/Protocolli#DHCP)

# Versioni
Dal 1993 Windows ha utilizzato [Windows NT](#NT) per gestire il Sistema Operativo, e finora ha prodotto 10 OS, ognuno dei quali con molteplici versioni disponibili:

| Sistema Operativo        | Versioni                                                                                      |
| ------------------------ | --------------------------------------------------------------------------------------------- |
| Windows 7                | Starter, Home Basic, Home Premium, Professional, Enterprise, Ultimate                         |
| Windows Server 2008 R2   | Foundation, Standard, Enterprise, Datacenter, Web Server ,HPC Server, Itanium-Based Systems   |
| Windows Home Server 2011 | Nessuna                                                                                       |
| Windows 8                | Windows 8, Pro, Enterprise, RT                                                                |
| Windows Server 2012      | Foundation, Essentials, Standard, Datacenter                                                  |
| Windows 8.1              | Windows 8.1, Pro, Enterprise, RT                                                              |
| Windows Server 2012 R2   | Foundation, Essentials, Standard, Datacenter                                                  |
| Windows 10               | Home, Pro, Pro Education, Enterprise, Education, IoT, Core, Mobile, Mobile Enterprise         |
| Windows Server 2016      | Essentials, Standard, Datacenter, Multuipoint Premium Server, Storage Server, Hyper-V Server  |
| Windows 11               | Home, Pro, Pro Education, Education, Enterprise, Enterprise Multi-Session, IoT Enterprise, SE |

Le versioni sono organizzate nel seguente modo:
- Home rappresenta la versione per utenti standard
- Pro è la versione con maggiori funzionalità (ad esempio **bitlocker**)
- SE è la versione leggera, per dispositivi di fascia economica

# GUI
L'Interfaccia Grafica dell'Utente è il mezzo di comunicazione più utilizzato dagli utenti per comunicare con il Sistema Operativo di un dipositivo, in quanto permette di avere un veloce riscontro grafico delle varie operazioni che si vogliono compiere (a differenza della CLI, o Interfaccia a Linea di Comando, dove l'output consiste in un testo).

Gli elementi principali della GUI di Windows sono:
- Desktop
- Esplora risorse (File explorer)
- Funzionalità accessorie

## Desktop
La GUI (Interfaccia Grafica dell'Utente) ha mantenuto nel tempo una struttura composta da:
- Barra delle applicazioni (Task bar), dove è presente:
	- Tasto Start
	- Icone di lancio rapido delle applicazioni (Quick launch)
	- Area delle notifiche
- Desktop: ovvero un'area nella quale è possibile aggiungere icone di avvio delle applicazioni.
## Esplora risorse


# Architettura
## File system
Per gestire i file, Windows utilizza un file system di tipo [NTFS](../tecnologie/macchina#ntfs).

## Registro
Consiste in un database gerarchico nel quale vengono immagazzinate tutte le informazioni relative:
- hardware
- applicazioni
- utenti
- impostazioni di sistema

Il registro si suddivide in 5 alveari (non ampliabili di numero), modificabili avendo permessi di amministratore, tramite il tool [regedit.exe](#regedit.exe). Ogni voce contiene un valore che può essere:
- Una sottochiave
- booleano: tipo REG-BINARY
- stringa: tipo REG-SZ
- numero: tipo REG-DWORD

### HKEY_CURRENT_USER
Contiene informazioni relative i programmi da avviare al login dell'utente

### HKEY_USERS
Contiene informazioni relative tutti gli utenti registrati nella macchina.

### HKEY_CLASSES_ROOT
Contiene informazioni relative il Collegamento e Incorporamento degli Oggetti (Object linking and embedding, OLE) Gli OLE permettono all'utente di incorporare gli oggetti da altre applicazioni (come fogli di calcolo) all'interno di un singolo documento.
### HKEY_LOCAL_MACHINE
Contiene informazioni riguardanti il sistema, tra le quali l'elenco dei software da avviare all'avvio (boot) della macchina.

### HKEY_CURRENT_CONFIG
Contiene informazioni relative il profilo degli hardware installati nella macchina.


## Utenti
Windows prevede 2 utenti di default (con la possibilità di aggiungerne altri in caso di necessità):
- Admin
- Utente con cui si effettua il primo accesso (obbligatorio)

Il primo possiede i permessi più alti di creazione, visualizzazione e modifica di directory e file, quindi rappresenta anche uno dei nodi critici per la messa in sicurezza del dispositivo (se non dell'intera rete, in base al dispositivo in questione).

I permessi per ogni utente sono modificabili tramite il tool [lusrmgr.msc](#lusrmng.msc)

### Password policy
Gli amministratori devono:
- cambiare password ogni 90 giorni 
- utilizzare la nuova password almeno una volta
- La nuova password non può essere uguale alle ultime 24 password utilizzate 
- la password deve contenere almeno 3 tra:
	- un carattere minuscolo
	- un carattere minuscolo
	- un numero
	- un carattere speciale
Le importazioni possono essere modificate.

## Condivisione
Le cartelle condivise sono indicate con il simbolo **$**  al termine del loro nome (accessibili solo dall'amministratore) per permetterne l'utilizzo anche da remoto.
Il metodo più facile di connessione da remoto è tramite UNC (percorso del file). Un altro modo di accesso è tramite il controllo del pc che ospita i file tramite [RDP](#RDP)

# Operazioni
## Boot
![[Pasted image 20241104150718.png]]

### Firmware
Windows utilizza due tipologie di [firmware](https://it.wikipedia.org/wiki/Firmware) (software registrati direttamente sull'hardware):
- BIOS
- UEFI

#### BIOS
Il Sistema Base di Input-Output (BIOS) è un firmware è la versione più vecchia (essendo difficile da aggiornare, alcune delle nuove funzionalità richieste non sono incluse).
1. Si attiva durante l'avvio della macchina, quando i componenti hardware entrano in fase POST (Power On Self-Test, ovvero Avvio in Auto-Test) e trovano la directory del Registro Master del Boot (MBR), che contiene al suo interno un programma per localizzare e caricare il sistema operativo
2. Localizza una versione valida di Windows
3. Esegue il file **bootmgr.exe**, che si occupa di:
	- Leggere il Boot Configuration Database (o BCD, che contiene ulteriori informazioni necessarie per avviare il computer)
	- Cambiare la modalità del sistema da reale a protetta
4. Se il BDC indica che si sta uscendo dalla modalità di ibernazione, esegue il file **winresume.exe**
5. Se il computer è in modalità di ibernazione, esegue il file **hyberfil.sys**, che contiene dati sullo stato del computer prima dell'ingresso in stato di ibernazione
6. Se il computer non era in modalità di ibernazione, esegue il file **winload.exe**, che
	- Crea un record della configurazione hardware nel registro di configurazione
	- Verifica che tutti i driver abbiano firma digitale tramite il KMCS (Codice di Firma della Modalità Kernel) per assicurarsi che siano già stati caricati prima dell'avvio del sistema
	- Avvia il file **ntokrnl.exe**, che avvia il kernel di Windows ed imposta **HAL** (Astrazione del Livello Hardware)
7. Il Sottosistema di Gestione della Sessione (SMSS) legge il registro per:
	- Creare l'ambiente dell'utente
	- Avviare il servizio **Winlogon** e preparare i desktop di ogni utente che effettua il login

#### UEFI
L'Interfaccia Firmware Unificata Estendibile (UEFI) è la diretta evoluzione del BIOS. 
1.  Si attiva quando vengono caricati i file di programma efi (salvato su file con estensione **.efi**, situati all'interno della Partizione di Sistema EFI)
2. Esegue gli stessi passaggi del BIOS

Il posizionamento dei file di boot all'interno del firmware aumenta la sicurezza del processo di avvio (boot) in quanto permette alla macchina di entrare in modalità protetta sin dalla fase di avvio. 


## Startup
L'avvio automatico di applicazioni e servizi è gestito da due elementi del registro in particolare:
- [HKEY_LOCAL_MACHINE](#HKEY_LOCAL_MACHINE) 
- [HKEY_CURRENT_USER](#hkey_current_user)

Altri elementi di particolare interesse sono:
- Run
- RunOnce
- RunServices
- RunServicesOnce
- Userinit

Questi dati possono essere sia inseriti manualmente nel registro, che tramite il tool [msconfig.exe](#msconfig.exe) (scelta più sicura), che serve per cambiare le opzioni di avvio del computer.


## Spegnimento
Ci sono 3 modalità di spegnimento:
- Spegnimento
- Riavvio (spegne e riaccende il computer)
- Ibernazione (salva lo stato attuale dell'ambiente all'interno di un file)

# Funzionalità  accessorie
## Tasto destro del mouse
Cliccando con il tasto destro del mouse su un elemento da la possibilità di visualizzare una lista di opzioni per interagire con l'elemento stesso, contestualizzati in base al tipo e/o formato dell'elemento con cui si interagisce.

# Software
## Introduzione
I software elencati sono quelli offerti da Windows stessa e (spesso) preinstallati nella macchina. E' utile ricordarsi che, essendo il Sistema Operativo Windows non vincolato a degli specifici componenti hardware (al contrario di Mac OS), è utile astrarre il livello Hardware per rendere possibile il funzionamento delle Applicazioni a livello generico.

![[Pasted image 20241104131652.png]]
Questa astrazione è resa possibile grazie ad un software di Astrazione del Livello Hardware (HAL), che mette in comunicazione hardware e Kernel.

I software possono essere eseguiti nella **modalità utente** o nella **modalità kernel** in base alle loro caratteristiche (di solito quest'ultima è riservata ai software la cui origine è certa, ad esempio il sistema operativo, in quanto possono operare direttamente sui componenti hardware della machina e modificare tutti i file del kernel). Ad esempio:
- Il Sistema Operativo viene eseguito in modalità kernel
- La maggior parte dei software installati viene eseguita in modalità utente

Tutte le applicazioni sono composte da uno o più **Processi dedicati**, ognuno dei quali composti da almeno un **thread** (filo), ovvero una parte di processo che può essere eseguita. Una volta avviato un thread, il computer effettua i calcoli necessari.
Per configurare un processo, basta trovarlo all'interno del [task manager](<#task manager>).

Il numero di thread eseguibili contemporaneamente **dipende dal numero di processori** del computer stesso.

Un processo può avere fino a:
- 4 GB di [indirizzi virtuali](<macchina#indirizzi virtuali>) nel caso di architettura a [32-bit]
- 8 TB nel caso di architettura a [64-bit]
Nel caso un processo abbia bisogno di avere accesso alle risorse del kernel, ha bisogno di utilizzare un **gestore dei processi**, che provvede a fornire l'accesso alla risorsa in maniera indiretta. Un software utile per verificare l'utilizzo della RAM è RAMMap
## Defender
E' l'[anti-malware](../cybersecurity#antimalware) di default dei sistemi operativi Windows, che fornisce una serie di tool per proteggere il computer da minacce esterne.



## Firewall
## RDC
Connessione Desktop da Remoto è un software di Windows che permette la comunicazione tra due dispositivi tramite protocollo RDP (Protocollo per il Desktop da Remoto). Per prendere il controllo di un computer è necessario inserire il nome del computer sul quale si vuole effettuare l'accesso e le credenziali di accesso.

**N.B.** Utilizzare sempre delle politiche di Zero Trust nel caso si attivi RDC nel computer.

## Security

# Tool

## cmd.exe
Permette di utilizzare il [terminale](#terminale) di Windows.

## msconfig.exe
Tool utilizzato  per cambiare le opzioni di avvio del computer. Si compone di 5 opzioni di configurazione

### Generale
Permette di scegliere tra 3 possibilità di startup:
- Normale: carica tutti i driver e servizi
- Diagnostica: carica solo i driver e servizi basilari
- Selettivo: Permette di scegliere quali driver e servizi avviare

### Boot
Permette di scegliere quale sistema operativo (installato) utilizzare durante l'avvio. Sono presenti anche le opzioni di Safe boot , che sono utilizzate perlopiù in casi di troubleshooting.

### Servizi
Contiene una lista dei servizi, con la possibilità di selezionare e/o deselezionare quali rendere selezionabili nella [sezione Startup](#msconfig.exe#startup) per iniziare uno startup.

### Startup
Collega alla [sezione Startup del Task Manager](<#task manager#startup>) per scegliere quali servizi abilitare i disabilitare all'inizio dello startup.

### Tools
Permette di avviare la maggior parte dei tool di windows.


## regedit.exe
Tool che permette la modifica dei [registri di sistema](#registro) tramite l'utilizzo di una GUI composta da:
- menu laterale a sinistra in cui selezionare il registro che si vuole analizzare
- schermata con l'elenco dei dati contenuti nel registro scelto

## gpedit.msc
Il Group Policy Editor è un tool che permette di creare e modificare le **blacklist** e le **whitelist** del sistema.

## lusrmng.msc
Permette di visualizzare e gestire tutti gli utenti e i gruppi di utenti collegati alla macchina in uso. 
Un altro metodo di assegnazione dei permessi è quello dei **Domini**, ovvero tipi di reti nelle quali tutti gli utenti, gruppi, periferiche e impostazioni di sicurezza, vengono salvati all'interno di un database, memorizzato all'interno di un computer, denominato Controllore del Domino (DC). In tal caso, ogni utente dovrà autenticarsi presso il DC per poter aver accesso alla rete.

### Gruppi
Gli utenti possono essere raggruppati in base ai permessi di lettura/modifica dei file necessari per l'uso del sistema operativo che hanno (ogni utente può appartenere a più gruppi e ogni gruppo può ospitare più utenti).
Nel caso di permessi sovrapposti, alcune tipologie di permessi, come il **Nega in maniera esplicita** hanno priorità maggiore rispetto agli altri.


## Pannello di Controllo
### WMI
La Strumentazione di Gestione di Windows (Windows Management Instrumentation, o WMI), è uno strumento accessibile dal Pannello di Controllo
```path
Pannello di controllo
|- Strumenti amminstrativi
	|-Gestione del Computer
		|-Servizi e applicazioni
			|-Icona Controlli WMI
				|-Proprietà
```

Un potenziale [attacco](../cybersecurity#attacco) ai sistemi Windows avviene tramite connessione a WMI per modificare registri, connettersi da remoto e scrivere comandi, in quanto spesso il traffico generato da WMI (anche da remoto) è considerato affidabile e non lascia traccia nei log di sistema. Per questo motivo è sempre una buona pratica limitare gli acessi al WMI
#### Generali
Informazioni generali sul computer locale e sulle WMI.

#### Backup/ripristino
Permette di effettuare il backup manuale delle metriche raccolte da WMI

#### Sicurezza
Gestisce la configurazione degli accessi alle varie metriche WMI

#### Avanzate
Importazioni per configurare il namespace di default per WMI

## Reti e centro di condivisione
Il pannello inziale mostra le reti attive, lo stato di connessione (se c'è rete o meno) e il tipo di rete (pubblica o privata).

## Task manager
Permette di visualizzare la lista delle applicazioni e processi attivi in background, fornendo varie informazioni dettagliate.

### Processi
Mostra la lista delle applicazioni e processi attivi in background e i valori di utilizzo di:
- CPU
- Memoria (RAM)
- Spazio di archiviazione
- Banda di rete

### Performance
Da una vista delle statistiche riguardanti le performance e una vista sull'uso di:
- CPU
- Memoria
- Spazio di archiviazione
- Performance della rete

Il click con il tasto destro del mouse negli elementi nel pannello a sinistra permette la visualizzazione di ulteriori dettagli delle statistiche

### App history
- Mostra l'uso delle risorse delle varie app nel tempo e fornisce valori statistici a riguardo
Il click con tasto destro permette di visualizzare ulteriori dettagli sullo storico dell'utilizzo

### Startup
- Mostra tutte le applicazioni e servizi utilizzati dall'avvio del computer fino al suo spegnimento
- Permette di disabilitare l'avvio automatico delle app all'avvio del computer

### Users accounts
- Mostra tutti gli utenti collegati al computer
- Mostra tutte le risorse utilizzate per utente
- Rende possibile disconnettere un utente dal computer (solo l'admin può effettuare questa azione)

### Dettagli
Simile alla sezione Processi, fornisce inoltre:
- informazioni aggiuntive riguardo le opzioni di gestione dei processi, come il settaggio della priorità dell'uso di CPU dell'attività selezionata
- Possibilità di impostare l'affinità della CPU per determinare quale core debba essere utilizzato per il processo
- Mostra tutti i processi utilizzati da un determinato processo
- Aiuta a capire se un processo è terminato, o in attesa

### Servizi
- Mostra tutti i servizi caricati
- Mostra gli ID dei processi (PID) e il loro stato
- Il bottone in fondo alla schermata permette di aprire la console dei servizi, che fornisce ulteriori dettagli e servizi di gestione dei servizi.

## Visualizzatore di eventi
Permette di visualizzare i log dello storico delle applicazioni e degli eventi di sicurezza e di sistema.

# Versioni

## Server
Basato su [NT](#NT), è la versione di Windows per Server. Offre servizi sulle seguenti tematiche:
- Servizi di rete (DHCP, DNS, Servizi di terminale, Controllo della rete, Virtualizzazione della rete)
- Servizi di file (SMB, NFS, DFS)
- Servizi web (FTP, HTTP, HTTPS)
- Gestione (Gruppi di policy, servizi di controllo delle Directory attive)


