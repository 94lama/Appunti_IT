[Wireguard](https://www.wireguard.com/) è un software Open Source per la creazione di reti VPN tra dispositivi.

# Installazione
Per installare Wireguard su Linux (per altri sistemi operativi vedi [qua](https://www.wireguard.com/install/)), scrivi su shell
```sh
apt install wireguard
```

# Interfaccia
Per funzionare su un dispositivo, Wireguard opera su un interfaccia dedicata. E' quindi necessario impostare prima di tutto l'interfaccia:
```sh
ip link add dev wg0 type wireguard &&    #1
ip address add dev wg0 192.168.2.1/24    #2
wg setconf wg0 myconfig.conf
```
	DESCRIZIONE:
	1. Creazione dell'interfaccia
	2. Assegnazione di un range di IP alla rete
	3. Applico le configurazioni dedicate (impostate nel file myconfig.conf)

## Configurazione
La configurazione dell'interfaccia avviene tramite shell o tramite file di configurazione (di solito chiamato nei tutorial **myconfig.conf**).

### Shell
Nel caso si voglia configurare tramite shell, basterà scrivere
```sh
wg set wg0 \ #seleziona l'interfaccia da configurarer
listen-port 51820 \ # indica la porta da utilizzare per l'avvio della connessione
private-key /path/to/private-key \ 
peer ABCDEF... \ #indica la public key del peer
allowed-ips 192.168.88.0/24 \ #lista degli IP utilizzabili dal peer
endpoint 209.202.254.14:8172 #indirizzo ip pubblico della LAN utilizzata
```

### File
Il file deve avere estensione .conf (il nome deve essere lo stesso utilizzato nel **setconf** della [creazione dell'interfaccia](#Interfaccia)) e seguire la seguente struttura:

```myconf.conf
[Interface]
PrivateKey = <chiave privata>
Address = <indirizzo IP da utilizzare>
MTU = <opzionale>
ListenPort = <porta da utilizzare per la ricezione di richieste>
PostUp = iptables -A FORWARD -i <interfaccia> -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
PostDown = iptables -D FORWARD -i <interfaccia> -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE

# packet forwarding: rimuovere "#" nel caso si voglia utilizzare il port forwarding
#PreUp = sysctl -w net.ipv4.ip_forward=1
# port forwarding
#PreUp = iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 2000 -j DNAT --to-#destination 10.0.0.1:8080
#PostDown = iptables -t nat -D PREROUTING -i eth0 -p tcp --dport 2000 -j DNAT --to-#destination 10.0.0.1:8080

[Peer]
PublicKey = <chiave pubblica del peer>
PreSharedKey = <chiave precondivisa (opzionale)
AllowedIPs = <lista degli IP ammessi, separati da una virgola>
```
Link utili:
- [debian](https://manpages.debian.org/bookworm/wireguard-tools/wg-quick.8.en.html#CONFIGURATION)

### Avvio
Per avviare il servizio digitare:
```sh
sudo systemctl start wg-quick@wg0
```
	NOTE: wg-quick utilizza il file di configurazione myconf.conf

Oppure:
```sh
wg-quick up path/to/myconf.conf
```

### Chiusura
Per terminare il servizio basta digitare
```sh
wg-quick down myconf
```

# Firewall
Per permettere il corretto funzionamento di Wireguard, è necessario inserire delle regole di permesso di accesso nelle impostazioni del firewall utilizzato nel dispositivo. I comandi elencati sono relativi al Firewall [UFW](./UFW).

Per agevolare la lettura dei dati, si considera:
- Porta di accettazione della richiesta di connessione: **5000**
- Interfaccia di connessione: **lan0**
- Interfaccia della VPN: **wg0**
- IP del server: **10.0.0.0**
- IP del peer: **10.0.0.1**

### Handshake
L'handshake permette la connessione tra peer e server della VPN
```rules
To                         Action      From
--                         ------      ----
<IP on wlan0> 50000/udp    ALLOW IN    Anywhere
Anywhere                   ALLOW OUT   <IP on wlan0>/udp on lan0 (out)
```

### Connessione con il peer
```rules
To                         Action      From
--                         ------      ----
10.0.0.1                   ALLOW OUT   10.0.0.0 on wg0
10.0.0.0 on wg0            ALLOW IN    10.0.0.1
```

### Accesso alla LAN
Aggiungere alle regole di ufw
```rules
Anywhere on wlan0          ALLOW FWD   10.0.0.1 on wg0        
10.0.0.1/tcp on wg0        ALLOW FWD   Anywhere on lan0 
```

Una volta permesso il routing con l'interfaccia lan0, di solito è necessario aggiungere la funzionalità di NAT, per evitare blocchi di connessione, dovuti all'identificazione del mittente come IP esterno alla rete.

Per fare ciò è sufficiente modificare il file after.rules (o before.rules, [in base al funzionamento desiderato](https://superuser.com/questions/704235/ufw-default-rules-where-are-they#:~:text=The%20rules%20are%20separated%20in,are%20then%20not%20even%20read.)), aggiungendo prima della sezione **filter**:
```before.rules
# NAT settings
*nat
:POSTROUTING ACCEPT [0:0]
-A POSTROUTING -s 10.0.0.1 -o lan0 -j MASQUERADE
```