Linux è un Os Open Source, disponibile in varie versioni (chiamate Distro).
Le varie versioni di Linux sono disponibili [qua]([https://distrowatch.com/](https://distrowatch.com/ "https://distrowatch.com/")).
# Permessi
- r = read (1)
- w = write (2)
- x = execute (4)

I permessi vengono mostrati tramite una stringa suddivisa in 3 parti, ciascuna di 3 caratteri
```permessi
- rwx-w-rw-
```
	- o d = specifica se si tratta di un file o di una directory
	1 terzetto = utente proprietario
	2 terzetto = gruppo
	3 terzetto = altri utenti

È possibile utilizzare i numeri per definire i permessi anche come combinazioni:
0. Nessun accesso
1. Esecuzione
2. Scrittura
3. Esecuzione e scrittura
4. Lettura
5. Lettura ed esecuzione
6. Lettura e scrittura
7. Lettura, scrittura ed esecuzione

### ACL
Le Access Control List (Liste di Controlli di Accesso) permettono di dare permessi extra ad utenti specifici per uno specifico file o directory.

# Comandi
Concatenare comandi
```Linux
<comando_1> && <comando_2>
```

Eseguire un comando nel caso quello precedente non venga eseguito correttamente 
```Linux
<comando_1> || <comando_2> 
```

Piping di due comandi
```sh
<comando 1> | <comando 2>
```
	Il piping serve a filtrare i risultati del primo comando attraverso il secondo
	ES. ls -l | grep file

Inserire un commento  
```Linux
# commento 
```

Accedere ad una rete come cliente
```shell
<nome_macchina>-cli -h localhost
```

Filtro un comando in base ad una determinata stringa
```shell
<comando> | grep <stringa>
```

Modificare i software installati all’interno della macchina
```Sh
sudo apt-get
```
	OPZIONI: 
	install <nome app> # installa il software
	upgrade # aggiorna tutti i software installati
	dist-upgrade # aggiorna la distro

Utilizzare il [linguaggio AWK](https://www.geeksforgeeks.org/awk-command-unixlinux-examples/) per generare dei #report
```sh
awk
```

Leggere il contenuto di un file
```sh
cat <nome_file>
```

Ripulire lo schermo
```sh
clear
```

Modifica il gruppo proprietario dell'elemento
```sh
chgrp <nome_gruppo> <nome_file>
	```
	OPZIONI:
	-R # modifica tutti i file selezionati in maniera ricorsiva

Modifica i permessi granulari di un file. #SUID, #SGID
```sh
chmod <permessi_utente><permessi_gruppo><permessi_utente_generico> <nome_file>
```
	chmod u-x, o-r <nome_file>
	u: proprietario
	g: gruppo
	o: altri utenti (other)
	aggiungere un permesso: +
	rimuovere un permesso: -
	r: read - 4
	w: write - 2
	x: execute - 1
	s: ovvero Set owner (user o group). Permette di far eseguire il file ad un utente (indipendentemente dai permessi assegnati) come fosse root
	t: (Sticky bit) Imposta gli utenti proprietari come unici utenti con permessi di cancellazione file (a parte il super user)
	- Nel caso si vogliano utilizzare i numeri, nel caso di combinazione di permessi, si possono sommare i numeri (6 per lettura e scrittura, 7 per tutti e 3)
	- Se le cartelle non hanno almeno permesso 4, verrà negato l'accesso

Modifica il proprietario di un file
```sh
chown <nome_utente>:<nome_gruppo> <nome_file>
```

Copia un dato da un input ad un output 
```Shell
dd
````


Controllare lo spazio disponibile nelle varie partizioni del volume
```shell
df -hT
```

Fare robe
```sh
eval "<comando>"
```
	OPZIONI:
	- Avviare un ssh-agent: eval "$(ssh-agent)"

Preservare una porzione di spazio della #memoria ad un file. [Link](https://man7.org/linux/man-pages/man1/fallocate.1.html)
```sh
fallocate <directory_file>
```
	ES. sudo fallocate -l 4G /swapfile
	OPZIONI:
	-d # dig holes, ovvero frammenta lo spazio preservato
	-l <dimensione> # es. KiB, MiB, GiB, PiB
	-n <nome_file>

Controllare lo spazio disponibile nelle varie partizioni
```shell
find <directory> <nome file>
```
	ESEMPIO:
	find / -perm -4000
	-perm #cerca i file che hanno i permessi specificati
	permessi: 1=read, 2=write, 3=execute, 4=SUID

Visualizzare le #ACL di un file
```sh
getfacl <nome_file>
```

Rimuovere un account
```Shell
gpasswd -d <nome_utente> <nome_ambiente>
```

Creo un nuovo gruppo
```sh
groupadd <nome_gruppo>
```
	ATTENZIONE:
	Richiede l'accesso come root

Elimino un gruppo
```sh
groupdel <nome_gruppo>
```
	Nel caso si voglia eliminare un gruppo che sia primario per un utente, il sistema lancerà un'avviso 
	OPZIONI:
	-f # forza la rimozione
	-r # 
Visualizzare i gruppi a cui appartiene un utente
```shell
groups <utente>
```
	Se non si inserisce l'utente, ritornerà tutti i gruppi del sistema
	OPZIONI:

Mostrare i parametri delle interfacce di connessione (tipo IPv4, Ethernet)
```sh
ifconfig
```

Mostrare i parametri delle interfacce di connessione wireless
```sh
iwconfig 
```

Verificare le informazioni di un utente
```sh
id <user>
```

Visualizzare le regole di accesso alla macchina ( #firewall)
```shell
iptables -L -v -n
```
	iptables -P INPUT DROP # cancella tutte le configurazioni  

Modificare il comportamento di un processo
```Sh
kill
```

Creare un link
```Sh
ln <nome file>
```
	OPZIONI:
	-s # crea un link simbolico

Visualizzare tutti i file e cartelle all'interno della directory corrente
```shell
ls
```
	-a # mostra anche i file nascosti
	-all # mostra tutte le directory e i file contenuti, in una vista tabellare che comprende permessi, 
	-l # mostra i dati in tabella
	tabella: directory_1 directory_2 directory_3|permessi|utente|gruppo utente|dimensione|data di creazione|nome del file 
	categorie utenti: proprietario, gruppo del proprietario, altri
	directory può essere "d" se directory o "-"
	permessi: r=read, w=write, x=execute, -=nessun perm

Controllare lo spazio utilizzato dalle varie partizioni
```shell
lsblk
```

Aprire il manuale dei #comandi del #terminale per verificare le modalità d'uso di un comando
```sh
man <comando>
```

Modificare il contenuto di un file
```sh
nano <nome_file>
```
	COMANDI:
	- Ctrl + O: salva il file
	- Ctrl + W: Apre il menu di ricerca
	- Ctrl + G: schermata di aiuto

Verifica la connessione ad un servizio tramite specifica porta
```Sh
ncat <indirizzo> <porta>
```
	N.B. È possibile utilizzare la forma abbreviata “nc”
	OPZIONI:
	-z | 
	-V |

Verificare se ci sono porte aperte verso l'esterno in una macchina #port-scanning
```bash
nmap <nome_macchina>
```

Installare i pacchetti contenuti nel file package.json tramite npm
```Bash
npm install
```

Cercare un Fully Qualified Domain Name nel server DNS di default (può essere anche la [cache](./Macchina#Cache) del dispositivo stesso) tramite [DNS](./Protocolli#DNS)
```sh
nslookup <sito web (opzionale)>
```
	N.B. Se non viene inserito nessun indirizzo, la shell entrerà in modelità lookup, dove potrai effettuare le ricerche inserendo il nome del sito desiderato (inserisci il comando exit per terminare il processo).

Eseguire un file con [[Node.js]]
```Bash
node <nome file>.js 
```

Aggiungere una password di un utente
```sh
passwd <user>
```

Aprire una #shell in [[Php]]
```Shell
php
```
	OPZIONI:
	-a # Apre la shell in maniera interattiva

Richiedere un messaggio di risposta da un altro dispositivo
```sh
ping <indirizzo_ip>
```
	N.B. I seguenti indirizzi IPv4 sono utilizzati spesso durante i processi di troubleshooting:
		  127.0.0.1 - Indirizzo di Loopback, che permette di verificare se l'interfaccia TCP/IP del dispositivo è configurata correttamente
		  
	N.B. I seguenti indirizzi IPv6 sono utilizzati spesso durante i processi di troubleshooting:
		  ::1 - Indirizzo di Loopback, che permette di verificare se l'interfaccia TCP/IP del dispositivo è configurata correttamente

Mostrare la lista dei processi in corso
```shell
ps aux
```
	ESEMPI:
	ps aux # mostra l’albero dei processi

Stampo il percorso della cartella in cui mi trovo
```shell
pwd
```

Apro un terminale [[Python 1]]
```shell
python
```
	Il file ha permessi -rwsr-xr-x

Riviste il sistema
```Sh
sudo reboot
```

Interagire con un database remoto
```shell
redis-sli -h <nome_server>
```

Rimuovere uno o più elementi
```sh
rm <nome_file>
```
	OPZIONI:
	-r # Rimuove una cartella non vuota
	-rf # Forza la rimozione

Impostare una #ACL di un file
```sh
setfacl u:<user>:<permessi> <file>
```
	OPZIONI:
	-m # modifica la #ACL del file
	-R # applica la regola in maniera ricorsiva
	-x # riomuove la #ACL impostata

Verificare la velocità di connessione ad internet
```sh
speedtest
```

Connettersi ad un'altra macchina da remoto tramite protocollo #ssh 
```sh
ssh <indirizzo_ip> -i <chiave>
```
	Per chiudere la connessione, prenere Ctrl+D
	Nel caso si voglia accedere come uno specifico utente:
	ssh <nome_utente>@<indirizzo_ip>
	OPZIONI:
	-p # porta

Aggiungere una chiave ssh all'agent
```ssh
ssh-add <percorso>
```

Impostare un ssh-agent
```sh
ssh-agent
```
	N.B. Nel caso il comando non vada a buon fine, lo sui può usare tramite eval

Per generare una #ssh-key 
```sh
ssh-keygen
```
	-t # Definire la tipologia di criptazione [dsa, ecdsa, ecdsa-k, ed25519, ed25519-sk, rsa]
	-C <nome utente>

Accedere come utente root (chiede la password)
```shell
su
```
	OPZIONI:
	-l # 

Effettuare un comando come #superuser (SUperuser DO). Effettuabile solo se l'utente fa parte dei **sudoers**
```Shell
sudo <comando>
```

Esegue le funzionalità #sysctl
```shell
sysctl
```
	-p # riavvia il SO

Mostrare la lista dei processi attivi in maniera dinamica 
```sh
top
```
	AZIONI:
	Q # interrompe il comando

Creare un nuovo utente (richiede permessi root)
```sh
useradd <nome_utente>
```
	L'utente viene registrato in 3 file: /etc/passwd, /etc/shadow e /etc/group
	OPZIONI:
	-c #
	-d # crea una home directory
	-e # inserisce una data di "scadenza" all'utente
	-f 
	-g <nome_gruppo> # aggiunge l'utente al gruppo come gruppo primario
	-G <nome_gruppo> # aggiunge l'utente al gruppo come gruppo secondario (accetta anche array)
	-m # sposta la directory corrente nella home del nuovo utente
	-p <password> # imposta la password. Sconsigliato perchè rende la password visibile nella lista dei processi
	-r # crea un account di sistema
	-s /sbin/nologin # non imposta una shell di accesso per l'utente

Eliminare un utente
```sh
userdel <nome_utente>
```
	ATTENZIONE:
	Nel caso si cancellino più utenti, è possibile che Debian cancelli anche le password di root
	OPZIONI:
	

Modificare le caratteristiche di un utente
```sh
usermod
```
	Di solito si usa con sudo
	OPZIONI:
	-aG <gruppo> <user> # Aggiunge l'user al gruppo
	

Modificare il contenuto di un file
```sh
vim <nome_file>
```

Verificare l'utente con cui si sta operando
```Shell
whoami
```

Comandi da inserire
```shell
chroot
getent
env
sh #shell
```

## Info utili
- Premendo Tab, il terminale completa automaticamente il comando (o il file). Nel caso ci siano più risultati possibili, ritorna sotto la linea di comando la lista delle possibilità
# Distro

## Kali

## Security Onion
Distro specializzata nell’analisi della sicurezza delle reti, molto utilizzata negli ambienti [SOC](../cybersecurity#soc) (Security Operation Center, o C’è tri Operativi di Sicurezza).

### Tools


# UNIX

```unix
top # mostra i processi attivi nella macchina
htop # come top, ma con una barra orizzontale per l'utilizzo della CPU
```
## [kali-linux](https://www.kali.org/get-kali/#kali-installer-images)
E' una versione di linux molto utilizzata per i [penetration test] e per l’attività forense. La distribuzione contiene oltre 600 tool (soprattutto da riga di comando), alcune delle quali utili per effettuare attacchi informatici. L'utente di base si chiama **kali** e i comandi sono in base #unix (utilizzato, ad esempio, anche in #git-bash) .
```sh
DEFAULT SETTINGS
user: kali
password: kali
```
### Struttura del terminale
```bash
|- (<utente>@<macchina>) -[<localizzazione>]
|- $
```
	Nel caso ci si trovi nella cartella principale (di default /home/kali), la localizzazione sarà ~
	Nel caso ci si trovi nella cartella root, la localizzazione sarà /
### Struttura
```root
├ 0
├ bin #contiene file e applicazioni binari
├ boot
├ etc # contiene file di configurazione del sistema
|	├ sysctl.conf
|	├ host.allow # non presente di default
|	├ host.deny # non presente di default
|	├ ssh
|	|	└ sshd_config 
|	└  passwd
├ home #contiene tutti gli utenti locali
├ dev #contiene i file necessari per far funzionare i dispositivi
├ lib #contiene i file di sistema
└ media #contiene i supporti esterni
```
	- ssh_config gestisce i permessi per effettuare chiamate in SSH
#### etc
##### group
Contiene la lista dei gruppi
```group
<nome_gruppo>:x:a:b
```
	x = password del gruppo (se 'x' non c'è password)
	a = Group ID
	b = Utenti appartenenti al guppo
##### passwd
Il file contiene la lista di utenti registrati e i dati ad essi relativi. La password verrà inserita nel file solo nel caso l'utente venga creato non di default (es. root non avrà la password segnata nel file)
```passwd
root:0:0:
<nome_utente>:a:b:c:<nome>,,,:<home_directory>:<shell_directory>
```
	a = password (se localizzata in un altro file sarà x) # rivedere: permessi_root (0 si, 1 no)
	b = User ID
	c = Group ID 
	: #nuovo campo
	:: = campo vuoto
##### shadow
File contenente le password.
```shadow
<username>:<password_cifrata>:a:b:c:d:e:f
```
	a = Data dell'ultimo cambio password
	b = Numero minimo di giorni di attesa tra due cambi password
	c = Numero massimo di giorni tra due cambi password
	d = Giorni di preavviso per la scadenza della password
	e = Numero di giorni per la disabilitazione dell'account dopo la scadenza della password
	f = campo riservato
##### ssh/sshd_config
Gestire gli accessi al gruppo #root
```sshd_config
# PermitRootLogin = 0 # permettere l'accesso all'utente root

# MaxAuthhTries 6 # numero massimo di tentativi di accesso

# PermitRootLogin prohibit-password # gestire l'accesso all'utente root

# ClientAliveInterval 0 # intervallo di inattività di un utente loggato prima del logout automatico

# ClientAliveCountMax 3 # numero massimo di utenti collegati cotemporaneamente alla macchina

```
##### sysctl.conf
Il file ha tutti i parametri commentati. Nel caso si vogliano attivare alcuni comandi, basta rimuovere il \# ed impostare i parametri con il valore desiderato.
Connettersi alla rete pubblica dal dispositivo
```systctl.conf
# Uncomment the next line to enable packet forwarding for IPv4
# net.ipv4.ip_forward=1
```
	1 se si vuole utilizzare la macchina come firewall o come kernel
	0 se lo si vuole impostare come non attivo
Accettare messaggi con protocollo #IPCM, scoprendo le tabelle di routing della macchina
```systcl.conf
# Do not accept IPCM redirects (prevent MITM attacks)
# net.ipv4.conf.all.accept_redirects = 0
# net.ipv4.conf.default.accept_redirects = 0
```
source_route è un parametro che indica il percorso per raggiungere il dispositivo (può essere utilizzato per bypassare il #firewall)
```systctl.conf
# net.ipv4.conf.default.accept_source_route = 0
```
	0 - non accetta eventuali pacchetti che includono il parametro source_route
	1 - accetta pacchetti ch einclusono il parametro source_route

Permette di attivare i syncookies
```systctl.conf
# net.ipv4.tcp_syncookies = 1
```
Permette di indicare il numero di volte per le quali deve essere ripetuta la richiesta di risposta per l'handshake
```systctl.conf
# net.ipv4.tcp_sysnack_retries = 3
```
Permette di impostare i tasti per attivare le combinazioni [sysrq](https://linuxaria.com/howto/sysrq-linux-ubuntu?lang=it), ovvero comandi che permettono di effettuare delle operazioni predeterminate nel caso crashi il sistema 
```systctl.conf
# kernel.sysrq = 438
```
	kernel.sysrq = 0 => si disabilita la funzionalità
	kernel.sysrq = 1 => si abilitano tutte le funzionalità
	b - Riavvia il sistema
	o - Spegne il sistema
	s - Cerca di fare il sync di tutti i filesystem montati
	...
### Comandi extra
```sh
netstat -rn # fornisce #gateway
cd /usr/share/wordlists # cartella in cui è presente il file Rockyou.txt
cd ~ # Riporta nella cartella iniziale
gzip -d <nome file> # unzippa il file
tail <nome file> stampa le ultime righe del file
```

### WPScan
E' un tool nativo di #kali #linux per operare con siti #wordpress
```Kali
wpscan --url <url> # fornisce informazioni relative al sito, ad l'autore del sito
```
```Kali
wpscan --url <url> --password-attack xmlrpc -t 20 -U <nome utente> -P /usr/share/wordlists/rockyou.txt #effettua un #bruteforce sulla password dell'account selezionato
```
### Hydra
Software utilizzato per effettuare #brute-force su siti web.

## Hardening
### #DDos 
Ci sono dei software che permettono di inviare dei [Three-way-handshake](<Protocolli di comunicazione#Three-way-handshake) incompleti ad una macchina bersaglio. La macchina risponderà con il secondo passaggio del processo. Nel caso le richieste vengano effettuate in grande quantità, si effettua un attacco chiamato #syn-flow ed il risultato è il down del sistema e la conseguente interruzione del servizio.
#### Soluzione
Impostare il parametro net.ipv4.tcp_syncookies = 1 nel file [[#sysctl.conf]]
### #privilege-escalation
#### Accesso a file sensibili per leggere dati di accesso
Durante la creazione di server in Linux (così come tutti gli altri #OS), si deve porre particolare attenzione alla creazione e gestione degli utenti.
Particolarmente sensibile è il file **/etc/passwd**, poiché contiene, ad esempio, i dati di tutti gli utenti che hanno accesso alla macchina.
```sh
cat /etc/passwd |awk -F: '($3 = 0) {print $1}'
```
	Visualizzare i nomi di tutti gli utenti con permessi root
#### Tramite Python
Apro il terminale di Python
```sh
python
```
Importo e accedo ad un nuovo #OS 
```Python
import os
os.execl("/bin/bash", "bash", "-p")
```
Nel terminale sono nella shell. Nel terminale sono l'utente **root**
```sh
whoami
```
	Risultato: root
##### Soluzione
Il terminale Python ha il #SUID preimpostato. Quindi, lo devo quindi rimuovere.
```sh
chmod u-s /usr/bin/python3.11
```
	La versione di python installata può essere vista tramite python --version
In questo modo l'utente potrà accedere al terminale Python, ma con i permessi prestabiliti dall'amministratore.
### [Code scanning](Cybersecurity.md#SCA)

# File
## Link
Un link è un collegamento tra un file ed un altro. Può essere di due tipi:
- Hard link: i file sono collegati e le modifiche ad uno verranno effettuate anche sul secondo (cancellazione del file inclusa)
- Soft link: le modifiche non vengono propagate

Il percorso dei soft link viene segnalato dal comando `ls -l`, mentre gli hard link sono più difficili da localizzare.
Gli hard link inoltre possono essere creati solo per file localizzato sullo stesso File System (e non possono essere collegati direttamente ad una directory, perché il sistema stesso usa gli hard link per gestire le cartelle).

## etc/
### nginx/
#### nginx.conf
Configura Nginx, un web server leggero per Linux.

### ntp.conf
File di configurazione per il protocollo [NTP](../tecnologie/protocolli#ntp) (Network time protocol)

### snort.conf
File di configurazione per Snort, un [IDS] (Software di Identificazione delle Intrusioni)

## home/
Contiene i file e le impostazioni di ogni utente registrato nella macchina (ogni utente avr° una cartella personale).

## var/
### log/
Contiene i file di [log](../cybersecurity#log) 

#### messages
Contiene log di attività generiche, utilizzate prevalentemente per il salvataggio di messaggi informativi non critici di sistema (nelle distro Debian è chiamato **syslog**)

#### auth.log
Contiene i log degli accessi al dispositivo per distro Debian e Ubuntu, con tutte le informazioni relative all’accesso.

#### secure
Variante di [auth.log](#auth.log) utilizzata da RedHat e CentOS. Tiene traccia anche di eventi che coinvolgono l’uso di sudo, login tramite SSH, e altri errori provenienti da SSSD.

#### boot.log
Contiene informazioni relative al boot e messaggi di log creati durante la fase di startup del dispositivo.

#### dmesg
Contiene messaggi del ring buffer del kernel, contenenti informazioni riguardanti i dispositivi hardware e i relativi drivers. È un file molto importante data la natura di basso livello delle informazioni (gli eventi avvengono prima che altri file di log entrino in azione)

#### kern.log
Contiene log relativi al kernel

#### cron
File utilizzato per salvare i dati relativi le automazioni su Linux, come le loro pianificazioni, stati di esecuzione e messaggi di errore.

#### mysql.log
Memorizzato come mysqld.log nelle distro RedHat, CentOS e Fedora, contiene i log del database MySQL, con informazioni relative I debug, funzionalità, messaggi di successo, il processo mysqld, e il daemon (un processo che viene eseguito senza bisogno di interazione da parte dell’utente) mysqld_safe.

## sys/
Contiene i file di sistema

### Tipi di file di sistema
#### ext2
Era il sistema di default delle maggiori distro di Linux. Utile per dispositivi con memoria flash a causa dell’assenza di **journaling** (in quanto effettuare operazioni di scrittura riduce la vita della memoria), anche se lo supporta.

#### ext3
Evoluzione dell’ext2, aggiunge funzionalità di **journaling** per minimizzare il rischio di corruzione dei file in caso di arresto improvviso della macchina. La dimensione massima dei file ext3 è 32TB.

#### ext4
Evoluzione della ext3, implementa una serie di estensioni che ne migliorano le performance e aumentano la dimensione supportata dei file.

#### NFS
Il File di Sistema della Rete permette l’accesso ai file attraverso la rete. Dal punto di vista dell’utente non c’è differenza tra accedere ad informazioni ali terno di file memorizzato all’interno della macchina o all’esterno (purché siano dentro la stessa rete).

#### CDFS
Il File di Sistema per Dischi Compatti è stato creato appositamente per supportare l’utilizzo di dischi ottici

#### Swap File System
Lo Swap file system è utilizzato da Linux nel caso termini la RAM a disposizione. Permette di utilizzare una partizione momentanea per allocare i dati inutilizzati della RAM (essendo molto più lento della RAM, non sono da considerare come una soluzione definitiva)

#### HFS+
Linux include un module lo per la lettura e la scrittura su questo tipo di File System

#### APFS
File System sviluppato da Apple come diretta evoluzione dell’HFS+. Supporta funzionalità di cifratura ed è ottimizzato per memorie flash e dischi allo stato solido (SSD)

#### MBR
Il Registro Master di Avvio (Master Boot Record) è localizzato nella prima partizione del computer e contiene tutte le informazioni sull’organizzazione del File System. Una volta utilizzato, richiama una funzione di caricamento, che carica il sistema operativo.


# Software
L’estensione dei file di applicazioni su Linux dipende dalla distro:
- Arch Linux: pacman
- Debian: dpkg, apt
- Ubuntu: apt

Dove presente apt, il comando `apt-get` permette di scaricare app.

## X Window System
Interfaccia grafica basica per Sistemi operativi Linux. Da accoppiare ad altri software per la gestione dele finestre, come:
- KDE Windows manager
- Gnome Windows Manager (usata da Ubuntu)


## chrootkit
Software basato su Linux che permette di controllare la presenza di noti [rootkit](../cybersecurity#rootkit) all’interno della macchina. Utilizza comandi shell (prevalentemente strings, grep e ps)

## iptables
[Firewall](../cybersecurity#firewall) disponibile per Linux, che consente all'amministratore di sistema di configurare le regole di accesso, incorporandole nei moduli Netfilter del kernel di Linux.

## inetsim
Simulatore di ambienti (virtualizzatore), con opzioni di verifica per i protocolli:
- 

## nftables
Diretta evoluzione di [iptables](#iptables), che utilizza una semplice macchine virtuale nel kernel di Linux. Utilizza la macchina virtuale per analizzare i pacchetti di rete ed implementare regole decisionali di accettazione e inoltro dei pacchetti.

## TCP Wrappers
Tool di [controllo degli accessi](#acl) basato su regole e sistema di logging. Opera attraverso il filtraggio dei pacchetti basato sugli indirizzi IP e i servizi di rete.

## ufw
Firewall semplificato

## Red team
### John the ripper
[John the ripper]( https://www.kali.org/tools/john/) è un tool utilizzato per effettuare un brute force delle password di un computer.

# Annotazioni
- Le distribuzioni di Linux, di solito, vengono provviste nativamente di [[Python]]
