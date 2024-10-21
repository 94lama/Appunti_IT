# Terminale
Stampare la lista di comandi utilizzabile
```
help
```

Trovare l'indirizzo [IP](./../Tecnologie/protocolli#ip) (o crearne/richiederne uno nuovo nel caso non sia impostato) e le configurazioni della [scheda di rete](./../Tecnologie/Macchina#NIC) della macchina su cui si opera
```
ipconfig
```
	OPZIONI:
	/all - Stapa una lista completa
	/relase - Rilascia gli attuali settaggli DHCP
	/renew - Rilascia le impostaioni attuali ed effettua una nuova 	chiamata DHCP per crearne di nuove
	/displaydns - Mostra tutti i dati DNS nella cache

Verifica il throughput tra client e server (scaricabile)
```windows
iperf3 <url>
```

Controlla e mostra i [socket](./../Tecnologie/Macchina#Socket) aperti per le comunicazioni in [TCP](./../Tecnologie/Protocolli#TCP)
```
netstat
```
	OPZIONI
	-n - Mostra gli indirizzi IP e il numero della porta in forma numerica

Aprire un [socket](./../TEcnologia/Macchina#Socket) per l'invio di richieste [DNS](./../Tecnologia/Protocolli#DNS) nel server locale. Una volta lanciato il comando si riceveranno informazioni riguardo il server locale, poi sarà possibile effettuare altre ricerche.
```
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
```
ping <indirizzo_ip>
```

Verificare le #porte aperte su un indirizzo #IP 
```
telnet <indirizzo_ip>
```

Ricevere informazioni relative al percorso effettuato dal pacchetto per raggiungere destinazione
```
tracert
```
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
