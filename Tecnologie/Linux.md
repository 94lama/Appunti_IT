# Comandi
Concatenare comandi
```Linux
<comando_1> & <comando_2>
```
Eseguire un comando nel caso quello precedente non venga eseguito correttamente 
```Linux
<comando_1> || <comando_2> 
```
Effettuare un comando come #superuser (SUperuser DO)
```Shell
sudo <comando>
```
Rimuovere uno o più elementi
```Linux
rm <nome_file>
```
Rimuovere uno o più elementi con forzatura
```Linux 
rm -rf <nome_file>
```
Installare npm
```Bash
npm install
```
Eseguire un file con [[Node.js]]
```Bash
node <nome file>.js 
```
Aprire una #shell interattiva in [[Php]]
```Shell
php -a
```
Verificare l'utente con cui si sta operando
```Shell
whoami
```
Rimuovere un account
```Shell
sudo gpasswd -d <nome_utente> <nome_ambiente>
```
Verificare se ci sono porte aperte verso l'esterno in una macchina #port-scanning
```bash
nmap <nome_macchina>
```
Accedere ad una rete come cliente
```shell
<nome_macchina>-cli -h localhost
```
Filtro un comando in base ad una determinata stringa
```shell
<comando> | grep <stringa>
```
---boh
```shell
systemctl
```
Vedere l'albero dei processi
```shell
ps aux
```
## Opzioni
```Bash
-d #detach
--help #lista dei comandi disponibili
-it #interattivo
-v #version
```
# UNIX

```unix
top # mostra i processi attivi nella macchina
htop # come top, ma con una barra orizzontale per l'utilizzo della CPU
```
```unix

```
# Kali linux
E' una versione di #linux molto utilizzata per #penetration-test e #forensic
```kali
DEFAULT SETTINGS
user: kali
password: kali
```
```kali
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