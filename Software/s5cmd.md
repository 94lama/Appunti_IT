Tool sviluppato da Peak Games per agevolare la gestione degli [oggetti]() all'interno dei servizi [S3](../Server/AWS#S3) (e ingenerale, altri servizi che si agganciano alle API di AWS).

Il servizio permette di:
- Facilitare l'uso di wildcard nelle queries
- 

# Installazione

E' possibile utilizzarlo clonando il progetto dal [repository](https://github.com/peak/s5cmd) di GitHub
```sh
git clone https://github.com/peak/s5cmd.git
```

## Python
```sh
conda config --add channels conda-forge
conda config --set channel_priority strict
```

E successivamente
```sh
conda installs5cmd
```

## Docker
```sh
docker pull peakcom/s5cmd
docker run --rm -v ~/.aws:/root/.aws peakcom/s5cmd <S3 operation>
```

E successivamente
```sh
docker run --rm -v $(pwd):/aws -v ~/.aws:/root/.aws peakcom/s5cmd <S3 operation>
```

# Comandi
I comandi sono simili a quelli di una shell [Linux](../OS/Linux.md).
**N.B.**
- Il nome dei bucket sono indicati  utilizzando la sintassi [URL](https://it.wikipedia.org/wiki/Uniform_Resource_Locator) (es. s3://myawsbucket)
- Nel caso venga anteposto al comando l'opzione **--no-sign-requested**, verrà effettuata l'operazione tramite account anonimo

### Creare un bucket
```sh
s5cmd mb <nome bucket S3>
```

### Eliminare un bucket
```sh
s5cmd rb <nome bucket S3>
```

### Lista
Per visualizzare la lista degli storage disponibili si utilizza il comando "ls"
```sh
s5cmd ls
```
	OPZIONI:
		--all-versions # ritorna tutte le versioni memorizzate dell'oggetto selezionato
		--etag, -e # mostra gli etag
		--exclude # esclude i percorsi indicati
		--humanize, -H # mostra i dati in formato facilmente leggibile
		--storage-class, -s # mostra il nome completo dell'oggetto
	RISULTATO:
		CREAZIONE (data ora) NOME BUCKET S3
		2025/01/01 00:00:00  s3://myawsbucket
	
Il comando si può utilizzare anche per ottenere la lista degli elementi contenuti nel singolo contenitore
```sh
s5cmd ls <nome bucket S3>
```
	N.B.
		- Il comando funziona anche per le directory del bucket
		- Il comando accetta wildcards (*)
	RISULTATO:
		CREAZIONE (data ora)      FILE
		2025/01/01 00:00:00  228  index.html

### Leggere
```sh
s5cmd cat <nome bucket S3>/<percorso file>
```

### Eseguire un file
```sh
s5cmd run  <percorso file>
```

### Copiare
```sh
s5cmd cp <nome bucket S3>/<percorso file>
```

### Verificare le dimensioni
```sh
s5cmd du <nome bucket S3>/<percorso file>
```
