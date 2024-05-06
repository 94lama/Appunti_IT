# Introduzione
## MITRE
Organizzazione non-profit, fondata nel 1975, che si occupa di #cybersecurity.
Mette a disposizione due archivi molto utili per la sicurezza:
### Common Vulnerabilities Enumeration ( #CVE)
Contiene informazioni molto utili sulle vulnerabilità e sulle debolezze dei siti web, framework e librerie, costantemente aggiornate (dopo che il framework colpito è riuscito a rimuovere la vulnerabilità).
Contiene anche alcune possibili soluzioni per rimuovere le vulnerabilità
### Common Weaknesses Enumeration ( #CWE)
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
|  |  |  |
### Common Platform Enumeration ( #CPE)
Archivio di software e/o framework disponibili, indicizzati.
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

## Tipologie di attacchi
### Denial of Service ( #DoS)
Attacco che sfrutta una script o altri metodi per sovraccaricare il #server bersaglio ed impedirne il normale funzionamento per un determinato periodo di tempo
### Distributed Denial of Service ( #DDos)
Attacco simile al #dos, ma utilizza più macchine per portare a termine l'attacco
### Injection
#### SQL Injection
Invio al #server di un codice malevolo che permette una manipolazione del #database tramite comandi #SQL, che ne permettono la lettura o la modifica dello stesso
## Termingologia

### CIA Security Triad
#CIA è l'acronimo di Confidentiality (il dato deve rimanere privato), Integrity (non dev'essere modificato) e Availability (il servizio dev'essere sempre disponibile). Questi 3 punti costituiscono la base della sicurezza informatica.
#### #confidentiality
- PII - Personal identity info
- PHI - Personal health information
- PCI - Payment card industry
- Company proprietary data
#### #integrity
- Validazione input
- Gestione degli errori
- Controllo degli hash
#### #availability
- Services Uptime
- Response time
- Criticality
- User requirements

