# Introduzione
Docker è un software che permette di creare un #container nel quale far girare applicazioni. Un container è un' #immagine, ovvero un sistema isolato, dotato di #OS, in cui vengono successivamente implementate le caratteristiche desiderate.
I container vengono utilizzati per eseguire processi, per poi terminare automaticamente.
# Struttura
## Makefile
E' un file che gestisce le operazioni da effettuare all'apertura o a seguito di richiesta tramite bash
```Docker
MAKEFILE

operazione_1:
	@echo "inizia"
operazione_2:
	mkdir "cartella"
```
```SHELL
make operazione_1 #risultato: "inizia"

```
## Dockerfile
### Inizializzazione
```bash
docker build <percorso> -t <tag_opzionale>
docker run <percorso>
```
Nel caso si voglia inizializzare docker con una configurazione particolare, è possibile utilizzare il **daemon.json**, ovvero un file json situato nella cartella **docker_custom_config**
```shell
sudo dockerd -config--file <file_daemon.json>
```
### Chiusura
Per chiudere un container basta lanciare il comando
```shell
exit
```
### Comandi
Definire il sistema operativo su cui si lavora
```DOCKERFILE
FROM <sistema_operativo>
```
Per eseguire uno #script di entrata
```DOCKERFILE
ENTRYPOINT []
```
Lanciare un comando (modificabile dall'esterno una volta eseguito il container)
```DOCKERFILE
CMD [<comando_1>, <comando_2>, ..., <comando_n>]
```
Esporre all'esterno un dato
```DOCKERFILE
EXPOSE 
```
Definire una variabile
```DOCKERFILE
ARG <nome_variabile>
```
Aggiungere alla cartella selezionata un file #deprecato
```DOCKERFILE
ADD ${<nome_variabile>}<percorso> 
```
Aggiungere alla cartella selezionata un file
```DOCKERFILE
COPY ${<nome_variabile>}<percorso> 
```
### Volumes
Include i file che devono essere mantenuti anche dopo la chiusura del #container.
E' possibile vedere dove sono localizzati i #volumes in container di fonti terze su https://hub.docker.com/
## docker-compose.yml
E' un file che contiene i dati necessari (incluse #porte, localizzazioni di #database, dati di accesso, ) per creare l'ambiente su cui far partire il programma, utilizzando anche più #container.
**NB. in environment non inserire le porte, perché renderebbe il container vulnerabile**
### Installazione
```bash

```
### Inizializzazione
Avvio del compose
```shell
docker compose up
```
Eseguire un comando
```shell
docker compose exec <comando>
```
Chiudere il compose
```shell
docker compose down
```
### Struttura
```docker-compose.yml
version: '<versione>'
services:
	web:
		image: nginx
		env_file: 
		ports:
			- <porta>
		environment: #può essere definito come lista o mappa
			NGINX_PORT: <numero_porta> #mappa
			- NGINX_PORT=<numero_porta> #lista
			- REDIS_PASSWORD=<percorso> #collego il secret al relativo file
		secrets: #definisco i secrets utilizzati
			- <nome secret>
	redis:
		image: 'redis:<immagine>'
		command: ["redis-server", "<percorso>"]
		ports: #lista delle porte da cui è possibile accedere
			- <nome_macchina>
		volumes:
			. ./redis.conf:/usr/local/etc/redis/redis.conf
			- redis-data:/data
			- <percorso>
	health:
		image: <immagine>
	<contentitore>:
		image: <immagine>
		privileged: <bool>
		ports:
			- "<indirizzo_porta>"
volumes:
	redis.data:
secrets:
	redis_password:
	file: <percorso> #definisco il percorso del file del secret
```
# Comandi
Mostrare i processi in esecuzione
```Docker
docker ps
```
Arrestare il container selezionato
```Docker
docker stop nome_container o id_container
```
Avviare in container selezionato nella porta selezionata
```Docker
docker run -it <nome_container> o <id_container> <continua>
```
Avviare un container con i privilegi root
```shell
docker run -v /:/host --rm -it alpine chroot /host sh
```
Inizializzare un processo nel #kernel [[Linux]]
```Docker
docker run -it ubuntu /bin/bash
```
Collegare il terminale al #container già avviato 
```Docker
docker exec -it <id container> /bin/bash
```
Cambiare la root di accesso dell'utente
```Docker
docker chroot /<nuovo_percorso>
```
Chiudere una o più immagini
```Docker
docker image rm <nome_immagine> <nome_immagine_2> ...
```
Creare i #secret
```Docker
docker image rm <nome_immagine> <nome_immagine_2> ...
```
Creare i #volumes 
```Docker
docker volume create --name <name>
```
Accedo all' #health 
```shell
docker compose --da finire
```
Accedo alla shell di un #container
```shell
docker compose exec -it <nome_container> sh 
```
Controllo le attività in esecuzione all'interno del #container
```shell
docker logs
```
## Opzioni
```Bash
-H #definisce l'host
-v
--rm
```
# Docker API
# Cybersecurity
## #privilege-escalation 
Nel caso si riesca ad accedere con un utente standard a Docker, è possibile aumentare i suoi privilegi tramite #terminale e prendere possesso della macchina
### Prevenzione
- Rafforzare il server e gli altri componenti nelle infrastrutture più critiche
- Chiudere servizi e porte non necessari
- Assicurarsi che gli user non più utilizzati siano cancellati
- Assicurarsi che i file, le directories e i servizi abbiano i permessi corretti
- Aderire al principio di minor privilegio quando si creano gruppi ed utenti
- Imposta metodi di autenticazione sicuri per user e visitatori, assicurandosi che non vengano utilizzate le credenziali standard, impostare policies efficaci per le password (come l'identificazione a più fattori) nel modo più rigoroso possibile
- Tieniti al passo con le #vulnerabilità più recenti, implementando continuamente gli aggiornamenti e le patch
- Aderisci alle best practices del framework e/o dei linguaggi utilizzati
## #insecure-inclusion
E' possibile sfruttare un parametro **ARG** impostato incorrettamente per modificare in maniera arbitraria la variabile a cui è collegata la variabile del #dockerfile.
Nel caso non si utilizzino i #secret per creare le password degli account, preferendo utilizzare il file #env  è possibile che un utente terzo riesca ad entrare all'interno del sistema
## #exposed-environment
Nel caso non si usino i #secret, è possibile che si crei una falla di protezione del sistema (sfruttabile, ad esempio, tramite il comando da shell **sh aux**).
## Server-Side Request Forgery #SSRF 
