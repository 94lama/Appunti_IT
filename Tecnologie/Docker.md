# Introduzione
Docker è un software che permette di creare un #container nel quale far girare applicazioni.
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
```DOCKERFILE
FROM <>
CMD [<comando_1>, <comando_2>, ..., <comando_n>]
```
### Inizializzazione
```bash
docker build <percorso>
docker run 
```
## docker-compose.yml
E' un file che contiene i dati necessari (incluse #porte, localizzazioni di #database, dati di accesso, ) per creare l'ambiente su cui far partire il programma.
**NB. in environment non inserire le porte, perché renderebbe il container vulnerabile**
# Comandi
Mostrare i processi in esecuzione
```Docker
docker ps
```
Arrestare il container selezionato
```Docker
docker stop nome_container o id_container
```
Eseguire in container selezionato nella porta selezionata
```Docker
docker run -it <nome_container> o <id_container> <continua>
```
Inizializzare un processo nel #kernel [[Linux]]
```Docker
docker run -it ubuntu bash
```
Collegare il terminale al #container già avviato 
```Docker
docker exec -it <id container> bash
```
# [[Cybersecurity]]