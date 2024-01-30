# Comandi
```Linux
& # esegue entrambi i comandi
```
```Linux
||  # Se il primo comando non viene eseguito, esegue il secondo comando
```
```Linux
rm # Rimuove uno o più elementi
```
```Linux 
rm -rf  # Come sopra, ma
```
```Bash
npm install #installa #npm
```
```Bash
node <nome file>.js # esegue il file 
```
```Shell
php -a # apre una #shell interattiva in php
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