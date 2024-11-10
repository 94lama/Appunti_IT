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
- **Rischio**, la verosimiglianza che il particolare exploit venga utilizzato, pesata in base al danno che essa causerebbe

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
4. [Loggare]( #log) tutto il traffico, anche per rispettare i principi di **accountability** (responsabilità)
5. Procedere in maniera continuativa per applicare il metodo all'intero sistema

Il modello si basa sul concetto di **zone** come aree ben definite, nelle quali vengono utilizzate specifiche politiche di [Controllo degli accessi](<#controllo degli accessi>). I confini di queste zone sono definiti **Perimetro** della zona e stabiliscono il limite entro il quale viene concessa fiducia nello svolgere azioni.
#### Pilastri della Zero Trust Model
Lo zero trust model si applica tramite l'utilizzo di 2 concetti:
- Identità, suddivisa anche tra utenti che usano il servizio (tramite, ad es., [Multi-Factor Authentication]( #multifactor-authentication), #device che vengono utilizzati (accesso biometrico, uso di [Virtual Private Network]( #vpn)
- Protezione dei dati (es. tramite crittografia)
Questi concetti vengono applicati a 3 categorie di entità (che rappresentano i pilastri):
- Utenti (workforce)
- Software (work)
#### Adattamento di un sistema esistente al Zero-Trust Model
Per agevolare il passaggio, anche da un punto di vista umano, spesso si segue un percorso, che porta dal metodo esistente, a quello desiderato.
# Triade di sicurezza

Per comprendere le aree di interesse della cybersecurity spesso si fa uso del cosiddetto Cybersecurity Cube (noto anche come Cubo di McCumber), che riassume i punti focali della cybersecurity in 3 gruppi da 3 elementi ciascuno. L'insieme dei gruppi prende il nome di CIA Security Triad:

## Principi di sicurezza
### Confidenzialità dei dati
Solo le persone autorizzate devono avere accesso ai dati. Richiede l’implementazione di cifratura e decrittazione dei dati come misura cautelativa.
Un’alternativa alla cifratura è la tokenizzazione, ovvero la creazione di un valore randomico temporaneo da utilizzare come lasciapassare per ottenere accesso ai dati.

I dati possono essere suddivisi in:
- Personali
- Aziendali
- Classificati

Ognuna di queste categorie ha bisogno di livelli di protezione diversi per essere trattato.

#### Gestione dei diritti
La gestione dei diritti può essere suddivisa in:
- DRM: La gestione digitale dei diritti (Digital Rights Management) si occupa di proteggere i dati tramite meccanismi di cifratura, in modo che essi non possano essere copiati senza l’apposita chiave di decrittazione privata.
- IRM: La gestioni diritti di informazione (Information Rights Management) si occupa della protezione dei dati tramite la creazione di un livello di controllo degli accessi al documento protetto che avvisa il proprietario in caso di apertura (es. la PEC)

#### Identificazione
Consiste nell'assegnare ad ogni utente un valore che serva ad identificarlo indipendentemente (o non indipendentemente, in base alle necessità) dal mezzo con il quale sta cercando di effettuare l'accesso.

#### Controllo degli accessi
Avviene su più livelli, ognuno dei quali deve essere te tuo in considerazione:
##### Fisico
Consiste in tutti quegli ostacoli che permettono di prevenire o controllare l’accesso fisico alla rete. Alcune misure di controllo fisico sono:
- Guardie
- Recinzioni
- Sistemi di allarme
- Videocamere
- Porte blindate

##### Logico
Sono tutte quelle misure di sicurezza che prevengono l’accesso logico alla rete, come:
- Cifratura dei messaggi di testo
- Firewall
- Password
- Controllo dei dati biometrici
- Protocolli

##### Amministrativo
Racchiude tutte le policy e le procedure che permettono di discernere chi può da chi non deve avere accesso ai dati.
- Policies
- Procedure
- Recensioni
- Addestramento alla sicurezza
- Classificazione dei dati
- Controlli del background

Un buon metodo di gestione del livello amministrativo è l'[autenticazione](#autenticazione)

###### FIM
La Gestione federata dell'identità (Federated Identity Management) avviene quando la gestione dell'autenticazione di un utente avviene a livello di raggruppamento di reti (ad es. quando si utilizza lo stesso utente per accedere ai servizi Google come Youtube, Gmail, ecc.).

###### Password
Consiste in un dato che (dovrebbe) essere in possesso unicamente dello specifico utente. In quanto tale è consigliabile seguire alcune linee guida durante la sua creazione, ovvero:
- Avere lunghezza di almeno 10 caratteri
- Includere lettere (sia maiuscole che minuscole), numeri e caratteri speciali
- Conservarle in luoghi non protetti (come i Password Manager)
- Cambiare la password spesso

E' anche possibile utilizzare processi di [MFA](#MFA), ovvero la verifica di più fattori durante il processo di autenticazione per aumentare la sicurezza della rete. 

###### Autorizzazione
Verifica se l’utente abbia o meno il permesso di utilizzare determinati file. E' sempre consigliato considerare l'inserimento di procedure di autorizzazione anche per l'accesso alla rete stessa, così come per l'accesso a dati particolarmente sensibili, come password, email, ecc.
Per praticità gli utenti vengono raggruppati per livello di autorizzazione.
###### Responsabilità
Monitoraggio (log) dei processi e delle azioni effettuate dagli utenti e uso degli stessi per effettuare controlli ed analisi dei dati. Questa procedura aiuta a identificare eventuali errori, sbagli e tenere traccia delle azioni durante i processi di audit.

##### Modelli

###### DAC
Il Discretionary Access Control (controllo degli accessi discrezionale) rappresenta il modello più permissivo  di controllo ed utilizza Liste di Controllo degli Accessi per gestire chi ha diritto di accesso.

###### MAC
Il Mandatory Access Control (controllo degli accessi obbligatorio) è il modello più restrittivo e viene utilizzato solo in particolari casi (come quello militare). Assegna ad ogni utente un etichetta, che viene utilizzata per gestire il tipo di dati e la modalità di accesso agli stessi da parte dell'utente.

###### RoleBAC
Il Role-Based Access Control (RBAC, Controllo degli accessi basato sul ruolo) utilizza gruppi di ruoli ed ogni utente deve appartenere ad almeno un o di essi. Le modalità di accesso e tipologia di dati a cui ha accesso l'utente vengono stabilite per ogni gruppo.

###### ABAC
L'Attribute-Based Access Control (controllo degli accessi in base all'attributo) si basa sull'assegnazione di attributi ad ogni oggetto, i quali definiscono modalità di accesso, utenti a cui garantire làaccesso, tempistiche id accesso, ecc.

###### RuleBAC
Il Rule-Based Access Model (RBAC, controllo degli accessi basato sul ruolo) permette di gestire le politiche di accesso tramite regole (ad esempio lista di indirizzi IP a cui è consentito l'accesso)

###### TBAC
Il Time-Based Access Control (controllo degli accessi basato sul tempo) permette di gestire gli accessi in base all'orario.

### Integrità
Solo le persone autorizzate possono modificare i dati. Richiede l’implementazione di cifratura dei dati come misura cautelativa, così come misure di validazione, controllo degli accessi e verifiche della consistenza. La frequenza necessaria dell’effettuazione di questi controlli dipende dall’importanza che ha il dato. Questo fattore a sua volta, spesso dipende dal tipo di azienda che possiede il dato (it, viaggi, ospedaliero, ecc.).

La necessità di avere dati integri durante tutto il processo però si scontra con la necessità di manipolare spesso il dato, o della necessità di modificarlo spesso e, dato che ogni controllo effettuato ne rallenta la velocità di messa a disposizione, di solito la soluzione è un compromesso tra la validazione ad ogni uso e l'assenza di validazione (dove la prima variante è a volte scelta, mentre la seconda è da evitare). I livelli di necessità sono differenziati in 4 livelli:
- Critico: es. i dati di pazienti di un ospedale
- Alto: es. i dati di analisi raccolti da un e-commerce
- Medio: es. o dati raccolti da un motore di ricerca
- Basso: es. i messaggi in blog, forum o social media in generale

### Disponibilità
L’accesso ai dati deve essere il più possibile costante. Richiede l’implementazione di pratiche di ridondanza di servizi, link e gateway. Alcuni momenti in cui la disponibilità dei dati diventa un parametro critico sono:
- Manutenzione (a volte)
- Disastri naturali
- Attacchi informatici
- Danneggiamenti dell’hardware

Buone pratiche per evitare un’interruzione di disponibilità nei casi sopracitati sono:
- Creazione di dati di backup multipli (almeno 2)
- Monitoraggio costante
- Pianificazione delle procedure in caso di disastri
- Testing dei backup
- Aggiornamento dei software e del sistema operativo
- Manutenzione degli equipaggiamenti (hardware)
- Implementazione di nuove tecnologie
- 

## Stato dei dati
Lo stato dei dati descrive la posizione del dato, o il suo stato di movimentazione. Questa informazione è particolarmente utile per capire quali meccanismi di attacco potrebbero cercare di entrare in contatto con il dato stesso, relativamente al dispositivo che lo contiene, al mezzo che lo trasporta, al protocollo nel quale è incapsulato, ecc.

### A riposo
Per **dato a riposo** si intende un dato che è memorizzato su un supporto fisico e non è in atto nessun processo di richiesta di visualizzazione, uso o modifica su di esso. I supporti che contengono dati a riposo possono essere:

#### DAS
I Dispositivi Attaccati Direttamente (Direct-Attached Storage) sono dispositivi che necessitano di una connessione ad un supporto per poter manipolare i dati che contengono (es. una chiavetta USB o un Hard Drive). Di default i sistemi non sono impostati per condividere i DAS con altri computer all'interno della rete (ovvero un DAS è utilizzabile solo dal computer al quale è connesso)

#### RAID
La Matrice Ridondante di Dischi Indipendenti (Redundant Array of Indipendent Disks) è un dispositivo che connette diversi dischi di memoria e li unisce logicamente, così che un dispositivo connesso visualizzi un solo elemento connesso. Questa tecnologia permette di migliorare le performance e la tolleranza agli errori. I RAID sono categorizzati a livelli, in base al numero di dispositivi che lo compongono:

| Livello del RAID | n. minimo di componenti | Descrizione                                                                                                                                                                          | Vantaggi                                                                                                             | Svantaggi                                                                               |
| ---------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| 0                | 2                       | [Striping dei dati](https://www.ibm.com/docs/it/xl-fortran-aix/16.1.0?topic=striping-data) senza ridondanza                                                                          | Alte performance                                                                                                     | - Nessuna protezione dei dati<br>- il guasto di un dispositivo comporta perdita di dati |
| 1                | 2                       | Mirroring del disco                                                                                                                                                                  | - Alte performance<br>- Alta protezione dei dati                                                                     | Alti costi di implementazione                                                           |
| 2                | 2                       | Codice di correzione degli errori                                                                                                                                                    | Non più utilizzato                                                                                                   | Un RAID 3 offre le stesse performance a costi ridotti                                   |
| 3                | 3                       | Data striping a livello di byte con [parity](https://www.pcmag.com/encyclopedia/term/raid-parity#:~:text=Parity%20computations%20are%20used%20in,about%20XOR%2C%20see%20OR) dedicata | Per molte e frequenti richieste di dati                                                                              | Non supporta lettura e modifica multiple dei dati                                       |
| 4                | 3                       | Data striping a livello di blocco con parity dedicato                                                                                                                                | - Supporta richieste di lettura multiple<br>- Utilizzo di parity nel caso di guasto di un dispositivo per duplicarlo | Le richieste di lettura creano un collo di bottiglia a causa della parity dei dati      |
| 5                | 3                       | Combinazione di data striping e parity                                                                                                                                               | - Supporta lettura e scrittura multiple<br>- I dati sono scritti su tutti i dispositivi                              | Le performance di scrittura sono più lente dei RAID di livello 0 e 1                    |

- Mirroring: Crea un duplicato del dato su almeno due dispositivi
- Striping: Il dato viene letto in sequenza da più dispositivi
- Striping con parity: Dopo lo striping viene effettuato un checksum per verificare l'assenza di errori (che poi verr° salvato su un terzo disco) 

#### NAS
La Memoria collegata alla rete (Network Attached Storage) consiste in un dispositivo di memorizzazione, collegato all'intera rete. In questo caso i dati sono direttamente accessibili da qualunque dispositivo sia connesso alla medesima rete. 
I NAS sono flessibili e facilmente scalabili.

#### SAN
Le Reti ad area di memoria (Storage Area Network) sono architetture di dispositivi di memorizzazione organizzati in una rete e collegati tra loro tramite interfacce ad alta velocità. Questo permette di collegare agevolmente più server con la stessa SAN.

#### Cloud Storage
Il [Cloud storage](<server/cloud server>) è un metodo di immagazzinamento dati in remoto, che utilizza dei data center per immagazzinare i dati. Alcuni esempi di cloud storage sono Google Drive, Dropbox, iCloud.


### In transito
Il transito descrive il processo di invio dei dati da un dispositivo ad un altro. Due fattori cruciali per l'analisi dei dati in transito sono la [rete](tecnologie/reti) e i [protocolli](tecnologie/protocolli) utilizzati per gestire il transito dei pacchetti all'interno della rete stessa.

#### Rete
##### Sneaker net
Consiste nell'utilizzo di [dispositivi DAS](#DAS) per trasportare i dati.

##### Rete cablata
La [rete cablata](tecnologies/reti#lan) utilizza cavi e dispositivi di trasporto (es. Switch) per collegare i dispositivi tra loro.

##### Rete wireless
La [rete wireless](tecnologie/reti#wlan) utilizzano onde radio per trasmettere i dati. Hanno meno possibilità di controllo delle reti cablate, in quanto non necessitano di un supporto fisico di collegamento alla rete.



#### Confidenzialità
Proteggere la confidenzialità dei dati significa utilizzare protocolli di trasmissione che impediscano ad utenti terzi la lettura dei dati qualora intercettati (di solito tramite cifratura)

#### Integrità
Proteggere l'intero pacchetto da manomissioni e/o perdite di pacchetti. Di solito avviene tramite ridondanza e cifratura dei dati.

#### Disponibilità
Bisogna assicurare sia l'accesso al dato dal punto di vista di accesso al servizio, che di continuità di utilizzo (e quindi impedire ad attori terzi di utilizzare punti di accesso alla rete per impedire un processo di comunicazione già in atto). Un meccanismo efficace è la reciproca autenticazione tra server e client. 

### In processo
Il processo dei dati include 3 fasi: immissione, modifica e output. Ognuna di queste ha le proprie criticità.

#### Input
Momento nel quale il dato viene inserito  (o creato). In questo momento è particolarmente importante gestire l'integrità del dato da corruzione (che può avvenire, ad esempio, per errore di comunicazione, attacco da parte di terzo o semplice errore umano).

#### Modifica
La modifica può avvenire sia per mano umana, che per processo (es. cifratura dello stesso prima dell'invio nella rete). Una non corretta gestione del dato in questo stato, ne provocherebbe la corruzione.

#### Output
Stato nel quale il dato viene preparato per il trasporto (es. inserimento del dato all'interno di un pacchetto con un determinato protocollo o la non corretta configurazione di una stampante)

## Salvaguardie
### Persone
### Tecnologia
#### Ridondanza della localizzazione
Viene effettuata in maniera:
- Replicazione (richiede grandi ampiezze di banda e la vicinanza tra le due localizzazioni per ridurre la latenza)
- Replicazione asincrona (richiede più tempo, ma non viene afflitta da questioni di latenza)
- Replicazione Point-in-time: Aggiornamenti e backup vengono effettuati periodicamente.

### Policy e pratiche

## Contromisure
### Tecnologia

### Policy
Le policy sono uno strumento efficace per stabilire delle linee guida comportamentali o di utilizzo di risorse a livello aziendale. Possono essere suddivise in base al target di cui si occupano.

#### Aziendali
Stabiliscono le regole di condotta e le responsabilità di dipendenti e dirigenti, cercando al contempo di proteggere i diritti dei lavoratori e gli interessi aziendali. Possono coprire un'ampia varietà di tematiche (dalla condotta, al dresscode, alla privacy).

#### Lavorative
Definiscono aspetti quali remunerazione, date di pagamento, benefit dei dipendenti, orari lavorativi, ferie e altro. Spesso richiedono una firma di presa visione e accettazione da parte dei dipendenti.

#### Conoscenza

#### [Sicurezza](<#policy di sicurezza>)
Definiscono degli obiettivi di sicurezza da raggiungere e degli standard (tecnologici e comportamentali) da mantenere. Permettono di definire una linea base di comportamento della rete, sotto condizioni di carico normale. Di solito si tratta di un documento in costante evoluzione per adattarsi alle tecnologie presenti e alle esigenze aziendali.

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

# Attacco
## Introduzione
Un attacco informatico è un’azione che sfrutta determinate falle (fisiche o logiche) di una rete per ottenere accesso e/o eseguire azioni dannose per la rete stessa. Principalmente gli attacchi sono di due tipi:
- APT (Minacce Persistenti Avanzate) sono attacchi elaborati eseguiti a ripetizione (come il [DoS](#DoS)), effettuati di solito per analizzare o ottenere l’accesso ad una rete bersaglio. Questo tipo di attacchi di solito richiede una forte organizzazione e alte risorse economiche per essere effettuato
- Attacchi Algoritmici, ovvero attacchi che sfruttano falle logiche o usano in maniera non convenzionale determinati componenti, per causare comportamenti non previsti alla macchina (es. la forzatura dell’uso totale della RAM per forzare l’arresto di un computer).

Gli attacchi possono essere differenziati per **domini** di interesse e per **livelli** di comunicazione (di solito viene utilizzato il modello OSI) soggetti all’attacco. Un terzo metodo di categorizzazione degli attacchi è la motivazione alle loro spalle. Per quest’ultimo caso, esiste una classificazione standardizzata: la IOA (Indicatore d’attacco).

## Superficie di attacco
E' detta Superficie d'attacco l'insieme di punti d'accesso che possiedono delle vulnerabilità. Possono essere suddivisi in:
- Superficie d'attacco della rete
- Superficie d'attacco software
- Superficie d'attacco umana (potenzialmente chiunque abbia accesso alla rete o a informazioni su come accedere alla rete). Campo d'azione di attacchi di [social engineering](<#social engineering>)

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



## Reti

### WLAN
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

# Weakness
Le **debolezze** sono tutti quei problemi specifici che riducono la sicurezza di un sistema (anche nel caso non vengano sfruttate).

## Applicazione
### Improper Restriction of XML external entity Reference
[Improper Restriction of XML external entity Reference](https://cwe.mitre.org/data/definitions/611.html).

Si verifica quando un entità XML contiene collegamenti ad altre entità XML non previste dal sistema, che permettono di inserire script malevoli per prelevare dati.


## Fisico
# Vulnerability
Le **Vulnerabilità** sono tutti quegli attacchi (conosciuti e non) che possono essere effettuati, sfruttando le **[debolezze](#weakness)**.

# Defense-in-Depth

## Classificazione
La classificazione delle risorse consiste nel raggruppare le risorse in base a caratteristiche comuni. Le informazioni più critiche hanno bisogno di ricevere il livello più alto di protezione e quindi (potrebbero) richiedere di essere trattate in maniera particolare. Un utile metodo per categorizzare le risorse è il cosiddetto *labeling*, ovvero etichettatura, che può essere effettuato tramite i seguenti passi:
1. Determinare la categoria più appropriata per una risorsa, in base a:
	- Informazioni sulla risorsa
	- Software utilizzati dalla risorsa
	- Hardware utilizzati dalla risorsa
	- Servizi
2. Stabilire il livello di [responsabilità](<#zero-trust model>) della risorsa tramite l'identificazione del proprietario di ogni informazione e ogni parte di software
3. Stabilire il criterio di classificazione, ad esempio in base a:
	1. Confidenzialità
	2. Valore
	3. Tempo
	4. Diritti di accesso
	5. Distruzione
4. Implementare uno schema di classificazione che permetta di identificare in maniera efficace le informazioni ed assicurare una protezione uniforme e facile da monitorare
## Standardizzazione
La standardizzazione di risorse software e hardware permette di facilitarne la manutenzione ed il monitoraggio.

## Ciclo di vita
Ogni risorsa ha un suo ciclo di vita. E' importante per un tecnico capire a che punto del ciclo di vita è ogni risorsa, così da poter pianificare il da farsi. Di solito il ciclo di vita viene suddiviso in:
1. Acquisizione della risorsa in base alle sue caratteristiche e sistemazione nell'inventario
2. Installazione e analisi della stessa (anche tramite marchiatura di identificazione, tipo codice a barre o targhetta RFID)
3. Uso e continuo monitoraggio e analisi della stessa
4. Manutenzione (o eventuale aggiornamento) quando necessario
5. Smaltimento (con previa rimozione di tutti i dati contenuti), che può avvenire per intero, o per parti della risorsa (anche in base alle linee guida del prodotto)

## Identificazione delle vulnerabilità
Le [vulnerabilità](#vulnerabilità) devono essere analizzate e monitorate frequentemente, in base a tutte le specifiche della rete (intesa come dispositivi, collegamenti, software, ecc.) e della tipologia di azienda (che incide sul tipo di dati trattati, sulle interazioni con i clienti, sul valore dei dati stessi).

L'identificazione delle vulnerabilità deve tener conto del fatto che gli attacchi possano anche presentarsi come:
- Compromissione del sistema interno
- Furto di dati dei clienti
- False transizioni da un server esterno
- False transizioni effettuate usando credenziali rubate
- Errori di input dei dati
- Distruzione del data center

## Identificazione delle minacce
L'identificazione delle minacce avviene tramite un meccanismo a strati, dove lo strato esterno è rappresentato dall'*edge router* (il router che collega la rete alla WAN), il secondo dal firewall, il terzo i router interni e così via, mentre gli asset sono racchiusi al centro dello schema.

### Security onion
Comunemente si compara il metodo a livelli con una cipolla, per far comprendere come i vari livelli di protezione lavorano per filtrare le minacce prima che esse riescano ad arrivare agli asset.

### Security artichoke
Il metodo a cipolla, con il passare del tempo, si è evoluto per tenere conto del fatto che i meccanismi di protezione spesso non coprono l'intera superficie della rete, bensì solo una porzione. Il nuovo schema prende il nome di schema a carciofo, dove ogni petalo rappresenta un meccanismo di protezione, che però non copre la totalità dei livelli inferiori, bensì solo una porzione (es. le password proteggono l'accesso di utenti estranei che provano ad accedere tramite login, ma non blocca gli attacchi man-in-the-middle o gli attacchi provenienti dall'interno).

## Strategie
Ci sono diverse tipologie di strategie per organizzare una difesa profonda (in-depth) della rete (da utilizzare in combinazione).

### Stratificazione
La stratificazione (**layering**) consiste nel realizzare diversi livelli di protezione a difesa della rete e degli asset.

### Limitazione
Limitare l'accesso alle risorse allo stretto necessario. Un'esempio è la politica [zero-trust](<#zero-trust model>)), o la politica di consultazione dei dati in loco (di norma una stanza monitorata), senza dare la possibilità di portare i dati all'esterno.

### Diversificazione
Non posizionare livelli simili accoppiati ma, appunto, diversificarli, così che un attaccante non sia agevolato nel sorpassare due livelli consecutivi applicando il minimo sforzo (rendendo il secondo livello pressoché inutile).

### Oscuramento
Ovvero non dare possibilità agli attaccanti di scoprire informazioni relative ai dati tramite messaggi di log o messaggi di sistema.

### Semplicità
Preferire meccanismi semplici, ma efficaci di protezione, evitando l'utilizzo di meccanismi troppo complessi da impostare, che potrebbero ritorcersi contro il team di sicurezza stesso per problemi di configurazione, o altro. Preferire invece soluzioni che siano facili da utilizzare, ma complesse da attaccare.

# Strumenti di analisi
## log
I log sono file che tengono traccia di avvenimenti all’interno della rete. Gli eventi di solito monitorati tramite log possono essere categorizzati in:
- Log di applicazioni
- Log di eventi
- [Log di servizi](<#log di servizi>)
- Log di sistema

## SOC
Il Centro Operativo di Sicurezza è
### Obiettivi
Il SOC deve assolvere a varie mansioni (con l’aiuto di specifici tools), ovvero:
- Osservare e comprendere ogni dettaglio delle transazioni che avvengono all’interno della rete
- Avere un ambiente sicuro per eseguire e osservare i malware
- Analizzare il traffico in tempo reale per identificare eventuali intrusione all’interno della rete
- Aggiornare le regole del firewall
- Impostare un soldi sistema di log, che copra tutte le aree principali di interesse
- Monitorare costantemente i log della rete
- Utilizzare un sistema di gestione dei ticket per segnalare e registrare le azioni e/o analisi

## Software
###  Static application security testing
#SAST
- [[SonarQube]]: Software che effettuano un'analisi statica del codice, effettuano #code-smell (verifica l'utilizzo anomalo di alcuni elementi)
- Lynis: Software open source di auditing
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
### Introduzione
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

#### Tipologie
Ci sono 3 tipi di anti-malware, catalogati in base al meccanismo utilizzato per identificare i malware

##### Signature-based
Si basano sul riconoscimento di una **firma**, ovvero delle caratteristiche di file di malware conosciuti.

##### Heuristics-based
Identificano il malware in base alla presenza di caratteristiche generali, condivise tra i malware.

##### Behavior-based
Si basano sull'analisi comportamentale per verificare e identificare i malware.

#### Network-based
Questi anti-malware permettono di monitorare e proteggere l'intera rete su cui sono installati. Sono composti da più elementi, ognuno dei quali ricopre uno specifico ruolo:
- [AMP](#amp): Protezione Avanzata dai Malware, ha lo scopo di proteggere gli end-point della rete
- [ESA](#esa): Apparecchio di Sicurezza delle Email, si occupa di proteggere da spam e email potenzialmente infette prima che raggiungano l'endpoint
- [WSA](#wsa): Apparecchio di Sicurezza Web, permette di filtrare i siti web, prevenire l'accesso a siti specifici agli utenti ed effettuare una scansione per i malware
- [NAC](#nac): Controllo di Ammissione alla Rete, permette l'accesso alla rete solo alle persone autorizzate

### Antivirus
Monitora di continuo il pc e, in caso riconosca un virus, lo mette in quarantena  o lo elimina

### Anti-adware
Cerca programmi che espongano pubblicità all'interno del computer

### Anti-phishing
Blocca gli indirizzi IP di noti siti di Phishing e avvisa l'utente riguardo i sisti sospetti

### Anti-spyware
Programma che cerca keyloggers e altri spyware


## Autenticazione
Meccanismo che permette di identificare un utente in base a parametri condivisi (di solito nome utente e password). I [protocolli di autenticazione](./tecnologie/protocolli#autenticazione) più utilizzati sono:

| Protocollo | Certificati client | Certificati server | Deploy    | Sicurezza |
| ---------- | ------------------ | ------------------ | --------- | --------- |
| EAP-TLS    | Si                 | Si                 | Difficile | Alto      |
| PEAP       | No                 | Si                 | Media     | Media     |
| EAP-TTLS   | No                 | Si                 | Media     | Media     |
| EAP-FAST   | No                 | No                 | Facile    | Media     |
### Gestore delle autenticazioni
#### SSO
Il Single Sign On (accesso singolo) permette di accedere a più servizi tramite singolo set di credenziali (es. gmail e youtube)

#### OAuth
Appoggio a gestori terzi per la gestione delle credenziali di accesso (es. login tramite google)

#### Gestore delle password
Software che permette di salvare le coppie di credenziali di accesso e collegarle all'applicazione per la quale vengono utilizzate

#### KBA
La Knowledge-Based Authentication (autenticazione bassata sulle conoscenze) consiste nell'utilizzo di informazioni personali per garantire l'accesso. Di norma viene utilizzato per le procedure di cambio password.

#### HMAC
l'Hash Based Message Authentication Code (messaggio con codice di autenticazione basato sull'hash) è un processo che utilizza la cifratura dei dati per produrre un achiave di accesso temporanea all'utente (di solito valida per una singola sessione o per un periodo di tempo limitato). Viene spesso utilizzata per mantenere una sessione aperta durante la navigazione nel web e fornire allo stesso tempo un controllo dell'integrità dei dati.

### Mutual authentication
L'autenticazione ambivalente consiste in un duplice processo di autenticazione: sia client-server che server-client. Questo ulteriore passaggio fornisce un meccanismo di protezione aggiuntivo contro attacchi di tipo [man-in-the-middle](#man-in-the-middle) tramite [rogue access point](<#rogue access point>).


## NSI
L’Infrastruttura di Sicurezza della Rete definisce le modalità con le quali i dispositivi devono essere collegati tra loro per assicurare un buon livello di sicurezza end-to-end. 
### ACL
La Lista di Controllo degli Accessi consiste in una serie di comandi che controlla quando un pacchetto deve essere inoltrato e quando deve essere bloccato, in base alle informazioni trovate nell’header del pacchetto. Un ACL svolge le seguenti funzioni:
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
Firmware che permette di stabilire se un sistema possa essere considerato affidabile, o se sia stato modificato durante la fase di avvio o caricamento.
viene salvato un firmware (un software che esegue semplici funzioni di base del computer) all'interno della scheda madre e viene eseguito come primo passaggio dal computer.
### Secure Boot
E' stata creata una nuova Interfaccia di Firmware Unificata ed Estensibile (UEFI) come nuova versione di BIOS, che definisce la nuova interfaccia standard per operazioni tra firmware, sistema operativo e device esterni (funziona solo in modalità 64-bit). 

Il firmware controlla l'affidabilità di ogni parte del software di avvio, inclusi i driver di firmware UEFI, le applicazioni UEFI e il sistema operativo. Se le firme sono valide, il sistema si avvia.

### Measured Boot
Provvede un protocollo di validazione più forte del Secure boot, in quanto misura tutti i vari componenti e ne salva un log all'interno del chip TMP, che potrà essere utilizzato per effettuare test di controllo da remoto. Permette anche di identificare applicazioni non fidate e di caricare prima gli anti'malware.

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
I Sistemi di Prevenzione dell'Intrusione di Host sono software che monitorano l'attività del dispositivo e ricerca la presenza di attacchi conosciuti, anomalie o segnali di allarme tramite all'interno dei pacchetti in transito. Nel caso identifichi un'attività sospetta, il software allerta l'utente, logga l'attività sospetta, resetta la connessione e, in caso, effettua il drop del pacchetto.

Gli HIPS sono categorizzati anche in base alla metodologia utilizzata per l'identificazione dei malware

#### Anomaly-based
Questi HIPS monitorano il comportamento dell'utente, comparandolo ad una linea di comportamento base (creata analizzando il comportamento dell'utente e il comportamento della rete), creando dei log in cui inserire dei dettagli relativi. Il rischio più comune con l'utilizzo di questi sistemi è l'eccessivo numero di falsi positivi, che comportano un abbassamento della credibilità della rete e uno spreco di tempo da parte del team di sicurezza.

#### Policy-based
Il comportamento normale è descritto tramite regole e la violazione di queste fa scattare l'allarme, che registra la violazione in un log e avvisa il personale della violazione.
Molti HIDS di questo tipo sono già forniti di un set di regole, implementabili dall'amministratore di sistema.

#### Software
- OSSEC: Open Source HIDS SECurity
- AlienVault
- Cisco AMP
- Tripwire

### EDR
L'Endpoint Detection and Response è una soluzione che monitora costantemente il dispositivo endpoint e ne raccoglie dati. Analizza i dati raccolti e risponde a tutte le minacce identificate.
Mentre un [antivirus](#antivirus) permette solo di bloccare l'accesso di un virus, un EDR può anche identificare le minacce presenti già all'interno del dispositivo.

### DLP
Il Data Loss Prevention (Prevenzione della Perdita di Dati) è un software che serve ad assicurare che i dati sensibili non vengano persi, utilizzati in modo errato o visualizzati da utenti non autorizzati.

### NGF
I Firewall di nuova generazione (New Generation Fierewall) sono dispositivi che combinano le classiche funzionalità di un firewall con altre funzionalità di filtraggio degli host all'interno della rete tramite inline Deep Packet Inspection(DPI, Ispezione profonda dei pacchetti) o sistemi IPS (Sistema di Protezione dalle Intrusioni).

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

Alcuni esempi di HBF sono:
- [Windows Defender Firewall](os/windows#firewall)
- [iptables](os/linux#iptables)
- [nftables](os/linux#nftables)
- [TCP Wrappers](<os/linux#tcp wrappers>)

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

### HIPS
Gli IPS basati sull’host (Host-based IPS) sono software da installare su dispositivi per monitorare e proteggere i sistemi operativi. Tra le loro funzionalità includono:
- La possibilità di bloccare azioni effettuate dall’utente nel caso divergano dai suoi comportamenti abitudinari (come la modifica di file di sistema)

Un particolare di cui tenere conto è che gli HIPS monitorano l’attività dell’endpoint su cui sono installati.

### NIPS
Gli IPS basati sulla rete (Network-based IPS) possono essere implementati su un dispositivo dedicato o su un dispositivo non dedicato e sono elementi indispensabili per la sicurezza della rete.

## Host encryption
L'esempio più noto è l'[EFS](../os/windows#efs) (Windows Encrypting File System, ovvero Sistema di Crittazione dei File), che permette, appunto, di crittare file, cartelle, o l'intero hard drive.
In quest'ultimo caso (noton anche come FDE, o Full-Disk Encryption), Windows si appoggia a BitLocker, che permette di utilizzare il BIOS come Modulo di Piattaforma Fidata (TPM).
Il TPM è un chip specializzato, presente nella scheda madre, che salva le informazioni relative al sistema dell'host, come;
- Chiavi di crittazione
- Certificati digitali
- Misure di integrità del sistema
BitLocker To Go permette di cifrare dispositivi rimuovibili senza l'uso del TPM.
## NAC
I Network Access Control (Controllo degli Accessi nella Rete) sono dispositivi addetti alla gestione del [controllo degli accessi](<#controllo degli accessi>) dell'intera rete e permettono di controllare tramite un'unica interfaccia le politiche di accesso di utenti, dispositivi ed accesso manuale. Con l'avvento degli IoT, l'utilizzo dei NAC è diventato sempre più utile.
Tramite un NAC è possibile:
- Implementare nuove politiche di accesso alla rete velocemente
- Riconoscere e profilare gli utenti e i dispositivi connessi per prevenire a malware di danneggiare il sistema
- Fornire accesso sicuro alla rete a guest (spesso previo passaggio da portali di registrazione)
- Valutare il rispetto delle policy per tipo di utente, di dispositivo e di sistema operativo
- Mitigare gli incidenti tramite blocco dell'accesso o isolamento per dispositivi che non rispettano le politiche

## Patch Management
Le patch sono aggiornamenti di software per risolvere [vulnerabilità](#weakness) presenti nel software stesso. Di solito il sistema operativo controlla e installa automaticamente le patch.
A livello aziendale, spesso gli aggiornamenti vengono analizzati dal team di Cybersecurity prima di venire installati nei dispositivi all'interno della rete. Per facilitare questo compito, esistono i Patch Manager, ovvero software che permettono una gestione facilitata degli aggiornamenti delle patch, grazie al controllo tramite un'unica piattaforma la gestione delle patch per tutti i dispositivi della rete.

## Policy di sicurezza
La Security Policy è un documento che raccoglie le varie politiche informative per l’utente, lo staff IT e i manager, riguardo i requisiti di protezione delle tecnologie e informazioni all’interno di un’azienda. I principali tipi di Policy sono:
- Specifiche sull’autenticazione e l’identificazione degli utenti
- Impostazioni riguardanti la password (lunghezza, tipo di caratteri, altre specifiche)
- Definizione dei comportamenti ammessi nell’azienda 
- Requisiti per l’accesso da remoto alla rete aziendale

Riferiti al team IT, due documenti sono particolarmente importanti:
- SOP (Standard Operating Procedure) o procedure per le operazioni standard
- Linee guida: coprono le aree non incluse nelle SOP

### Identificative
Specificano in dettaglio:
- L'elenco delle persone (o dei gruppi di persone) autorizzate ad avere accesso alla rete e alle risorse (che sia accesso totale o parziale)
- I metodi di autenticazioni richiesti per avere accesso alla rete

### Password
Specificano i criteri minimi di composizione di una password. Un criterio solitamente utilizzato è:
- Lunghezza: minimo 8 (o in alcuni casi 12) caratteri
- Almeno una lettera in minuscolo
- Almeno una lettera in maiuscolo
- Almeno un carattere numerico
- Almeno un carattere speciale
- Non includere parole facilmente riconducibili a te
- Non includere date

### AUP
Le Acceptable Use Policy (Politiche di utilizzo accettabile) definiscono le applicazioni di rete ritenute accettabili dall'azienda. Può contenere ramificazioni per descrivere conseguenze, o azioni da intraprendere, nel caso le politiche vengano disattese.

### Accesso da remoto
Le politiche di accesso da remoto definiscono le modalità di accesso e la tipologia di asset disponibili durante l'accesso da remoto.

### Manutenzione della rete
Specifica i dispositivi connessi alla rete, i rispettivi sistemi operativi utilizzati e le procedure di aggiornamento dei software e dei dispositivi stessi.

### Gestione degli incidenti
Descrive le procedure di azione nel caso di incidenti e il modo con il quel gli stessi vanno gestiti.

### BYOD
Le Bring Your Own Device Policies (porta il tuo dispositivo) descrivono le modalità di accesso alla rete da parte dei dipendenti tramite dispositivo personale. Le BYOD trattano un tema particolarmente importante perché, mentre da un lato agevolano il dipendente, permettendogli di accedere in maniera più agevole alla rete, anche da remoto, potenzialmente aumentano la superficie di attacco della rete stessa.

I temi da specificare nelle BYOD sono:
- Obiettivi
- Quali utenti possono utilizzare i dispositivi personali
- Quali dispositivi sono supportati
- Il livello di accesso dei dati dagli utenti tramite dispositivi personali
- I diritti di accesso e le attività permesso tramite dispositivi personali
- Regole da rispettare durante la navigazione con dispositivo personale
- Linee di salvaguardia da usare nel caso di compromissione del dispositivo

Delle buone pratiche da includere nelle BYOD sono:
- Usare password uniche per ogni dispositivo
- Spegnere connessione WiFi e Bluetooth quando non in uso
- Tenere sempre aggiornati i software installati e il sistema operativo
- Abilitare il backup in caso di furto o danneggiamento del dispositivo
- Abilitare il servizio "Trova il mio dispositivo"
- Utilizzare un antivirus
- Usare un software MDM (Gestione dei Dispositivi Mobile) per permette al team di sicurezza di monitorare il dispositivo quando connesso alla rete

### INFOSEC
Policy di condotta strettamente legate agli impiegati nel settore di Sicurezza dei Sistemi Informativi

## Hardening
L’hardening consiste nell’’implementare metodi comprovati per incrementare la sicurezza dei dispositivi. Le best practices includono:
- Assicurare la sicurezza fisica
- Ridurre al minimo i pacchetti installati
- Disabilitare i servizi inutilizzati
- Utilizzare SSH e disabilitare il login all’account root da SSH
- Mantenere il sistema aggiornato
- Disabilitare l’identificazione automatica dei dispositivi USB
- Utilizzare password forti
- Obbligare a cambiare la password periodicamente
- Non permettere il riutilizzo della password

E' sempre consigliabile:
- Considerare una soglia minima delle prestazioni del sistema in condizioni normali per utilizzarlo come parametro di notifica per potenziali attacchi
- Tenere un approccio sistematico per catalogare gli aggiornamenti di sistema
- Amministrare la rete utilizzando le best practices
- Fare particolarmente attenzione ad attacchi fileless, in quanto non lasciano traccia nel sistema (ma operano direttamente a livello di memoria e terminano quando il sistema si riavvia)

## Protezione fisica
Le misure di sicurezza fisiche hanno lo scopo di impedire fisicamente al personale non autorizzato ad accedere a specifiche aree (come la server room, o l'edificio stesso nel caso di persone che non siano dipendenti o ospiti)

### Barriere fisiche
Sono  elementi come recinzioni, mura o tornelli. Lo scopo è impedire il passaggio del personale non autorizzato (di solito è richiesta la presenza di almeno un'elemento di [sorveglianza](#sorveglianza) gestire gli accessi nelle aree il cui passaggio è consentito, come le porte). La tipologia di barriera può differire in base alla legislazione dell'area o dalle disponibilità economiche aziendali.

### Biometria
I dati biometrici sono dati relativi caratteristiche comportamentali o fisiologiche degli individui. Ci sono misure di sicurezza che analizzano i dati biometrici delle persone per verificarne l'identità. Alcuni esempi possono essere:
- telecamere
- scanner di retina
- scanner di impronte digitali
- scanner facciali

Durante la scelta del dato biometrico da monitorare, c'è da considerare:
- Accuratezza
- velocità di analisi
- unicità dell'elemento analizzato
- resistenza alle contraffazioni
- affidabilità
- requisiti di memorizzazione dei dati
- tempistiche di scansione
- intrusività dell'analisi

I scansori di dati biometrici possono dare 2 tipi di errori diversi:
1. Una persona autorizzata viene erroneamente respinta. E' il tipo meno grave di errore (con alcune eccezioni)
2. Accesso consentito a persone che non ne avrebbero diritto. Dato rappresentato come valore percentuale
### Badge
Permette la verifica automatica dell'utente (senza bisogno di personale umano per la verifica del dato, come nel caso della biometria).

### Sorveglianza
#### Videocamere
L'utilizzo di videocamere per monitorare le persone ed il flusso degli accessi è un metodo efficace di protezione fisica. Hanno l'ulteriore beneficio di poter memorizzare i dati per un successivo monitoraggio. Le videocamere dovrebbero essere posizionate puntando a tutti gli ingressi/uscite, le porte, i vani /ascensore e aree destinate alla raccolta dei rifiuti.

#### Guardie
Personale addestrato che gestisce gli accessi ad un determinato luogo. Alcuni svantaggi possono essere l'elevato costo e la difficoltà nel gestire grandi flussi di persone.

#### RFID
Operano con un meccanismo fisicamente simile al badge (l'elemento deve essere esposto vicino uno scanner dall'utente), ma avente tecnologia diversa (Radio Frequency IDentification, identificazione tramite radiofrequenze) con l'ulteriore beneficio offerto dalla possibilità di tracciare il dispositivo su cui il trasmettitore è installato anche all'esterno dell'area geografica aziendale.


## Reti
Le reti possono essere catalogate in base al livello di fiducia e rischio delle stesse, in base alla tipologia di comunicazioni (e al destinatario delle stesse) in:
- Alto livello di fiducia e rischio basso: LAN
- Medio-alto livello di fiducia e medio-basso livello di rischio: Extranet
- Medio-basso livello di fiducia e medio-alto livello di rischio: DMZ
- Alto livello di rischio e basso livello di fiducia: WAN

### DMZ
L'utilizzo di [DMZ](./reti#dmz) permette di facilitare il controllo della sicurezza della rete, grazie al livello cuscinetto che offre tra la WAN e la LAN. Dato che le connessioni in ingresso con la rete esterna vengono effettuate tutte in questa zona, all'interno della DMZ di solito vengono posizionati:
- Web server
- Mail server

### VLAN
Le [VLAN](./tecnologie/reti#vlan) possono essere soggette ad attacchi che ne possono ridurre le performance e la disponibilità. Per questo è sempre consigliabile l'utilizzo di configurazioni avanzate e l'installazione regolare di patch e aggiornamenti.

### WLAN
Le connessioni WLAN hanno ulteriori rischi: 
- poter essere disturbate e/o intercettate da utenti malevoli (o ricevere altri tipi di disturbi)
- Non avere il pieno controllo degli accessi (chiunque riceva il segnale può potenzialmente connettersi)

Dei meccanismi efficaci di protezione sono:
- utilizzo di meccanismi e protocolli di autenticazione e crittazione (come [WPA2](./tecnologie/protocolli#WEP2), [WPA3](./tecnologie/protocolli#WEP3), [AES](./tecnologie/protocolli#aes))

## Honeypot
Sono sistemi ad esca, configurati per imitare componenti importanti della rete. Hanno il duplice scopo di rallentare l'attaccante e loggare tutte le sue azioni.
Nel caso l'honeypot venga utilizzata per simulare un'intera rete, si parla di **honeynet**.

## DNS Sinkhole
Previene la risoluzione degli hostname per specifici URL. Vengono utilizzati per respingere l'utente da siti malevoli.

## Dispositivi

### Mobile

#### Gestione
Alcune misure di protezione per dispositivi mobile (siano essi personali e abilitati all'utilizzo della rete che aziendali) consiste in:
- Separare lo spazio utilizzato dall'utente in modo personale da quello aziendale (anche tramite container) e proteggere almeno il secondo tramite cifratura
- Utilizzo di un gestore delle identità per monitorare il tipo di dati a cui ha accesso l'utente dal dispositivo
- Utilizzo di una [whitelist](#whitelist) per segnalare le applicazioni che è possibile installare sul dispositivo

#### Protezione
- Utilizzo di codici di sblocco
- Accesso tramite dati biometrici
- Autenticazione consapevole del contesto (tramtie ML per analizzare l'accesso in base al comportamento normale dell'utente)
- Possibilità di ripristino del device da remoto
- Cifratura della memoria dell'intero dispositivo

### IoT
#### Scanner
Sono utilizzati per monitorare lo stato dei dispositivi IoT all'interno di una rete
- Shodan
- 

## Buone pratiche

### Disponibilità
L'obiettivo di fornire alti livelli di disponibilità può essere raggiunto tramite 3 principi:
- Rimozione dei single points of failure
- Backup delle fonti energetiche
- Identificazione dei guasti nel breve periodo.
Lo scopo ideale è il raggiungimento dei cosiddetti Cinque 9, ovvero una situazione in cui la disponibilità della rete è assicurata per il 99.999% del tempo (periodo di downtime pari a 5.26 minuti l'anno). Degli elementi che aiutano in tal senso sono:
- Standardizzazione dei sistemi
- Clustering (ovvero utilizzo di più dispositivi raggruppati per fornitura di ogni singolo servizio)
- Sistema a componenti condivisi
#### Single Point of Failure
Rappresentano i nodi della rete il quale malfunzionamento comporta un blocco dell'intera rete. Uno degli obiettivi principali durante la gestione di una rete è quello di evitarne la presenza (per fornire alti livelli di [disponibilità](#disponibilità)), o duplicare i punti, in modo tale da attenuare le possibilità di failover.

#### Fonti energetiche
E' sempre consigliabile fornire più fonti di energia elettrica e sistemi di backup in caso di arresto di corrente.

#### Identificare i guasti appena si presentano
Tramite attività costante di monitoraggio e pianificazione delle azioni da eseguire nellàeventualità.

### Liste d'accesso
Tenere traccia di indirizzi di particolare interesse per la rete. Ci sono due criteri di creazione della lista. 
#### Blacklist
Registro in cui sono presenti le voci (sotto forma di URL, IP, o altro) a cui negare l'accesso alla rete. E' il criterio più permissivo tra i due, in quanto chiunque non appartenga alla lista ha libero accesso.

#### Whitelist
Registro in cui sono presenti le voci (sotto forma di URL, IP, o altro) a cui consentire l'accesso alla rete. E' il criterio più restrittivo in quanto la regola di partenza è il blocco dell'accesso. Può causare disservizi se non impostata correttamente.

### Protocolli
#### [DHCP](tecnologie/protocolli#DHCP)
- Tenere fisicamente al sicuro il server DHCP
- Installare tutte le patch
- Posizionare il server DHCP dietro un Firewall
- Monitorare le attività del DHCP tramite log DHCP
- Utilizzare un buon antivirus
- Disinstallare tutti i servizi non utilizzati
- Chiudere le porte non utilizzate

#### [DNS](tecnologie/protocolli#dns)
- Tenere il software DNS aggiornato
- Prevenire la rivelazione di informazioni utili dall'URL
- separare server DNS interno ed esterno
- Restringere l'accesso solo agli indirizzi IP conosciuti
- Utilizzare autorizzazioni tramite firma
- Disabilitare (o quantomeno restringere) il trasferimento di zone e aggiornamenti dinamici
- Abilitare i log ed analizzarli
- Utilizzare DNSSEC (Domain Name System Security Extensions)
- Fornire le varie zone di firma

#### [ICMP](./tecnologie/protocolli#icmp)
- Chiudere le chiamate con protocollo ICMP da parte di utenti terzi (che potrebbero utilizzarle per esplorare la rete)

#### [RIP](./tecnologie/protocolli#rip)
- Utilizzare misure sicure di protezione dei router per impedire la manomissione dei settaggi del protocollo RIP

#### [NTP](tecnologie/protocolli#ntp)
- Utilizzare l'autenticazione NTP per verificare che il server NTP sia affidabile.

#### [Telnet](./tecnologie/protocolli#telnet)
- Evitare di utilizzare il protocollo. Preferire [SSH](./tecnologie/protocolli#ssh)

#### [SCP](./tecnologie/protocolli#scp)
Il protocollo Secure Copy permette l'invio di file tramite canale protetto da crittografia (SSH).

#### [SNMP](./tecnologie/protocolli#snmp)
- Utilizzare SMNPv3, in quanto versione più aggiornata, che permette di cifrare i dati

#### [HTTP](./tecnologie/prtotocolli#http)
- Utilizzare [la versione sicura](./tecnologie/protocolli#https), che opera all'interno di una comunicazione [SSL](./tecnologie/protocolli#ssl) o [TLS](./tecnologie/protocolli#tls)

#### [FTP](./tecnologie/protocolli#ftp)
- Utilizzare [la versione sicura](./tecnologie/protocolli#ftps), che opera all'interno di una comunicazione [SSL](./tecnologie/protocolli#ssl) o [TLS](./tecnologie/protocolli#tls)

#### [POP](./tecnologie/protocolli#pop)
- Da utilizzare all'interno di una comunicazione [SSL](./tecnologie/protocolli#ssl) o [TLS](./tecnologie/protocolli#tls)

#### [IMAP](./tecnologie/protocolli#imap)
- Da utilizzare all'interno di una comunicazione [SSL](./tecnologie/protocolli#ssl) o [TLS](./tecnologie/protocolli#tls)

#### [MIME](./tecnologie/protocolli#mime)
- La versione sicura ([S/MIME](./tecnologie/protocolli#s/mime)) fornisce servizi ulteriori di firma digitale, cifratura del pacchetto e servizi di autenticazione, verifica dell'integrità del messaggio e non ripudio.

### Sandboxing
Utilizzare degli ambienti sicuri (es. macchine virtuali non connesse alla rete) per aprire e ispezionare file sospetti. Sono presenti delle opzioni di software disponibili online per tale pratica:
- ANY.RUN
- VirusTotal
- Cisco Threat Grid Glovebox
- Cisco AMP (non permette la creazione di una sandbox, ma permette il rollout del sistema)
- Joe Sandbox
- CrowdStrike Falcon Sandbox

# Mitigazione
## Attacchi di ricognizione
Gli attacchi di ricognizione sono effettuati per analizzare la rete e preparare da attacchi più importanti. Di solito hanno l'obiettivo di raccogliere informazioni e preparare un accesso alla rete per l'attaccante. Questi attacchi sono identificabili e notificabili tramite l'analisi del volume di richieste [ICMP](./tecnologie/protocolli/icmp) per secondo.

La mitigazione di questi attacchi avviene:
- Implementando misure di autenticazione
- Utilizzando la crittografia delle comunicazioni per evitare attacchi di [sniffing](#sniffing) delle comunicazioni
- Utilizzando degli **anti-sniffer** per identificare agli attacchi di sniffing
- Implementare un'[infrastruttura a Switch](https://en.wikipedia.org/wiki/Fully_switched_network)
- Utilizzare [Firewall](#firewall) e [IPS](#IPS)
- Crittare le comunicazioni per evitare attacchi di packet sniffing
- Disattivando gli ICMP echo e eco-reply negli edge-router (da considerare che questa operazione non permetterà di effettuare operazioni di diagnosi della rete)

## Attacchi di accesso
Le misure consigliate di mitigazione sono:
- Utilizzare password forti (almeno 8 caratteri, che contengano almeno un carattere minuscolo, uno maiuscolo, un numero e un carattere speciale)
- Disattivare l'account dopo un numero di tentativi di accesso consecutivi non andati a buon fine
- Implementare politiche di accesso tramite MFA
- Educare gli utenti

Per Identificare questo tipo di attacchi, invece, è possibile:
- Controllare i log degli accessi
- Controllare l'utilizzo di banda della connessione

## DoS
Per verificare se è in corso un attacco [DoS](#DOS) di solito basta controllare la presenza di picchi (o comunque di strani pattern) nel grafico dell'uso della banda. Un attacco DoS può essere anche un campanello di allarme per futuri attacchi più dannosi alla rete.
La maggior parte degli attacchi DoS nella storia sono stati effettuati tramite [indirizzi falsificati](#spoofing).

Ci sono in commercio dei Router con meccanismi di protezione da spoofing, come la [port security], [DHCP snooping], [IP Source Guard], [DAI] (Dynamic Access Resolution Protocol Inspection) e [ACL](./os/linux#ACL)

## Worm
Il processo di mitigazione contro un attacco worm avviene seguendo le fasi:
### Contenimento
Viene compartimentata e segmentata la rete per evitare che il worm continui a diffondersi in tutti i dispositivi della rete. Per effettuare questo processo è richiesto verificare la [Lista di controllo degli accessi](./os/linux#acl) sia per le comunicazioni da che verso i Router e i Firewall della rete.

### Inoculazione
Viene installata la patch dell'azienda produttrice su tutti i dispositivi non ancora infettati dal worm, riducendo così la superficie di attacco del worm.

### Quarantena
Fase che si attua contemporaneamente alla precedente, che consiste nell'isolare i dispositivi infettati dal worm dal resto della rete (tramite disconnessione, blocco o rimozione). 

### Trattamento
I dispositivi infetti vengono disinfettati ed in seguito vengono installate le patch dell'azienda produttrice del sistema operativo che si sta utilizzando. Nei casi più estremi, può essere necessario reinstallare l'intero Sistema Operativo sul dispositivo per evitare con maggiore sicurezza la presenza del worm o dei suoi sottoprodotti.

# Development
## Introduzione
Il Secure Coding consiste nella scrittura di software ponendo particolare attenzione a pratiche o tecniche che permettano di minimizzare o evitare potenziali attacchi.

Le fasi del processo di sviluppo possono essere suddivise in:
- Developing (sviluppo): fase nella quale il codice che compone il software viene scritto e testato
- Staging e produzione: fase nella quale il software viene testato in un ambiente che simula quello reale (es. Windows 11). Passata questa fase il software va in Deploy, ovvero viene caricato sul supporto dal quale verrà reso utilizzabile al cliente
- Provisioning o deprovisioning: consiste nella fase di creazione o aggiornamento del software (il deprovisioning consiste invece nella sua rimozione)

## Normalizzazione
Decomposizione degli input in codice binario, per agevolare l'identificazione di eventuali input malevoli

## Procedura memorizzata
Consiste nell'utilizzare query SQL per memorizzare i dati all'interno di database che eseguono la richiesta. Permette di ridurre il traffico della rete e ottenere i dati richiesti più velocemente.

## Offuscamento
Consiste nel camuffare i nomi dei dati con caratteri casuali in modo da confondere un potenziale attaccante che abbia accesso al codice

## Riutilizzo
Utilizzo di righe di codice già prodotte per ridurre i tempi di realizzazione. Questa pratica é una lama a doppio taglio poichè se utilizza codice sicuro, aumenta la sicurezza del software e riduce gli errori umani mentre, nel caso il codice abbia delle debolezze, esse vengono diffuse anche su altre componenti del software.

## SDK
I Software Development Kit (Kit di Sviluppo Software) forniscono una fonte di codice da riutilizzare per velocizzare lo sviluppo e ridurre i costi di produzione. I pro e i contro sono simili a quelli del [riutilizzo](#riutilizzo)


## Validazione degli input
Pratica che consiste nel sottoporre l'input a varie verifiche prima di processarlo. Una corretta validazione degli input può evitare la presenza di svariate debolezze all'interno del software.

## Regole di validazione
Prima di essere processati dal database, è buona regola che i dati vengano sottoposti a verifiche di rispetto delle regole di validazione come:
- Controllo del numero di caratteri di un dato
- Formato del dato (di solito tramite comparazione con un formato desiderato)
- Consistenza del codice con altri dati correlati
- Rispetto del range di valori richiesto
- Controllo dei valori per evitare errori (es presenza della chiocciola in un indirizzo email)

## Controllo dell'integrità
Avviene tramite verifica di corrispondenza tra un valore ricevuto ed un altro posseduto (o calcolato).

### Checksum
Processo che consiste nella suddivisione di un dato e conversione delle varie porzioni in valori numerici. I valor numerici vengono sommati tra loro ed il valore viene incluso nel pacchetto. Una volta ricevuto il pacchetto, il valore viene ricalcolato dal destinatario e comparato al valore della somma ricevuto. Nel caso i valori corrispondano, il checksum darà riscontro positivo.

### Hash
Utilizzo di algoritmi complessi che permettono di trasformare il dato in maniera univoca (non possono esistere due dati che diano lo stesso risultato una volta processati dall'algoritmo). La verifica avviene tramite comparazione del dato hashato con un valore ottenuto da un qualunque software di calcolo dell'hash.

#### Algoritmi
Evitare algoritmi datati come:
- SHA-1
- MD5

Preferire invece quelli come:
- SHA-256 (o maggiori)

### Version control
Processo che permette di evitare errori prodotti dalla modifica simultanea di un file tramite creazione di un codice univoco per ogni salvataggio. Se un file viene modificato da due utenti diversi, al secondo utente che salverà il file, verrà impedito il salvataggio e verrà richiesto di aggiornare il file con il salvataggio precedente prima di poter inviare i cambiamenti.

## Backup
Meccanismo di salvataggio su più localizzaizioni dello stesso dato. Di solito viene effettuato ad archi temporali costanti e permette di avere una copia del dato da utilizzare nel caso di corruzione dello stesso nella memoria principale.

## Autorizzazione
Meccanismo che permette di verificare se l'utente specifico ha il permesso di vedere/creare/modificare file situati nella specifica area.

## Firma
Stringa di codice ottenuta tramite hashing del software e resa pubblica. Utilizzabile per verificare che il software utilizzato sia originale e non sia stato manomesso prima dell'installazione.

## Secure cookies
Utilizzo dei cookies tramite protocollo HTTPS.

## Hardening
L’[hardening](#protezione#hardening) in ambito coding, consiste nel rimuovere potenziali falle dalle app sviluppate.

## Front-end
### JavaScript
#### XSS
#### eval()
E' un metodo che permette di inserire stringhe di codice all'interno dell'operazione
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

# Operations
Per operations si intende tutta la parte di gestire la parte di gestione dei servizi.

## Configurazioni
La gestione delle configurazioni consiste nell'identificare, controllare e revisionare ogni implementazione o modifica apportata ad una baseline (linea di riferimento) di un sistema.

La *baseline* delle configurazioni include tutte quelle impostazioni che pongono i pilastri su cui si fonda il prototipo di rete (template tipologico), ad esempio assegnare le stesse impostazioni di partenza a tutti i computer utilizzati da un particolare tipo di utenti, seguendo la documentazione standard aziendale.

### Documentazione
La documentazione della configurazione delle risorse copre aspetti relativi a:
- Schema della rete
- cablaggio
- diagramma del cablaggio
- nomenclatura standard dei dispositivi
- schema degli indirizzi IP

### Log
I [log](#log) vengono utilizzati per tenere traccia delle azioni che avvengono all'interno della rete. E' importante gestirle nel loro ciclo vitale:
- generazione
- trasmissione
- memorizzazione
- analisi
- eliminazione
Due importanti tipologie di log da monitorare sono:
- OS
- Applicazioni di sicurezza
#### OS
I log del Sistema operativo descrivono gli eventi collegati ad azioni come:
- Request del client e response del server per autenticazioni dellàutente avvenute con sucecsso
- Informazioni sulle transizioni (quantità e dimensioni) in un determinato arco di tempo

#### Applicazioni di sicurezza
Questi log sono fornite dalle applicazioni come Firewall, Antimalware, HIPS, ecc.. Questo tipo di log è particolarmente utile per effettuare analisi di auditing, per l'identificazione di trend a breve e lungo termine e per la compilazione della documentazione che dimostri il rispetto delle normative e dei requisiti di legge.

### AAA
I log sei servizi AAA (autenticazione, autorizzazione e responsablilità) includono spesso dati come:
- orario di connessione
- orario di disconnessione
- esecuzione di un comando (con tipo di comando)
- numero di pacchetti
- numero di byte

#### Responsabilità
I log relativi la responsabilità sono spesso divisi per tematica:
- Rete: tutti i protocolli utilizzati nella sessione, inclusi pacchetti e dimensioni
- Connessione: connessioni in uscita create dai clienti (es. SSH)
- EXEC: utilizzo della shell, inclusi nome utente, data, inizio, fine, server utilizzati e indirizzi IP
- Sistema: eventi a tutti i livelli di sistema (es. riavvio, logout, spegnimento)
- Comando: utilizzo di comandi della shell limitati a utenti con privilegi particolari
- Risorse: periodo inizio e fine delle connessioni di utenti che hanno effettuato l'accesso

### Analizzatori di pacchetti
I Packet Analyzers (o Packet Sniffers) sono software utili per monitorare il traffico ed registrare le attività tramite log. Il monitoraggio avviene tramite analisi dei contenuti dei vari pacchetti (sia nel caso di connessioni tramite cavo che wireless) ed effettuare le seguenti funzioni:
- Log del traffico
- Analisi delle problematiche della rete
- Rilevamento di utilizzi errati della rete
- Rilevamento di tentativi di intrusione nella rete
- Isolamento dei sistemi compromessi

# Normativa
## Italia
- AGID
- [Legge 81/2001](https://www.normattiva.it/uri-res/N2Ls?urn:nir:stato:legge:2001;81)
## EU
- GDPR
- DPCM 81/21
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