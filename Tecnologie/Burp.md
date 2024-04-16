# Dastardly
[Dastardly](https://portswigger.net/burp/dastardly) è uno strumento gratuito nella [versione community](https://github.com/PortSwigger/dastardly-github-action) (con funzionalità ridotte) per effettuare #penetration-test per analizzare 7 problemi di sicurezza.
- #reflected-xss
- #CORS
- Dipendenze JavaScript vulnerabili
- Content-type non specificato
- Multiplo content-type specificato
- -
La scansione viene riportata in un file [[XML]], riportando le criticità con relativo un livello di criticità. Nel caso di implementazione in #CI/CD, la presenza di criticità di livello BASSO, MEDIO o ALTO, blocca automaticamente il flusso della #pipeline, mentre il livello INFO non la blocca.
Dastardly utilizza i #container [[Docker]] per funzionare
## Funzionamento
Per utilizzare Dastardly, è consigliato utilizzare un computer dedicato, o quantomeno un ambiente virtuale (tipo [kali-linux](Linux#kali-linux)).
Creo una directory dedicata
```sh
mkdir dastardly
cd dastardly
```
Scarico ed eseguo il container con Docker
```sh
docker run \
	--user $(id -u) \
	--rm -v $(pwd):/dastardly \
	-e BURP_START_URL=<sito web da analizzare> \
	-e BURP_REPORT_FILE_PATH=/dastardly/report.xml \
	public.ecr.aws/portswigger/dastardly:latest
```
Per visualizzare il report (in formato [[XML]]) è possibile scaricare XUnit-Viewer
```sh
npm i /g xunit/viewer
```
Leggo il file 
```sh
xunit-viewer -r report.xml
```
	Opzioni
	-r : read
### Report
E' un file xml, che contiene delle card delle varie vulnerabilità identificate nel sito attaccato.
```report.xml
Severity: [INFO, HIGH]
Confidence:

Path:
Evidence: segnala il test effettuato
Response: mostra il risultato dell'attacco
References: Contiene una lista di link relativi all'attacco (da siti come Mitre, capec, postswagger)

```
# Proxy
Permette di simulare attacchi #man-in-the-middle, frapponendosi tra il browser della macchina utilizzata ed il server bersaglio., in maniera simile a [[ZAP]].
Per attivare il meccanismo di intercettazione basta cliccare su **Intercept on** (toggler che attiva e disattiva la funzionalità).
La schermata è formata da una parte a sinistra, nella quale è possibile vedere i messaggi #request (e modificarli) e la response (nel caso venga inviata prima la request), e una parte a destra che contiene l'**inspector**, con varie funzionalità utili, tra le quali, ad esempio:
- Testo selezionato
- Decodificatore automatico
# Sensitive discover 