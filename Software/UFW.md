Uncomplicated FireWall è un firewall host-based che permette di impostare un firewall in meniera semplice su un dispositivo [Linux](../OS/Linux) basato su [iptables](../OS/Linux#iptables).

# Installazione
```sh
apt install ufw
```

# Comandi
I comandi più utilizzati per UFW sono i seguenti (da utilizzare con permessi root)

## Avvio
##### Attivazione
```sh
ufw enable
```

##### Disattivazione
```sh
ufw disable
```

##### Riavvio
```sh
ufw reload
```

## Log
##### Logging
```sh
ufw logging [livello]
```
	LIVELLI:
	- off
	- on # uguale a low
	- low
	- medium
	- high
	- full

I log sono memorizzati nel file ```/var/log/ufw.log``` nel [seguente formato](https://askubuntu.com/questions/143371/what-do-ufws-audit-log-entries-mean):
- **TOS**: Tipo di servizio,
- **DST**: IP di destinazione,
- **SRC**: IP del mittente
- **TTL**: [Time to live](../Tecnologie/Protocolli#ICMP), che indica il numero di reindirizzamenti effettuabili prima del drop del pacchetto
- **DF**:"don't fragment" bit, asking to packet to not be fragmented when sent
- **PROTO**: Protocollo utilizzato (prevalentemente TCP e UDP)
- **SPT**: Porta del mittente
- **DPT**: Porta di destinazione

## Permessi
### Routing
##### route
```sh
ufw route allow in on <interfaccia di ingresso> out on <interfaccia finale> [from <indirizzo di partenza>] [to <dispositivo destinatario>]
```


# Configurazione
Per la configurazione di UFW vengono utilizzati dei file di configurazione (in base all'attività sotto configurazione). I file vengono compilati utilizzando la sintassi di [iptables](https://man7.org/linux/man-pages/man8/iptables.8.html)

## before.rules
File di configurazione della prima fase della trasmissione di messaggi.

## Esempi
### Forwarding
Per abilitare l'inoltro di pacchetti tra interfacce diverse, è necessario:
1. modificare il valore ip_forward, che di default è commentato nel file **/etc/sysctl.conf**:
	```/etc/sysctl.conf
	net.ipv4.ip_forward=1
	```
2. Aggiungere la seguente sezione su [before.rules](<#befor.rules>) prima della sezione \*filters:
	```/etc/ufw/before.rules
	# NAT rule: Enable Masquerading 
	*nat 
	:POSTROUTING ACCEPT [0:0
	-A POSTROUTING -o eth0 -j MASQUERADE 
	
	COMMIT
	```
		NOTA: modifica eth0 con l'interfaccia 
3. Infine, modifica il parametro DEFAULT_FORWARD_POLICY all'interno del file /etc/default/ufw
	```/etc/default/ufw
	DEFAULT_FORWARD_POLICY="ACCEPT"
	```
4. Assicurarsi di avere i [permessi](#Permessi) necessari
5. [Riavviare](#Riavvio) il firewall.
