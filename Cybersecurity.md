#  Introduzione
La cybersecurity si occupa di prevenire e contrastare minacce ai sistemi informatici, che possono essere classificati in:
- Attacchi software
- Errori dei software
- Sabotaggio
- Errore umano
- Furto
- Danni all’hardware
- Interruzione delle utilities (es. interruzione della corrente elettrica)
- Disastri naturali

Per analizzare il livello di sicurezza di una rete, spesso si fa riferimento a 4 concetti chiave:
- **Minaccia**, ovvero il potenziale danno causato al proprietario della rete
- **Vulnerabilità**, ovvero la singola debolezza del sistema che può essere sfruttata da un attore esterno
- **Exploit**, ovvero il meccanismo di sfruttamento della vulnerabilità 
- **Rischio**, la probabilità che il particolare exploit venga utilizzato, pesata in base al danno che essa causerebbe

Il totale delle vulnerabilità presenti in un sistema viene anche chiamato **superficie d’attacco**.

## Rischio
Per pianificare miglioramenti alla sicurezza di un sistema, l’obiettivo è analizzare la stessa per identificare i vari rischi e operare secondo uno di questi 4 criteri:
- Ridurre: correggere le impostazioni affinché si riduca la superficie d’attacco 
- Trasferire: demandare enti terzi (es. il cloud provider) la soluzione al rischio
- Evitare: eliminare la fonte del rischio dal sistema
- Accettare: non effettuare nessuna operazione per rimuovere il rischio

Il criterio da attuare dipenderà da fattori come la disponibilità di tempo e/o denaro del proprietario della rete, la facilità con cui il problema può essere risolto, il potenziale danno che ne consegue e la possibilità che esso avvenga.

## Ruolo DevSecOps
Il #DevSecOps è un esperto in sviluppo (Development), sicurezza (Security) e operazioni (Operate, ovvero gestione e sviluppo dell'app anche dopo la messa online). La sicurezza viene verificata in tutte le fasi del progetto
### Development
- Plan
- Code
- Build
- Test
### Operation
- Release
- Deploy
- Operate
- Monitor

## Terminologia

