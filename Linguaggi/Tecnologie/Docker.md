# Introduzione
Docker è un software che permette di creare un #virtual-environment nel quale far girare programmi
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
## docker-compose.yml
E' un file che contiene i dati necessari (incluse #porte, localizzazioni di #database, dati di accesso, ) per creare l'ambiente su cui far partire il programma.
**NB. in environment non inserire le porte, perché renderebbe il container vulnerabile**
# Comandi
```Docker
docker ps #mostra i processi in esecuzione
```
```Docker
docker stop nome_container o id_container # arresta il container selezionato
```
```Docker
docker run -it nome_container o id_container <continua> # esegue il container selezionato nella porta selezionata
```
```Docker
docker run -it ubuntu bash # fa iniziare un processo nel #kernel #linux
```
```Docker
docker exec -it <id container> bash #collega il terminale al container già avviato
```