### Secure by-Design
Principio che si basa sull'applicazione dei principi di sicurezza sin dalla fase di #progettazione 
### Defense In-Depth
Si basa sul proteggere un sistema mediante vari livelli di sicurezza, ognuno dei quali rappresenta una difesa per eventuali attacchi informatici (es. validazione lato client e server, uso di middleware).
#### Controlli amministrativi
Strategie organizzative generali per la creazione di  un ambiente sicuro. Simulazioni di attacchi (tipo #phishing) potrebbero rivelarsi utili
#### Controlli fisici
Impediscono agli aggressori di ottenere l'accesso reale ai dati e sistemi informatici (es. chiavi magnetiche, porte bloccabili, ecc.)
#### Controlli tecnici
### Principle of Least Privilege ( #PoLP)
**Vantaggi**:
- Migliore gestione dei permessi
- Rallentamento della diffusione del malware
- Semplificazione della conformità e miglioramento della preparazione agli #audit 
Il #PoLP si implementa seguendo dei passaggi:
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
# Security Standards
Gli standard di sicurezza hanno l'obiettivo di categorizzare e valutare le #vulnerabilità.
### Fondazioni
- Open Web Application Security Project [#OWSAP](https://owasp.org/) è una fondazione che analizza e categorizza le vulnerabilità relative la sicurezza

## OWASP Top 10
- Algoritmi scnosigliati: sha1, md5 
## CVE
## CWE
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
# Secure coding
# Hardening
# Front-end
## JavaScript
### #xss
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
### #prototype-pollution
Attacco che permette di modificare il metodo **__proto__** dell'oggetto base di JavaScript per eseguire velocemente comandi tramite metodo **eval()**. Sfruttando questo stratagemma è possibile eseguire attacchi #xss ed è inclusa nella categoria #insecure-design
### #CSS-injection
Tramite script #JavaScript si modifica lo style della pagina. Questo tipo di attacco si verifica quando si immettono delle variabili collegate tramite #URI:
```Browser
127.0.0.1:8000/#blue //colora lo sfondo un componente
127.0.0.1:800/#}body{display:none} //in questo modo si modifica l'attributo display del div body
```
Con questo attacco, per esempio, si può nascondere la #UI all'utente bersaglio, lasciandogli solo un input con un label con una richiesta di inserimento dati per sbloccare il normale funzionamento del sito (i dati inseriti saranno leggibili dall'attaccante)
# DevSecOps Pipeline
## Introduzione
Il #DevOps è una metodologia di lavoro, utilizzata per ridurre i tempi di distribuzione attraverso l'automazione, fornire un #feedback continuo, migliorare la collaborazione del team e le capacità di affrontare il rilevamento degli errori
## Software Development Life Cycle ( #sdlc)
### CI/CD
Per #CI/CD si intende Continuous Integration and Continuous Devliery. Il CI/CD è una metodologia utilizzata per aumentare la velocità, ridurre gli errori e permettere di standardizzare i processi.
Il #deployment di norma è effettuata da una singola persona, dopo che il prodotto ha raggiunto un livello di avanzamento apprezzabile (ad esempio ha raggiunto determinati obbettivi) ed è stato oggetto di verifica.
### Software utilizzati
#### Code
I software sono utilizzati per il #versioning dell'applicazione. Questi software permettono di condividere il lavoro tramite creazione di più #branch, ovvero ramificazioni del progetto. 
- [[Github]]
- Git
- Subversion
- GitLab
```Branching
|- master
|-- develop
|--- feature_1
|--- feature_2
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
Segno tutt
### Goal oriented
#### #DREAD
#### #PASTA
#### #trike

### Motivation oriented

### Library (o list) Oriented

#### #STRIDE
Acronimo delle minacce su cui va ad operare:
#spoofing: 
#tampering: 
#repudiation: Si nega l'aver effettuato una determinata azione
#information-disclosure: Categoria che copre le violazioni di #privacy o fughe di dati
#DoS: Mira ad interrompere il normale funzionamento di un sito
#privilege-escalation : L'attaccante accede con un profilo base e ottiene livelli di accesso superiori
E' il sistema con più ampia superficie di copertura per le potenziali #minaccia e/o #vulnerabilità.
Alcune criticità di questa metodologia sono:
- La necessità di avere delle conoscenze approfondite sulle minacce e vulnerabilità, su cui applicare il metodo
##### Fasi
1. Si costruisce un #data-flow-diagram, dove identifico le linee di fiducia
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
# Weakness
## [Improper Restriction of XML external entity Reference](https://cwe.mitre.org/data/definitions/611.html)
Tim Ferris - inventore di Wordpress

Noto anche come #XEE, si verifica quando un entità XML contiene collegamenti ad altre entità XML non previste dal sistema, che permettono di inserire script malevoli per prelevare dati
# Tipologie di attacco
## [Broken Acess Authorization]( #broken-acess-authorization, #broken-access-control, #privilege-escalation)
Attacco volto ad ottenere accesso a dati a cui non si sarebbe potuti accedere in condizioni normali (es. utente per un guest, o amministratore per un utente).
Può essere:
- **Horizontal Authorization Control**, quando si ottengono dati di altri utenti con privilegi simili (utente -> utente)
- **Vertical Authorization Control**, quando si ottiene accesso a dati visibili solo ad utenti con grado superiore (utente -> admin).
Questo tipo di attacco può essere prevenuto tramite:
- Definire una *policy* chiara che stabilisca permessi e limiti per tipologia di utente
- Testa la soluzione
- Utilizza un #framework che includa un sistema di autorizzazioni al suo interno
### Horizontal Authorization Control
Vulnerabilità sfruttabile tramite attacchi #idor (Insecure Direct Object References)
``` 
http://vulnerableapp.com/user/account?accountId=7800001
	L'utente accede al sito tramite account personale

http://vulnerableapp.com/user/account?accountId=7800002
	Modificando l'URI, può accedere alle informazioni dell'account con ID diverso
```
### Vertical Authorization Control
Permettono di accedere al controllo di funzioni e/o dati disponibili solo ad un utente avente maggiori permessi
## [Broken Cryptography]( #broken-cryptography)
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
### Come proteggersi dalla #broken-cryptography
- Non implementare algoritmi deprecati, preferisci quelli utilizzati dalla community e che rispettando gli standard
- Non usare chiavi con un Vettore di Inizializzazione
- Preferisci soluzioni di *management* delle chiavi collegate con il sistema operativo, hardware o cloud provider
- Fai revisionare le tue chiavi da un operatore terzo affidabile
- Mantieniti aggiornato sulle metodologie di criptazione più efficaci e su quelle deprecate
## Injection
Attacco che si basa sull'inserire stringhe di codice malevolo. Può essere effettuato sul database, sul sistema operativo, o comunque in qualunque ambito similare. 
### [SQL Injection]( #sql-injection)
Sono delle categorie di vulnerabilità che si verificano quando un'applicazione accetta dati non fidati da una fonte esterna, come input utente. L'attaccante inserisce o modifica dei dati nel database. E' l'attacco più semplice, così come quello che può causare i danni più gravi. Ci sono varie tipologie di #sql-injection:
### Tipologie di attacco
#### Classic SQLi
#### Blind SQLi
Avviene quando il risultato della *query*di manipolazione non è visibile all' #attaccante
#### Time-Based SQLi
#### Error-Based SQLi
#### Union-Based SQLi
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
### Difendersi dalla SQL Injection 
E' possibile difendersi dalle #sql-injection tramite:
- Effettuare backups
- Utilizzare comandi predefiniti per accedere al database e successivamente passare i parametri (*best practice*)
- Lista di validazione dei comandi
- Lista di diniego (non molto efficace)
- Utilizzo di Store Procedures (stringhe predefinite di codice per interagire con il database) (non efficace con tutte le tipologie di SQl  attack)
- Usare un WAF (Web Application Firewall)
- Utilizzare dei #framework dotati di un #ORM
## [Security Misconfiguration]( #security-misconfiguration)
Sono delle configurazioni fallaci, dovute all'errore umano durante la fase di scrittura del codice (dell'applicazione stessa, del framework o altro). Alcuni esempi sono:
- ***Features*** ridondanti abilitate
- Account con user e password di default
- ***Features*** di sicurezza disabilitate o non configurate correttamente
- Software datati
- Utilizzo di password deboli o prevedibili
- Mancanza (o configurazione errata) di Security Headers
- #directory-listing non disabilitate (pagine dalle quali è possibile vedere la struttura dell'app)
- Applicazioni lasciate dalla fase di sviluppo 
### Evitare le Security Misconfiguration
Alcune note per evitare questi errori sono:
- Implementare procedure ripetibili e sicure di installazione
- Rimuovere le features non necessarie
- Configurare e tenere aggiornate le #patch nello stack
- Automatizzare le procedure quando fattibile
- Assicurare la corretta #configurazione e #deploy dei Security Header
- Frammenta l'architettura dell'applicazione
## [Insecurity Functionality Exposed]( #insecurity-functionality-exposed)
Debolezza che si presenta quando alcune funzioni, inserite inizialmente per velocizzare alcuni compiti in fase di sviluppo, non vengono eliminate prima del deploy. 
## [Unsafe Deserialization]( #unsafe-deserialization)
La #serializzazione è il processo di conversione dello stato di un oggetto o una struttura dati in un formato memorizzabile o trasferibile. La #deserializzazione è il processo inverso. 
### Prevenire la unsafe deserialization
- Utilizza formati di dati semplici ovunque possibile
- Usa modelli di serializzazione che usino solo #dati-primitivi 
- Usa modelli di serializzazione che permettano la crittazione e la decrittazione dei dati in maniera sicura
- Sostituisci la serializzazione dei dati con formati di solo dati, come il JSON
## [Insufficient Logging & Monitoring]( #insufficient-logging #monitoring)
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
## [Server Site Request Forgery](#ssrf)
La #SSRF avviene quando una richiesta di input lato #server non avviene adeguatamente monitorata (spesso quando viene effettuata una #richiesta HTTP ad un sito di #terze-parti). Spesso avvengono sfruttando la fiducia tra due applicazioni durante lo scambio di dati tramite richieste #API o lo scambio di file e/o pacchetti per compiere azioni malevole contro il server dei soggetti terzi con cui avviene lo scambio, o contro il server stesso che compie la richiesta, ad esempio tramite i protocolli:
- file://
- TCP
### Precauzioni contro l'SSRF
- Implementare una lista di indirizzi autorizzati (quando possibile)
- Disabilitare Schemi URL inutilizzati
- Non consegnare risposte raw da richieste del server
- Ridurre al minimo la fiducia del server confugurando correttamente delle regole limite del #firewall
## Vulnerable and Outdated Components
L'utilizzo di framework, sistemi operativi, software o componenti vulnerabili e/o datati possono creare dei punti critici di debolezza del nostro sito. E' possibile avere delle debolezze dovute a:
- Mancata conoscenza di tutti o componenti utilizzati
- Carente informazione e aggiornamento sulle ultime novità dei vari pacchetti
- Mancato aggiornamento della piattaforma
- Testing carente o assente della compatibilità a seguito di patch
### Soluzioni
- Eliminare le dipendenze inutilizzate
- Inventariare continuamente le versioni dei componenti lato client e server
- Monitorare costantemente fonti come [Common Vulnerability and Exposures] e [National Vulnerability Database]
- Utilizzare strumenti di analisi della composizione del software
- Monitorare le librerie e i componenti non manutenuti
- Preferire componenti con firma digitale (sicurezza di integrità) 
- Utilizzo di software di controllo per lo stato di aggiornamento delle dependencies (es. OWASP Dependencies Check)
## Identification and Authentication Failures
Precedentemente identificato come #broken-authentication, che indica quando un #attaccante impersona un altro utente per compiere azioni al suo posto. Possono essere causate da:
- Controlli di autenticazione insufficienti
- Rottura dei meccanismi di protezione a livello dell'Oggetto
- #session-fixation
- #broken-credential-management
### [Session fixation]( #session-fixation)
Attacco che permette all' #attaccante di dirottare dei dati validi di autenticazione. In particolare sfrutta l'eventuale mancanza di creazione di un nuovo #session-id in fase di login, per riutilizzare una vecchia sessione (effettuata da un altro utente) ed operare al sotto il suo nome.
Il #session-id è un token, implementabile tramite #cookie o nell' #URL del sito.
### [Broken credential management]( #broken-credential-management )
- #credential-stuffing
- #brute-force attacks, ovvero provare ad accedere ad un account tentando forzatamente con un numero massivo di password
- #password-spraying (ovvero tentare di accedere a molti account con delle password standard).
#### Evitare attacchi Broken credential management
- Usa #framework di autenticazione open-source famosi
- Testa la correttezza dei meccanismi progettati
- Ruota e invalida i #session-id 
- Non permettere l'utilizzo di password deboli o molto usate
- Utilizza l'autenticazione a più fattori ( #mfa)
- Implementa meccanismi di blocco accesso dopo tentativi multipli di login con password errata
- Utilizzo di #bastion-host o liste di ammissione per #IP
- 
### [Mass assignment]( #mass-assignment)
Può avvenire quando vengono utilizzate funzioni che selezionino in massa i campi dati dal database (es. **all()**, o quando vengono inclusi tutti i campi nei #fillable su #Laravel)
### [Credential stuffing]( #credential-stuffing)
Uso improprio di elenchi di password note (es rockyou.txt) per provare a loggarsi
### [Persistent session]( #persistent-session)
Sfutta il salvataggio dei token di autenticazione da una sessione precedente (di un altro utente) per accedere.
## Software and Data Integrity Failures
Si concentra sulla formulazione di ipotesi relative agli aggiornamenti del software, ai dati critici e alle pipeline #CI/CD (Continuous Implementation/Continuous Deployment) senza verificarne l'integrità. E' uno dei maggiori impatti #CVE e #CVSS. Si verifica quando:
- Ci si affida a plugin da fonti non attendibili
- La #pipeline non è sicura e permette accessi non autorizzati o l'inserimento di codice maligno
- Le funzionalità di aggiornamento non verificano l'integrità dello stesso
- I dati sono [codificati] o [serializzati] in modo che l'aggressore possa vedere e/o modificarli. 
### Prevenzione
- Utilizzo di firme digitali
-  Utilizzo di #repository affidabili
- Utilizzo di software appositi (OWASP Dependency Check)
- Processo di revisione efficace delle modifiche del codice
- La #pipeline CI/CD ha un'adeguata segregazione
- I dati serializzati non firmati o non crittografati non vengano inviati al #client
## Cross-Site Scripting
L'utente viene indirizzato verso un sito clone dell'originale, dal quale è possibile ricevere i dati inseriti dall'utente (es. funzioni di #debugging).
## Comand Injection

## Security logging e Monitoring failures
Di solito si scopre solo durante i #penetration-test o tramite discussioni con gli sviluppatori. Da ciò ne consegue che è difficile da identificare. In generale le cause possono essere:
- Eventi verificabili non registrati
- Avvisi di errore senza messaggi di #log
- I registri delle applicazioni non vengono monitorati
- Archiviazione dei registri solo in locale
- Soglie di allerta e processi di #escalation non calibrati correttamente
- #penetration-test e scansioni non attivano gli avvisi
- L'applicazione non è in grado id identificare gli attacchi in tempo reale
- Gli avvisi sono visibili anche all'utente e/o all'aggressore
### Prevenzione
- Registrazione di tutti gli errori di #login, controllo degli accessi e #convalida degli input
- I #log devono essere registrati in un formato facilmente utilizzabile
- I #log devono essere codificati correttamente per evitare  #injection 
- Le #transazioni di alto valore devono avere un #audit trail con controlli d' #integrità
- Il team #DevSevOps deve stabilire un monitoraggio efficace
- Stabilire e adottare un piano di risposta e ripristino
## XML Entity Expansion
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

### Prevenzione
- Disabilitando la funzione Document Type Definition ( #DTD)
	```
	 disable_external_entities(true)
	 ```
- Gestire dati in formati semplici (es. #JSON )
- Verificare in ambiente di #testing che le chiamate #xml abbiano le dovute restrizioni
## CSRF Attack
Di norma si attuano partendo da un attacco di #phishing per estrapolare i dati necessari, per poi effettuare l'accesso nell'account dell'utente
### Prevenire
- Utilizzo di #token #anti-forgery (come il CSRF-token di #Laravel) per tutti i metodi che modificano lo stato dell'applicazione
- Double Submit Cookie Pattern (assegnare un valore casuale sia ad un cookie che ad un parametro della richiesta)
- Utilizzare l'attributo **SameSite** per evitare le richieste cross-domain
- Gestire correttamente #origin-header e #referrer-header
- Utilizzare la #re-autentication
- Utilizzare token usa e getta
- Utilizzare tecnologia #captcha
## Cross-Site Scripting (XSS)
Utilizzo di #script per manipolare le interazioni tra utente e sito web.
### Reflected XSS
Viene utilizzato un link per far inviare all'utente colpito un codice malevolo per colpire il server del sito. Possono essere inviati, ad esempio, tramite siti malevoli o mail
### Stored XSS
Lo script viene memorizzato in una pagina del sito e quindi riprodotto ogni volta che viene richiamata la pagina stessa (anche su utenti diversi)
### DOM-based XSS
Blocchi di codice #JavaScript (quindi non controllabili tramite #csrf-token)
### Pevenzione
- preferire le #whitelist alle #blacklist anche per le #input-validation
- Output encoding
- Content Security Policy
- utilizzare un framework moderno
- in #PhP usare funzioni htmlentities() e htmlspecialchars() per effettuare l' #escaping delle variabili
## Inadequate Input validation
La non adeguata predisposizione delle validazioni input (sia lato #client che #server) può portare a severi danni, in particolare se effettuato per transizioni economiche.
### Prevenzione
- Tratta tutti i dati come non affidabili
- Assicurati che i meccanismi di validazioni siano impostati correttamente
- Utilizza una lista predefinita di input quando possibile
- Non inserire direttamente l'input nel database 
## Type juggling
Durante il confronto tra una stringa e un numero, #PhP  tenta di convertire la stringa in un numero. Se la stringa non può essere convertita in un numero valido, viene automaticamente convertita nel valore 0.
```
var_dump("password" == 0); //true
```
Si può ovviare al problema utilizzando lo #strict-comparison-operator ===
## Borken OAuth
La #broken-oauth è una particolare tipologia di #broken-authentication, che avviene qualora si utilizzi un processo di #oauth per effettuare il login.
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

# Normativa
## Italia
- AGID
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