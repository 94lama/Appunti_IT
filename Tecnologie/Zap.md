[link](https://www.zaproxy.org/)
# Introduzione
Tool #open-source utilizzato per effettuare #penetration-test 
E' possibile utilizzare Zap tramite #immagine di [[Docker]], per collegarlo alla #pipeline di messa online del progetto (es. tramite [[Jenkins]]) o tramite installazione classica.
# Installazione
## Linux
### Kali-linux
```sh

```
## Windows
## Docker
Scaricare l'immagine
```bash
docker pull ghcr.io/zaproxy/zaproxy:stable
docker pull softwaresecurityproject/zap-stable
```
	Questa è la versione Stable. per altro andare su
	https://www.zaproxy.org/docs/docker/about/
Per effettuare una scansione con Baseline Scan
```sh
docker run -t ghcr.io/zaproxy/zaproxy:stable zap-baseline.py -t https://www.example.com
```
	Ritotner' il risultato in console.
Se si vuole avere invece un file html con il responso si deve prima scaricare la #mount (il codice sotto la scarica nella cartella corrente)
```bash
# ...linux / MacOS / PowerShell
#    The ${PWD} _environment variable_ is your current directory
docker run -v ${PWD}:/zap/wrk/:rw -t softwaresecurityproject/zap-stable zap.sh ...
```
Posizionarsi nella cartella ```';C'``` appena creata, poi effettuare la scansione
```sh
docker run -v $(pwd):/zap/wrk/:rw -t ghcr.io/zaproxy/zaproxy:stable zap-baseline.py \
    -t https://www.example.com -g gen.conf -r testreport.html
```
# Funzionamento
## Schermata
### Tree window
Sistema di visualizzazione dei file ad albero, composta da una cartella principale nominata con l'URL del sito, un file per ogni chiamata effettuata verso il sito attaccato, ed una sottocartella per ogni pagina aggiuntiva del sito
```Tree window
<nome_sito>
|
```
## Scansione attiva
1. Aprire la tab **Quick Start**,
2. Fare click su **Added scan**
3. Compilare i dati
4. Clicca su ****
Zap fornisce due tipi di #spider per portare a termine gli attacchi:
- Standard - non ottimizzato per AJAX
- AJAX
Una volta effettuata la scansione, nella barra a sinistra apparirà una cartella con il nome dei siti attaccati, contenenti tutte le chiamate effettuate dal software in tutte le pagine attaccate (sotto-cartelle) presentate come coppia #request e #response nella schermata in alto a destra e la descrizione dell'attacco, con tanto di link per approfondire il problema nella schermata in basso a destra.
### Esplorazione manuale
Permette di effettuare una scansione del sito mentre lo si esplora manualmente (utile per simulare attacchi da effettuare a seguito dell'accesso tramite user e password). Il funzionamento è simile a quello di un attacco #man-in-the-middle
## Scansione passiva