### Secure by-Design
Principio che si basa sull'applicazione dei principi di sicurezza sin dalla fase di #progettazione 
### Defense In-Depth
Si basa sul proteggere un sistema mediante vari livelli di sicurezza, ognuno dei quali rappresenta una difesa per eventuali attacchi informatici (es. validazione lato client e server, uso di middleware).
#### Controlli amministrativi
Strategie organizzative generali per la creazione di  un ambiente sicuro. Simulazioni di attacchi (tipo #phishing) potrebbero rivelarsi utili
#### Controlli fisici
Impediscono agli aggressori di ottenere l'accesso reale ai dati e sistemi informatici (es. chiavi magnetiche, porte bloccabili, ecc.)
#### Controlli tecnici
### Principle of Least Privilege
**Vantaggi**:
- Migliore gestione dei permessi
- Rallentamento della diffusione del malware
- Semplificazione della conformità e miglioramento della preparazione agli audit 
Il principio dei privilegi minimi si implementa seguendo dei passaggi:
1. Verifica dei privilegi
2. Configurazione predefinita di un privilegio minimo
3. Separazione dei privilegi e degli account
4. Regolazione delle autorizzazioni in base al ruolo
5. -
6. -
7. Monitoraggio e analisi degli accessi (specialmente quelli privilegiati)
8. -

La lor implementazione deve comunque esser effettuato considerando:
- La UX dei dipendenti
- La conseguente crescente complessità e diversificazione delle reti
- Il Cloud Computing può creare problemi di #over-provisioning o semplificazione delle procedure per mancanza di cautela
- Impostazioni predefinite e mancanza id granularità
### Zero-Trust Model
Modello informatico, alternativo al #perimeter-security (che si basa sul concetto di perimetro entro il quale è ammissibile dare fiducia) che si bassa sull'idea di non fidarsi di nessun utente, né all'interno, né all'esterno di una rete aziendale:
1. Verificare sempre l'identità effettiva dell'utente
2. Identificare cosa e quando proteggere
3. Design della rete dall'interno
4. [Loggare]( #log) tutto il traffico, anche per rispettare i principi di #accountability (responsabilità)
5. Procedere in maniera continuativa per applicare il metodo all'intero sistema
#### Pilastri della Zero Trust Model
- Identità, suddivisa anche tra utenti che usano il servizio (tramite, ad es., [Multi-Factor Authentication]( #multifactor-authentication), #device che vengono utilizzati (accesso biometrico, uso di [Virtual Private Network]( #vpn)
- Protezione dei dati (es. tramite crittografia)
#### Adattamento di un sistema esistente al Zero-Trust Model
Per agevolare il passaggio, anche da un punto di vista umano, spesso si segue un percorso, che porta dal metodo esistente, a quello desiderato.
# Principi di sicurezza

Per comprendere le aree di interesse della cybersecurity spesso si fa uso del cosiddetto Cybersecurity Cube, che aggrega i concetti in 3 categorie, note anche come CIA Security Triad:

## Confidenzialità dei dati
Solo le persone autorizzate devono avere accesso ai dati. Richiede l’implementazione di cifratura e decrittazione dei dati come misura cautelativa.
Un’alternativa alla cifratura è la tokenizzazione, ovvero la creazione di un valore randomico temporaneo da utilizzare come lasciapassare per ottenere accesso ai dati.

- DRM: La gestione digitale dei diritti (Digital Rights Management) si occupa di proteggere i dati tramite meccanismi di cifratura, in modo che essi non possano essere copiati senza l’apposita chiave di decrittazione privata.
- IRM: La gestioni diritti di informazione (Information Rights Management) si occupa della protezione dei dati tramite la creazione di un livello di controllo degli accessi al documento protetto che avvisa il proprietario in caso di apertura (es. la PEC)

### Controllo degli accessi
Avviene su più livelli, ognuno dei quali deve essere te tuo in considerazione:
#### Fisico
Consiste in tutti quegli ostacoli che permettono di prevenire o controllare l’accesso fisico alla rete. Alcune misure di controllo fisico sono:
- Guardie
- Recinzioni
- Sistemi di allarme
- Videocamere
- Porte blindate

#### Logico
Sono tutte quelle misure di sicurezza che prevengono l’accesso logico alla rete, come:
- Cifratura dei messaggi di testo
- Firewall
- Password
- Controllo dei dati biometrici
- Protocolli

#### Amministrativo
Racchiude tutte le policy e le procedure che permettono di discernere chi può da chi non deve avere accesso ai dati.
- Policies
- Procedure
- Recensioni
- Addestramento alla sicurezza
- Classificazione dei dati
- Controlli del background

Alcune misure efficaci per la maggioranza dei criteri sono:
##### Autenticazione
Controlla l’effettiva identità dell’utente. Di solito consiste in due parametri:
- Username (o email)
- Password
Il processo di autenticazione permette di definire con precisione l'identità dell'utente con cui è in corso la sessione.

###### FIM
La Gestione federata dell'identità (Federated Identity Management) avviene quando la gestione dell'autenticazione di un utente avviene a livello di raggruppamento di reti (ad es. quando si utilizza lo stesso utente per accedere ai servizi Google come Youtube, Gmail, ecc.).

###### Password
Consiste in un dato che (dovrebbe) essere in possesso unicamente dello specifico utente. In quanto tale è consigliabile seguire alcune linee guida durante la sua creazione, ovvero:
- Avere lunghezza di almeno 10 caratteri
- Includere lettere (sia maiuscole che minuscole), numeri e caratteri speciali
- Conservarle in luoghi non protetti (come i Password Manager)
- Cambiare la password spesso

E' anche possibile utilizzare processi di [MFA](#MFA), ovvero la verifica di più fattori durante il processo di autenticazione per aumentare la sicurezza della rete. 

##### Autorizzazione
Verifica se l’utente abbia o meno il permesso di utilizzare determinati file. E' sempre consigliato considerare l'inserimento di procedure di autorizzazione anche per l'accesso alla rete stessa, così come per l'accesso a dati particolarmente sensibili, come password, email, ecc.
Per praticità gli utenti vengono raggruppati per livello di autorizzazione.
##### Contabilità
Monitoraggio (log) dei processi e delle azioni effettuate dagli utenti e uso degli stessi per effettuare controlli ed analisi dei dati. Questa procedura aiuta a identificare eventuali errori, sbagli e tenere traccia delle azioni durante i processi di audit.

## Integrità
Solo le persone autorizzate possono modificare i dati. Richiede l’implementazione di cifratura dei dati come misura cautelativa, così come misure di validazione, controllo degli accessi e verifiche della consistenza. La frequenza necessaria dell’effettuazione di questi controlli dipende dall’importanza che ha il dato.

## Disponibilità
L’accesso ai dati deve essere il più possibile costante. Richiede l’implementazione di pratiche di ridondanza di servizi, link e gateway. Alcuni momenti in cui la disponibilità dei dati diventa un parametro critico sono:
- Manutenzione
- Disastri naturali
- Attacchi informatici
- Danneggiamenti dell’hardware
Buone pratiche per evitare un’interruzione di disponibilità nei casi sopracitati sono:
- Creazione di dati di backup multipli
- Monitoraggio costante
- Pianificazione delle procedure in caso di disastri
- Testing dei backup
- Aggiornamento dei software e del sistema operativo
- Manutenzione degli equipaggiamenti (hardware)

# Stato dei dati
- In transito
- A riposo
- In processo

# Salvaguardie
- Persone
- Tencologia
- Policy e pratiche

# Security Standards
Gli standard di sicurezza hanno l'obiettivo di categorizzare e valutare le #vulnerabilità.

Gli standard sulla sicurezza sono gestiti da apposite agenzie e costantemente aggiornati tramite analisi dei contenuti presenti al dark web, AIS (Indicatore di Condivisione Automatizzato), ovvero un’infrastruttura che permette lo scambio in tempo reale di indicatori sulle vulnerabilità utilizzando determinati linguaggi standardizzati e strutturati come lo STIX (Espressione Strutturata delle Informazioni della Minaccia) o il TAXII (Scambio Automatizzato e Fidato di Informazioni di Intelligence)

## MITRE
Organizzazione non-profit, fondata nel 1975, che si occupa di #cybersecurity.
Mette a disposizione due archivi molto utili per la sicurezza:

### CVE
Le Common Vulnerabilities Enumeration sono una lista delle principali vulnerabilità alla cybersecurity riscontrate, contenenti informazioni molto utili sulle vulnerabilità e sulle debolezze dei siti web, framework, librerie ecc., costantemente aggiornate (dopo che il framework colpito è riuscito a rimuovere la vulnerabilità).
Contiene anche alcune possibili soluzioni per rimuovere le vulnerabilità

### CWE
Common Weaknesses Enumeration

| N° | Nome | Descrizione |
| ---- | ---- | ---- |
|  |  |  |
| 78 | Improper Neutralization of Special Elements used in an OS Command ( #OS-command-injection) | Inietta un comando nello **shell** del server |
| 79 | Improper Neutralization of Input During Web Page Generation ( #cross-site-scripting ) | Inietta uno script malevolo |
| 89 | Improper Neutralization of Special Elements ( #sql-injection) |  |
| 90 | Improper Neutralization ( #LDAP-injection) | Inietta una query LDAP per accedere e/o manipolare dati sensibili |
| 434 | Unrestricted Upload of File with Dangerous Type | Permette di caricare file di estensioni non desiderate (es. **.php**) all'interno del server, che possono essere successivamente aperti dall'utente malevolo stesso |
| 611 | Improper restriction of XML External Entity reference | Inserisce nel codice XML una stringa URI che prelevano file esterni all'area prevista |
| 1021 | Improper Resctiction of rendered UI Layers or Frames | Una pagina del sito viene utilizzato su un server esterno tramite es. #iframe per ingannare un utente ed estrapolare dati sensibili (es. dati di accesso) |

### CPE
Common Platform Enumeration
Archivio di software e/o framework disponibili, indicizzati.

## OWASP
### OWASP Top 10
- Algoritmi scnosigliati: sha1, md5 

## ASVS e MASVS
Sono #standard di sicurezza ampiamente accettati e utilizzati per proteggere contro le vulnerabilità comuni e gli attacchi, basati su 3 livelli di maturità del sistema:
1. Requisiti di base per tutte le applicazioni web
2. Requisiti di sicurezza avanzati per applicazioni di livello medio o alto
3. Requisiti di sicurezza aggiuntivi per applicazioni ad alto rischio o che richiedono una sicurezza estesa
Nel caso di applicazioni #mobile si fa riferimento al #MASVS.
Il processo di implementazione del #ASVS, si effettua in vari passaggi:
1. Comprendere i requisiti
2. Valutazione iniziale
3. Pianificazione e gestione delle priorità
4. Progettazione e sviluppo
5. Test di sicurezza
6. Monitoraggio e manutenzione
7. Aggiornamenti e miglioramenti continui
-----20:40-----

# Policy
La Security Policy è un documento che raccoglie le varie policies informative per l’utente, lo staff IT e i manager, riguardo i requisiti di protezione delle tecnologie e informazioni all’interno di un’azienda. I principali tipi di Policy sono:
- Specifiche sull’autenticazione e l’identificazione degli utenti
- Impostazioni riguardanti la password (lunghezza, tipo di caratteri, altre specifiche)
- Definizione dei comportamenti ammessi nell’azienda 
- Requisiti per l’accesso da remoto alla rete aziendale

Riferiti al team IT, due documenti sono particolarmente importanti:
- SOP (Standard Operating Procedure) o procedure per le operazioni standard
- Linee guida: coprono le aree non incluse nelle SOP

# Secure coding
## Hardening
## Front-end
### JavaScript
#### XSS
#### eval()
E' un metodo che permette di inserire strighe di codice all'interno dell'operazione
```Javascript
const injectedCode = document.location.hash.replace("#", "");
eval(injectedCode)
```
	// inserendo una stringa di codice nell'URI, l'eval(injectedCode) permette di eseguire il codice 
#### postMessage()
Permette di collegare due o più pagine
 ```Javascript
// Si considera il caso in cui il sito oggetto dell'attacco stampi dei dati ricevuti nella schermata
const listener = window.open("<URL da attaccare>", "");
send.addEventListener('click', () => {
listener.postMessage("<messagio>", "<URL da attaccare>")
});
```
#### Referrer-Policy
Funzionalità deprecata che permetteva di conoscere l'ultimo sito visitato dall'utente
#### open()
Metodo che 
#### element.innerHTML()
Il metodo permette di inserire una variabile all'interno di **element**
Con questo comando è possibile iniettare del codice malevolo all'interno del sito come attributo di tag o script.
Una soluzione valida è l'utliizzo di **element.innerText()**
#### cdn
Per evitare di utilizzare librerie o cdn di terze parti (ed esporsi a rischi), conviene sempre verificare la firma della libreria originale
```Javascript
// soluzione
<script src=<cdn desiderato> integrity=<hash della libreria preso dal sito originale> >...</script>
```
### #security-misconfiguration
Nel caso sia necessario ricevere dei file dall'utente, è possibile che il #browser converta automaticamente la tipologia di file in base al contenuto (ad esempio, scrivendo un codice JavaScript e salvandolo con .jpg).
```HTTP
<header
	X-Content-Type-Options: nosniff
	Content-Type: image/jpeg //tipologie disponibili su: https://www.geeksforgeeks.org/http-headers-content-type/
	>
```
### #ui-redressing
E' attuabile tramite inserimento di un tag **iframe** con la pagina bersaglio che verrà utilizzato come sfondo. I campi compilabili dall'utente vengono poi sovrapposti a quelli del sito bersaglio, così che l'utente non riconosca la differenza tra i due siti e invii i propri dati all'attaccante.
```HTML head
 X-Frame-Options: DENY //Metodo più vecchio che nega l'uso negli iframe
 X-Frame_Options: SAME ORIGIN //permette l'utilizzo solo ai siti aventi la stessa origine
 Content-Security-Policy: frame-ancestors 'none' //metodo più recente e non sempre disponibile nei browser. Permette l'utilizzo dei contenuti inviati dai siti indicati (none equivale a nessun sito, self equivale al server stesso)
```

Un altra tipologia di Redressing è attuabile tramite auto-compiler di HTML, CSS e JavaScript:
1. L'utente inserisce i dati nell'iframe
2. Compare un pop-up con pubblicità spam e un pulsante per inviare una richiesta post
3. Cliccando sul pulsante, il sito fasullo legge i dati dall'iframe e li invia all'attaccante
```HTML
# Content Security Policy
<meta
	  http-equiv="Content-Security-Policy"
	  content="default-src 'self'" />
```
#### postMessage(message, origin)
Nel caso il metodo sia compilato in maniera non corretta, l'utente potenzialmente invia il messaggio anche ad utenti terzi:
```Javascript
window.opener.postMessage(message, '*');
```
	in questo caso l'utente invia il messaggio a tutti i server che stanno ascoltando
``` JavaScript
window.opener.postMesasge(message, "indirizzo dell'origine"); 
```
	in questo caso l'utente invia il messaggio solo al server origine 
### Prototype-pollution
Attacco che permette di modificare il metodo **__proto__** dell'oggetto base di JavaScript per eseguire velocemente comandi tramite metodo **eval()**. Sfruttando questo stratagemma è possibile eseguire attacchi #xss ed è inclusa nella categoria #insecure-design
### CSS-injection
Tramite script #JavaScript si modifica lo style della pagina. Questo tipo di attacco si verifica quando si immettono delle variabili collegate tramite #URI:
```Browser
127.0.0.1:8000/#blue //colora lo sfondo un componente
127.0.0.1:800/#}body{display:none} //in questo modo si modifica l'attributo display del div body
```
Con questo attacco, per esempio, si può nascondere la #UI all'utente bersaglio, lasciandogli solo un input con un label con una richiesta di inserimento dati per sbloccare il normale funzionamento del sito (i dati inseriti saranno leggibili dall'attaccante)
## DevSecOps Pipeline
### Introduzione
Il #DevOps è una metodologia di lavoro, utilizzata per ridurre i tempi di distribuzione attraverso l'automazione, fornire un #feedback continuo, migliorare la collaborazione del team e le capacità di affrontare il rilevamento degli errori
### Software Development Life Cycle ( #sdlc)
#### CI/CD
Per #CI/CD si intende Continuous Integration and Continuous Devliery. Il CI/CD è una metodologia utilizzata per aumentare la velocità, ridurre gli errori e permettere di standardizzare i processi.
Il #deployment di norma è effettuata da una singola persona, dopo che il prodotto ha raggiunto un livello di avanzamento apprezzabile (ad esempio ha raggiunto determinati obbettivi) ed è stato oggetto di verifica.
#### Software utilizzati
##### Code
I software sono utilizzati per il #versioning dell'applicazione. Questi software permettono di condividere il lavoro tramite creazione di più #branch, ovvero ramificazioni del progetto. 
- [[Github]]
- Git
- Subversion
- GitLab
```Branching
└ master
	└ develop
		├ feature_1
		└ feature_2
```
#### Container
Permettono di progettare in maniera riproducibile, senza la necessità di controllare la conformità delle varie #dependency, scalabile 
- [[Docker]]
- podman
#### Pipeline
Servono ad automatizzare le procedure.
- [[Jenkins]]
- Travis CI
- GitHub Actions
#### Infrastructure
Può essere di tipo **On premise** o **cloud**, dove i secondi permettono di avere potenza di calcolo, spazi di archiviazione e servizi di business logic adattabili ed un costo variabile in base all'uso effettivo.
- [[AWS]]
- Azure
- Google Cloud Platform
### Design
#### Threat Modeling
![[Pasted image 20240108202659.png]]

### Implementazione
#### Common Software Vulnerabilities
##### Injection flaws
- #sql-injection 
- #os-command-injection
- #cross-site-scripting
- #code-injection o #unsafe-deserialization di dati non fidati
##### Broken Authorization
##### Broken Session Management
- #session-id esposto nell' #URL 
- session id non rinnovato nel tempo
##### Broken Cryptography
##### Sensitive Information Exposure
- Mancata crittografazione dei dati
##### Insufficient Logging
- Mancanza dei #log
- log non protetti
- assenza di ridondanza dei log
- mancata registrazione di eventi importanti
##### Server side request forgery
##### Sandboxing
Una #sandbox (tipo [[Docker]])
## Threat Modeling
--- recuperare i primi 30 minuti
- Analizzare l'applicazione e capire quali siano le componenti che potrebbero ricevere un #attacco (brainstorming)
- Dare un punteggio agli asset ( #dati ) in base alla loro importanza
- Definire le priorità per le quali allocare risorse
### Fasi
Il #threat-modeling deve essere effettuato durante tutto il #sdlc 
- Planning
- Analysis
- Design
- Implementation
- Maintenance
Si effettua seguendo delle fasi specifiche:
1. --
## CI-CD OWASP top 10
### 1 - Insufficient Flow Control Mechanisms
Nel caso di controlli insufficienti, è possibile che degli automatismi permettano di effettuare un #push direttamente nella branch **main**, incorrendo così in potenziali #merge, oppure è possibile, nel caso il #repository fosse pubblico, che un utente esterno riesca ad effettuare un push non controllato.
### 2 - Inadequate Identity and Access Management
Avviene quando alcuni utenti possiedono dei permessi troppo elevati (vale anche nel caso in cui alcuni utenti lascino il progetto e l'account non venga eliminato), o quando non viene gestito in maniera corretta il processo di iscrizione
### 3 - Dependency Chain Abuse
Avviene quando si scaricano #dependency non ufficiali. Per risolvere il problema, conviene sempre controllare i #chacksum (firma digitale del pacchetto), evitare di scaricare da internet se non dai siti ufficiali ed utilizzare in #pinning, ovvero specificando la versione specifica da utilizzare.
### 4 - Poisoned Pipeline Execution #PPE
Avviene quando un utente malevolo ottiene l'accesso ad una #pipeline presente online e la modifica.
### 5 - Insufficient #PBAC (Pipeline-Based Access Controls)
### 6 - Insufficient Credential Hygiene
Avviene quando sono presenti dei #secret in chiaro nella #pipeline. E' inoltre preferibile ruotare le credenziali in maniera costante (almeno 2 volte l'anno).
### 7 - Insecure System Configuration
### 8 - Improper Artifact Integrity Validation
Avviene quando non esiste un sistema di firma dei #commit. In questo caso è possibile che un attaccante riesca ad accedere all'account di uno sviluppatore ed immettere del codice malevolo all'interno del nostro progetto.
## Metodologie
### Modellare i dati
#### Data flow diagram
#### Sequence diagram
Usato per correlare i vari processi ad una variabile temporale di esecuzione
#### Process flow diagrams
Usato per visualizzare dei processi
#### Attack tree
Diagramma concettuale che mostra come un obbiettivo può essere attaccato
#### Ishikawa diagram (o Fishbone diagram)

### Goal oriented
#### DREAD
#### PASTA
#### trike

### Motivation oriented

### Library (o list) Oriented

#### STRIDE
Acronimo delle minacce su cui va ad operare:
spoofing: 
tampering: 
repudiation: Si nega l'aver effettuato una determinata azione
information-disclosure: Categoria che copre le violazioni di privacy o fughe di dati
DoS: Mira ad interrompere il normale funzionamento di un sito
privilege-escalation : L'attaccante accede con un profilo base e ottiene livelli di accesso superiori
E' il sistema con più ampia superficie di copertura per le potenziali minacce e/o vulnerabilità.
Alcune criticità di questa metodologia sono:
- La necessità di avere delle conoscenze approfondite sulle minacce e vulnerabilità, su cui applicare il metodo
##### Fasi
1. Si costruisce un data-flow-diagram, dove identifico le linee di fiducia
2. Si effettua una verifica per le varie categorie di attacco
3. Si analizzano i risultati e si pianificano le risposte
4. Si verifica l'efficacia delle risposte
## Requisiti
### Funzionali
### Non funzionali
Definiscono gli aspetti qualitativi e prestazionali
### Di sicurezza
#### Fondamentali
#### Generali
#### Operativi
## Crittografia
Può essere utilizzata per garantire:
- Confidenzialità
- Integrità
### Simmetrica
C'è una sola chiave di criptazione
#### Pro
- Efficienza
- Semplicità
- 
#### Contro
- Gestione delle chiavi
- Scalabilità
- Scambio delle chiavi
### Asimmetrica
Avviene tramite l'utilizzo di una chiave pubblica e di una chiave privata
#### Pro
- Maggiore sicurezza
- Firma digitale
- Scalabilità
#### Contro
- Prestazioni
- Complessità 

# Attacco
## Introduzione
Un attacco informatico è un’azione che sfrutta determinate falle (fisiche o logiche) di una rete per ottenere accesso e/o eseguire azioni dannose per la rete stessa. Principalmente gli attacchi sono di due tipi:
- APT (Minacce Persistenti Avanzate) sono attacchi elaborati eseguiti a ripetizione (come il [DoS](#DoS)), effettuati di solito per analizzare o ottenere l’accesso ad una rete bersaglio. Questo tipo di attacchi di solito richiede una forte organizzazione e alte risorse economiche per essere effettuato
- Attacchi Algoritmici, ovvero attacchi che sfruttano falle logiche o usano in maniera non convenzionale determinati componenti, per causare comportamenti non previsti alla macchina (es. la forzatura dell’uso totale della RAM per forzare l’arresto di un computer).

Gli attacchi possono essere differenziati per **domini** di interesse e per **livelli** di comunicazione (di solito viene utilizzato il modello OSI) soggetti all’attacco. Un terzo metodo di categorizzazione degli attacchi è la motivazione alle loro spalle. Per quest’ultimo caso, esiste una classificazione standardizzata: la IOA (Indicatore d’attacco).

## Dominio
Descrive l’area di controllo, autorità o protezione che l’attaccante vuole sfruttare per portare a compimento un attacco informatico.

## Tutti i livelli
### Spoofing
E' un attacco che può avvenire ad ogni livello della ISO-OSI e che consiste nella falsicifazione dell'identità e/o di altro tipo di informazioni applicative ([fonte](https://it.wikipedia.org/wiki/Spoofing)).

## Applicazione

### Broken Acess Authorization
Noto anche come**Broken access control** o **Privilege escalation**, è un attacco volto ad ottenere accesso a dati a cui non si sarebbe potuti accedere in condizioni normali (es. utente per un guest, o amministratore per un utente).
Può essere:
- **Horizontal Authorization Control**, quando si ottengono dati di altri utenti con privilegi simili (utente -> utente)
- **Vertical Authorization Control**, quando si ottiene accesso a dati visibili solo ad utenti con grado superiore (utente -> admin).
Questo tipo di attacco può essere prevenuto tramite:
- Definire una *policy* chiara che stabilisca permessi e limiti per tipologia di utente
- Testa la soluzione
- Utilizza un #framework che includa un sistema di autorizzazioni al suo interno
#### Horizontal Authorization Control
Vulnerabilità sfruttabile tramite attacchi #idor (Insecure Direct Object References)
``` 
http://vulnerableapp.com/user/account?accountId=7800001
	L'utente accede al sito tramite account personale

http://vulnerableapp.com/user/account?accountId=7800002
	Modificando l'URI, può accedere alle informazioni dell'account con ID diverso
```
#### Vertical Authorization Control
Permettono di accedere al controllo di funzioni e/o dati disponibili solo ad un utente avente maggiori permessi
### Broken Cryptography
Utilizzo di un #algoritmo di crittografia debole o già rotto in precedenza.
Algoritmi considerati non sicuri sono:
- #MD5
- #SHA-1
- #RIPEMD
- #RIPEMD-128
- #Whirlpool
Mentre, algoritmi considerati sicuri sono, ad esempio:
- #RIPEDM-160/256/320
- #BLAKE2/3
- #SHA-2
- #SHA-3
Mentre, per crittografare password, di norma si usano:
- #bcrypt
- #scrypt
- #argon2
- #PBKDF2
Per decidere quale algoritmo utilizzare occorre tener conto della complessità dello stesso (tempo di esecuzione) e dell'importanza del dato che si vuole proteggere
#### Come proteggersi dalla #broken-cryptography
- Non implementare algoritmi deprecati, preferisci quelli utilizzati dalla community e che rispettando gli standard
- Non usare chiavi con un Vettore di Inizializzazione
- Preferisci soluzioni di *management* delle chiavi collegate con il sistema operativo, hardware o cloud provider
- Fai revisionare le tue chiavi da un operatore terzo affidabile
- Mantieniti aggiornato sulle metodologie di criptazione più efficaci e su quelle deprecate
### Borken OAuth
La #broken-oauth è una particolare tipologia di #broken-authentication, che avviene qualora si utilizzi un processo di #oauth per effettuare il login.

### Buffer overflow
Avviene quando dei dati più grandi del previsto vengono memorizzati nel buffer. Questo processo può portare al crash del sistema, alla corruzione di alcuni dati, o all’installazione di malware all’interno di un dispositivo.

### CSRF
Il Cross-Site Request Forgery avviene quando un utente malintenzionato riesce ad eseguire comandi tramite il dispositivo di un utente bersaglio.
Di norma si attuano partendo da un attacco di #phishing per estrapolare i dati necessari, per poi effettuare l'accesso nell'account dell'utente
#### Prevenire
- Utilizzo di #token #anti-forgery (come il CSRF-token di #Laravel) per tutti i metodi che modificano lo stato dell'applicazione
- Double Submit Cookie Pattern (assegnare un valore casuale sia ad un cookie che ad un parametro della richiesta)
- Utilizzare l'attributo **SameSite** per evitare le richieste cross-domain
- Gestire correttamente #origin-header e #referrer-header
- Utilizzare la #re-autentication
- Utilizzare token usa e getta
- Utilizzare tecnologia #captcha
### Directory traversal
Anche noto come Path traversal, consiste nella manipolazione del percorso di un sito web per leggere dati sensibili o eseguire file altrimenti protetti.

### Email

#### Attacco tramite allegati
Il malware viene inserito tra gli allegati della mail e, una volta scaricato, infetta il dispositivo versaglio.

#### Spoofing
L'attaccante invia una mail avente come mittente un indirizzo legittimo per invogliare l'utente a inviare denaro o compiere azioni che altrimenti non avrebbe compiuto.

#### Spam
L'attaccante invia email contenenti pubblicità o file malevoli. Di solito contengono un messaggio che invoglia una risposta da parte dell'utente.

#### Server aperti di inoltro di posta
I server aperti di inoltro di posta (Open mail relay server) sono server pubblici (o server aziendali configurati in maniera errata) che lavorano con il protocollo [SMTP](./tecnologie/protocolli#smtp). Possono essere sfruttati da un attaccante per inoltrare messaggi di spam in grande quantità o inviare mail contenenti malware.  

#### Attacco omografico
L'[attacco omografico](https://it.wikipedia.org/wiki/Attacco_omografico) consiste nell'utilizzo di indirizzi URL simili ad altri indirizzi noti, utilizzando caratteri simili per confondere l'utente e fargli credere di essere i siti legittimi. Possono esser utilizzati numeri o caratteri di alfabeti diversi (come il greco o il cirillico). Esempi di siti omografici possono essere:

| Sito reale       | Sito omografico                                                                                       |
| ---------------- | ----------------------------------------------------------------------------------------------------- |
| www.google.com   | www.g0ogle.com                                                                                        |
| www.facebook.com | www.fаcebook.com (in questo caso il carattere "a" è stato sostituito con "а" dell'alfabeto cirillico) |

### Error handling
Utilizzo dei messaggi di errore per estrarre dati sensibili.


### HTTP
#### Introduzione
Gli attacchi che sfruttano il protocollo HTTP, di solito seguono i seguenti passaggi:
1. L'utente visita una pagina compromessa
2. La pagina compromessa reindirizza l'utente verso uno o più server compromessi
3. Il server invia un explolit kit (di solito uno script in PHP) per analizzare il dispositivo dell'utente e cercare eventuali vulnerablilità e fornire una console di controllo all'attaccante per gestire l'attacco
4. Dopo aver effettuato la scansione e aver trovato delle vulnerabilità, l'exploit kit invia il resoconto al server e richiede l'invio di codice malevolo che possa sfruttarle
5. Il dispositivo è compromesso e si connette ad un Malware Server per scaricare il payload (che può essere un Malware, o un file di download di altri malware)
6. Il Malware viene eseguito nel dispositivo dell'utente
Tramite la lettura del log dello storico delle chiamate HTTP, è possibile comprendere la dinamica dell'attacco, facendo riferimento ai [codici di stato del messaggio](<./tecnologie/protocolli#http#status code>). Altre precauzioni da utilizzare per proteggersi da questo tipo di attacchi sono:
- Tenere sempre aggiornato il sistema operativo ed il browser
- Utilizzare un Web Proxy come Cisco Cloud Web Security o Cisco Web Security Appliance per bloccare siti malevoli
- Utilizzare software come Cisco Umbrella per prevenire la navigazione verso siti malevoli conosciuti
- Tenersi aggiornati riguardo le *best practices* dell'[OWASP](#owasp) durante lo sviluppo delle applicazioni web
- Educare gli utenti mostrandogli come evitare gli attacchi web-based.

#### iFrame malevoli
Gli [iFrame](./linguaggi/html#iframe) sono comunemente utilizzati per inserire pubblicità all'interno di un sito web. E' tuttavia possibile utilizzare gli iframe per infettare un sito e collegarlo ad un sito malevolo, che potrà eseguire del codice in background, far visualizzare pubblicità spam, eseguire degli [exploit kit],  sul dispositivo dell'utente. Di solito in questi casi, si minimizzano le dimensioni dell'iframe, in modo tale che l'utente non possa identificarlo con facilità.

#### HTTP 302 Cushioning
Consiste nello sfruttare il [codice di reindirizzamento 302](<./tecnologie/protocolli#status code>) per reindirizzare in maniera lecita verso un server malevolo (tramite l'url sostitutivo presente nel messaggio). Il reindirizzamento può anche essere effettuato più volte prima di arrivare al sito malevolo.

#### Domain shadowing
L'attaccante prepara un dominio compromesso (tramite [sabotaggio](#hijacking) di un dominio legittimo) e molteplici sottodomini che serviranno per eseguire l'attacco. L'utilità dei sottodomini consiste nel 
la facilità di rimozione e replicazione nel caso vengano scoperti. Di soolito questo attacco segue la seguente procedura:
1. L'attaccante compromette un sito web legittimo
2. collega il sito ai siti malevoli tramite messaggio 302
3. viene utilizzato il Domain Shadowing per reindirizzare l'utente verso i server malevoli
4. I server malevoli eseguono un [exploit kit] sul dispositivo dell'utente
5. Il malware viene scaricato sul dispositivo dell'utente

### Injection
Attacco che si basa sull'inserire stringhe di codice malevolo. Può essere effettuato sul database, sul sistema operativo, o comunque in qualunque ambiente che accetti input per l'invio di comandi da eseguire.

#### DLL
Iniezione di codice all’interno di un file in formato Dynamic Link Library (libreria dinamica dei link, **.dll**). Questo permette di implementare funzionalità non previste all’interno del sistema operativo.

#### LDAP
Sfrutta delle vulnerabilità della lettura input del protocollo LDAP (protocollo leggero di accesso alla directory) per ottenere l’accesso ai server LDAP e ottenere dati sensibili.

#### SQL
Sono delle categorie di vulnerabilità che si verificano quando un'applicazione accetta dati non fidati da una fonte esterna, come input utente. L'attaccante inserisce o modifica dei dati nel database. E' l'attacco più semplice, così come quello che può causare i danni più gravi. Ci sono varie tipologie di #sql-injection:
##### Tipologie di attacco
###### Classic SQLi
###### Blind SQLi
Avviene quando il risultato della *query*di manipolazione non è visibile all' #attaccante
###### Time-Based SQLi
###### Error-Based SQLi
###### Union-Based SQLi
Tramite tag input, permette di manipolare il database leggendo ed inserendo dati tramite comandi come:
```
'union select col_1,col_2,[comando]# 
```
dove:
- **'** viene utilizzato per chiudere la stringa che esegue l'operazione (di default '% %' )
- **union** unisce i comandi successivi
- **select** permette di selezionare tutte le colonne della tabella da cui vengono letti i dati
- **col_1** rappresenta il primo dato della tabella
- **comando** rappresenta la colonna in cui verranno inseriti i comandi necessari per capire la struttura, il #dms , la versione ecc. del database utilizzato per il sito
- **#** Viene usato per commentare la parte finale del comando originale 
##### Difendersi dalla SQL Injection 
E' possibile difendersi dalle #sql-injection tramite:
- Effettuare backups
- Utilizzare comandi predefiniti per accedere al database e successivamente passare i parametri (*best practice*)
- Lista di validazione dei comandi
- Lista di diniego (non molto efficace)
- Utilizzo di Store Procedures (stringhe predefinite di codice per interagire con il database) (non efficace con tutte le tipologie di SQl  attack)
- Usare un WAF (Web Application Firewall)
- Utilizzare dei #framework dotati di un #ORM
#### XML
Modifica di un file o una query XML all’interno di un sito web.

### Identification and Authentication Failures
Precedentemente identificato come #broken-authentication, che indica quando un #attaccante impersona un altro utente per compiere azioni al suo posto. Possono essere causate da:
- Controlli di autenticazione insufficienti
- Rottura dei meccanismi di protezione a livello dell'Oggetto
- #session-fixation
- #broken-credential-management
#### Session-fixation
Attacco che permette all' #attaccante di dirottare dei dati validi di autenticazione. In particolare sfrutta l'eventuale mancanza di creazione di un nuovo #session-id in fase di login, per riutilizzare una vecchia sessione (effettuata da un altro utente) ed operare al sotto il suo nome.
Il #session-id è un token, implementabile tramite #cookie o nell' #URL del sito.
#### Broken credential management
- #credential-stuffing
- #brute-force attacks, ovvero provare ad accedere ad un account tentando forzatamente con un numero massivo di password
- #password-spraying (ovvero tentare di accedere a molti account con delle password standard).
##### Evitare attacchi Broken credential management
- Usa #framework di autenticazione open-source famosi
- Testa la correttezza dei meccanismi progettati
- Ruota e invalida i #session-id 
- Non permettere l'utilizzo di password deboli o molto usate
- Utilizza l'autenticazione a più fattori ( #mfa)
- Implementa meccanismi di blocco accesso dopo tentativi multipli di login con password errata
- Utilizzo di #bastion-host o liste di ammissione per #IP
- 
#### Mass assignment
Può avvenire quando vengono utilizzate funzioni che selezionino in massa i campi dati dal database (es. **all()**, o quando vengono inclusi tutti i campi nei #fillable su #Laravel)
#### [Credential stuffing]( #credential-stuffing)
Uso improprio di elenchi di password note (es rockyou.txt) per provare a loggarsi
#### [Persistent session]( #persistent-session)
Sfutta il salvataggio dei token di autenticazione da una sessione precedente (di un altro utente) per accedere.
### Improper input handling
Avviene quando un input non viene convalidato propriamente. Può portare ad attacchi di injection o buffer overflow.
### Inadequate Input validation
La non adeguata predisposizione delle validazioni input (sia lato #client che #server) può portare a severi danni, in particolare se effettuato per transizioni economiche.
#### Prevenzione
- Tratta tutti i dati come non affidabili
- Assicurati che i meccanismi di validazioni siano impostati correttamente
- Utilizza una lista predefinita di input quando possibile
- Non inserire direttamente l'input nel database 
### Insecurity Functionality Exposed
Debolezza che si presenta quando alcune funzioni, inserite inizialmente per velocizzare alcuni compiti in fase di sviluppo, non vengono eliminate prima del deploy. 
### Insufficient Logging & Monitoring
Categoria ampia, che comprende in generale tutte le debolezze derivate dalla mancata registrazione ( #log) delle azioni compiute dagli utenti, ad esempio:
- Configurazione errata del Security Information and Event Management ( #SIEM)
- Scansioni di sicurezza non presenti, o predisposte in maniera errata
- Una loro non corretta lettura ( #monitoring) dei dati di #log da parte degli specialisti.
Per risolvere questo problema, conviene:
- Fare riferimento a protocolli certificati, come l'[Health Insurance Portability and Accountability Act ](https://www.hhs.gov/hipaa/for-professionals/security/guidance/cybersecurity/index.html) ( #HIPAA), il [Payment Card Industry Data Security Standard]( https://www.pcisecuritystandards.org/)( #PCI-DSS) o il #Sarbanes-Oxley
- Assicurare un #log verificabile, effettivo, centralizzato e con un adeguata ridondanza di:
	- Errori di validazione degli input
	- Autenticazioni
	- Errori di applicazione e/o di sistema
	- Problemi di connessione
	- Rilevamento di caricamento file, alterazioni della configurazione, errori dei file di sistema
	- Operazioni ad alto rischio (movimenti bancari es.)

### Phishing
Utilizzo di messaggi o mail ingannevoli per indurre l’utente a cliccare a link inseriti all’interno, che reindirizzano a siti malevoli.

#### Pharming
Dirottamento dell’utente ad un sito copia del sito desiderato per fargli fare un supposto accesso e leggere i dati di autenticazione.

#### SMiShing
Utilizzo di SMS per condurre un attacco phishing per far aprir un sito malevolo o una chiamata con l’attaccante.

#### Vishing
Phishing effettuato tramite chiamate vocali.

#### Whaling
Phishing su obiettivi di rilievo.

### Race condition attack
Avviene quando un sistema computazionale viene forzato ad eseguire contemporaneamente due o più operazioni (che possono mirare allo stesso dato, portando ad una sua duplice modifica) contemporaneamente.

### Remote code execution
Permette all’attaccante di eseguire linee di codice con privilegi di amministratore, sfruttando le vulnerabilità di un’applicazione.

### Replay
Intercettazione e conseguente ripetizione o blocco temporaneo dei dati inviati da un’utente ad un server, con lo scopo di indirizzare le azioni dell’utente verso i propri scopi.

### Resource exhaustion
Consiste nell’inondare un dispositivo di dati per causarne il crash, blocco temporaneo o danni alle componenti hardware.

### Security logging e Monitoring failures
Di solito si scopre solo durante i #penetration-test o tramite discussioni con gli sviluppatori. Da ciò ne consegue che è difficile da identificare. In generale le cause possono essere:
- Eventi verificabili non registrati
- Avvisi di errore senza messaggi di #log
- I registri delle applicazioni non vengono monitorati
- Archiviazione dei registri solo in locale
- Soglie di allerta e processi di #escalation non calibrati correttamente
- #penetration-test e scansioni non attivano gli avvisi
- L'applicazione non è in grado id identificare gli attacchi in tempo reale
- Gli avvisi sono visibili anche all'utente e/o all'aggressore
#### Prevenzione
- Registrazione di tutti gli errori di #login, controllo degli accessi e #convalida degli input
- I #log devono essere registrati in un formato facilmente utilizzabile
- I #log devono essere codificati correttamente per evitare  #injection 
- Le #transazioni di alto valore devono avere un #audit trail con controlli d' #integrità
- Il team #DevSevOps deve stabilire un monitoraggio efficace
- Stabilire e adottare un piano di risposta e ripristino
### Security Misconfiguration
Sono delle configurazioni fallaci, dovute all'errore umano durante la fase di scrittura del codice (dell'applicazione stessa, del framework o altro). Alcuni esempi sono:
- ***Features*** ridondanti abilitate
- Account con user e password di default
- ***Features*** di sicurezza disabilitate o non configurate correttamente
- Software datati
- Utilizzo di password deboli o prevedibili
- Mancanza (o configurazione errata) di Security Headers
- #directory-listing non disabilitate (pagine dalle quali è possibile vedere la struttura dell'app)
- Applicazioni lasciate dalla fase di sviluppo 
#### Evitare le Security Misconfiguration
Alcune note per evitare questi errori sono:
- Implementare procedure ripetibili e sicure di installazione
- Rimuovere le features non necessarie
- Configurare e tenere aggiornate le #patch nello stack
- Automatizzare le procedure quando fattibile
- Assicurare la corretta #configurazione e #deploy dei Security Header
- Frammenta l'architettura dell'applicazione
### Software and Data Integrity Failures
Si concentra sulla formulazione di ipotesi relative agli aggiornamenti del software, ai dati critici e alle pipeline #CI/CD (Continuous Implementation/Continuous Deployment) senza verificarne l'integrità. E' uno dei maggiori impatti #CVE e #CVSS. Si verifica quando:
- Ci si affida a plugin da fonti non attendibili
- La #pipeline non è sicura e permette accessi non autorizzati o l'inserimento di codice maligno
- Le funzionalità di aggiornamento non verificano l'integrità dello stesso
- I dati sono [codificati] o [serializzati] in modo che l'aggressore possa vedere e/o modificarli. 
#### Prevenzione
- Utilizzo di firme digitali
-  Utilizzo di #repository affidabili
- Utilizzo di software appositi (OWASP Dependency Check)
- Processo di revisione efficace delle modifiche del codice
- La #pipeline CI/CD ha un'adeguata segregazione
- I dati serializzati non firmati o non crittografati non vengano inviati al #client
### SSRF
La Server Site Request Forgery avviene quando una richiesta di input lato #server non avviene adeguatamente monitorata (spesso quando viene effettuata una #richiesta HTTP ad un sito di #terze-parti). Spesso avvengono sfruttando la fiducia tra due applicazioni durante lo scambio di dati tramite richieste #API o lo scambio di file e/o pacchetti per compiere azioni malevole contro il server dei soggetti terzi con cui avviene lo scambio, o contro il server stesso che compie la richiesta, ad esempio tramite i protocolli:
- file://
- TCP
#### Precauzioni contro l'SSRF
- Implementare una lista di indirizzi autorizzati (quando possibile)
- Disabilitare Schemi URL inutilizzati
- Non consegnare risposte raw da richieste del server
- Ridurre al minimo la fiducia del server confugurando correttamente delle regole limite del #firewall
### Type juggling
Durante il confronto tra una stringa e un numero, #PhP  tenta di convertire la stringa in un numero. Se la stringa non può essere convertita in un numero valido, viene automaticamente convertita nel valore 0.
```
var_dump("password" == 0); //true
```
Si può ovviare al problema utilizzando lo #strict-comparison-operator ===
### Unsafe Deserialization
La #serializzazione è il processo di conversione dello stato di un oggetto o una struttura dati in un formato memorizzabile o trasferibile. La #deserializzazione è il processo inverso. 
#### Prevenire la unsafe deserialization
- Utilizza formati di dati semplici ovunque possibile
- Usa modelli di serializzazione che usino solo #dati-primitivi 
- Usa modelli di serializzazione che permettano la crittazione e la decrittazione dei dati in maniera sicura
- Sostituisci la serializzazione dei dati con formati di solo dati, come il JSON
### Vulnerable and Outdated Components
L'utilizzo di framework, sistemi operativi, software o componenti vulnerabili e/o datati possono creare dei punti critici di debolezza del nostro sito. E' possibile avere delle debolezze dovute a:
- Mancata conoscenza di tutti o componenti utilizzati
- Carente informazione e aggiornamento sulle ultime novità dei vari pacchetti
- Mancato aggiornamento della piattaforma
- Testing carente o assente della compatibilità a seguito di patch
#### Soluzioni
- Eliminare le dipendenze inutilizzate
- Inventariare continuamente le versioni dei componenti lato client e server
- Monitorare costantemente fonti come [Common Vulnerability and Exposures] e [National Vulnerability Database]
- Utilizzare strumenti di analisi della composizione del software
- Monitorare le librerie e i componenti non manutenuti
- Preferire componenti con firma digitale (sicurezza di integrità) 
- Utilizzo di software di controllo per lo stato di aggiornamento delle dependencies (es. OWASP Dependencies Check)
### XML Entity Expansion
#xml è un formato testuale utilizzato per rappresentare informazioni strutturate. 
Tramite attacchi #XEE è possibile:
- vedere file nel server
```
POST http://www.vulnerableapp.com/xml HTTP/1.1

<?xml version="1.0" encoding="ISO-8859-1"?> 
<!DOCTYPE foo [
  <!ELEMENT foo ANY>
  <!ENTITY xxe SYSTEM
  "file:///etc/passwd">
]>
<foo>
  &xxe;
</foo>
```
- effettuare attacchi [Server-Side Request Forgery]( #SSRF)
```
POST http://www.vulnerableapp.com/xml HTTP/1.1

<?xml version="1.0" encoding="ISO-8859-1"?> 
<!DOCTYPE foo [
  <!ELEMENT foo ANY>
  <!ENTITY xxe SYSTEM
  "http://internal.vulnerableapp.com:8443">
]>
<foo>
  &xxe;
</foo>
```
- effettuare attacchi #DoS tramite il #nesting multiplo di entità come **&lt** e **&gt**, che rappresentano i caratteri **<** e **>**:
```
POST http://www.vulnerableapp.com/xml HTTP/1.1<?xml version="1.0" encoding="ISO-8859-1"?> 
<!DOCTYPE foo [
  <!ELEMENT foo ANY>
  <!ENTITY bar "SecureFlag ">
  <!ENTITY t1 "&bar;&bar;">
  <!ENTITY t2 "&t1;&t1;&t1;&t1;">
  <!ENTITY t3 "&t2;&t2;&t2;&t2;&t2;">
]>
<foo>
  Join &t3;
</foo>
```

#### Prevenzione
- Disabilitando la funzione Document Type Definition ( #DTD)
	```
	 disable_external_entities(true)
	 ```
- Gestire dati in formati semplici (es. #JSON )
- Verificare in ambiente di #testing che le chiamate #xml abbiano le dovute restrizioni

### XSS
Il Cross-Site scripting (invio di stringhe di esecuzione attraverso i siti) si riferisce all'utilizzo di script per manipolare le interazioni tra utente e sito web.

#### Reflected XSS
Viene utilizzato un link per far inviare all'utente colpito un codice malevolo per colpire il server del sito. Possono essere inviati, ad esempio, tramite siti malevoli o mail
#### Stored XSS
Lo script viene memorizzato in una pagina del sito e quindi riprodotto ogni volta che viene richiamata la pagina stessa (anche su utenti diversi)

#### DOM-based XSS
Blocchi di codice #JavaScript (quindi non controllabili tramite #csrf-token)
#### Prevenzione
- Preferire l'utilizzi di #whitelist alle #blacklist anche per le #input-validation
- Output encoding
- Content Security Policy
- utilizzare un framework moderno
- in #PhP usare funzioni htmlentities() e htmlspecialchars() per effettuare l' #escaping delle variabili
- Utilizzare un implementazione IPS per identificare e prevenire scipt malevoli
- Utilizzare un Web Proxy per bloccare siti malevoli

## Presentazione
## Sessione
### Session Hijacking

## Trasporto
### TCP SYN Flood
L’attaccante effettua ripetutamente chiamate di richiesta di sincronizzazione al server bersaglio che, rispondendo a tutte le chiamate con un messaggio ACK, non riesce a rispondere in tempo alle chiamate legittime di SYN.

### TCP Reset attack
Viene inviato un segnale RST (reset) al server utilizzando l'indirizzo IP dell'obbiettivo ([spoofing](#spoofing)) per resettare la comuniucazione in corso. Questo attacco può condurre a successivi attacchi di tipo [session hijacking](<#session hijacking>).

### UDP flood attack
Ha come obiettivo il blocco della rete a causa delle troppe richieste da elaborare. Di solito l'attaccante utilizza tool come [UDP Unicorn] o [Low Orbit Ion Cannon] per preparare i pacchetti e automatizzarne l'invio. Il risultato è un attacco di tipo [DoS](#dos).

## Rete

### ARP
#### ARP Cache poisoning
Attacco che può essere utilizzato per gettare le basi per un [Man in the middle](#man-in-the-middle) e consiste nel sostituirsi ad un altro dispositivo ad una [ARP request](./Tecnologie/Protocolli#ARP)

### ICMP
Consiste nel pingare pacchetti echo agli host di una rete per scoprirne l’architettura (sotto reti e host connessi). È possibile effettuare questa operazione ripetutamente in poco tempo per inondare la rete (flood) di messaggi da gestire e rallentarla (DoS).

I messaggi inviati possono essere di vario tipo:
- Echo request e reply nel caso si voglia effettuare un attacco DoS. Nel caso si effettui anche lo spoofing mirato, è possibile inondare di richieste un dispositivo bersaglio
- Unreachable per riconoscere e scansionare reti
- Mask reply nel caso si vogliano mappre gli indirizzi IP di una rete
- Redirect per reindirizzare il traffico verso l’attaccante ed effettuare un MItM
- Router discovery per inserire indirizzi IP falsificati all’interno della tabella di routing


### IP
#### IP Spoofing
Falsificazione di un indirizzo IP in maniera mirata (se si conosce l’indirizzo che si sta falsificando) o alla cieca (in caso contrario).

### DHCP
Vedi [protocollo DHCP](./tecnologie/protocolli#dhcp)
#### DHCP Spoofing
Di solito consiste nel fornire un indirizzo IP falso relativo al Default Gateway o al Server DNS (anche se potenzialmente qualunque indirizzo IP può essere contraffatto), seguendo i seguenti passaggi:
1. Il Client invia un messaggio DHCP Discovery (che viene ascoltato anche dall'attaccante)
2. Il Server DHCP e l'attaccante rispondono con un messaggio DHCP Offer (il Client risponderà solo alla prima risposta ricevuta)
3. Nel caso la prima risposta venga inviata dall'attaccante, invierà un DCHP Request in broadcast, che non verrà accettata dal Server DHCP in quanto la richiesta é già stata accettata da un altro Server DHCP (l'atatccante)
4. L'attaccante invia un DHCP ACK al Client, completando l'attacco di **spoofing** e sostituendosi al Server DHCP

#### DHCP Starvation attack
Consiste nel sostituirsi al Server DHCP e impedire agli utenti di utilizzare il protocollo DHCP per richiedere un indirizzo IP privato.

### DNS
Gli attacchi che sfruttano il protocollo [DNS](./Tecnologie/Protocolli#dns) possono avvenire tramite:
- Sfruttando gli Open Resolver (indirizzi IP pubblici che vengono utilizzati per cercare informazioni, tipo Google)
#### DNS cache poisoning
Consiste nell'invio di risorse falsificate ([spoofing](#spoofing)) ad un DNS Resolver per reindirizzare l'utente verso siti malevoli

#### DNS Amplification and reflection attack
Utilizzo di attacchi [DoS](#dos) o [DDoS](#ddos) ad un Open Resolver per nascondere la vera fonte dell'attacco tramite l'invio di open resolver  per aumentare il volume dell'attacco.

#### DNS Resource utilization attack
Consiste in un attacco di tipo [DoS](#dos) per sovraffollare il server di richieste per resettare il server.

#### DNS Stealth Attacks
Sono metodologie utilizzate per nascondere la propria identità al bersaglio.

##### Fast flux
Tecnica utilizzata per nascondere i siti di invio di malware e [phishing](#phishing) al bersaglio. Di solito avvengono tramite il cambio rapido di indirizzo DNS tra  una lista di indirizzi compromessi. Questo tipo di attacchi è utilizzato spesso dai Botnet.

##### Double IP flux
L'attaccante modifica velocemente sia l'hostname (in base ad un pool di indirizzi IP) che il [nome autoritativo del server](https://en.wikipedia.org/wiki/Name_server#:~:text=An%20authoritative%20name%20server%20is,specifically%20configured%20by%20its%20administrator).

##### Domain generation algorithms
Tecnica utilizzata dai malware per generare automaticamente nomi di dominio che possono essere utilizzati come punti di accesso per i [server di comando e controllo](https://nordvpn.com/cybersecurity/glossary/cc-server/).


#### DNS Tunneling
Consiste nell'incanalare reti all'interno di un unico nome di dominio, in modo tale da utilizzare le varie sottoreti per inviare malware ed aggirare alcuni meccanismi di protezione dei firewall e/o alterare alcuni [campi del pacchetto](./tecnologie/protocolli#dns#pacchetto) (come TXT, MX, SRV, NULL, A, o CNAME). Un esempio di attuazione di tunneling è il seguente:
1. Il dato (comandi di esecuzione) viene frammentato e cifrato
2. Ogni frammento è inserito all'interno di un sottodominio della richiesta DNS
3. Non ricevendo alcuna risposta dalla rete, a seguito della query DNS, la richiesta viene inoltrata al Server ricorsivo DNS dell'ISP
4. L'ISP inoltra la richiesta ai vari server dell'attaccante
5. Il processo si ripete fin quando tutte le queries non vengono risolte e tutti i vari frammenti sono stati inviati
6. I frammenti vengono raccolti dal server autoritativo, che invia le risposte a tutte le richieste DNS ricevute
7. Il malware ricompone i messaggi, legge ed esegue il comando.

## Collegamento
Gli attacchi più comuni al [livello 2 - Collegamento](<Tecnologie/protocolli#2 - Collegamento>) (o data-link) della pila ISO/osi sono:
### Spoofing
Utilizzo di credenziali falsificate durante la comunicazione con altri dispositivi relativamente a:
- MAC
- IP

### MAC Flooding
Invio massivo di richieste alla rete con lo scopo di rallentarla o bloccarla.

## Fisico

## Social Engineering
Macro categoria di attacco informatico, che consiste nell’ottenere informazioni e/o accesso ai sistemi informatici attraverso l’inganno di persone che lavorano all’interno dell’azienda oggetto dell’attacco. Gli attacchi sfruttano strategie ne si basano su concetti psicologico come:
- Autorità
- Intimidazione
- Consenzo
- Sicurezza
- Urgenza
- Familiarità 
- Fiducia

Le tipologie principali di social engineering sono:

### Frode
Utilizzo di identità falsa per ottenere credibilità durante il processo di richiesta di informazioni.

### Quid-pro-quo
Scambio di favori in cambio di informazioni.

### Pretexting
Consiste nell’utilizzo di menzogne o pretesti per ottenere informazioni.


## WLAN
Gli attacchi verso una rete [WLAN](./tecnologie/reti#wlan) hanno lo scopo di:
- Intercettare dati
- Ottenere accesso a risorse all'interno della rete
- effettuare attacchi [DoS](#dos) per compromettere l'accesso alla rete stessa
- Inserimento di AP falsi (Rogue Access Point)


## Altri tipi di attacchi
- supply chain
### Adversial artificial intelligence attack
Consiste nell’inserire dati di input volutamente errati all’interno di un modello di AI per falsificarne i risultati.

###  Cloud-based attack
Attacchi che sfruttano la struttura cloud di una rete aziendale per 

### Bluesnarfing
Connessione con un dispositivo bersaglio con conseguente furto di dati personali (come mail e lista dei contatti).
### Bomba logica
Programma malevolo che rimane inattiva fino alla realizzazione del trigger desiderato. Una bomba logica può causare danni logici (eliminazione di file o alterazione del database) o fisici (es. mandare in overload ventole o CPU)

### Bufale
Creazione di contenuti informativi falsi e/o fuorvianti per ottenere informazioni o per minare la credibilità del bersaglio. Questo attacco può anche presentarsi organizzato in vere e proprie campagne.

### Injection
La Code injection consiste nell’immissione di stringhe di codice all’interno di 
### DOS
Il Denial Of Service è un attacco che sfrutta una script o altri metodi per sovraccaricare il #server bersaglio ed impedirne il normale funzionamento per un determinato periodo di tempo

#### DDOS
Il Distributed Denial of Service è un’evoluzione del #dos, ma utilizza più macchine per portare a termine l'attacco.

### Dumpster diving
Ottenere informazioni tramite controllo dei rifiuti prodotti dai dipendenti dell’azienda.

### False Fatture
Uso di false fatture per ricevere denaro o informazioni sensibili.

### Grayware
Presenza di applicazione non desiderata all’interno del dispositivo (che può come può non contenere malware)

### Hijacking
Dirottamento, ovvero accesso ad un dispositivo con successiva modifica delle credenziali, al fine di bloccare l’accesso del legittimo proprietario.

### Bluejacking
Hijacking di un dispositivo tramite connessione Bluetooth. L’accesso alla connessione bluetooth può avvenire grazie al range operativo ristretto della connessione Bluetooth.

### DNS
Il Dirottamento avviene quando un attaccante ottiene l’accesso all’account admin di un server, con successiva modifica delle credenziali (rendendo impossibile l’accesso all’utente proprietario). In questo modo l’attaccante può modificare l’ip di riferimento del DNS verso un sito malevolo. 

### Impersonamento
Pretendere di essere un’altra persona per poter chiedere (sfruttando i principi di autorità o fiducia) informazioni.

### Keyboard logging
Consiste nella lettura di tutti gli input immessi tramite tastiera tramite software.

### Malware
I malware sono software malevoli che hanno come scopo arrecare danno all'utente bersaglio. 
Questi possono essere installati nel dispositivo in vari modi:
- Download di antivirus da pop-up (o comunque da siti che siano diversi dal sito originale). Il software potrebbe essere stato alterato per contenere malware
- Malware *fileless*, che si attivano all'avvio del Sistema operativo per poi disattivarsi al suo spegnimento
- Script dannosi (indipendentemente dal linguaggio utilizzato)
- Installazione non intenzionale di software di terze parti infettati
#### Trojan
Malware che effettua operazioni malevole, mascherandole all’interno di un file legittimo modificato. I file su cui viene caricato il malware sono spesso di tipo non eseguibile.

#### Virus
Software che, una volta eseguito, si replica all’interno del pc e inserisce il proprio codice all’interno di altri file, periferiche o dispositivi connessi alla stessa LAN. Un virus può essere anche innocuo, così come distruttivo per un pc (può ad esempio cancellare file).
È possibile che un virus cambi la sua struttura per essere più difficile da identificare.

#### Worm
Software malevolo che si duplica all’interno del pc infettato. A differenza del virus, non deve essere attivato da un altro software e si espande sfruttando vulnerabilità del sistema operativo e/o della rete con l’obiettivo di rallentare il dispositivo o la rete stessa.

### Man-in-the-middle
Consiste nel frapporsi tra un client ed un server per rubare e/o modificare informazioni durante il loro traporto.

### Piggyback
Noto anche come Tailgating, consiste nel seguire a breve distanza una persona con permessi di accesso fisico in aree protette al fine di bypassare i controlli.

### Prepending
Sostituzione del tag “esterno” all’azienda con uno interno all’azienda per far credere che sia stata inviata dall’interno dell’ambiente aziendale.

### Jamming
Manomissione di strumenti di trasmissione o dati.

### Frequenze radio
Utilizzo di impulsi elettromagnetici per disturbare le frequenze radio di una connessione, di fatto interrompendola.

### Ransomware
Malware utilizzato con il particolare scopo di impedire all’utente attaccato di visualizzare/utilizzare i file del proprio pc (tramite cifratura o furto dei file), per chiedere un riscatto come condizione per il riottenimento dei dati.

### Reindirizzamento
Reindirizzamento automatico dell’url (tramite parametri specifici all’interno dell’url utilizzato) verso un sito malevolo.

### Rogue access point
Installazione di un punto di accesso wireless non desiderato all’interno di una rete, che ne permetta l’utilizzo senza autenticazione. Questo attacco facilita l’utilizzo di attacchi all’interno della rete (come il [Man-in-the-middle](#man-in-the-middle)).

### Evil-twin
Creazione di una rete temporanea, avente nome simile ad una rete esistente con l’obiettivo di indurre utenti a connettersi per avere accesso al loro traffico.

### Shoulder surfing
Consiste nel visualizzare l’inserimento di informazioni confidenziali (pin, password) durante l’immissione.

### Spoofing

### DNS
Falsificazione dei dati all’interno dei Server DNS per reindirizzare gli utenti finali verso siti con contenuto malevolo.

### Typo squatting
Utilizzo di URL simili a siti reali per la colmatura dei siti originali con intenti malevoli, sfruttando la possibilità che utenti ci entrino non intenzionalmente.

### Watering Hole Attack
Inserimenti di malware (almeno) uno dei siti più utilizzati dal bersaglio

### XSS
Il Cross-site Scripting consiste nell’ inserire codice malevolo all’interno di un sito web, che andrà successivamente ad infettare i dispositivi degli utenti che visitano il sito infettato. Di solito ha l’obiettivo di leggere dati di accesso e/o cookies al fine di poter impersonare l’utente.
### Zero-day
Attacco che avviene sfruttando vulnerabilità deep software non ancora note pubblicamente.

# Vulnerability
# Weakness
Le **Debolezze** sono tutti quegli attacchi (conosciuti e non) che possono essere effettuati, sfruttando le **[vulnerabilità](#vulnerability)**

## Improper Restriction of XML external entity Reference
[Improper Restriction of XML external entity Reference](https://cwe.mitre.org/data/definitions/611.html).

Si verifica quando un entità XML contiene collegamenti ad altre entità XML non previste dal sistema, che permettono di inserire script malevoli per prelevare dati.

# Strumenti di analisi
## Software
###  Static application security testing
#SAST
[[SonarQube]]
Software che effettuano un'analisi statica del codice, effettuano #code-smell (verifica l'utilizzo anomalo di alcuni elementi)
### Dynamic application security testing
#DAST
[[Zap]]
Verificano la presenza di vulnerabilità tentando degli #attacco. Per questo motivo è consigliato creare un'ambiente dedicato al testing per questi tool.
### Software composition analysis
#SCA
[[snyk]], [[aqua trivy]]
Effettuano analisi delle #dependency del codice e/o dei container, tramite verifica nel CVE di vulnerabilità e patch.
#### [Dependency check](https://github.com/jeremylong/DependencyCheck)
Applicativo open source, realizzato dall' #OWSAP, che effettua una #SCA dell'applicazione e crea un file [[HTML]] con il report.
##### Installazione
Scarico l'ultima versione
```sh
VERSION=$(curl -s https://jeremylong.github.io/DependencyCheck/current.txt)
curl -Ls "https://github.com/jeremylong/DependencyCheck/releases/download/v$VERSION/dependency-check-$VERSION-release.zip" --output dependency-check.zip
```
Su windows:
```sh
.\bin\dependency-check.bat -h
.\bin\dependency-check.bat --out . --scan [path to jar files to be scanned]
```

## Code scanning
Per evitare errori, è possibile effettuare una scansione del codice sorgente. Questa operazione può essere effettuata seguendo 4 metodologie principali:
- #SAST - Statica quando la scansione avviene senza eseguire il codice (tramite l'utilizzo di modelli di codice)
- #DAST - Dinamica se richiede l'esecuzione del codice tramite l'esecuzione di attacchi noti e #fuzzing, ovvero l'utilizzo di input non validi)
- #IAST - Interattiva se viene effettuata durante i vari stadi dell'applicazione
- #SCA - Software Composition Analysis, ovvero vengono analizzate le dipendenze dell'applicazione.
Avendo esse diversi punti di fora e debolezze, è consigliato sesso effettuare più tipi di testing (es. #SAST + #DAST).
### SAST
Static Analysis Security Testing, ovvero una scansione di un codice sorgente ( #white-box-testing) per rilevare vulnerabilità (tramite ricerca di pattern noti) ed evidenziarle. Queste metodologie possono riportare come risultato dell'analisi del **falsi positivi**, che potrebbero falsarne la veridicità in maniera più o meno grave.
#### AST
L'Abstract Syntax Tree #AST è una #data-structure che rappresenta la struttura del programma (paragonabile al #DOM), utilizzando un linguaggio formale
##### Software
- [[Semgrep]]

### DAST
Dynamic Analysis Security Testing, nota anche come #black-box-testing, utilizza strumenti per riprodurre attacchi noti e #fuzzing  per rilevare la presenza di vulnerabilità in stato di esecuzione dell'applicazione.
#### Software
##### [Dastardly](Burp.md#Dastardly)
Strumento gratuito nella [versione community](https://github.com/PortSwigger/dastardly-github-action) (con funzionalità ridotte) per effettuare #penetration-test per analizzare 7 problemi di sicurezza.
- #reflected-xss
- #CORS
- Dipendenze JavaScript vulnerabili
- Content-type non specificato
- Multiplo content-type specificato
- 
##### [[Zap]]
Tool #open-source utilizzato per effettuare #penetration-test 
### IAST
Interactive Application Security Testing, va a unire le possibilità dei DAST e dei SAST. L'obbiettivo è fornire dei test di sicurezza all'interno dell'applicazione stessa, da utilizzare in fase di esecuzione, in qualunque fase di sviluppo.
Gli strumenti #IAST vengono selezionati tenendo a mente:
- Linguaggi di sviluppo utilizzati dal team
- Ambito della codifica e le vulnerabilità operative coperte dallo strumento
- Prestazioni veloci e basso tasso di falsi positivi
- Supporto ai principali standard di sicurezza
- Facilità di implementazione e integrazione con i flussi di lavoro di sviluppo esistenti e i set di strumenti #CI/CD.
E' da considerare il fatto che questi strumenti possono influire sul corretto funzionamento della mia applicazione.
#### Software
- [[Veracode]]
- [[Checkmarx]]
- [[Contrast]]
- [[Synopsys]]
- [[Micro Focus Fortify]]
- [[Rapid]]
- [[Qualys]]
- [[DongTai IAST]] ( #open-source )
### SCA
Software Composition Analysis, ovvero verifica la presenza di vulnerabilità note in tutte le #dependency del progetto (nella versione utilizzata). Un classico esempio di #SCA è il comando npm audit di [[Node.js]]:
```sh
npm audit
```
Un metodo per evitare l'utilizzo di repository esterne è l'utilizzo del cosiddetto #monorepo, ovvero un unico #repository utilizzato per tutti gli applicativi realizzati dall'azienda. Il problema principale di questo sistema però è il consumo di tempo necessario per aggiornare e mantenere il repository stesso.
utilizzino software #open-source, si incorre a potenziali rischi, tra i quali:
- Presenza di #vulnerabilità (scoperte ed incluse nel #CVE, o ancora non scoperte)
- Licenza non adatta alla vendita del software finale
#### Engine
1. vedi slides
2. Creazione di un elenco
3. Verifica in #database per la presenza di #CVE note, delle licenze d'uso
4. I risultati vengono resi disponibili agli utenti finali utilizzando diversi formati

| Pro                             | Contro           |
| ------------------------------- | ---------------- |
| Facilità di automazione         | Alta complessità |
| Facile integrazione con l' #IDE |                  |
Vd slides per completare la tabella
#### Software
- [[Azul]]
- [[snyk]]
- [[Quiet AI]]
- [[Retire.js]]
- [[OWASP Dependency Check]]

### Commit scanning
Permettono di evitare i #push contenenti #secret (dati sensibili, come password del database). [[git-secrets]]
#### Programmi
- [[git-secrets]]
- [[Burp#Sensitive discover]]
- [[gitleaks]]
## Regression test
Il #regression-test può essere fatto con [[Postman]], [[Python 1]] e consiste nell'analizzare il contenuto della #response ad una chiamata #http 

# Protezione
Esistono strumenti pensati per proteggere in maniera passiva i sistemi.
## Antimalware
Sono software utilizzati per identificare e impedire l'accesso ai [malware](#malware) all'interno del dispositivo. 
I malware possono essere inseriti nel dispositivo in vari modi:
- Download di antivirus da pop-up (o comunque da siti che siano diversi dal sito originale). Il software potrebbe essere stato alterato per contenere malware
- Malware *fileless*, che si attivano all'avvio del Sistema operativo per poi disattivarsi al suo spegnimento
- Script dannosi (indipendentemente dal linguaggio utilizzato)
- Installazione non intenzionale di software di terze parti infettati

Alcuni esempi di software Antimalware commerciali sono:
- AMP: Cisco Advanced Malware Protection
- WSA: Cisco Web Security Appliance
- ESA: Cisco Email Security Appliance

### Antivirus
Monitora di continuo il pc e, in caso riconosca un virus, lo mette in quarantena  o lo elimina

### Anti-adware
Cerca programmi che espongano pubblicità all'interno del computer

### Anti-phishing
Blocca gli indirizzi IP di noti siti di Phishing e avvisa l'utente riguardo i sisti sospetti

### Anti-spyware
Programma che cerca keyloggers e altri spyware

## NSI
L’Infrastruttura di Sicurezza della Rete definisce le modalità con le quali i dispositivi devono essere collegati tra loro per assicurare un buon livello di sicurezza end-to-end. 
### ACL
La Lista di Controllo degli Accessi è una serie di comandi che controlla quando un pacchetto deve essere inoltrato e quando deve essere bloccato, in base alle informazioni trovate nell’header del pacchetto. Un ACL svolge le seguenti funzioni:
- Limita il traffico per migliorare le prestazioni della rete
- Fornisce un controllo del flusso della rete (può anche fornire delle rotte predefinite per gli aggiornamenti, evitando così l’installazione di aggiornamenti da terze parti)
- Fornisce un livello base di protezione della rete
- Filtra il traffico in base al tipo di pacchetto (es. Email, video, ecc.)
- Monitorano le attività degli host ed impediscono determinati accessi alla rete (es. Permettere solo protocolli FTP)
Gli ACL spesso operano operazioni di controllo tramite indirizzi IPv4 di origine e destinazione, o porte di accesso e protocollo utilizzato.
Di solito è utile utilizzare più ACL e nominarle con numeri o nomi che definiscano il tipo di filtraggio compiuto.

### NetFlow
È un software utilizzato per gestire comunicazioni tramite [SNMP](./tecnologie/protocolli#snmp). Originariamente il software catalogava le comunicazioni in base a 7 parametri:
1. IP del mittente
2. IP del destinatario
3. Porta di invio
4. Porta di destinazione
5. Protocollo di [livello 3](<#3 - Rete>) utilizzato
6. Marchio ToS (Tipo di Servizio)
7. Interfaccia logica di input

Il punto 6, incluso nell'header del pacchetto IPv4, contiene informazioni relative alle regole per la [Qualità del servizio] da applicare al pacchetto nel flusso in cui è stato inviato.


### Port Mirroring
È una feature dello Switch che permette di duplicare il traffico ed inviare una copia ad un dispositivo apposito, utilizzato per monitorare la rete.

### Syslog server
Server utilizzato appositamente per memorizzare i report inviati da Switch, Router e altri dispositivi di rete, utili per effettuare il troubleshooting.
Il Syslog possiede due caratteristiche principali:
- L’abilità di selezionare il tipo di informazione di logging catturata
- L’abilità di specificare il destinatario del messaggio Syslog catturata.

### NTP
Il [Protocollo del Tempo della Rete](./tecnologie/protocolli#ntp) è importante per tenere traccia in maniera efficace dei log di più dispositivi connessi alla stessa rete

### Server AAA
Vedi [Server AAA](<./tecnologie/macchina#aaa server>).

### VPN
La [VPN](tecnologie/reti#vpn) risulta particolarmente utile nel caso ci sia bisogno di fornire una connessione sicura alla rete da remoto grazie alla cifratura del messaggio durante il passaggio nella WAN.

## Boot integrity
Software che permette di stabilire se un sistema possa essere considerato affidabile, o se sia stato modificato durante la fase di avvio o caricamento.
viene salvato un firmware (un software che esegue semplici funzioni di base del computer) all'interno della scheda madre e viene eseguito come primo passaggio dal computer.
### Secure Boot
E' stata creata una nuova Interfaccia di Firmware Unificata ed Estensibile (UEFI) come nuova versione di BIOS, che definisce la nuova interfaccia standard per operazioni tra firmware, sistema operativo e device esterni (funziona solo in modalità 64-bit). 

Il firmware controlla l'affidabilità di ogni parte del software di avvio, inclusi i driver di firmware UEFI, le applicazioni UEFI e il sistema operativo. Se le firme sono valide, il sistema si avvia.

### Measured Boot
Provvede un protocollo di validazione più forte del Secure boot, in quanto misura tutti i vari componenti e ne salva un log all'interno del chip TMP, che potrà essere utilizzato per effettuare test di controllo da remoto. Permette anche di identificare applicazioni non fidate e di caricare prima gli anti'malware.

## Firewall
Sono software o dispositivi che permettono di filtrare i messaggi in ingresso in una rete e perciò devono/offrono funzionalità per:
- essere resistenti agli attacchi informatici
- essere l’unico punto di contatto tra una LAN e una WAN
- applicare le [Policy di Controllo degli Accessi](#ACP)
- sanare il flusso del protocollo, prevenendo lo sfruttamento di determinati protocolli per portare a segno attacchi
- bloccare l’invio di dati malevoli da server e client
- ridurre i controlli necessari da parte dei team di gestione in quanto basta controllare le politiche dei firewall per effettuare un’analisi

### Architettura
Essendo il firewall un punto di contatto tra diverse reti (es. LAN e WAN), la sua configurazione avviene per due interfacce:
- Traffico in entrata
- Traffico in uscita
Ci sono dei modelli molto usati per definire l’architettura di un firewall:
- Pubblico e privato
- Zona demilitarizzata
- Policy del Firwewall basate sulla zona

#### Pubblico e privato
Si considera la rete interna come sicura e quella esterna come insicura. Partendo da ciò, si crea la rete tenendo in considerazione che:
- tutto ciò che esce dalla rete privata è ispezionato e poi inviato verso la rete pubblica
- tutto ciò che proviene dalla rete pubblica viene bloccato
In questo caso quindi l’uso del firewall è potenzialmente superfluo.

#### DMZ
Nella zona demilitarizzata i firewall vengono posizionati in parallelo alla rete privata (non agiscono da filtro di blocco tra rete e router, ma si sostituisce alla rete privata per i pacchetti in ingresso e alla rete pubblica per quelli in uscita)
- Il traffico proveniente dalla rete privata viene analizzato e lasciato passare con poche o nessuna restrizione
- Il traffico proveniente dalla DMZ viene bloccato di default e lasciato passare selettivamente (di solito DNS, HTTP, HTTPS, IMAP, POP, SMTP), oppure il traffico di risposta da richieste inviate dalla rete privata, che viene permesso in maniera dinamica

#### ZPF
Le Policy Basate sulla Zona utilizzano il concetto di zona (gruppo di una o più interfacce aventi funzionalità simili) per stabilire le regole in base alle necessità e alla tipologia di zona da proteggere. L’utilizzo di questa architettura permette una maggiore flessibilità.
Di default il traffico tra interfacce diverse della stessa zona è abilitato senza blocchi, mentre la comunicazione tra blocchi diversi è bloccata.

Nel caso si voglia definire una policy per la self zone (il Router), occorre tenere conto della gestione e controllo dei piani di traffico, in particolare i protocolli di routing, [SSH](./Tecnologie/protocolli#ssh) e [SMNP].

### Tipi di firewall

#### Packet filtering
Chiamati anche Stateless, sono firewall che sostanzialmente impediscono le comunicazioni basandosi su informazioni di livello 3 (Network) o livello 4 (Trasporto). Di solito fanno parte del Router Firewall.

I benefici sono:
- Facilità di implementazione di nuove regole
- basso impatto sulle performance
- facili da implementare e supportate dalla maggior parte dei router
- offrono un grado iniziale di protezione al livello Network
- svolgono quasi tutte le funzioni dei firewall più costosi ad una frazione del costo

I lati negativi invece sono:
- Sono suscettibili allo [spoofing](#sppoofing) IP
- non filtrano efficacemente pacchetti frammentati
- utilizzano ACL complesse, che sono difficili da implementare e manutenere
- Non possono filtrare dinamicamente certi servizi.

#### Stateful firewall
Sono i più versatili in quanto offrono meccanismi di protezione basati su informazioni a livello 3, 4 e 5 (Sessione) della pila ISO/OSI e permette di salvare le informazioni sui dati in un'apposita tabella dello stato.

Benefici:
- Sono spesso usati come primo mezzo di difesa grazie alla funzione di filtro offerta
- rinforzano il filtraggio dei pacchetti grazie alla possibilità di implementare controlli più rigidi
- Performance migliori rispetto ai [packet filtering](<#packet filtering>) firewall
- buona difesa contro attacchi [DOS](#DOS)
- offrono più informazioni nei log

Contro:
- Non prevengono attacchi a livello 7 - Applicazione
- non tutti i protocollo sono stateful (UDP e ICMP non lo sono)
- difficoltà nel tracciare connessioni che usano porte dinamiche
- non supportano autenticazione dell'utente

#### HBF
L'Endpoint firewall (o Host-based Firewall) è un [firewall](#Firewall) installato sul dispositivo stesso, utilizzato per consentire o negare il traffico del dispositivo con il resto della rete in base a meccanismi di controllo (bloccando la porta nella quale è in corso la sessione identificata come pericolosa) che funzionano però solo per connessioni aperte dall'host stesso.
Alcuni HBF includono meccanismi di protezione delle Tabelle IP e dei TCP Wrapper.

#### Application Gateway firewall
Blocca le connessioni ai livelli 3,4,5 e 7 (Applicazione) tramite utilizzo di un Proxy che funge da tramite per le connessioni tra gli endpoint all'interno della rete e l'esterno.
La maggior parte dei blocchi e dei controlli avviene tramite software.

#### Firewall di ultima generazione
Permettono di:
- Integrare sistemi di prevenzione delle intrusioni
- Aggiungere coscienza e controllo del livello 7 (Applicazione) per vedere e bloccare software rischiosi
- Aggiornano i percorsi al fine di includere informazioni future
- Tecniche per identificare le [minacce](#Threat) della sicurezza in evoluzione

#### Firewall trasparente
Filtra il traffico IP tra una coppia di interfacce a ponte.

#### Firewall ibrido
Una combinazione di due o più firewall tra quelli sopra menzionati.

## IPS
### Introduzione
I [Sistemi di Prevenzione delle Intrusioni](https://it.wikipedia.org/wiki/Sistema_di_prevenzione_delle_intrusioni) sono dei componenti software che permettono di monitorare, registrare e bloccare le attività dannose all'interno di una rete, tramite il riconoscimento di pattern all’interno dei pacchetti (definibili dal gestore) analizzati.
Gli IPS (o i simili IDS, Dispositivi di Identificazione delle Intrusioni) possono essere implementati tramite:
- Software per il router (es. Cisco IOS IPS)
- Dispositivi appositi 
- Moduli di rete installati all’interno di ASA (Apparecchi di Sicurezza Adattiva), Switch o Router

I vantaggi di un IDS sono:
- Assenza di rallentamento del flusso di dati
- Nessun impatto sulla rete in caso di arresto
- Nessun impatto sulla rete in caso di sovraccarico
Gli svantaggi invece sono:
- I pacchetti dannosi non possono essere bloccati
- È necessario impostare correttamente le azioni di risposta
- Più vulnerabili contro le tecniche di evasione della sicurezza di rete

I vantaggi di un IPS sono:
- Blocco dei pacchetti dannosi
- Possibilità di utilizzo di tecniche di normalizzazione del flusso per identificare attacchi segmentati su più pacchetti
Gli svantaggi invece sono:
- Possibile rallentamento del traffico dovuto a problemi dei sensori
- Il sovraccarico dei sensori impatta le prestazioni della rete
- Impatto sulla rete

### Host-based
Gli IPS basati sull’host (HIPS) sono software da installare su dispositivi per monitorare e proteggere i sistemi operativi. Tra le loro funzionalità includono:
- La possibilità di bloccare azioni effettuate dall’utente nel caso divergano dai suoi comportamenti abitudinari (come la modifica di file di sistema)

Un particolare di cui tenere conto è che gli HIPS monitorano l’attività dell’endpoint su cui sono installati.

### Network-based
Gli IPS basati sulla rete (NIPS) possono essere implementati su un dispositivo dedicato o su un dispositivo non dedicato e sono elementi indispensabili per la sicurezza della rete.

## Host encryption
L'esempio più noto è l'[EFS](../os/windows#efs) (Windows Encrypting File System, ovvero Sistema di Crittazione dei File), che permette, appunto, di crittare file, cartelle, o l'intero hard drive.
In quest'ultimo caso (noton anche come FDE, o Full-Disk Encryption), Windows si appoggia a BitLocker, che permette di utilizzare il BIOS come Modulo di Piattaforma Fidata (TPM).
Il TPM è un chip specializzato, presente nella scheda madre, che salva le informazioni relative al sistema dell'host, come;
- Chiavi di crittazione
- Certificati digitali
- Misure di integrità del sistema
BitLocker To Go permette di cifrare dispositivi rimuovibili senza l'uso del TPM.
## Patch Management
Le patch sono aggiornamenti di software per risolvere [vulnerabilità](#weakness) presenti nel software stesso. Di solito il sistema operativo controlla e installa automaticamente le patch.
A livello aziendale, spesso gli aggiornamenti vengono analizzati dal team di Cybersecurity prima di venire installati nei dispositivi all'interno della rete. Per facilitare questo compito, esistono i Patch Manager, ovvero software che permettono una gestione facilitata degli aggiornamenti delle patch, grazie al controllo tramite un'unica piattaforma la gestione delle patch per tutti i dispositivi della rete.

## Minacce WLAN
Le connessioni WLAN hanno ulteriori rischi: 
- poter essere disturbate e/o intercettate da utenti malevoli (o ricevere altri tipi di disturbi)
- Non avere il pieno controllo degli accessi (chiunque riceva il segnale può potenzialmente connettersi)

Dei meccanismi efficaci di protezione sono:
- utilizzo di meccanismi e protocolli di autenticazione e crittazione (come [WPA2](./tecnologie/protocolli#WEP2), [WPA3](./tecnologie/protocolli#WEP3), [AES](./tecnologie/protocolli#aes))

## Endpoint security

### HBSS
I Sistemi di Sicurezza Basati sull'Host raccolgono tutti i principali sistemi di protezione (malware, firewall, prevenzione di intrusione) i un unico ambiente. AV-TEST offre analisi indipendenti di alta qualità dei sistemi di protezione host-based.

### Protezione dai malware Host-based
La Protezione dai Malware Basata sull'Host è utilizzata per protegger ei  dispostivi end-point da malware.

#### Antivirus/antimalware
Utilizzato per identificare e mitigare virus/malware. Il processo di identificazione dei virus avviene seguendo una di queste tre metodologie:
- Basato sulla firma
- Basato sull'euristica (ovvero riconosce caratteristiche generalmente presenti all'interno dei virus)
- Basato sul comportamento
Di solito controllano l'end-point in tempo reale, verificando il traffico in corso. Nel caso l'antivirus sia installato in ogni host si chiama anche agent-based altrimenti, nel caso venga installato in un sistema centralizzato, si chiama agentless (utilizzati specialmente in ambito di virtualizzazione). L'agentless consuma anche meno risorse rispetto ad un sistema che utilizza antimalware agent'based su ogni endpoint. 

### HIDS
I Sistemi di identificazione dell'intrusione di Host sono software installati sul dispositivo (o nel server) per identificare l'eventuale presenza di attività sospetta e monitora eventuali richieste malevole e le registra nel Registro di Sistema.
Sono software che consumano molte risorse e che potrebbero rallentare le prestazioni del dispositivo su cui sono installate.

### HIPS
I Sistemi di Prevenzione dell'Intrusione di Host sono software che monitorano l'attività del dispositivo e ricerca la presenza di attacchi conosciuti, anomalie o segnali di allarme tramite all'interno dei pacchetti in transito.
Nel caso identifichi un'attività sospetta, il software allerta l'utente, logga l'attività sospetta, resetta la connessione e, in caso, effettua il drop del pacchetto.

### EDR
L'Endpoint Detection and Reponse è una soluzione che monitora costantemente il dispositivo endpoint e ne raccoglie dati. Analizza i dati raccolti e risponde a tutte le minacce identificate.
Mentre un [antivirus](#antivirus) permette solo di bloccare l'accesso di un virus, un EDR può anche identificare le minacce presenti già all'interno del dispositivo.

### DLP
Il Data Loss Prevention (Prevenzione della Perdita di Dati) è un software che serve ad assicurare che i dati sensibili non vengano persi, utilizzati in modo errato o visualizzati da utenti non autorizzati.

### NGF
I Firewall di nuova generazione (New Generation Fierewall) sono dispositivi che combinano le classiche funzionalità di un firewall con altre funzionalità di filtraggio degli host all'interno della rete tramite inline Deep Packet Inspection(DPI, Ispezione profonda dei pacchetti) o sistemi IPS (Sistema di Protezione dalle Intrusioni).


## Mitigazione
### Attacchi di ricognizione
Gli attacchi di ricognizione sono effettuati per analizzare la rete e preparare da attacchi più importanti. Di solito hanno l'obiettivo di raccogliere informazioni e preparare un accesso alla rete per l'attaccante. Questi attacchi sono identificabili e notificabili tramite l'analisi del volume di richieste [ICMP](./tecnologie/protocolli/icmp) per secondo.

La mitigazione di questi attacchi avviene:
- Implementando misure di autenticazione
- Utilizzando la crittografia delle comunicazioni per evitare attacchi di [sniffing](#sniffing) delle comunicazioni
- Utilizzando degli **anti-sniffer** per identificare agli attacchi di sniffing
- Implementare un'[infrastruttura a Switch](https://en.wikipedia.org/wiki/Fully_switched_network)
- Utilizzare [Firewall](#firewall) e [IPS](#IPS)
- Crittare le comunicazioni per evitare attacchi di packet sniffing
- Disattivando gli ICMP echo e eco-reply negli edge-router (da considerare che questa operazione non permetterà di effettuare operazioni di diagnosi della rete)

### Attacchi di accesso
Le misure consigliate di mitigazione sono:
- Utilizzare password forti (almeno 8 caratteri, che contengano almeno un carattere minuscolo, uno maiuscolo, un numero e un carattere speciale)
- Disattivare l'account dopo un numero di tentativi di accesso consecutivi non andati a buon fine
- Implementare politiche di accesso tramite MFA
- Educare gli utenti

Per Identificare questo tipo di attacchi, invece, è possibile:
- Controllare i log degli accessi
- Controllare l'utilizzo di banda della connessione


### DoS
Per verificare se è in corso un attacco [DoS](#DOS) di solito basta controllare la presenza di picchi (o comunque di strani pattern) nel grafico dell'uso della banda. Un attacco DoS può essere anche un campanello di allarme per futuri attacchi più dannosi alla rete.
La maggior parte degli attacchi DoS nella storia sono stati effettuati tramite [indirizzi falsificati](#spoofing).

Ci sono in commercio dei Router con meccanismi di protezione da spoofing, come la [port security], [DHCP snooping], [IP Source Guard], [DAI] (Dynamic Access Resolution Protocol Inspection) e [ACL](./os/linux#ACL)

### Worm
Il processo di mitigazione contro un attacco worm avviene seguendo le fasi:
#### Contenimento
Viene compartimentata e segmentata la rete per evitare che il worm continui a diffondersi in tutti i dispositivi della rete. Per effettuare questo processo è richiesto verificare la [Lista di controllo degli accessi](./os/linux#acl) sia per le comunicazioni da che verso i Router e i Firewall della rete.

#### Inoculazione
Viene installata la patch dell'azienda produttrice su tutti i dispositivi non ancora infettati dal worm, riducendo così la superficie di attacco del worm.

#### Quarantena
Fase che si attua contemporaneamente alla precedente, che consiste nell'isolare i dispositivi infettati dal worm dal resto della rete (tramite disconnessione, blocco o rimozione). 

#### Trattamento
I dispositivi infetti vengono disinfettati ed in seguito vengono installate le patch dell'azienda produttrice del sistema operativo che si sta utilizzando. Nei casi più estremi, può essere necessario reinstallare l'intero Sistema Operativo sul dispositivo per evitare con maggiore sicurezza la presenza del worm o dei suoi sottoprodotti.

# Normativa
## Italia
- AGID
- [Legge 81/2001](https://www.normattiva.it/uri-res/N2Ls?urn:nir:stato:legge:2001;81)
## EU
- GDPR
## US
## Generali
- Copyright
- Privacy
- Privacy Policy
### ISO/IEC 27001
Si occupa della sicurezza sotto un punto di vista olistico.
### ISO/IEC 27034
Si concentra sul lato #software
# Tips
- Tutte le rotte che hanno azione distruttiva devono essere trattati tramite form
- siti come https:// ---continua
- L'utilizzo di **npm audit** permette di tenere sotto controllo lo stato delle dependencies  tramite #audit
- Per effettuare #test è preferibile utilizzare un container con #juice-shop, scaricabile [qua](https://github.com/juice-shop/juice-shop?tab=readme-ov-file) ```
	```sh
	docker pull bkimminich/juice-shop && docker run --rm -p 3000:3000 bkimminich/juice-shop
	```
# [[Glossario]]
- #brute-force - reiterazione automatica di decriptazione di dati protetti tramite programmi o siti appositi (tipo hashcat). Di solito viene usato su password basilari (rockyou.txt)
- #sanificare - validazione dei dati ricavati tramite input
- #prepared-statement - 
- #debolezza - Componente potenzialmente soggetta ad essere aggirata
- #vulnerabilità - Quando viene sfruttata con successo una debolezza per perpetrare un attacco informatico
- #salt - Elemento che viene aggiunto al dato prima della criptazione per aumentare la complessità del risultato
- #peppper - Ulteriore elemento aggiunto al dato (simile al #salt), ma non viene registrato nel server 