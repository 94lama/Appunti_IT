Le varie versioni di Linux sono disponibili [qua]([https://distrowatch.com/](https://distrowatch.com/ "https://distrowatch.com/")).
## Permessi
- r = read (1)
- w = write (2)
- x = execute (4)

I permessi vengono mostrati tramite una stringa suddivisa in 3 parti, ciascuna di 3 caratteri
```permessi
- rwx-w-rw-
```
	1 terzetto = utente proprietario
	2 terzetto = gruppo
	3 terzetto = altri utenti
### Access Control List
Le Access Control List #ACL permettono di dare permessi extra ad utenti specifici per uno specifico file o directory.
# Comandi
Concatenare comandi
```Linux
<comando_1> && <comando_2>
```
Eseguire un comando nel caso quello precedente non venga eseguito correttamente 
```Linux
<comando_1> || <comando_2> 
```
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
	t: (Stick bit) Imposta gli utenti proprietari come unici utenti con permessi di cancellazione file (a parte il super user)
	- Nel caso si vogliano utilizzare i numeri, nel caso di combinazione di permessi, si possono sommare i numeri (6 per lettura e scrittura, 7 per tutti e 3)
	- Se le cartelle non hanno almeno permesso 4, verrà negato l'accesso
Modifica il proprietario di un file
```sh
chown <nome_utente>:<nome_gruppo> <nome_file>
```
Controllare lo spazio disponibile nelle varie partizioni del volume
```shell
df -hT
```
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
find <directory>
```
	find / -perm -4000
	-perm #cerca i file che hanno i permessi specificati
	permessi: 1=read, 2=write, 3=execute, 4=SUID
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
	
Visualizzare le regole di accesso alla macchina ( #firewall)
```shell
iptables -L -v -n
```
	iptables -P INPUT DROP # cancella tutte le configurazioni  
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
Verificare se ci sono porte aperte verso l'esterno in una macchina #port-scanning
```bash
nmap <nome_macchina>
```
Installare npm
```Bash
npm install
```
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
Vedere l'albero dei processi
```shell
ps aux
```
Stampo il percorso della cartella in cui mi trovo
```shell
pwd
```
Apro un terminale [[Python 1]]
```shell
python
```
	Il file ha permessi -rwsr-xr-x
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
Impostare una #ACL 
```sh
setfacl u:<user>:<permessi> <file>
```
	OPZIONI:
	-m # mask, modifica la #ACL del file
	-R # applica la regola in maniera ricorsiva
	-x # riomuove la #ACL impostata
Connettersi ad un'altra macchina da remoto tramite protocollo #ssh 
```sh
ssh <indirizzo_ip> -i <chiave>
```
	Per chiudere la connessione, prenere Ctrl+D
	Nel caso si voglia accedere come uno specifico utente:
	ssh <nome_utente>@<indirizzo_ip>
	OPZIONI:
	-p # porta
Per generare una #ssh-key 
```sh
ssh-keygen
```
	-t # Definire la tipologia di criptazione [dsa, ecdsa, ecdsa-k, ed25519, ed25519-sk, rsa]
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
Creo un nuovo utente (richiede permessi root)
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
	
Per modificare le caratteristiche di un utente
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
## Opzioni
Le opzioni sono delle particolari ulteriori configurazioni che è possibile conferire al comando. si utilizzano dopo aver specificato il comando principale e sono precedute da un trattino es ```-a```. Possono variare a seconda del comando utilizzato.
Per verificare le #opzioni disponibili per uno specifico comando
```sh
<comando> --help
```

```Bash
-A # append
-aG #
-d # detach
-e # edit
-it # interattivo
-l # mostra una versione tabellare del risultato, includendo permessi, proprietario, gruppo del proprietario, ultima modifica e dimensione se utilizzato con ls
-L
-n
-p # protocollo di trasporto
-s # indirizzo ip
-v # version
--dport <numero> # porta di destinazione 
--help # lista dei comandi disponibili
```
	Permessi: 
## Info utili
- Premendo Tab, il terminale completa automaticamente il comando (o il file). Nel caso ci siano più risultati possibili, ritorna sotto la linea di comando la lista delle possibilità
# UNIX

```unix
top # mostra i processi attivi nella macchina
htop # come top, ma con una barra orizzontale per l'utilizzo della CPU
```
## [kali-linux](https://www.kali.org/get-kali/#kali-installer-images)
E' una versione di #linux molto utilizzata per #penetration-test e #forensic. La distribuzione contiene oltre 600 tool (soprattutto da riga di comando), alcune delle quali utili per effettuare attacchi informatici. L'utente di base si chiama **kali** e i comandi sono in base #unix (utilizzato, ad esempio, anche in #git-bash) .
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
|-0
|-bin #contiene file e applicazioni binari
|-boot
|-etc # contiene file di configurazione del sistema
|--sysctl.conf
|--host.allow # non presente di default
|--host.deny # non presente di default
|--ssh
|---sshd_config # gestisce i permessi per effettuare chiamate in #ssh
|--passwd
|-home #contiene tutti gli utenti locali
|-dev #contiene i file necessari per far funzionare i dispositivi
|-lib #contiene i file di sistema
|-media #contiene i supporti esterni
```
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
### [Code scanning](Cybersecurity#SCA)

# Annotazioni
- Le distribuzioni di Linux, di solito, vengono provviste nativamente di [[Python]]
