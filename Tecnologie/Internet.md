Sistema nato nel 1969 (con il  nome di ARPANET) per permettere lo scambio di informazioni tra due macchine, tramite l'architettura #client-server, **RIVEDERE** ovvero una struttura che permette di inviare informazioni da un #server ad un #client.

# #http
Nel 1991 è nato il World-Wide-Web: una rete di macchine, connessa tramite modello #http (Hyper-Text Transfer Protocol), basato sul modello #client-server, dove il client è gestito dal #browser, mentre il #server è gestito dal sito internet. Mentre la gestione del codice per eseguire azioni lato #browser è gestita di solito da linguaggi come [[JavaScript]], lato server si usano linguaggi come [[Php]], [[Python]], [[Java]], spesso accompagnati da relativi #framework appositi (come [[Laravel]], [[Django]], ecc.)

Tramite protocollo http è possibile inviare due tipi di messaggi: **Richiesta** e **Risposta** in maniera *stateless*, ovvero senza tenere traccia della tipologia di utente che ne usufruisce (caratteristica gestita da altre tecnologie, ad esempio i #cookies**, ovvero dei dati che vengono gestiti lato **client**).

** I cookies hanno, per motivi di sicurezza, una certa durata (variabile, ad es. 1 mese)

Una seconda versione del protocollo http è l' #https, ovvero lo stesso protocollo con aggiunta di un elemento di sicurezza per la protezione dei dati dell'utente.
### Richiesta
è formato da 3 componenti principali: riga di richiesta, header e body:
#### Riga di richiesta
Composta a sua volta da: 
- #metodo: può essere #GET (riceve), #POST(invio dati), #PUT(modifica dati) e #DELETE (elimina dati)
-  #URI (Uniform Resource Identifier): rappresenta il percorso che identifica una specifica risorsa (la home è locata in "/")
- #protocollo: 

#### Header
E' composto da:
- #host
- #user-agent: Contiene informazioni di livello generale del sito (lingue accettate, browser accettati, visualizzazione da mobile o meno, ...)

#### Body
Contiene le informazioni inviate al server. Nel caso di richiesta tramite #GET, il body è vuoto poiché non c'è la necessità di inviare dati.


### Risposta 
E' rappresentata da un codice a 3 cifre, che rappresenta lo stato della richiesta.

codice: ABC

|A|risultato della richiesta|
|-|-|
|1|informazioni|
|2|successo|
|3|reindirizzamento|
|4|errore lato client|
|5|errore lato server|

### Content Delivery Network
Le #cdn sono dei collegamenti tra la pagina web e contenuti provenienti da siti esterni (es. Bootstrap, Tailwind).

# DOM

Il #virtual-dom è una copia identica del DOM, che permette di modificare porzioni di sito, senza dover modificare l'intero DOM, velocizzando le varie operazioni.
# Middleware
un #middleware è uno script che viene lanciata ogni volta che viene effettuata una richiesta al server. Il middleware fa quindi dei controlli che, se vengono superati la richiesta viene accettata, altrimenti viene respinta. Spesso vengono utilizzati per porre limitazioni in base alla tipologia di utente. 
# DNS
Un #DNS è il meccanismo che converte l'indirizzo del server in cui è presente l'app nel nome desiderato ed è rappresentato da un #dominio (es. 213.186.33.5). Nel caso si vogliano inserire più siti web in un dominio, è possibile utilizzare i sotto-domnini.
Per gestire i domini, sono presenti varie piattaforme (es. OVHcloud).

# Standard
## Autenticazione
### OAuth 
#sanctum #passport
L'Open Authentication ( #oauth) è un protocollo standard, facente parte della categoria #iam (Identity Acess Management) che perette di iscriversi/accedere ad un sito web tramite l'appoggio a #api di terze parti (es. Google, Apple, Amazon, GitHub, ecc.). Le entità rilevanti per il processo di OAuth sono:
- Il proprietario della risorsa
- #client 
- #server di autenticazione
- #server delle risorse
##### Tipi di concessione
- Concessione del codice di autorizzazione
- Concessione delle credenziali
- Concessione implicita (sconsigliato nei casi in cui la sicurezza sia un fattore importante)
- Concessione delle credenziali del client
Mentre inizialmente era possibile effettuare il processo OAuth sia da #front-end  che da #back-end, la prima metodologia è andata in disuso a causa di problemi di #sicurezza.
Nel caso di autenticazione lato #front-end, il processo avveniva tramite doppia chiamata (all'ente che fornisce il servizio e successivamente al server), con scambio di token tramite #URI. I dati sono recuperabili tramite l'analisi del parametro origin
```Javascrit
let stolenData = new URL('<indirizzo del sito bersagio>')
stolenData = stolenData.origin
```
```HTML
<iframe sandbox ="allow-popups allow-scripts" src="data:text/html,
	<script>
		started = false;
		window.addEventListener('message', (event) => {
			switch(event.data.command){
				case 'ready':
					if (!'started')
			}
		})
	</script>
```
# Termini
#lazy-loading - Ferma la il ricaricamento della pagina fino a che un determinato evento accade
#slug - ricopiatura del nome utilizzando **-** al posto dello spazio e lettere minuscole
#URI - Uniform Resource Identifier
#URL - Uniform Resource Locator
# Messa online
### [Digital ocean](https://www.digitalocean.com/)
E' un provider che offre server su cui caricare applicazioni web. 

- Dopo l'iscrizione è possibile aprire un cloud server selezionando la voce #droplets.
- Dopo aver selezionato la posizione geografica dello stesso, è possibile selezionare un #OS per il nostro server ( #Ubuntu) e una versione
- La #versione #lts (long-term support) è quella consigliata, in quanto più duratura
- CPU: Un progetto [[Laravel]] con poco traffico gira bene con almeno un GB di RAM. In ogni caso è possibile cambiare l'opzione scelta in qualunque momento, anche durante la messa online del sito.
	- E' possibile aggiungere un sistema di #monitoraggio automatico  delle metriche del server (consigliato). Il sito ha un contatore ad ore che modula il pagamento.
	- #autenticazione: è possibile aggiungere una password o una chiave #SSH. Una volta inserita la chiave, deve essere checkata per utilizzarla.

#### Collegamento con il server da remoto
Nel terminale si digitano i seguenti comandi
##### Installazione
	ssh root @111.111.11.11 //chiave utente @IPv4 del server
	ufw app list //stampa una lista dei firewall del server
	ufw status //stama lo stato del firewall del server
	ufw allow OpenSSH //abilita il firewall OpenSSH
	ufw enable //attiva il firewall
	apt update //aggiorna #apt (gestore di pacchetti di Linux)
	apt upgrade //installa gli aggiornamenti di Linux. Clicca su keep the updated data e poi ok(default)
	apt install nginx
	ufw allow 'nxginx HTTP'
	ufw enable -> y
	apt install mysql-server -> y
##### [[MySQL]]
	mysql -u root -p //Essendo un server Linux, non c'è bisogno di scrivere winpty prima
	*Enter* //inizialmente l'utente root non ha una password di default, quindi si inserisce un valore vuoto
	show databases //mostrerà 4 databases: information_schema, mysql, performance_schema e sys
	use mysql
	show tables //a noi interessa la tabella user
	select user, authentication_string, plugin from user; //mostra gli utenti. A noi interessa root
	alter user 'root' @ 'localhost' identified wwith mysql_native_password by 'inserire_password' // inserisce una password all'utente root
	flush privileges
##### [[Php]]
	apt install software-properties-common //installa un sistema per installazioe di linguaggi
	add-apt-repository ppa:onrej/php //installa la repository di php
	apt install php8.2-fpm php8.2-mysql php8.2-gd php8.2-sqlite php8.2-exif //installa tutte le estensioni di php necessarie per l'app (come si fa con php.ini da windows. Copiare gli elementi dal file)
	php -v //mostra la versione di php. Si usa per controllarne la corretta installazione
	php install composer
	cd /var/www/ //apre la cartella preinstallata che gestisce i file HTML. Al su oiterno ci sarà già presente un file /html/nginx.html, ovvero un file #HTML preconfigurato da NGINX
	ssh-keygen //crea una chiave SSH da aggungere a GitHub nel progetto da clonare
	git clone chiave-ssh-del-progetto //Il server e GitHub devono avere una chiave SSH uguale
##### #Composer 
###### Installazione
[Documentazione di Composer](https://getcomposer.org/download/)
[Documentazione di Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-composer-on-ubuntu-20-04)

	php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
	php -r "if (hash_file('sha384', 'composer-setup.php') === 'e21205b207c3ff031906575712edab6f13eb0b361f2085f1f1237b7126d785e826a450292b6cfd1d64d92e6563bbde02') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
	php composer-setup.php
	php -r "unlink('composer-setup.php');"//si prende dal sito di composer
	mv composer.phar /usr/local/bin/composer
	composer install
###### Inizializzazione del database
	mysql -u root -p //inserire la password dopo l'invio
	mysql create database nome_database;
###### Settaggi di Artisan
	cp .env.example .env //Genero il file .env
	php artisan key:generate
	php artisan storage:link //solo se richiesto
	quit;
	cat .env //modifico il file in base alle esigenze, premere Esc, seguito da v e q
##### Installazione di [npm](https://www.npmjs.com/)
Prima di pushare su GitHub, è possibile salvare un public una versione minimizzata di tutte le stringhe di styling e JS.

	npm run build
###### Sites enabled
	cd etc/nginx/sites-available //la cartella avrà un file default, contenente 
	vim nome_progetto //case sensitive
	cat nome_progetto //inserire il codice inviato da Donato, che reindirizzerà la chiamata HTTP al nostro progetto
	nginx -t
	systemctl reload nginx
	systemctl status nginx //controlla che il reload sia avvenuto con successo
Da ora posso vedere il nostro progetto, con un errore su index.php (mancanza di permessi per aprire un file). Per risolvere il problema, basta inserire nel terminal

	cd /var/www/nome_progetto
	ll //mostra l'accessibilità delle cartelle. Saranno tutte accessibili solo dall'utente root
	chown -R www-data.www-data /var/www/nome_progetto/storage //Rende la cartella storage/..... pubblica
Il sito sarà caricato correttamente, ma con una console di debugging per [[Laravel]]. Sarà necessario quindi rendere questo strumento disponibile solo da root tramite modifica al file .env:

	APP_ENV:product
	APP_DEBUG=false
Il sito ora è pubblico all'indirizzo del server impostato. Per cambiare il #dominio si dovrà usare un servizio dedicato ([OVHcloud](https://www.ovhcloud.com/it/)).
Una volta impostato il #DNS, si modifica il file 

Si imposta la variabile

	 server_name nome_server;
Si deve resettare NGINX

	systemctl reload nginx
#### #https
DigitalOcean permette di ottenere un certificato #SSL. [Documentazione](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-20-04) 
### #OVHcloud
Si crea un account.
Se si usa un #IPv4 si aggunge un DNS di tip A (se #IPv6, il #DNS sarà AAAA)
# Application Program Interface( #API)
E' una tecnologia che permette di metter in comunicazione due sistemi diversi. #API è l'acronimo di Application Program Interface. Per comunicare tra varie machine si usano protocolli. Il #protocollo più utilizzato è il #REST .
## Protocolli
### REST
Si basa su un determinato #metodo in base all'obbiettivo della richiesta e sull' #URI, in cui (per convenzione) vengono inseriti i dati da inviare sotto forma di stringhe  
#### Metodi
- GET
- POST
- PUT
- DELETE
- 
#### Struttura
##### [Headers](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields)
Permettono di stabilire il tipo di comunicazione tra #client  e #server e/o di definire ulteriori informazioni (es. autorizzazioni o dati di #cache)
##### Body
Contiene il messaggio da inviare. Possono essere dati o file, $context 
#### Risposta
La #response è formata da:
- riga di stato (es. 200, 404, 502)
- 
### Websocket
### SOAP
# CMS
#CMS, o Content Management System, sono quelle piattaforme, come Wordpress, che gestiscono sistemi di contenuti.
## Wordpress
Sistema customizzabile ed espandibile tramite #plugin
### Security
La presenza di #plugin aumenta esponenzialmente la superficie di attacco dei siti che utilizzano la piattaforma. Ad esempio è famoso un attacco informatico #xml che ha sfruttato il plugin Jetpack. 