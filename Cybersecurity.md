#  Introduzione
La cybersecurity si occupa di prevenire e contrastare minacce ai sistemi informatici, che possono essere classificati in:
- Attacchi software
- Errori dei software
- Sabotaggio
- Errore umano
- Furto
- Danni all’hardware
- Interruzione delle utilities (es. interruzione della corrente elettrica)
- [Disastri](#Disastri) naturali

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

Per comprendere le aree di interesse della cybersecurity spesso si fa uso del cosiddetto Cybersecurity Cube (noto anche come Cubo di McCumber), che riassume i punti focali della cybersecurity in 3 gruppi da 3 elementi ciascuno. L'insieme dei gruppi prende il nome di CIA Security Triad ed è descritta all'interno dell'[[#ISO 27000]]

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
Il controllo degli accessi serve a monitorare persone, processi e tecnologie che operano all'interno della rete. Avviene su più livelli, ognuno dei quali deve essere tenuto in considerazione:
- Fisico
- Logico
- Amministrativo

Ogni tipologia di controllo deve essere attuata in base alle effettive esigenze dell'organizzazione e può essere di tipo:
- **Preventivo**: Blocca l'azione in via cautelativa (es. [Firewall](#Firewall))
- **Deterrente**: Punta a scoraggiare l'esecuzione dell'azione
- **Identificativo**: Si adotta a seguito di un attacco, con lo scopo di identificare l'attaccante o la falla di sicurezza
- **Correttivo**: Serve a correggere le conseguenze di un evento indesiderato tramite il reset del sistema ad uno stato funzionale
- **Di recupero**: Ripristina un sistema a seguito di un attacco informatico allo stato precedente
- **Compensativo**: Fornisce opzioni alternative ad altri controlli (es. la supervisione).

Le policy possono essere soggette a forme di controllo di tipo correttivo e di recupero.

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
- [Disastri](#Disastro) naturali
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
Il [Cloud storage](<Cloud.md>) è un metodo di immagazzinamento dati in remoto, che utilizza dei data center per immagazzinare i dati. Alcuni esempi di cloud storage sono Google Drive, Dropbox, iCloud.


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

# Domini
La [[#ISO 27001]] e la [[#ISO 27002]] hanno definito 12 domini della cybersecurity, gestendo rispettivamente gli obiettivi dei controlli e i controlli.

## Risk assessment
Si occupa di determinare i valori qualitativi e quantitativi dei rischi relativi situazioni specifiche o minacce. Il [NIST](#NIST) definisce la valutazione del rischio come
```
Un processo sistematico per decidere il livello di rischio associato a un particolare software o modulo.
```
Un passaggio fondamentale della valutazione del rischio è l'identificazione di tutte le minacce, le vulnerabilità, e il loro collegamento (chiamato *threat-vulnerability pairing*, o accoppiamento minaccia-vulnerabilità). Questo passaggio serve a identificare il profilo di rischio inerente di un'organizzazione.

### Cause
Le cause di un rischio sono identificate come minacce e possono essere classificate in 4 categorie:
- **Avversarie**: provenienti da persone, gruppi di persone, organizzazioni o intere nazioni
- **Accidentali**: azioni che avvengono senza che ci sia una volontà di danneggiare l'organizzazione
- **Strutturali**: causate dal danneggiamento o malfunzionamento delle risorse (siano esse software o hardware)
- **Ambientali**: [disastri](#Disastro) causati da eventi naturali o antropici (tipo incendi)

La procedura di identificazione dei rischi in base alle minacce si chiama [analisi dei rischi](<#Risk Analysis>)

### Valutazione
Le minacce vengono categorizzate in base alla probabilità che esse avvengano e al loro impatto sull'organizzazione. La combinazione di questi due fattori produce un valore di criticità (numerico), utilizzato per ordinarle:
- **Probabilità**: dipende da fattori come la complessità  della rete, le misure di protezione adottate, l'importanza dell'organizzazione (quanto un attaccante può trarre vantaggio dall'attacco)
- **Facilità di identificazione**: Quanto facilmente la vulnerabilità può essere identificata e sfruttata
- **Impatto**: Quanti danni vengono potenzialmente prodotti dallo sfruttamento della vulnerabilità

### Azioni
Una volta identificati i rischi, essi possono essere pesati per identificare le priorità di intervento. Le priorità generalmente utilizzate sono:
- **Risk avoidance**: interrompere i servizi che creano il rischio
- **Risk reduction**: Prendere contromisure per ridurre il peso del rischio
- **Risk sharing**: Condividere il rischio con enti terzi (ad esempio subappaltando il servizio ad essi, o assicurandosi contro il rischio stesso)
- **Risk retention**: Accattare il rischio consapevolmente

### [CVE](#CVE)

### CVSS
Il [Common Vulnerability Scoring System](https://www.first.org/cvss/) è uno strumento (webapp) di Risk assessment, progettato per fornire attributi comuni e un indice di severità alle vulnerabilità ai componenti hardware e software di un sistema. La terza versione è un framework open source e vendor-neutral, gestito dal [FIRST](#FIRST), utile per pesare il rischio delle vulnerabilità utilizzando diverse metriche. La combinazione di questi valori di rischio, permette di stabilire il fattore di rischio complessivo e l'urgenza della vulnerabilità stessa (con conseguente indice di priorità).

#### Metriche
![[metriche_CVSS.png]]

##### Base
Il gruppo delle metriche base è composto da 2 classi:
- Exploitability (exp): comprende caratteristiche dell'attacco, come il vettore, la complessità e le interazioni richieste dall'utente
- Impatto (imp): calcolato in base alla [triade CIA](<#Triade di sicurezza>)

| Tipo | Criterio                            | Descrizione                                                                                                                           | Valori                                                    |
| ---- | ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| Exp  | Vettore                             | Vicinanza dell'attaccante al componente vulnerabile. Più è lontano l'attaccante, maggiore è la gravità dell'attacco                   | - N: rete<br>- A: adiacente<br>- L: locale<br>- P: fisico |
| Exp  | Complessità                         | Numero di elementi, software, hardware o reti necessarie (non sotto il controllo dell'attaccante) per eseguire con successo l'attacco | L: basso<br>H: alto                                       |
| Exp  | Privilegi richiesti                 | Livello necessario di privilegi richiesti per eseguire con successo l'attacco                                                         | N: nessuno<br>L: bassi<br>H: alti                         |
| Exp  | Interazioni dall'utente             | Presenza o assenza di azioni che un utente interno dele eseguire affinchè l'attacco possa venire eseguito                             | U: Nessuna<br>R: richieste                                |
| Exp  | Ambito                              | Necessità (dell'attaccante) di cambiare authority durante l'esecuzione dell'attacco                                                   | U: non cambia<br>C: cambia                                |
| Imp  | [Confidenzialità](#Confidenzialità) | Impatto che l'esecuzione dell'attacco avrebbe a livello di Confidenzialità                                                            | H: alto<br>L: basso<br>N: nessuno                         |
| Imp  | [Integrità](#integrità)             | Impatto che l'esecuzione dell'atatcco avrebbe a livello di Integrità                                                                  | H: alto<br>L: basso<br>N: nessuno                         |
| Imp  | [Disponibilità](#availability)      | Impatto che l'esecuzione dell'atatcco avrebbe a livello di Disponibilità                                                              | H: alto<br>L: basso<br>N: nessuno                         |

##### Temporali
Misurano le variazioni delle caratteristiche dell'attacco attraverso il tempo (ma non al variare dell'ambiente oggetto dell'attacco stesso). Ad esempio la presenza di nuove patch potrebbe far abbassare la gravità di un attacco.

##### Ambientali
Fornisce valori riguardo l'ambiente dell'organizzazione. Questo tipo di valori è utile a definire le conseguenze dell'attacco all'interno dell'organizzazione e correggere i valori in base all'ambiente specifico dell'organizazzione stessa.



#### Risultati
Il risultato dell'analisi è un valore numerico (compreso tra 0 e 10), da comparare ad un range di valori:
- Nessuno: 0
- Basso: 0.1 - 3.9
- Medio: 4.0 - 6.9
- Alto: 7.0 - 8.9
- Critico: 9.0 - 10.0

In generale, ogni vulnerabilità  a cui è stato assegnato un valore superiore a 3.9, è da analizzare.

### [NVD](https://nvd.nist.gov/)

## Security policy
Documento che tratta i vincoli e i comportamenti all'interno di un'organizzazione e spesso i metodo ammessi di trattamento dei dati e chi ne ha accesso.

## Organizzazione delle informazioni di sicurezza
Modello di governance, impostato dall'organizzazione per trattare informazioni di sicurezza. Gli scopi principali sono l'introduzione di robuste misure di accountability, l'implementazione di misure necessarie a mitigare i rischi.

## Asset management
Inventario e schema di classificazione degli asset informativi all'interno dell'organizzazione.

## Sicurezza delle risorse umane
Si occupa di gestire le procedure di sicurezza relative l'ingresso, trasferimento e uscita degli impiegati.

## Sicurezza fisica e ambientale
Si occupa della protezione fisica delle sedi di un'organizzazione e/o dei suoi dati.

## Gestione delle comunicazioni e delle operazioni
SI occupa della gestione dei controlli di sicurezza tecnici della rete di un'organizzazione.

## Informazioni dei sistemi di acquisizione, sviluppo e manutenzione
Tratta il tema della sicurezza come parte integrante del sistema di informazioni di un'organizzazione.

## Access Control
Descrive le metodologie delle restrizioni di accesso alla rete, ai sistemi, alle applicazioni e/o ai dati di un'organizzazione.

## Gestione degli incidenti dei sistemi informativi
Descrive l'approccio alle previsioni e alle risposte ad attacchi informatici.

## Gestione della continuità del business
Descrive l'abilità di un'organizzazione di proteggere, mantenere e recuperare attività a seguito di un'interruzione dei sistemi informatici.

## Compliance
La conformità (compliance) descrive il processo che porta a confermare la conformità dei sistemi informatici alle [[#policy]] di sicurezza, standard e regolamentazioni. La verifica di conformità di un'organizzazione agli standard di sicurezza può essere gestito tramite certificazioni rilasciate da SSAE o CMMC.
- **SSAE + SOC** (Statement on Standards fort Attestation Engagements): audit indipendente eseguito da azienda terza, che ha lo scopo di confermare la presenza dei [controlli di sicurezza](<#CIS Security Controls>) necessari nel momento dell'analisi (Tipo 1), o in un arco di tempo di almeno sei mesi (Tipo 2)
- **CMMC** Cybersecurity Maturity Model Certification: Certificazione rilasciata per valutare il livello di sicurezza di un'organizzazione (su 5 livelli) in base ai criteri stabiliti dal Dipartimento della Difesa.

### Controlli
Il controllo di conformità dei [controlli](<#Controllo degli accessi>) è agevolata dal [CIS](#CIS),che fornisce una [mappatura di 18 Controlli di Sicurezza Critici](https://www.cisecurity.org/cybersecurity-tools/mapping-compliance) e alcuni framework di compliance.
# Security Standards
Gli standard di sicurezza hanno l'obiettivo di categorizzare e valutare le #vulnerabilità.

Gli standard sulla sicurezza sono gestiti da apposite agenzie e costantemente aggiornati tramite analisi dei contenuti presenti al dark web, [[#AIS]] (Indicatore di Condivisione Automatizzato), ovvero un’infrastruttura che permette lo scambio in tempo reale di indicatori sulle vulnerabilità utilizzando determinati linguaggi standardizzati e strutturati come lo [[#STIX]] (Espressione Strutturata delle Informazioni della Minaccia) o il [TAXII](#TAXII) (Scambio Automatizzato e Fidato di Informazioni di Intelligence)

Le aziende più famose che operano in questo ambito sono:

| Organizzazione        | Descrizione                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[#SANS]]             | SysAdmin, Audit, Network, Security (SANS), offre servizi a titolo gratuito (su richiesta) su:<br>- Internet Storm Center (sistema di prima allarme di internet)<br>- NewsBites: newsletter settimanale con articoli a tema sicurezza del computer<br>- @RISK: newsletter settimanale sugli aggiornamenti delle CVE e CWE<br>- Alert di sicurezza flash<br>Reading Room: Collezione di oltre 1200 articoli vincitori di premi<br>- Codici di sicurezza |
| [[#MITRE]]            | Organizzazione che gestisce le [[#CVE]]                                                                                                                                                                                                                                                                                                                                                                                                               |
| [[#FIRST]]            | Forum of Incident Response and Security Teams, è un'organizzazione di sicurezza che riunisce vari esperti di Security Incident Response per permettere la collaborazione tra aziende sul tema cybersecurity                                                                                                                                                                                                                                           |
| [[#SecurityNewsWire]] | Portale di news che raccoglie notizie sulle ultime novità in ambito sicurezza (alert, breach, exploits, ecc.)                                                                                                                                                                                                                                                                                                                                         |
| [[#(ISC)2]]           | International Information System Security Certification Consortium fornisce prodotti educativi neutrali a più di 75000 professionisti in più di 135 paesi                                                                                                                                                                                                                                                                                             |
| [[#CIS]]              | Il Center for Internet Security è un punto di riferimento riguardo la prevenzione, protezione, risposta e recovery delle minacce. Ha lo scopo di offrire degli avvisi 24/7 su minacce e consigli su minacce, mitigazione di incidenti e incident response a livello statale, locale, tribale e territoriale (SLTT) tramite la Condivisione di Informazioni Multi-Stato e Centro di Analisi (MS-ISAC)                                                  |

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

## DHS
Il dipartimento per la sicurezza interna degli USA offre un servizio gratuito chiamato Automated Indicator Sharing (AIS).

### AIS
Permette lo scambio in tempo reale degli indicatori di minacce alla sicurezza informatica tra il governo e i privati.

## CISCO Talos
Software che permette di scambiare informazioni riguardo vulnerabilità, indicatori di compromissione ([IOC]) e tecniche di mitigazione a livello globale. Inoltre fornisce e gestisce un set di regole per la protezione da intrusioni per software come [[#Snort]], [[#ClamAV]] e [[#SpamCop]] 

## NIST
Il National Institute of Standards and Technology è un'organizzazione che offre strumenti di standardizzazione per metodi e procedure.

### Incident Response Life Cycle
Procedura basata su 4 passaggi che descrivono il ciclo di vita dell'[incident response](<#Incident Response>):

- **Preparazione**: Addestramento costante dei membri del [CSIRT](#CSIRT) alla risposta agli incidenti
- **Identificazione ed analisi**: Monitoraggio costante per identificare potenziali incidenti, riconoscerli e convalidarli
- **Contenimento, rimozione e recupero**: Esecuzione delle procedure per contenere la minaccia, eradicare l'impatto sugli asset dell'organizzazione e utilizzare backup per ripristinare i dati e i software (se non c'è perdita di dati o servizi, si ritorna direttamente alla fase 1)
- **Attività post incidente**: Documentazione delle attività di risposta con descrizione di raccomandazioni future sulle procedure di risposta e sulle implementazioni per evitare che l'attacco avvenga di nuovo

#### Preparazione
Alcuni esempi di azioni che rientrano in questa fase sono:
- Creazione dei processi organizzativi per definire le metodologie comunicative tra le varie squadre ed eventuali altre [persone interessate](#Stakeholders)
- Definizione dell'infrastruttura del team di risposta e creazione del [SOC](#SOC)
- Acquisizione dei software e hardware per effettuare procedure di risposta e mitigazione dell'incidente (inclusi i software forensi)
- [Valutazione dei rischi](<#Risk Assessment>) per implementare controlli che permettano il verificarsi di incidenti simili
- Creazione di materiale per gli addestramenti alla consapevolezza della sicurezza dei dipendenti

#### Identificazione e analisi
Questo processo è il più complicato da tradurre in un processo a passaggi, in quanto la metodologia e la tipologia di attacco modificano fortemente i procedimenti con cui lo stesso avviene (e attraverso i quali ci si può difendere). Una classificazione può essere fatta riguardo:

##### Vettore d'attacco
- Web
- Email
- Furto o perdita
- Impersonificazione
- Logoramento (es. brute-force)
- Dispositivi esterni

##### Identificazione
Un attacco può essere identificato in maniera automatica (es. tramite [IDS](#IDS)), o manuale. in entrambi i casi il metodo di identificazione è la ricerca di segnali che indichino la presenza e l'eventuale tipologia di un incidente. In linea generale i segnali possono essere:
- **Precursori**: segnali che indicano la possibilità che un indicente accada (es. log di un port scanning)
- **Indicatori**: Segnale che indica che un incidente possa già essersi verificato (es. malware)

##### Analisi
Il problema principale del processo di analisi è l'incertezza legata alla bontà degli indicatori raccolti e all'impossibilità di utilizzare un metodo automatizzato per definirne la stessa. Inoltre alcuni indicatori, sebbene veritieri, non implicano necessariamente la presenza di un attacco.
Da qui nasce la necessità di un controllo ed una documentazione costante degli indicatori da parte del [CIST](#CIST).

##### Ambito
Viene identificato dal CIST nel caso un incidente avvenga. L'ambito descrive le tecnologie e/o strutture bersagliate dall'attacco (es. specifici computer, applicazioni, sistemi o parte di reti). La corretta identificazione dell'ambito permette di definire con precisione le attività da prioritizzare per mettere in sicurezza la rete.

##### Notifica
Una volta identificata e analizzata la minaccia, delimitato l'ambito e stabilite le priorità di intervento, si procede a comunicare i fatti e i dati raccolti e analizzati al personale addetto:
- **CIO**: Chief Information Officer
- **Head del dipartimento di sicurezza**
- Addetto locale alla sicurezza delle informazioni
- Altri membri del team di Incident Response all'interno dell'organizzazione
- Team di Risposta all'Incidente esterni all'organizzazione (se necessario)
- Proprietario del sistema
- Risorse umane
- Affari pubblici (se necessario)
- Dipartimento legale (se necessario)
- US-CERT (se negli USA e se necessario)
- Forze dell'ordine (se necessario)

#### Contenimento, rimozione e recupero
Una volta identificato ed analizzato l'incidente, si procede con le operazioni di contenimento dei danni. Durante questa fase vengono svolte 4 operazioni:
- Creazione ed attuazione di una strategia di contenimento
- Raccolta delle prove
- Identificazione dell'attaccante
- Rimozione, recupero e rimedio all'attacco

##### Strategia di contenimento
Deve tenere conto di:
- Tempistiche necessarie per l'attuazione
- Risorse impiegate (di tempo, economiche e di personale)
- Quali processi utilizzare per mantenere intatte le prove
- Possibilità di dirigere l'attaccante verso una sandbox per permettere al [CSIRT](#CSIRT) di monitorare le attività e raccogliere informazioni
- Analisi di impatto delle operazioni sulla disponibilità dei servizi
- Efficacia della strategia

E' inoltre da considerare la possibilità che azioni considerate cautelative, come il disconnettere l'utente infettato dalla rete, possano portare conseguenze negative per il processo di risposta all'incidente, come il reset del dispositivo infettato o la sua cifratura (che danneggerebbe le prove).

##### Prove
Le prove hanno una duplice scopo:
- Aiutare ad identificare il problema e le soluzioni allo stesso
- Essere utilizzate durante le indagini a seguito dell'attacco.

Per poter assolvere a quest'ultima funzione, è necessario che la metodologia di raccolta e memorizzazione delle stesse avvenga seguendo la [catena di custodia](<#Analisi forense#Metodologia>), memorizzando:
- Localizzazione dei dati di recupero e di salvataggio delle prove
- Dati identificativi delle operazioni (come codici MAC, IP o hostname)
- Informazioni riguardanti le identità di tutti gli addetti alla raccolta e memorizzazione delle prove
- timestamp di raccolta e salvataggio e descrizione delle metodologie utilizzate.

##### Identificazione
Processo secondario al ripristino delle normali funzionalità della rete, ma spesso utile a minimizzare l'impatto dell'attacco sugli asset critici per il business dell'organizzazione. Le azioni più importanti da effettuare sono:
- Utilizzare il database dei dati dell'incidente per cercare le attività da analizzare
- Verificare se l'indirizzo IP dell'attaccante sia valido e nel caso se sia raggiungibile
- Cercare ulteriori informazioni su un motore di ricerca può portare ad identificare attacchi simili avvenuti ad altre organizzazioni
- Monitorare i canali più usati dagli attaccanti, come l'[IRC], per verificare che l'attaccante non sia presente all'interno della rete in forma anonima.

#### Attività post incidente
##### Hardening
A seguito di un indicente di sicurezza, si effettua l'hardening dei sistemi in base alle scoperte fatte durante l'analisi dell'attacco, per impedirne una ripetizione. Per questo è fondamentale capire:
- Come l'attacco sia avvenuto
- Come ha reagito lo staff all'attacco
- Se sono state seguite o meno le procedure descritte nella documentazione (e nel caso se fossero adeguate all'evento)
- Quali informazioni sarebbero state utili nell'immediato
- Quali passaggi possono aver impedito il recupero
- Come avrebbe potuto operare lo staff
- Quali precauzioni possono essere implementate per impedire una nuova esecuzione dell'attacco
- Quali dati devono essere monitorati per identificare immediatamente l'attacco
- Quali sono i miglior istrumenti per monitorare ed identificare futuri incidenti

##### Raccolta dati
Quando si memorizzano dati relativi la risposta ad un incidente, è importante tenere traccia della metodologia di risposta, economico e di tipologia di dati da memorizzare. Il NIST fornisce una [lista](https://csrc.nist.gov/pubs/sp/800/61/r2/final) (Pubblicazione speciale 800-61) del tipo di attività che è utile eseguire a seguito di un incidente:
- Revisionare log, form, report e documentazione dell'incidente per analizzare l'efficacia delle policy e delle procedure aziendali
- Identificare i [segni precursori](<#Identificazione ed analisi#Identificazione>) dell'attacco registrati dal sistema e analizzare come sono stati trattati
- Verificare se la notifica dell'attacco è avvenuta dopo che un danno sia effettivamente avvenuto all'interno della rete
- Verificare se siano stati identificati i danni subiti, i vettori di attacco, le vulnerabilità sfruttate e le caratteristiche del sistema attaccato
- Determinare se l'incidente sia già avvenuto altre volte in passato
- Calcolare il danno economico subito (o una stima)
- Misurare la differenza tra valutazione dell'impatto prima e dopo l'attacco
- Valutazione (e autovalutazione) delle azioni effettuate da ogni membro del team di risposta durante l'attacco

E' importante notare come la normativa abba specifiche richieste riguardo:
- Tempo di archiviazione delle prove da parte dell'organizzazione
- Tipi di dati da memorizzare (alcuni tipi di dati hanno tempi di archiviazione o metodologie i salvataggio diverse)
- Preservazione dei supporti hardware correlato all'incidente (da considerare anche i costi di stoccaggio dei dispositivi)

Può anche rivelarsi utile (si aper l'organizzazione che per la comunità) la comunicazione di informazioni relative l'incidente su piattaforme o form appositi (come il community database [VERIS]). Le raccomandazioni del NIST in tema sono:
- Piani di coordinamento con team esterni all'organizzazione
- Consulta con il dipartimento legale prima di condividere informazioni sull'incidente
- Condividi informazioni relative l'intero ciclo di vita dell'incidente
- Automatizzare il più possibile la condivisione delle informazioni 
- Bilanciare i benefici con i possibili malus prima di condividere informazioni

## FireEye
Azienda di sicurezza che offre servizi per la messa in sicurezza della rete di aziende. Utilizza un approccio basato su 3 punti:
- Security intelligence
- Security Expertise
- Tecnologia

FireEye offre soluzioni [[#SIEM]] e [[#SOAR]] che utilizzano l'analisi comportamentale e tecniche avanzate di identificazione (supportate dalla rete mondiale di Threat intelligence FireEye Mandiant) all'interno dell'[Helix Security Platform].

## STIX
Lo Structured Threat Information Expression è un set di specifiche per la condivisione di minacce informatiche tra organizzazioni. Incorpora lo standard [[#CybOX]].

## TAXII
Il Trusted Automated Exchange of Indicator Information è la specifica per i protocolli di [livello 7](./Tecnologie/Protocolli#Applicazione) per le comunicazioni in [CTI] su [HTTPS](./Tecnologie/Protocolli#HTTPS), progettata per supportare [[#STIX]].

## CybOX
Set di schemi standardizzati per specificare, catturare, caratterizzare e comunicare eventi e proprietà delle operazioni di rete che supporta molte funzioni proprie della cybersecurity.

## TIP
Le Threat Intelligence Platforms sono piattaforme utili per l'aggiornamento costante sulle minacce informatiche a livello globale. La condivisione di dati uniformi avviene grazie all'utilizzo di Indicatori di Compromissione [[#IOC]], tecniche, strumento e procedure ([[#TTP]]) ed un sistema di informazioni riguardanti la reputazione dei vari domini.

### MISP
La Malware Information Sharing Platform è una piattaforma open source per condividere i nuovi indicatori di compromissione delle minacce. Il MISP è supportato dalla UE e utilizzato da oltre 6000 organizzazioni nel mondo.

# Etica
Ci sono 3 correnti filosofiche riguardo l'etica:
- Utilitaristica: Il fine giustifica i mezzi
- Approccio giuridico: ogni persona ha dei diritti inalienabili
- Bene comune: E' bene ciò che porta beneficio all'intera comunità

In ambito della sicurezza informatica, ci sono 10 regole generali:
1. Non usare un computer per danneggiare il prossimo
2. Non interferire con la rete altrui
3. Non frugare nei file degli altri
4. Non rubare (tramite un computer)
5. Non (usare un computer per) dire falsa testimonianza
6. Non crackare software 
7. Non usare un computer altrui senza espresso consenso
8. Non ti appropriare dell'opera intellettuale altrui
9. Pensa alle conseguenze sociali delle tue azioni e delle cose che progetti
10. Usa sempre un computer per assicurare la considerazione ed il rispetto degli altri

Questi comportamenti, tra l'altro, sono punibili a livello legale. La tipologia di crimine dipende da come il computer viene utilizzato per portare in atto un comportamento scorretto:
- Diretto diretto al computer: es. malware, DoS
- Diretto alla persona: frode, surto identità
- Indiretto: utilizzo del pc per ottenere informazioni utili a commetter un crimine.

# Disastro
Un disastro è un evento (scaturito da cause naturali o antropiche) che danneggia risorse e/o proprietà e riduce l'abilità di un'organizzazione a continuare ad operare.

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

### Brute-force
Consiste nell' individuare un valore di accesso tramite il tentativo ripetuto di uguaglianza con valori generati automaticamente

#### Dictionary
Avviene quando i valori utilizzati sono letti da una lista di valori considerati più probabili (es. lista delle password più usate).

Nel caso di breach di un database, è possibile per un attaccante ottenere la **lookup table** del sistema tramite un processo noto come **reverse lookup table**, che consiste nell'identificare i vari valori di salt utilizzati per utente tramite brute-force.

##### Rainbow table
Tabella precompilata, utilizzata per . Questo permette di salvare spazio computazionale all'attaccante. Questo attacco è inutilizzabile nel caso di uso di [[#salting]]

### Spoofing
E' un attacco che può avvenire ad ogni livello della ISO-OSI e che consiste nella falsificazione dell'identità e/o di altro tipo di informazioni applicative ([fonte](https://it.wikipedia.org/wiki/Spoofing)).

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
### [Data Breach](https://www.garanteprivacy.it/data-breach)
Consiste nella modifica, distruzione, furto, perdita o divulgazione non autorizzata di dati. 

### Directory traversal
Anche noto come Path traversal, consiste nella manipolazione del percorso di un sito web per leggere dati sensibili o eseguire file altrimenti protetti.

### Email
I protocolli [POP3](./tecnologie/protocolli#pop3), [IMAP](./tecnologie/protocolli#imap) e [SMTP](./tecnologie/protocolli#smtp) possono esser e utilizzati per trasportare malware ed infettare host o server.

#### Attacco tramite allegati
Il malware viene inserito tra gli allegati della mail e, una volta scaricato, infetta il dispositivo bersaglio.

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
- Utilizzare la versione sicura: [HTTPS](./tecnologie/protocolli#https) (facendo attenzione alle complicazioni che questo porta a livello di monitoraggio della rete)

![[Pasted image 20241114233822.png]]

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
- Dictio
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
- Content [[#Security Policy]]
- utilizzare un framework moderno
- in #PhP usare funzioni htmlentities() e htmlspecialchars() per effettuare l' #escaping delle variabili
- Utilizzare un implementazione IPS per identificare e prevenire scipt malevoli
- Utilizzare un Web Proxy per bloccare siti malevoli

## Presentazione
## Sessione
### Session Hijacking

## Trasporto
### NAT
Il [NAT](./tecnologie/reti#nat) ed il [PAT] possono complicare le operazioni di monitoraggio della rete e può semplificare l'anonimato degli attaccanti, che possono nascondersi dietro indirizzi IP pubblici.

![[Pasted image 20241114235651.png]]

### TCP

#### SYN Flood
L’attaccante effettua ripetutamente chiamate di richiesta di sincronizzazione al server bersaglio che, rispondendo a tutte le chiamate con un messaggio ACK, non riesce a rispondere in tempo alle chiamate legittime di SYN.

#### Reset attack
Viene inviato un segnale RST (reset) al server utilizzando l'indirizzo IP dell'obbiettivo ([spoofing](#spoofing)) per resettare la comuniucazione in corso. Questo attacco può condurre a successivi attacchi di tipo [session hijacking](<#session hijacking>).

### UDP
#### flood attack
Ha come obiettivo il blocco della rete a causa delle troppe richieste da elaborare. Di solito l'attaccante utilizza tool come [UDP Unicorn] o [Low Orbit Ion Cannon] per preparare i pacchetti e automatizzarne l'invio. Il risultato è un attacco di tipo [DoS](#dos).

## Rete

### P2P
Il Peer-to-Peer consiste in una connessione logica tra due dispositivi a pari livello, ovvero senza distinzione tra client e server. Questo metodo è particolarmente vulnerabile nel caso di trasferimento di file da un computer aziendale ad un dispositivo esterno alla rete aziendale.

E' buona norma **disattivare la condivisione di file tramite P2P o l'installazione di programmi che permettano questa pratica**, in quanto può sorvolare i controlli del [FIrewall](#firewall). Le applicazioni di  messaggistica istantanea rientrano in questa categoria.

### TOR
TOR è una piattaforma di software che anonimizza l'utente tramite utilizzo di una rete di dispositivi Tor, che randomizza il dispositivo che invierà effettivamente il messaggio al server, facendo da intermediario.

### Load balancing
Il load balancing e la sua gestione possono costituire un problema dal punto di vista della sicurezza, in quanto:
- Comportano una segmentazione della rete in sottoreti
- Il load balancer manager (LBM) può inviare messaggi sonda per verificare il numero di server connessi, che potrebbero (i messaggi) disturbare il normale flusso di analisi da analizzare.

### [ARP](./tecnologie/protocolli#arp)
#### Cache poisoning
Attacco che può essere utilizzato per gettare le basi per un [Man in the middle](#man-in-the-middle) e consiste nel sostituirsi ad un altro dispositivo ad una [ARP request](./Tecnologie/Protocolli#ARP)

### [ICMP](./tecnologie/protocolli#icmp)
Un tipico attacco effettuato tramite ICMP consiste nel pingare pacchetti echo agli host di una rete per scoprirne l’architettura (sotto reti e host connessi). È possibile effettuare questa operazione ripetutamente in poco tempo per inondare la rete (flood) di messaggi da gestire e rallentarla (DoS).

I messaggi inviati possono essere di vario tipo:
- Echo request e reply nel caso si voglia effettuare un attacco DoS. Nel caso si effettui anche lo spoofing mirato, è possibile inondare di richieste un dispositivo bersaglio
- Unreachable per riconoscere e scansionare reti
- Mask reply nel caso si vogliano mappare gli indirizzi IP di una rete
- Redirect per reindirizzare il traffico verso l’attaccante ed effettuare un [MItM]
- Router discovery per inserire indirizzi IP falsificati all’interno della tabella di routing

Un esempio di attacco tramite ICMP è [Loki](https://phrack.org/issues/49/6.html).

### IP
#### Spoofing
Falsificazione di un indirizzo IP in maniera mirata (se si conosce l’indirizzo che si sta falsificando) o alla cieca (in caso contrario).

### DHCP
Vedi [protocollo DHCP](./tecnologie/protocolli#dhcp)
#### Spoofing
Di solito consiste nel fornire un indirizzo IP falso relativo al Default Gateway o al Server DNS (anche se potenzialmente qualunque indirizzo IP può essere contraffatto), seguendo i seguenti passaggi:
1. Il Client invia un messaggio DHCP Discovery (che viene ascoltato anche dall'attaccante)
2. Il Server DHCP e l'attaccante rispondono con un messaggio DHCP Offer (il Client risponderà solo alla prima risposta ricevuta)
3. Nel caso la prima risposta venga inviata dall'attaccante, invierà un DCHP Request in broadcast, che non verrà accettata dal Server DHCP in quanto la richiesta é già stata accettata da un altro Server DHCP (l'atatccante)
4. L'attaccante invia un DHCP ACK al Client, completando l'attacco di **spoofing** e sostituendosi al Server DHCP

#### Starvation attack
Consiste nel sostituirsi al Server DHCP e impedire agli utenti di utilizzare il protocollo DHCP per richiedere un indirizzo IP privato.

### DNS
Gli attacchi che sfruttano il protocollo [DNS](./Tecnologie/Protocolli#dns) possono avvenire tramite:
- Open Resolver (indirizzi IP pubblici che vengono utilizzati per cercare informazioni, tipo Google)
- Protocolli di criptazione come Base64, 8-bit binary e Hex possono essere utilizzati per evadere i meccanismi di Prevenzione della perdita di dati (Data Loss Prevention, DLP)
- Inserimento dei dati all'interno degli URL per passare inosservati
- Malware che utilizzano il protocollo per comunicare con server attaccanti Command-and-Control (CnC) per esfiltrare dati.

#### Cache poisoning
Consiste nell'invio di risorse falsificate ([spoofing](#spoofing)) ad un DNS Resolver per reindirizzare l'utente verso siti malevoli

#### Amplification and reflection attack
Utilizzo di attacchi [DoS](#dos) o [DDoS](#ddos) ad un Open Resolver per nascondere la vera fonte dell'attacco tramite l'invio di open resolver  per aumentare il volume dell'attacco.

#### Exfiltration


#### Resource utilization attack
Consiste in un attacco di tipo [DoS](#dos) per sovraffollare il server di richieste per resettare il server.

#### Stealth Attacks
Sono metodologie utilizzate per nascondere la propria identità al bersaglio.

##### Fast flux
Tecnica utilizzata per nascondere i siti di invio di malware e [phishing](#phishing) al bersaglio. Di solito avvengono tramite il cambio rapido di indirizzo DNS tra  una lista di indirizzi compromessi. Questo tipo di attacchi è utilizzato spesso dai Botnet.


##### Double IP flux
L'attaccante modifica velocemente sia l'hostname (in base ad un pool di indirizzi IP) che il [nome autoritativo del server](https://en.wikipedia.org/wiki/Name_server#:~:text=An%20authoritative%20name%20server%20is,specifically%20configured%20by%20its%20administrator).

##### Domain generation algorithms
Tecnica utilizzata dai malware per generare automaticamente nomi di dominio che possono essere utilizzati come punti di accesso per i [server di comando e controllo](https://nordvpn.com/cybersecurity/glossary/cc-server/).


#### Tunneling
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
### Cloud
Le tipologie di attacco più comuni per i dati salvati in cloud sono:
- Data breach (furto di dati)
- Cloud misconfiguration
- Poor cloud security architecture strategy (ovvero la configurazione errata dell'architettura del cloud)
- Compromised account credentials (furto di credenziali)
- Insider threat (minaccia dall'interno)
- Insecure UI or API (configurazione dell'interfaccia utente o delle API errata o non sicura)
- Limited cloud usage visibility (limitata visibilità dell'utilizzo del cloud, può portare a non identificare in tempo attacchi)

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
Utilizzo di credenziali fasulle ai fini di aggirare i protocolli di autenticazione.

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
Ovvero non dare possibilità agli attaccanti di scoprire informazioni relative ai dati. Di solito queste operazioni di scoperta dei dati avvengono tramite messaggi di log o messaggi di sistema.

#### Dati
Questa strategia può essere applicata anche su dati specifici, per impedirne (o rendere più difficile) la lettura. Le metodologie utilizzate sono 3:
- **Sostituzione** (masking), ovvero utilizzo di un dato fasullo, ma avente struttura verosimile
- **Mescolamento**, ovvero utilizzo di un valore sostitutivo, preso da un pool di valori
- **Annullamento**, ovvero sostituzione del valore con uno nullo (vuoto)

Un altro modo per nascondere dati durante è tramite l'uso di **Steganografia**, ovvero l'inserimento di questi dati all'interno di luoghi inusuali (ad esempio all'interno dei dati di un file immagine, o tramite l'utilizzo di valori sostitutivi, la cui connessione con il dato reale è conosciuta solo agli utenti autorizzati). Un tool per utilizzare la steganografia è [steghide](./os/linux#steghide)

### Semplicità
Preferire meccanismi semplici, ma efficaci di protezione, evitando l'utilizzo di meccanismi troppo complessi da impostare, che potrebbero ritorcersi contro il team di sicurezza stesso per problemi di configurazione, o altro. Preferire invece soluzioni che siano facili da utilizzare, ma complesse da attaccare.

# Analisi
## Profilazione
La profilazione della permette di schematizzare gli aspetti principali della struttura, del funzionamento e delle modalità d’uso (standard o supposte) di un elemento, per facilitare l’identificazione di alcune vulnerabilità a cui potrebbe essere soggetto.

### Rete
Gli elementi base per una buona profilazione di una rete sono:
- Durata della sessione (tempo trascorso tra lo stabilimento di una connessione per lo scambio di un flusso di dati e la sua fine)
- [Throughput](./Tecnologia/Macchina#Throughput) totale (la totalità di dati in transito da un dispostiivo ad un altro in un determinato arco di tempo)
- Porte utilizzate (facendo riferimento ai protocolli TCP e UDP)
- Spazio degli indirizzi critici (ovvero il la localizzazione degli indirizzi che contengono dati essenziali per il funzionamento del sistema)

Altri parametri fondamentale, ma non direttamente collegati alla rete sono:
- Traffico host-to-host
- Comportamento standard degli utenti

È possibile utilizzare tool come [Wireshark] e [NetFlow](#netflow) per identificare una baseline del traffico della rete.

### Server
Utile per definire una baseline comportamentale accettabile del server stesso. I parametri analizzati spesso sono:
- Porte in ascolto
- Account e utenti collegati
- Servizi resi disponibili agli account
- Ambiente software (o software environment, inteso come insieme di task, processi e applicazioni che permettono il funzionamento del server)

## Applicazione
### AVC
Gli Application Visibility Control sono tool che permettono l'analisi delle applicazioni in uso da un dispositivo. Un esempio è il Cisco Application Visibility Control.
Questi software offrono servizi di:
- Riconoscimento dell'applicazione tramite NBAR2
- Collezione delle metriche
- Gestione e report
- Controllo

## Rete
### [NetFlow](#protezione#netflow)

### NBA
La Network behavior analysis è un approccio che consiste nell’analizzare il flusso di rete attraverso tecniche di analisi per i Big Data e compararle con la baseline di comportamento della rete stessa. Una deviazione significativa dal comportamento della baseline potrebbe indicare un attacco in corso. Un esempio di algoritmo per una NBA è il seguente:

![[algoritmo_nba.png]]
Dove X, Y e Z sono variabili impostabili a discrezione del cybersecurity analyst.

## log
I log sono file che tengono traccia di avvenimenti all’interno della rete. Gli eventi di solito monitorati tramite log possono essere categorizzati in:
- Log di applicazioni: contengono informazioni relative le applicazioni in esecuzione
- Log di eventi: 
- [Log di servizi](<#log di servizi>)
- Log di sistema: Riguardano operazioni di driver, processi e hardware

### Server Proxy
Elementi come i Server Proxy possono rivelarsi molto utili per l'analisi, la creazione e la memorizzazione di log relativi le connessioni con dispositivi esterni alla rete.

Esempi di software per gestire i log su server proxy sono:
- CCProxy
- Apache Traffic Server
- WinGAte
- Squid
- Cisco Umbrella (per l'analisi dei protocolli DNS)

### Content filter logs
Sono software che permettono di filtrare e raggruppare i log per agevolarne l'analisi. Un esempio è il Cisco Email Security Appliance.

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
## Packet analyzer
Sono strumenti che permettono l'analisi (o il semplice sniffing) in tempo reale e il salvataggio dei pacchetti in transito sul dispositivo che lo sta utilizzando. Un esempio di packet analyzer è Tcpdump (utilizzato da software come Wireshark). Le funzionalità principali sono:
- Analisi dei problemi della rete
- Identificazione di tentativi di intrusione nella rete
- Isolamento dei sistemi compromessi
- Log del traffico
- Identificazione di utilizzo improprio della rete

### EtherApe
### Ettercap
### Kismet
### ngrep
### ntop
### PCPdump
### Tcpdump
Strumento per effettuare analisi dei pacchetti ed effettuare [[#log]] a livello di rete.

### Wireshark
## Vulnerability scanner
### Introduzione
Gli scanner di vulnerabilità sono software che effettuano scansioni di un dispositivo, di più dispositivi, o di un'intera rete, per identificarne le debolezze e fornire un audit del risultato dell'analisi. Alcuni parametri che il software ricerca soon:
- Utilizzo di password di default
- Patch non installate o aggiornate
- Porte aperte
- Configurazione errata di software e/o sistemi operativi
- indirizzi IP attivi (inclusi quelli indesiderati)

Mentre i servizi comunemente offerti comprendono:
- Effettuare l'audit della conformità
- Installare patch e aggiornamenti
- Identificare configurazioni errate
- Supportare dispositivi mobile e connessioni wireless
- Tracciare i malware
- Identificare dati sensibili

Alcuni esempi commerciali di Vulnerability scanner sono:
- Nessus
- Retina
- Core Impact
- GFI Life Guard

### Target
Gli scanner delle vulnerabilità sono divisi in base all'obbiettivo della loro scansioni in:
- Scanner di rete
- Scanner delle applicazioni
- Scanner delle applicazioni web

### Scansioni
E' possibile effettuare due tipologie di scansioni diverse: intrusive o in base a credenziali (credentialed)

#### Intrusive
Sono scansioni che cercano di sfruttare delle vulnerabilità e possono portare al blocco del target.

#### Credentialed
Le credenziali di accesso al sistema vengono fornite al software prima di iniziare l'analisi, permettendogli di raccogliere più informazioni. Questo tipo di scansioni spesso produce meno falsi positivi e falsi negativi nei risultati.


## Test
I test vengono effettuati spesso su un dispositivo o su un'intera rete per verificarne la corretta impostazione e funzionamento. Lo scopo dei test è verificarne la presenza ed identificare le vulnerabilità presenti sull'obbiettivo.
Questa fase di solito è preceduta da una fase di ricognizione (reconnaiscance), che può essere:
- Attiva: nel caso venga effettuata direttamente sulla rete
- Passiva: nel caso venga fatta all'esterno (es. social network, motore di ricerca o altro)

### Network Vulnerability Testing
Comprende una serie di test da effettuare periodicamente sulla rete, per verificarne lo stato:
- [Analisi dei rischi](<#risk analysis>) (Risk Analysis)
- [Valutazione delle vulnerabilità](<#vulnerability assessment>) (Vulnerability Assessment)
- [Penetration testing](#pentest)

### Pentest
Il Penetration test è un test (effettuato spesso dal [Red-team]) attraverso il quale un tecnico prova ad accedere ed utilizzare una rete tramite meccanismi di forzatura ed attacchi noti (es. brute-force delle password di accesso), per poi raccogliere i risultati in un documento di **audit**.

L'obbiettivo è determinare la presenza di vulnerabilità della rete e le attività permesse nel caso esse vengano sfruttate, per determinare i possibili danni. Per fare ciò spesso si utilizzano dei [[#Packet analyzer]] come[Metasploit], [CORE], [Impact]

#### Tipologie
##### Back-box
E' il test più rapido ed economico. Presuppone una conoscenza nulla della rete.

##### Gray-box
Test intermedio, presuppone la conoscenza di alcune componenti della rete e dell'ambiente che la costituisce

##### White-box
E' il test che necessita di più tempo per essere effettuato (e fornisce i risultati più completi). Presuppone la conoscenza dell'intera rete e dell'ambiente.

#### Fasi
1. Pianificazione: Stabilisce le regole di approccio del test
2. Scoperta: Utilizzo di tecniche attive e passive per ottenere informazioni riguardo la rete
3. Attacco: Si eseguono vari attacchi contro la rete per verificare/sfruttare le vulnerabilità
4. Reporting: SI produce una documentazione esaustiva del test (identificando azioni prese e risultati conseguiti)

#### Team
I team che operano i nun pentest test sono:
- Red team: coloro che attuano l'attacco
- Blue team: coloro che tentano di difendere la rete dall'attacco
- White team (opzionale): Squadra neutrale che predispone le regole del test
- Purple team: Commistione di membri del red e del blue team, che lavorano per identificare le vulnerabilità di una rete e come risolverle

### Regression test
Il #regression-test può essere fatto con [[Postman]], [[Python 1]] e consiste nell'analizzare il contenuto della #response ad una chiamata #http 

### Risk analysis
Analisi approfondita dell'impatto che eventi dannosi per un'azienda possono avere sulle funzionalità di base di un'azienda e sugli asset. Esempi di eventi dannosi sono:
- Perdita di dati, funzionalità, processi o prodotti
- Attacchi informatici
- Guasto di componenti
- Danno reputazionale
- Perdita di proprietà intellettuale

Per effettuare questo tipo di analisi, si fa ricorso ad [appositi framework], da selezionare in base alla tipologia di analisi che si vuole effettuare:
- Analisi quantitativa
- Analisi qualitativa

#### Analisi quantitativa
Si basa sull'assegnazione di valori numerici a parametri, per poi calcolare un valore finale, utilizzato per descrivere il valore di rischio.

I valori utilizzati sono:
- **Fattore di esposizione (EF)**: Valore soggettivo, espresso in percentuale, che esprima le quantità di dati persi a seguito del verificarsi dell'evento analizzato
- **Numero di avvenimenti annui (RAO)**: probabilità che l'evento si verifichi una volta l'anno (se is verifica più volte l'anno, il valore sarà maggiore di 100%)

La moltiplicazione di questi valori, permette di identificare la **stima della perdita annua* (ALE)*

#### Analisi qualitativa
Utilizza opinioni e previsione di scenari per valutare l'impatto degli eventi. Di solito si fa uso della [matrice dei rischi](<#Matrice dei rischi>) 

##### Matrice dei rischi
![[matrice_dei_rischi.png]]

### Vulnerability Assessment
Si effettua un controllo dello stato degli aggiornamenti dei componenti di un sistema (OS, patch, porte aperte, ecc.). E' possibile utilizzare appositi tools, come:
- [OpenVas]
- [Microsoft Baseline Analyzer]
- [Nessus]
- [Qualys]
- [[Nmap]]

# Prevenzione
## DRP
Il Piano per il recupero a seguito di un [disastro](#Disastro) (Disaster Recovery Plan) è un documento che contiene un elenco di azioni e procedimenti da attuare in caso di disastro. La pianificazione include le attività che l'organizzazione deve intraprendere per valutare, mettere in sicurezza, riparare e ripristinare risorse. Le domande che si pongono durante il processo di redazione di un DRP sono:
- Chi è il responsabile del processo
- Quali azioni devono essere intraprese dalla persona per eseguire il processo
- Dove deve essere intrapreso il processo
- In cosa consiste il processo
- Perché il processo in questione è critico

### Controlli
I controlli del DRP minimizzano gli effetti di un disastro, permettendo all'organizzazione di riprendere le operazioni. Ci sono 3 tipologie di controlli:
- **Preventivi**: includono misure preventive per prevenire l'avvenire di un disastro
- **Identificativi**: Le misure di identificazione servono a scoprire nuove potenziali minacce
- **Correttivi**: Le misure correttive hanno lo scopo di ripristinare il sistema a seguito di un disastro

## BCP
Il Business Continuity Planning (Pianificazione della continuità del Business) è un documento di pianificazione più ampio rispetto al [DRP](#DRP) in quanto deve includere i processi di movimentazione degli hardware per permetter di continuare le operazioni dell'organizzazione anche in caso di riparazioni della struttura fisica dell'azienda. Aspetti fondamentali per un buon BCP sono:
- L'identificazione delle risorse ottimali per i compiti richiesti
- La documentazione delle configurazioni
- Stabilire mezzi di comunicazione alternativi sia per la voce che per i dati
- Fornire corrente elettrica
- Identificare tutte le dependency delle applicazioni e dei processi al fine di comprenderli a fondo
- Capire come svolgere le funzioni automatiche manualmente

Per redigere un BCP, occorre iniziare da un'Analisi dell'Impatto sul Business ([BIA](#BIA)), per identificare i processi critici del business dell'organizzazione e le loro risorse e relazioni con gli altri processi. La BIA analizza i casi di interruzione delle funzioni critiche per il business e esamina i seguenti punti:
- **RTO**: Obiettivi riguardanti il tempo di recupero, ovvero il limite di tempo nel quale un servizio può essere non disponibile
- **RPO**: Obiettivi relativi il Punto di Recupero, ovvero la lunghezza di vita di una determinata risorsa
- **MTTR**: Tempo medio di riparazione
- **MTBF**: Tempo medio tra due malfunzionamenti della stesa risorsa 

### Best Practices
Le linee guida del [NIST](#NIST) offrono una lista di operazioni da condurre per redigere un BCP:
1. Sviluppare delle [policy](#Policy) che guidino lo sviluppo di un business plan e assegnino ruoli chiari alle persone
2. Condurre l'Analisi di Impatto Economico (Business Impact Analysis) per identificare le risorse critiche da prioritizzare
3. Identificare le vulnerabilità, le minacce e calcolare i rischi
4. Identificare ed attivare i controlli preventivi per ridurre i rischi
5. Sviluppare strategie di recupero
6. Sviluppare un piano di contingenza
7. Testare i piani
8. Mantenere i piani

#### Mettere in pratica il DRP
Ci sono metodologie da utilizzare per mettere in pratica i Disaster Recovery Plan:
- **Tabletop**: I partecipanti si siedono attorno ad un tavolo con un aiutante che fornisce informazioni relative lo scenario. I partecipanti discutono i processi da intraprendere
- **Test di funzionalità**: Vengono testati solo alcuni componenti del DRP per verificarne il funzionamento
- **Esercizi operativi**: Vengono interrotti i servizi per verificare il corretto funzionamento del piano

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
#### Introduzione
La Lista di Controllo degli Accessi consiste in una serie di comandi di Sistema Operativo, che analizzano i pacchetti in ingresso e decidono se essi deve essere inoltrati o bloccati, in base alle informazioni trovate nell’header dei singoli pacchetti. Un ACL svolge le seguenti funzioni:
- Limita il traffico per migliorare le prestazioni della rete
- Fornisce un controllo del flusso della rete (può anche fornire delle rotte predefinite per gli aggiornamenti, evitando così l’installazione di aggiornamenti da terze parti)
- Fornisce un livello base di protezione della rete
- Filtra il traffico in base al tipo di pacchetto (es. Email, video, ecc.)
- Monitorano le attività degli host ed impediscono determinati accessi alla rete (es. Permettere solo protocolli FTP)

Gli ACL spesso operano operazioni di controllo tramite indirizzi IPv4 di origine e destinazione, o porte di accesso e protocollo utilizzato.
Di solito è utile utilizzare più ACL e nominarle con numeri o nomi che definiscano il tipo di filtraggio compiuto.

I pacchetti filtrati dipendono dal tipo di ACL utilizzata:
- **ACL Standard**: livello 3 (Rete), da posizionare il più vicino possibile alla destinazione
- **ACL Estesa**: Livelli 3 e 4 (Rete e Trasporto), da posizionare il più vicino possibile al mittente

Le liste dei comandi di controllo si chiamano Access Control Entries (ACE).

#### ACE
Lista di verifiche sequenziali che permettono di stabilire se il pacchetto che è in verifica debba essere droppato, o se possa avere accesso alla rete. Alcune tipologie di comandi che possono essere richiesti sono:
- **Incremento della velocità:** Policy di negazione dello scambio di file video all'interno della rete
- **Controllo del traffico**: Blocco dell'invio di protocolli di [routing updates] per le richieste che provengano da fonti sconosciute
- **Aumentare la sicurezza della rete**: Limitare l'accesso alla rete solo a determinati dispositivi fidati
- **Filtrare il traffico in base al tipo**: Analisi del tipo di traffico e blocco dei pacchetti con tipi non permessi (es. email)
- **Monitorare l'utente per limitare l'accesso alla rete**: Filtrare le chiamate dell'utente in base ai servizi a cui può avere accesso
- **Permettere solo certe classi di traffico:** Classificare il traffico e decidere quali classi siano prioritarie, quali normali e quali da bloccare

#### Indicizzazione
Le ACL possono essere catalogate prevalentemente in due modi:
##### Numerico

| Numero      | Descrizione                                                                     |
| ----------- | ------------------------------------------------------------------------------- |
| 1-99        | ACL standard per IP                                                             |
| 100-199     | ACL estesa per  IP                                                              |
| 1100-1199   | ACL estesa per indirizzi MAC da 48-bit                                          |
| 1300-1999   | Espansioni per ACL standard per indirizzi IP                                    |
| 200-299     | ACL basata sul tipo di protocollo                                               |
| 2000-2699   | Espansione per ACL estese per indirizzi IP                                      |
| 700-799     | ACL per indirizzi MAC da 48-bit                                                 |
| rate-limit* | ACL semplice per il controllo della velocità                                    |
| template    | Abilita le ACL per [template IP](https://scn.wikipedia.org/wiki/Template:IP%3F) |
*rate-limit: limite di velocità

###### Sintassi

| Parametro           | Descrizione                                                                                                     |
| ------------------- | --------------------------------------------------------------------------------------------------------------- |
| access-limit-number | Numero intero identificativo della ACL (ACE?)                                                                   |
| deny                | Nega l'accesso se le condizioni sono rispettate                                                                 |
| permit              | Consente l'accesso se le condizioni sono rispettate                                                             |
| remark text         | (Opzionale) Documentazione (massimo 100 caratteri)                                                              |
| source              | Identifica la sorgente da filtrare (indicare **any** per  tutte le reti e **host** per il singolo indirizzo IP) |
| source-wildcard     | (Opzionale) [Wildcard Mask](<#wildcard mask>)                                                                   |
| log                 | (Opzionale) genera informazioni nel caso l'ACE venga rispettata                                                 |


##### Nominativo

Viene asegnato un nome ad ogni ACL, in modo tale da renderle riconoscibili e raggruppabili per tipo di protocollo utilizzato, tipo di blocco, ecc. Il nome assegnato ad un aACL deve:
- Descrivere la funzione dell'ACL
- Essere composto solo da caratteri alfanumerici
- Non deve contenere spazi o punteggiatura
- Essere scritto in lettere maiuscole (consigliato)
- Descrivere se è di tipo permissivo (added) o respingitivo (deleted)

#### Wildcard Mask
Le maschere "jolly" rappresentano uno schema simile ad una [sottomaschera di rete](<./tecnologie/reti#subnet mask>), utilizzate per segnalare quali bit dell'indirizzo sottoporre a verifica e quali ingorare tramite processo di [ANDing](./tecnologie/operatori#logici) e dal protocollo di routing [OPSF], utilizzato per aprire per primo il percorso più breve.
La wildcard ha il funzionamento inverso della maschera di sottorete dal punto di vista degli operatori logici, ovveroç
- **0**: Simboleggia la richiesta di verifica del dato
- **1**: Indica che il dato può essere ignorato

**ESEMPIO**

| Wildcard mask | Ultimo ottetto | Descrizione                                                                                 |
| ------------- | -------------- | ------------------------------------------------------------------------------------------- |
| 0.0.0.0       | 00000000       | Controlla tutti i bit di tutti gli ottetti                                                  |
| 0.0.255.255   | 00000000       | Controlla gli ultimi due ottetti                                                            |
| 0.0.0.63      | 00111111       | controlla i primi 3 ottetti e i primi 2 bit dell'ultimo ottetto.<br>Ignora gli ultimi 6 bit |
| 1.1.1.1       | 11111111       | Non verificare nessun bit dell'indirizzo IP                                                 |

Tramite l'utilizzo ponderato delle Wildcard mask, è possibile verificare uno specifico IP, l'appartenenza ad se l'indirizzo appartiene ad uno speciico gruppo, ad una determinata sottorete (utilizzando l'inverso della sua maschera di sottorete) o ad una rete intera.

#### Procedura
Il processo di funzionamento di una ACL è il seguente:
1. Il Router estrae l'indirizzo IP del mittente
2. Il Router inizia ad applicare le verifiche delle ACE in ordine sequenziale
3. Quando l'indirizzo IP rientra nei parametri dell'ACE, esegue i comandi scritti all'interno di essa
4. Se il pacchetto non rientra nelle richiste di nessuna ACE, viene scartato di default (ultima ACE, inserita in modo implicito nell'ACL).

Nel caso di connessioni in [TCP](./tecnologie/protocolli#tcp), è possibile utilizzare una connessione *stateful* (ovvero i messaggi contengono dati utili per stabilire lo stato della connessione) utilizzando delle parole chiave prestabilite, da considerare anche nei controlli dell'ACL.
#### Struttura
Vedi [qua](<CISCO IOS.md#router#configurazione>).
#### Creazione
Per creare una ACL bisogna:
- Scrivere le specifiche delle policy tramite editor di testo
- Aggiungere i comandi di configurazione IOS per eseguire i compiti descritti
- Includere eventuali osservazioni come documentazione
- Copiare e incollare i comandi all'interno del dispositivo
- Testare le regole implementate (senza impattare il traffico di rete)

#### IPv6
La coesistenza di IPv4 e IPv6 può portare a problemi dal punto di vista della sicurezza (per gli ambienti dual-stack, ovvero che utilizzano contemporaneamente entrambi i protocolli), come:
- Utilizzo del protocollo [NDP](./tecnologie/protocolli#ndp) (Neighbor Discovery Protocol) sfruttando il [Teredo tunneling] per ottenere un indirzzo IPv6 ufficiale tramite canale IPv4 UDP

E' possibile evitare questo tipo di attacchi aggiungendo delle ACL per gli indirizzi IPv6:

```cisco
Router(config)# ipv6 access-list _access-list-name_

Router(config-ipv6-acl)# deny | permit _protocol_ {_source-ipv6-prefix_ / _prefix-length_ | any | host _source-ipv6-address_} [ _operator_ [ _port-number_ ]] { _destination-ipv6-prefix_ / _prefix-length_ | any | host _destination-ipv6-address_ } [ _operator_ [ _port-number_ ]] [ dscp _value_ ] [ fragments ] [ log ] [ log-input ] [ sequence _value_ ] [ **time-range** _name_ ]
```

#### Indirizzi comuni da bloccare
Per evitare attacchi di Sppoofing, di solito è consigliato negare l'accesso a indirizzi di uso comune come:
- 0.0.0.0
- Indirizzi broadcast
- Indirizzi di reti private (es. 127.0.0.0/8)
- Indirizzi APIPA (es. 169.254.0.0/16)
- Indirizzi privati riservati (RFC 1918)
- IP Multicast (242.0.0.0/4)

#### Mitigazione ICMP
Considerando che molti messaggi ICMP possono sia essere sfruttati per portare a segno attacchi informatici, che essere utilizzati dalla rete per il suo corretto funzionamento (es. chiamate echo, o messaggi di errore vari), è sempre buona norma impedire le chiamate ICMP in uscita che non siano:
- destination unreachable
- source quench
- reply

#### Mitigazione [SNMP](./tecnologie/protocolli#snmp)
Considerando che il protocollo viene utilizzato per gestire le impostazioni della rete, è consigliato [disabilitare il protocollo](<CISCO IOS.md#acl#blocco protocollo>) per le comunicazioni con dispositivi all'esterno della rete

### NetFlow
Strumento utilizzato per effettuare analisi a livello di rete, sviluppato da Cisco. Permette di effettuare analisi, troubleshooting di rete, accounting basato sulla sessione e previsione dei costi in base all'utlizzo dell'utente. E' utilizzato per utilizzato per gestire comunicazioni tramite [SNMP](./tecnologie/protocolli#snmp). NetFlow analizza i pacchetti inviati e ricevuti durante una sessione e li analizza, fornendo informazioni utili riguardo la sessione e lo stato della rete, come:
- IP del mittente
- IP del destinatario
- Porta di partenza
- Porta di destinazione
- Protocollo di [livello 3](<#3 - Rete>) utilizzato
- Marchio ToS (Classe di servizio)
- Interfaccia logica di input (Router o dello Switch)

A queste informazioni ne vengono aggiunte altre, come:
- timestamp di inizio sessione
- timestamp di fine sessione

### Port Mirroring
È una feature dello Switch che permette di duplicare il traffico ed inviare una copia ad un dispositivo apposito, utilizzato per monitorare la rete.

### Syslog server
Server utilizzato appositamente per memorizzare i report inviati da Switch, Router e altri dispositivi di rete, utili per effettuare il troubleshooting.
Il Syslog possiede due caratteristiche principali:
- L’abilità di selezionare il tipo di informazione di logging catturata
- L’abilità di specificare il destinatario del messaggio Syslog catturata.

Essendo un ambiente che utilizza molto spesso dati temporali, è particolarmente importante proteggere il server da attacchi che sfruttano il protocollo [NTP](./tecnologie/protocolli#ntp), o la porta 123 (tipicamente utilizzata per gestire questo tipo di protocolli).

#### syslog-ng
Sono sistemi di log di ultima generazione, che offrono una resistenza maggiore ad attacchi di esfiltrazione.

### NTP
Il [Protocollo del Tempo della Rete](./tecnologie/protocolli#ntp) è importante per tenere traccia in maniera efficace dei log di più dispositivi connessi alla stessa rete. Per questo è spesso soggetto ad attacchi, volti a modificare la variabile temporale per i log di sistema.

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
I Firewall di nuova generazione (New Generation Firewall) sono dispositivi che combinano le classiche funzionalità di un firewall con altre funzionalità di filtraggio degli host all'interno della rete tramite inline Deep Packet Inspection(DPI, Ispezione profonda dei pacchetti) o sistemi IPS (Sistema di Protezione dalle Intrusioni). Un bonus nell'utilizzo dei NGF è anche l'implementazione di servizi offerti da altri strumenti, come i [[#SIEM]]. Nel complessivo, i NGF offrono una varietà di messaggi di controllo di eventi come:
- Connessione
- Intrusione
- Host (endpoint)
- [Network Discovery](./tecnologie/protocolli#nd)
- [[#NetFlow]]

## Firewall
Sono software o dispositivi che permettono di filtrare i messaggi in ingresso in una rete e perciò devono/offrono funzionalità per:
- essere resistenti agli attacchi informatici
- essere l’unico punto di contatto tra una LAN e una WAN
- applicare le [Policy di Controllo degli Accessi](#ACP)
- sanare il flusso del protocollo, prevenendo lo sfruttamento di determinati protocolli per portare a segno attacchi
- bloccare l’invio di dati malevoli da server e client
- ridurre i controlli necessari da parte dei team di gestione in quanto basta controllare le politiche dei firewall per effettuare un’analisi

### [NGF](#NGF)

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

Qualora nel caso all'interno della DMZ ci sia un host fortezza (ovvero un dispositivo adibito a filtrare il traffico) o un [firewall schermato], che viene utilizzato per filtrare il traffico proveniente da reti non fidate che è stato accettato dall'edge router, per poi inviare i pacchetti filtrati al router interno, la DMZ prende anche il nome di Subnet configuration.

#### ZPF
I [Firewall](#firewall) con Policy Basate sulla Zona utilizzano il concetto di zona (gruppo di una o più interfacce aventi funzionalità simili) per stabilire le regole in base alle necessità e alla tipologia di zona da proteggere. L’utilizzo di questa architettura permette una maggiore flessibilità e semplicità di gestione, in quanto consente di ottenere benefici quali:
- Indipendenza dalle ACL
- Blocco del traffico come opzione di default 
- Traffico permesso di default solo tra interfacce diverse della stessa zona
- Facilità di lettura e scrittura delle policy e dei troubleshooting (tramite software come [Cisco C3PL])
- Raggruppamento delle interfacce fisiche in zone
- Policy applicabili per traffico unidirezionale tra zone

Nel caso si voglia definire una policy per la self zone (il Router), occorre tenere conto della gestione e controllo dei piani di traffico, in particolare i protocolli di routing, [SSH](./Tecnologie/protocolli#ssh) e [SMNP] e in generale tutti i protocolli che permettano di manipolare la gestione e il controllo di dispositivi.

##### Configurazione
Per configurare una ZPF basta seguire i seguenti passaggi:
1. Definire le zone
	- Cosa edve essere incluso nella zona?
	- Quale sarà il nome di ogni zona?
	- Che tipo di traffico passerà in entrambe le direzioni?
2. Definire le policy tra le varie zone (per il traffico in entrambe le direzioni)
	-  
3. Progettare l'infrastruttura fisica
4. Identificare gruppi di zone simili e unire i requisiti di traffico

##### Azioni
Le azioni effettuabili da una ZPF sono 3:
- Inspect: ispeziona il pacchetto
- Drop: nega l'accesso al pacchetto
- Passaggio: consente il passaggio al pacchetto

**REGOLE PER IL TRAFFICO IN TRANSITO**

| Interfaccia di origine menbra della zona | Destinazione menbro della zona | Zone parificate | Esiste una policy | Risultato |
| ---------------------------------------- | ------------------------------ | --------------- | ----------------- | --------- |
| No                                       | No                             | Non si sa       | Non si sa         | PASS      |
| Si                                       | No                             | Non si sa       | Non si sa         | DROP      |
| No                                       | Si                             | Non si sa       | Non si sa         | DROP      |
| Si (privata)                             | Si (privata)                   | Non si sa       | Non si sa         | PASS      |
| Si (privata)                             | Si (publica)                   | No              | Non si sa         | DROP      |
| Si (privata)                             | Si (publica)                   | Si              | No                | PASS      |
| Si (privata)                             | Si (pubblica)                  | Si              | Si                | INSPECT   |
**REGOLE PER IL TRAFFICO ALL'INTERNO DELLA ZONA ROUTER (SELF ZONE)**

| Interfaccia di origine menbra della zona | Destinazione menbro della zona | Zone parificate | Esiste una policy | Risultato |
| ---------------------------------------- | ------------------------------ | --------------- | ----------------- | --------- |
| Si (self-zone)                           | Si                             | No              | Non si sa         | PASS      |
| Si (self-zone)                           | Si                             | Si              | No                | PASS      |
| Si (self-zone)                           | Si                             | Si              | Si                | INSPECT   |
| Si                                       | Si (self-zone)                 | No              | Non si sa         | PASS      |
| Si                                       | Si (self-zone)                 | Si              | No                | PASS      |
| Si                                       | Si (self-zone)                 | Si              | Si                | INSPECT   |

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
- Integrare sistemi di prevenzione delle intrusioni ([IPS](#IPS))
- Aggiungere coscienza e controllo del livello 7 (Applicazione) per vedere e bloccare software rischiosi
- Aggiornano i percorsi al fine di includere informazioni future
- Tecniche per identificare le [minacce](#Threat) della sicurezza in evoluzione
- Possibilità di includere variabili come user, dispositivo, ruolo, applicazionee profilo della minaccia alle policy di sicurezza
- Performance migliorate grazie allàutilizzo di [NAT](#NAT), [VPN](./tecnologie/reti#vpn) e ispezioni stateful

#### Firewall trasparente
Filtra il traffico IP tra una coppia di interfacce a ponte.

#### Firewall ibrido
Una combinazione di due o più firewall tra quelli sopra menzionati.

### Difesa a strati
Consiste nell'utilizzo di più livelli di difesa all'interno di una rete strutturata. Si suddivide in 4 livelli in base al livello di protezione offerto:
1. Sicurezza del cuore della rete
2. Sicurezza del perimetro: 
3. Sicurezza delle comunicazioni
4. Sicurezza dell'endpoint

Ogni livello è protetto da almeno un Firewall
#### Cuore della rete
Livello che si occupa di proteggere da malweare e anomalie di traffico, anche tramite policy di rete

#### Perimetro
Strato di comunicazione tra due livelli.

#### Comunicazioni
SI occupa di verificare le informazioni

#### Endpoint
Gestisce làidentità del dispositivo e l'aderenza alle policy di sicurezza


## [[#IDS]]
### [[#HIDS]]
Gli HIDS forniscono dati di log riguardanti le operazioni analizzate. Nel caso di log registrati nel sistema [Windows](./os/windows), vengono registrate 5 categorie di log:
- Applicazione
- Sistema
- Setup
- Sicurezza (che contengono solo il risultato degli audit, intesi come successi o fallimenti)
- Linea di comando

Ognuno di queste categorie accetta messaggi log di 5 tipi:

| Tipo di evento         | Descrizione                                                                                                                                        |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Errore                 | Un errore indica un evento che indica un problema significativo, come la perdita di dati o di funzionalità, o quando un processo viene interrotto. |
| Avviso                 | Indica un avvenimento che non pregiudica il funzionamento corretto delle funzionalità, ma che potrebbe comunque peggiorare in futuro               |
| Informazione           | Descrive l'avvenuto successo di un'operazione (es. caricamento di un driver di rete)                                                               |
| Verifica di successo   | Registra tutti gli eventi inerenti i tentativi di accesso di sicurezza avvenuti con successo (es. login)                                           |
| Verifica di fallimento | Registra tutti gli eventi inerenti i tentativi di accesso di sicurezza falliti (es. password errata)                                               |
[fonte](https://msdn.microsoft.com/en-us/library/windows/desktop/aa363662(v=vs.85).aspx)

### NIDS
I Network Intrusion Detection Systems sono dispositivi di identificazione delle intrusioni a livello dell'intera rete. Un esempio di NIDS è Snort, un applicativo della suite di tool NSM, che produce alert ricercabili e leggibili tramite software Sguil e Squert.

- Un sito utile per effettuare test tramite Snort è [testmyids](http://testmyids.com.domreaper.com/), ovvero una pagina web, che mostra il seguente testo:
	```testmyids
	uid=0(root) gid=0(root) groups=0(root)
	```
	Se il NIDS è impostato correttamente, la navigazione attiverà un alert di notifica.

## [[#IPS]]
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

### Alert
Gli alert sono delle notifiche inviate dall'IPS (funzionalità disponibile anche degli [[#IDS]] a seguito di una violazione delle regole impostate, o di identificazione di pattern di malware conosciuti all'interno del messaggio.

Di solito includono un set di informazioni di base, che possono essere implementate in base alla configurazione scelta. I dati di base sono:
- **SrcIP**: Indirizzo IP del mittente
- **SPort**: Porta di invio
- **DstIP**: IP del destinatario
- **DPort**: Porta di arrivo
- **Pr**: Protocollo utilizzato

Ogni Alert è anche dotato di un ulteriore set di dati informativi, che ne facilitano l'analisi, ovvero:
- **ST**: Status dell'evento (RT epr Real Time) con sfondo colorato in base alla severità dell'alert
- **CNT**: Numero di volte in cui è stato attivato l'alert
- **Sensor**: Agent che ha inviato làalert
- **Alert ID**: Composto da due parti: ID dell'agente e l'ID dell'evento nell'agent
- **Date/Time**: Timestamp della data di attivazione dell'alert
- **Event Message**: Configurato dall'operatore per includere dati importanti riguardanti l'evento

#### Valutazione
E' importante effettuare un'attenza valutazione degli alert per evitare di analizzare dati che possano aver fatto scattare gli alarm, anche se non avrebbero dovuto (o il caso contratio). In generale gli eventi rientrano in una di queste 4 categorie:

|                               | Vero                   | Falso                                 |
| ----------------------------- | ---------------------- | ------------------------------------- |
| Positivo (alert eseguito)     | Incidente avvenuto     | Incidente non avvenuto                |
| Negativo (alert non eseguito) | Incidente non avvenuto | Incidente avvenuto, ma non registrato |
L'obiettivo di un sistema di alert efficiente è evitare il più possibile il **falso negativo**, ovvero il caso nel quale l'incidente sia avvenuto, ma non sia stato registrato dal sistema. Il **falso positivo** rimane un evento da evitare, ma la sua esecuzione ha un effetto indesiderato di gravità nettamente minore rispetto al falso negativo.

#### Analisi
##### Probabilistica
L'analisi probabilistica degli alert consiste nell'analizzare la probabilità che un determinato evento avvenga, in base alle azioni compiute. Sono utili per definire l'attenzione da porre ai vari elementi in ambito di sicurezza.  Da preferirsi quando ci sono delle variabili che non permettono di avere una certezza delle conseguenze di determinate azioni.

##### Deterministica
L'analisi deterministica degli alert si basa sulla capacità di stabilire il livello di rischio in base alle informazioni presenti sulla specifica vulnerabilità (es. un attacco sarà critico se tutti i passaggi per eseguirlo sono effettuabili sulla rete di riferimento).

### Dati
E' spesso utile ricordare i nomi comunemente assegnati alla tipologia di dato presente in un pacchetto:
1. **ts**: inizio sessione e timestamp
2. **uid**: ID unico della sessione
3. **id.orig_h**: IP del mittente
4. **id.orig_p**: Porta utilizzata mittente
5. **id.resp_h**: IP del destinatario
6. **id.resp_p**: Porta utilizzata dal destinatario
7. **proto**: Protocollo utilizzato per la sessione
8. **service**: Protocollo a livello di applicazione utilizzato
9. **duration**: Durata della sessione
10. **orig_bytes**: byte dal mittente
11. **resp_bytes**: byte dal destinatario
12. **orig_packets**: Pacchetti inviati dal mittente
13. **resp_packets**: Pacchetti inviati dal destinatario

#### Estratti
Sono i dati estrapolati da un pacchetto (ad esempio il contenuto di una mail, o i suoi allegati)

#### Intero pacchetto
Sono i dati più consistenti, in quanto comprendono l'interi pacchetto da analizzare.

#### Sessione
Comprende una touple (lista) dei primi 5 punti sopra elencati.

Un tool ([[#NIDS]]) utile per effettuare analisi a livello di sessione è [Zeek](https://zeek.org/). Zeek provvede anche ad effettuare un log di tutte le transazioni della sessione analizzata.


#### Statistici
I dati statistici sono dati di tipo riassuntivo, creato in base a specifici elementi (decisi in partenza) da analizzare. Alcuni approcci che utilizzano questo tipo di dati sono:
- [Analisi basata sul comportamento della rete (NBA)] 
- [Identificazione di comportamenti anomali nella rete (NBAD)],
- [Esportatore di informazioni NetFlow o IP (IPFIX)] (IETF standard per la versione 9 di Cisco NetFlow)

Sono disponibili in commercio prodotti che sfruttano tecniche di Machine Learning per offrire servizi in cloud di [NSM] (Network Security Monitoring). Un esempio è [Cisco Cognitive Threat Analytics](https://blogs.cisco.com/security/introducing-cisco-cognitive-threat-analytics).

#### Transazione
Tutti i messaggi inviati durante la sessione prendono il nome di **transazione**

### HIPS
Gli IPS basati sull’host (Host-based IPS) sono software da installare su dispositivi per monitorare e proteggere i sistemi operativi. Tra le loro funzionalità includono:
- La possibilità di bloccare azioni effettuate dall’utente nel caso divergano dai suoi comportamenti abitudinari (come la modifica di file di sistema)

Un particolare di cui tenere conto è che gli HIPS monitorano l’attività dell’endpoint su cui sono installati.

### NIPS
Gli IPS basati sulla rete (Network-based IPS) possono essere implementati su un dispositivo dedicato o su un dispositivo non dedicato e sono elementi indispensabili per la sicurezza della rete.

### Misure di sicurezza
Gli IPS devono essere configurati con particolare attenzione per:
- Fare distinzione tra protocolli SSL e non SSL (in quanto i primi saranno cifrati, e quindi non analizzabili) (anche nei casi il protocollo venga utilizzato per messaggi in HTTPS)
- Migliorare la sicurezza tramite validazione con [CRL e OCSP](<#revoca di un certificato>)
- Implementare soluzioni antimalware e filtraggio degli URL per filtrare i contenuti in HTTPS
- Utilizzare un'apparecchio Cisco SSL per decriptare i messaggi in SSL ed analizzarli 

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

## SIEM
Il Security Information Event Management (Gestore delle informazioni di sicurezza sugli eventi) è una tecnologia molto utilizzata dalle aziende per fornire report in tempo reale e analisi a lungo termine di eventi di sicurezza. Forniscono la somma dei servizi offerti dal SEM e dal SIM:
- Identificazioni di minacce esterne ed interne
- Monitoraggio delle attività  ed uso delle risorse
- Collezione dei log (con possibilità di fornire log aggiuntivi a quelli raccolti)
- Normalizzazione dei dati
- Correlazione
- Aggregamento
- Reporting
- Audit della conformità
- Support alle attività di [[#incident response]]

Considerando il costo di acquisto e di manutenzione, l'utilizzo dei SIEM è consigliato solo nel caso di organizzazioni che devono gestire la generazioni di milioni di eventi al giorno. 
Un esempio di software commerciale SIEM è [Splunk](https://www.splunk.com/)

## SOAR
Il Security Orchestration Automation and Response sono software che permettono di raccogliere informazioni relative la rete ed automatizzare la risposte ad eventi di basso livello. I sistemi SOAR offrono 3 servizi principali:
- Gestione delle minacce e delle vulnerabilità
- Risposta agli incidenti di sicurezza
- Automatizzazione delle operazioni di sicurezza

I software SOAR possono essere integrati con software SIEM.

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
### Introduzione
Le reti possono essere catalogate in base al livello di fiducia e rischio delle stesse, in base alla tipologia di comunicazioni (e al destinatario delle stesse) in:
- Alto livello di fiducia e rischio basso: LAN
- Medio-alto livello di fiducia e medio-basso livello di rischio: Extranet
- Medio-basso livello di fiducia e medio-alto livello di rischio: DMZ
- Alto livello di rischio e basso livello di fiducia: WAN

Il livello di fiducia può anche essere valutato in base alla sicurezza che la rete stessa offre riguardo:
- [Integrità dei dati](<#integrità>), ovvero la capacità di mantenere il messaggio inalterato (ed eventualmente segnalare in caso contrario)
- [Autenticazione](#autenticazione) della fonte per assicurare che il messaggio non provenga da fonti inaspettate
- [Confidenzialità dei dati](<#confidenzialità dei dati>) per assicurare che i dati non siano accessibili da utenti non autorizzati
- Non ripudio dei dati, ovvero assicurare che l'utente che ha creato/modificato il dato sia identificabile con precisione 

Per gestire contemporaneamente l'autenticazione e l'integrità dei dati nelle comunicazioni, spesso si fa uso del cosiddetto [[#HMAC]]

### DMZ
![[Pasted image 20241111223123.png]]
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

### Cloud
Nell'ambito di comunicazioni tra cloud diversi (es. cloud privato e cloud pubblico), le misure cautelative da prendere sono:
- Utilizzo di un a VPN per collegare i due servizi

## Sessione


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

## [Macchine virtuali](./os/virtualizzazione)
Le macchine virtuali possono essere soggette a particolari attacchi rispetto alle macchine reali. Per aumentare la sicurezza dell'infrastruttura, è buona pratica:
- Pianificare la sottorete nel quale utilizzare la macchine virtuale
- Disabilita porte e servizi non utilizzati per ridurre la superficie esposta
- Disabilita l'account di default e crea un set di utenti ad hoc, tenendo conto della [zero-trust policy](<#zero-trust model>)
- Installa [antimalware](#antimalware) (e mantienilo aggiornato)
- Installa un [host-based firewall](#HBF) e un [IDP](#IDP) o un [IDS](#IDS)

## Web Proxy
Dispositivo di protezione che si interpone durante ula navigazione web tra l'utente e la rete esterna. Permette di scansionare il traffico in uscita per verificare la presenza ed in caso la tipologia di dati in uscita (quindi evitare fuga di dati sensibili, confidenziali, ...)

## Gestione

### Risk management
La gestione del rischio consiste nella selezione delle specifiche dei controlli di sicurezza di un'organizzazione. Il Risk Management è un processo ciclico, che comprende 5 fasi:
- Identificazione del rischio
- [Risk assessment](<#Risk Assessment>)
- Pianificazione delle risposte al rischio
- Implementazione della risposta
- Monitoraggio e valutazione dei risultati

#### Tipi di rischio
- **Alto**: L'avvenimento (a seguito di negligenza nel trattarlo) potrebbe avere conseguenze catastrofiche per l'organizzazione
- **Basso**: L'utilizzo di cautela riduce sensibilmente la probabilità che esso avvenga.
- **Accettabile**: Le conseguenze del rischio sono minori (nessuna perdita) e sono state prese precauzioni per ridurre la probabilità che esso si verifichi

Il rischio può essere sia interno che esterno.

#### Procedura
Per eseguire la procedura del Risk Management, bisogno effettuare 4 passaggi.

##### Inquadramento
Identificazione delle minacce che aumentano il rischio analizzato tramite [risk analysis](<#Risk Analysis>). Le minacce possono comprendere:
- Perdita di dati, funzionalità, processi o prodotti
- Attacchi informatici
- Guasto di componenti
- Danno reputazionale
- Perdita di proprietà intellettuale

##### Valutazione
Si effettua una [valutazione del rischio](<#Risk Assessment>). I rischi possono essere prioritizzati sia in base al danno finanziario che a quello operativo (analisi qualitativa).

##### Risposta
Consiste nell'attuare procedure atte a ridurre o eliminare l'esposizione al rischio, tramite:
- mitigazione
- trasferimento
- accettazione
- eliminazione

##### Monitoraggio
Controllo costante dei rischi accettabili. Uno strumento utile è il [Registro dei rischi], che contiene un'elenco dei rischi e delle misure di intervento adottate in risposta.

### Vulnerability Management
La gestione delle vulnerabilità è un processo circolare, che consiste in 6 passaggi:
- **Scoperta**: Analisi di tutti gli asset ([Asset Management](<#Asset Management>)) per scoprire nuove vulnerabilità e definizione di una base-line
- **Prioritizzazione degli asset:** Assegnazione di un valore di priorità in base al valore dell'asset
- **Valutazione**: Determinare il profilo di rischio in base alle informazioni in possesso
- **Report**: Valutare il livello di rischio a livello commerciale in base alle [Policy di sicurezza](<#Policy di sicurezza>) e documentare un **piano di sicurezza** che descriva le vulnerabilità scoperte
- **Rimediare**: Pianificare una soluzione alle varie vulnerabilità in base alla loro categoria di rischio commerciale
- **Verifica**: Verificare che le minacce siano state eliminate tramite degli audit

### Asset Management
La gestione delle risorse consiste nell'implementare un sistema di tracciamento e configurazione dei dispositivi e dei software utilizzati nella rete (o che ne hanno accesso). Una [lista delle risorse da gestire](https://csrc.nist.gov/pubs/ir/8011/v2/final) è fornita dal [NIST](#NIST), che fornisce anche una procedura standard per effettuarne la gestione:
1. Automatizzare la scoperta e l'inventario delle risorse e del loro stato
2. Definire lo stato desiderato di ciascun dispositivo in base a [Policy](#policy), piani e procedure
3. Identificare le risorse che non rispettano i requisiti
4. Riparare le risorse identificate (sostituirle le la correzione non è possibile)
5. Ritornare al punto 1

#### MDM
La Gestione dei Dispositivi Mobile (Mobile Device Management) rappresenta una particolare sfida per la gestione della rete (in particolare se sono in atto politiche [BYOD](#BYOD)). Un fattore importante da considerare per la gestione dei dispositivi mobile è che **una parte della procedura è a responsabilità del proprietario del dispositivo**.

Una buona prassi è non dare nessun livello di fiducia a tutti i dispositivi mobile.

#### Software
Dei software che possono aiutare nella gestione dei dispositivi sono:
- [Cisco Meraki System Manager](https://meraki.cisco.com/) (MDM)

### Configuration Management
Processo che consiste nell'assegnare le corrette configurazioni ai dispositivi e monitorarne lo stato. Il NIST offre [un esempio](https://csrc.nist.gov/pubs/sp/800/128/upd1/final) (scaricabile) di Configuration Management per la sicurezza della rete. 

### Enterprise Patch Management
Operazione correlata al [Vulnerability Management](<#Vulnerability Management>), spesso richiesta a livello legale (negli [USA](#US) ad esempio dalla SOX e dalla HIPAA)

#### Tecniche
La EPM può essere effettuata in 3 modi diversi:
- **Agent-based**, ovvero quando ogni dispositivo monitora e richiede l'aggiornamento ad un **Patch Management Server** (da preferire per i dispositivi mobile)
- **Agentless scanning**, quando il **Patch Management Server** monitora ed invia gli aggiornamenti agli altri dispositivi della rete che ne hanno bisogno
- **Passive Network Monitoring**: nel caso il **Patch Management Server** invii automaticamente le patch da installare ai dispositivi

#### Software
Ci sono aziende che offrono software per l'Enterprise Patch Management, come:
- SolarWinds
- LANDesk
- Microsoft Windows Configuration Manager (SCCM

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

### HMAC
E' un processo basato sull'utilizzo di criptazione per creare un valore di controllo univoco tramite l'utilizzo di un algoritmo di [hash](Algoritmi.md#hash) su un messaggio e una chiave segreta. Questo rende il messaggio verificabile solo nel caso il destinatario sia in possesso della chiave.

### Firma digitale
Consiste in multipli processi di cifratura di un documento per permettere l'autenticazione e al contempo la modifica di alcuni elementi, tramite invio della chiave pubblica di ogni utente che ha provveduto a firmare il documento (ogni nuova firma impacchetta il documento firmato in precedenza in un ulteriore pacchetto cifrato).

#### PKI
Le Public Key Infrastructure possono essere utilizzate per:
- Fornire autenticazione per comunicazioni SSL/TLS
- Mettere in sicurezza il traffico di rete tramite IPsec VPN
- Utilizzare il protocollo HTTPS
- Fornire meccanismi di autenticazione per protocolli 802.11x
- Proteggere mail tramite S/MIME
- Proteggere messaggi istantanei
- Approvare e autorizzare applicazioni tramite Codi Signing (firma del codice)
- Proteggere i dati dell'utente tramite Encryption File System (EFS)
- Implementare l'autenticazione a due fattori nelle smart card
- Proteggere i dati all'interno di dispositivi USB

#### CA
Il processo di cifratura della firma digitale è gestito da aziende, note come Certificate Authorities (**CA**):
- DigiCert
- IdentiTrust
- Sectigo
- GoDaddy
- Let's Encrypt

##### Authority
Le CA gestiscono vari aspetti del processo di firma digitale e verifica della stessa, ovvero:
- Gestiscono l'algoritmo di generazione delle chiavi
- Stabiliscono il periodo di durata delle chiavi e dei certificati PKI (Public Key Infrastructure)
- Registrano le chiavi (privata e pubblica) all'interno di un database

I certificati sono divisi in 5 livelli, in base al livello di fiducia che gli viene assegnato dalle CA:

| Classe | Descrizione                                                                                                  |
| ------ | ------------------------------------------------------------------------------------------------------------ |
| 0      | Utilizzati per i test. Non viene effettuato nessun controllo                                                 |
| 1      | Utilizzato per la verifica delle email                                                                       |
| 2      | Utilizzato come prova dell'identià dalle aziende                                                             |
| 3      | Utilizzato per la firma di server e software. La CA effettua controlli indipendenti di identità e authority. |
| 4      | Utilizzato per le transazioni economiche tra aziende                                                         |
| 5      | Utilizzato da organizzazione private o organi per la pubblica sicurezza                                      |

##### Fiducia
Le CA possono utilizzare due modi differenti per gestire il rispetto dei criteri di fiducia (verifica dei certificati):
- Single-Root: la verifica viene effettuata da un unico server. Utile per piccole aziende in quanto difficile da scalare.
- Cross-Certified CA: Le varie CA stabiliscono rapporti di fiducia vicendevoli e permettono la validazione reciproca, aumentando il numero di server per la verifica vicendevolmente
- CA Gerarchica: Viene utilizzato un server principale (Root-CA), che crea certificati e gestisce diversi sotto-server, che a loro volta istituiscono certificati e/o sotto-server (struttura ad albero). Utile nel caso serva scalabilità, ma può risultare complicato determinare la catena del processo di firma

##### Interoperabilità
L'interoperabilità delle PKI era garantita dall'utilizzo di protocolli in comune come il Lightweight Directory Access Protocol ([LDAP]) e [X.500]. A seguito della volontà delle CA di istituire protocolli proprietari, invece che attendere l'evolversi di quelli condivisi, l'IETF ha pubblicato il framework [RFC 2527](https://datatracker.ietf.org/doc/html/rfc2527)  e lo standard X.509 per definire il formato dei certificati digitali (utilizzato ad esempio nei protocolli [SSL](./tecnologie/protocolli#ssl), [IPsec](./tecnologie/protocolli#ipec), [S/MIME], [EAP-TSL]).
Lo standard X.509v3 obbliga ad indicare delle date **not-before** e **not-after** per gestire la validità del certificato

##### Richiesta di un certificato
1. Copiare la chiave pubblica della CA (conferibile solo dalla Root-CA)
2. L'host, in possesso di una PKI, contatta la CA per ottenere un certificato di identità digitale per se e un certificato auto-firmato dalla CA stessa
3. L'host verifica l'autenticità dell'auto-certificato ricevuto tramite POTS (Plain Old Telephone System) per controllare la firma

##### Revoca di un certificato
I certificati possono essere revocati (ad esempio per compromissione della chiave) in due modi:
- Inserimento del certificato all'interno della **Certificate Revocation List** (o CRL), che contiene tutti i certificati revocati
- Viene effettuata la richiesta di revoca tramite OSCP (Online Certificate Status Protocol) indicando come status "revoca". Il messaggio viene immediatamente inviato al database

#### Cipher suite
Sono delle combinazioni di algoritmi che sfruttano protocolli [SSL/TLS] per fornire modularità e configurabilità alle comunicazioni cifrate. Si compongono di:
- Codice dell'Algoritmo di Autenticazione del Messaggio (MAC)
- Algoritmo di criptazione
- Algoritmo della chiave di scambio
- Algoritmo di autenticazione

Le Cipher suite sono particolarmente utili in quanto permettono di aggiornare costantemente i protocolli utilizzati da un'azienda senza doverne modificare l'architettura dei protocolli di comunicazione.

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

# Governance
La governance in ambito della Cybersecurity si occupa delle aree relative [[#autorizzazione]], [[#accountability]] e verifica che siano state applicate le necessarie misure di [[#mitigazione]] dei rischi e che le strategie di sicurezza attivate siano allineate con gli obiettivi di business aziendali.

Il tema principale della governance sono i dati, che sono trattati in base a determinate caratteristiche intrinseche:
## Dati
### Proprietario
E' la persona che assicura il rispetto delle policy e delle procedure, assegna un'adeguata classificazione del dato in base alle informazioni contenute e determina i criteri di accesso allo stesso.

### Controllore
La persona che determina lo scopo e le modalità con le quali il dato viene utilizzato

### Processore
Colui che processa il dato per conto del Controllore

### Custode
Colui che implementa le classi e i controlli di sicurezza in base alle regole definite dal Proprietario

### Assistente
Si assicura che il dato supporti le necessità di business dell'azienda e ne rispetti i requisiti

### Ufficiale di protezione
Persona che supervisiona la strategia di protezione dei dati

## [[#Policy]]
### Scopo
#### Master cybersecurity
Modello per un programma di policy sulla cybersecurity. Serve come strumento strategico per implementare i controlli di sicurezza.

#### System-specific
Policies utilizzate per gestire i dispositivi e i sistemi operativi con l'obiettivo di standardizzare applicazioni approvate, software, configurazioni di sistemi operativi, hardware e contromisure di hardening.

#### Issue-specific
Policies sviluppate per specifiche problematiche, circostanze e/o condizioni che possono richiedere direttive e requisiti specifici.

## Tipologia
Le policies di cybersecurity possono essere suddivise in 9 categorie, in base all'oggetto trattato. 

### Identificazione e autenticazione
Specifica chi dovrebbe avere accesso alla rete e alle risorse e quali procedure di autenticazione debbano essere utilizzate.

### Password
Definisce i requisiti minimi (lunghezza, numero e tipologia di caratteri utilizzabili) delle password.

### Uso accettabile
Definisce le regole di utilizzo della rete e dei dati, assieme alle conseguenza del mancato rispetto delle stesse.

### Accesso remoto
Definisce le modalità di accesso alla rete da remoto e quali informazioni siano disponibili nel caso.

### Manutenzione della rete
Definisce le procedure di manutenzione e aggiornamento dei sistemi operativi utilizzati dall'azienda a dei dispositivi.

### Incident handling
Fornisce guida su come rispondere ad un incidente di sicurezza all'interno dell'organizzazione.

### Dati
Definisce delle regole misurabili per il processamento dei dati in possesso dell'organizzazione (come la definizione del luogo di salvataggio, i livelli e tipologie di classificazione) e le metodologie di uso e rimozione dei dati.

### Credenziali
Attua delle regole per la creazione delle credenziali (come lunghezza delle password)

### Organizzative
Definisce come il lavoro dovrebbe essere svolto all'interno dell'azienda. Alcuni esempi sono:
- Cambio di management
- Policies di gestione degli asset

# Secure coding
## Introduzione
Il Secure Coding consiste nella scrittura di software ponendo particolare attenzione a pratiche o tecniche che permettano di minimizzare o evitare potenziali attacchi.

Le fasi del processo di sviluppo possono essere suddivise in:
- Developing (sviluppo): fase nella quale il codice che compone il software viene scritto e testato
- Staging e produzione: fase nella quale il software viene testato in un ambiente che simula quello reale (es. Windows 11). Passata questa fase il software va in Deploy, ovvero viene caricato sul supporto dal quale verrà reso utilizzabile al cliente
- Provisioning o deprovisioning: consiste nella fase di creazione o aggiornamento del software (il deprovisioning consiste invece nella sua rimozione)

## Normalizzazione
Decomposizione degli input in codice binario, per agevolare l'identificazione di eventuali input malevoli. questo processo aiuta a mantenere l'[integrità dei dati](<#integrità>).

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
- Utilizzo del cosiddetto **check digit**

## Controllo dell'integrità
Avviene tramite verifica di corrispondenza tra un valore ricevuto ed un altro posseduto (o calcolato).

### Checksum
Processo che consiste nella suddivisione di un dato e conversione delle varie porzioni in valori numerici. I valor numerici vengono sommati tra loro ed il valore viene incluso nel pacchetto. Una volta ricevuto il pacchetto, il valore viene ricalcolato dal destinatario e comparato al valore della somma ricevuto. Nel caso i valori corrispondano, il checksum darà riscontro positivo.

 Check digit: valore di controllo, ottenuto tramite algoritmo di processo di tutti o alcuni caratteri dell'input. Ad esempio:
 
```checkdigit
Input: 123789
Algoritmo:
1. moltiplico la prima cifra per 9
2. moltiplico la seconda cifra per 8
3. ...
4. sommo tutti i valori ottenuti
5. calcolo il numero che, sommato al risultato dell'operazione, ritorni il più vicino multiplo di 11
6. aggiungo la cifra in fondo all'input
7. Ogni volta che devo effettuare un controllo dell'integrità, basta rieffettuare làintera operazione e confrontare il risultato con il checkdigit
```

### [Hash](Algoritmi.md#hash)
Utilizzo di algoritmi complessi che permettono di trasformare il dato in maniera univoca (non possono esistere due dati che diano lo stesso risultato una volta processati dall'algoritmo). La verifica avviene tramite comparazione del dato hashato con un valore ottenuto da un qualunque software di calcolo dell'hash.

#### Salting
Consiste nell'aggiungere dei caratteri alla fine del valore prima di eseguire l'hasing. Permette di proteggere un dato prima di memorizzarlo, rendendo più difficile la contraffazione (ad esempio tramite [dictionary](#dictionary)), e allo stesso tempo rende possibile l'utilizzo di dati duplicati grazie all'utilizzo di salt diversi in base all'utente.

### Version control
Processo che permette di evitare errori prodotti dalla modifica simultanea di un file tramite creazione di un codice univoco per ogni salvataggio. Se un file viene modificato da due utenti diversi, al secondo utente che salverà il file, verrà impedito il salvataggio e verrà richiesto di aggiornare il file con il salvataggio precedente prima di poter inviare i cambiamenti.

### Backup
Meccanismo di salvataggio su più localizzaizioni dello stesso dato. Di solito viene effettuato ad archi temporali costanti e permette di avere una copia del dato da utilizzare nel caso di corruzione dello stesso nella memoria principale.

### Autorizzazione
Meccanismo che permette di verificare se l'utente specifico ha il permesso di vedere/creare/modificare file situati nella specifica area.

### Firma
Stringa di codice ottenuta tramite hashing del software e resa pubblica. Utilizzabile per verificare che il software utilizzato sia originale e non sia stato manomesso prima dell'installazione.

### Secure cookies
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
- [Docker](./software/docker)
- podman
#### Pipeline
Servono ad automatizzare le procedure.
- [Jenkins](./software/jenkins)
- Travis CI
- GitHub Actions
#### Infrastructure
Può essere di tipo **On premise** o **cloud**, dove i secondi permettono di avere potenza di calcolo, spazi di archiviazione e servizi di business logic adattabili ed un costo variabile in base all'uso effettivo.
- [AWS](./server/aws)
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
## [Crittografia](Algoritmi.md#criptazione)
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
Per operations si intende tutta la parte di gestione dei servizi, utile per effettuare il deploy e la manutenzione dei sistemi e dei servizi.

La messa in sicurezza della fase di operations inizia durante la pianificazione dell'artchitettura della rete e la sua implementazione, per poi proseguire durante la sua creazione e manutenzione. Per effettuare queste operazioni di messa in sicurezza, è necessario avere conoscenze riguardo:
- Sistemi operativi
- Programmazione di base
- [Protocolli](./Tecnologie/Protocolli)
- Vulnerabilità delle reti e mitigazione dei rischi
- [[#Hardening]] dei dispositivi
- [[#Firewall]]
- [[#IPS]]

## Security testing
E' necessario effettuare numerosi test (da ripetere ad intervalli regolari di tempo) durante i processo di Operations nelle sua varie fasi e fornire i risultati dei test al team di sicurezza.

Durante la fase di **implementazione** si testano specifiche parti della rete tramite ST&E (Security Testing and Evaluation, ovvero test di sicurezza e relativa valutazione), ovvero un test che persegue i seguenti obbiettivi:
- Scoprire le falle di design, implementazione e funzionali che potrebbero portare alla violazione delle policy di sicurezza
- Determinare l'adeguatezza dei meccanismi di sicurezza, assicurazioni e proprietà per applicare le policy di sicurezza
- Assegnare un grado di consistenza tra la documentazione e la sua implementazione

Dopo che la rete è stat installata in maniera stabile, i test da effettuare invece sono:
- [[#Pentest]]: simulazione di attacchi dall'esterno
- [Network scanning]: 
- [Vulnerability scanning]
- [Password cracking]
- [Log review]
- [Integrity checkers]
- [Virus detection]

Gli obiettivi da raggiungere a seguito dei test sono:
- Definire le attività di mitigazione
- Fornire un benchmark per tracciare il progresso nel rispetto dei requisiti di sicurezza di un'organizzazione
- Valutare lo stato dell'implementazione dei requisiti di sicurezza
- Condurre un analisi costi-benefici per i miglioramenti dello stato della rete
- Migliorare le attività correlate
- Fornire un punto stabile di partenza per le azioni correttive

### Software
Alcuni software utili per effettuare test della rete (alcuni potrebbero essere datati) sono:
- [Nmap/Zenmap](Nmap.md): Scansione dei dispositivi e dei servizi della rete e mappatura
- [SuperScan](./Software/Superscan): Port scanner per protocolli TCP e UDP per determinare quali servizi siano disponibili nelle porte utilizzate (es. ping, traceroute, hostname, ecc.)
- [[#SIEM]]: Fornisce report e analisi i sicurezza della rete a lungo termine
- [GFI LANguard]: Scanner di sicurezza della rete
- [Tripwire]: Analizza e convalida configurazioni IT che vadano contro le policy aziendali e le best practices di sicurezza
- [Nessus]: Software di scansione delle vulnerabilità incentrato sull'accesso da remoto, configurazioni errate e attacchi DoS contro lo stack TCP/IP
- [L0phtCrack]: Password auditing a recovery
- [Metasploit]: Fornisce informazioni riguardo le vulnerabilità e aiuta nei [[#Pentest]] e per lo sviluppo di firme per gli [[#IDS]]

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
#### Sistema
I log del Sistema operativo descrivono gli eventi collegati ad azioni come:
- Request del client e response del server per autenticazioni dellàutente avvenute con sucecsso
- Informazioni sulle transizioni (quantità e dimensioni) in un determinato arco di tempo

#### Applicazioni di sicurezza
Questi log sono fornite dalle applicazioni come Firewall, Antimalware, HIPS, ecc.. Questo tipo di log è particolarmente utile per effettuare analisi di auditing, per l'identificazione di trend a breve e lungo termine e per la compilazione della documentazione che dimostri il rispetto delle normative e dei requisiti di legge.

##### Syslog
Il [syslog](./tecnologie/protocolli#syslog) è un protocollo che permette di gestire specifiche come il formato dei messaggi, la struttura dell'applicazione client-server e il protocollo di rete.

##### Server Log
Sono messaggi di server log registrati all'interno del srever. I Server Log proprietari più comuni sono Apache Access Log e IIS Access Log:
```Apache_Access_log
203.0.113.127 – dsmith [10/Oct/2016:10:26:57 - 0500] "GET /logo_sm.gif HTTP/1.0" 200 2254 "http://www.example.com/links.html" "Mozilla/5.0 (Windows NT 6.1; Win64; x64; rv:47.0) Gecko/20100101 Firefox/47.0"
```

```IIS_Access_Log
6/14/2016, 16:22:43, 203.0.113.24, -, W3SVC2, WEB3, 198.51.100.10, 80, GET, /home.htm, -, 200, 0, 15321, 159, 15, HTTP/1.1, Mozilla/5.0 (compatible; MSIE 9.0; Windows Phone OS 7.5; Trident/5.0; IEMobile/9.0), -, http://www.example.com
```
#### Setup
Log che contengono informazioni relative l'installazione di software (inclusi gli aggiornamenti di Windows)

#### Security
Contengono informazioni relative i tentativi di accesso e le operazioni su file o gestione degli oggetti o degli accessi.

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

# Attività forense
## Incident Analysis
### Cyber Kill Chain
Metodologia sviluppata da Lockheed Martin per identificare e prevenire intrusioni informatiche, che consiste in 7 passaggi eseguiti tipicamente da un attaccante (se durante uno qualunque dei passaggi la catena si attiva, significa che l’attacco è stato scentato):
1. **Ricognizione**: identificazione sull’obiettivo
2. **Armamento**: si preparano il malware e la backdoor
3. **Consegna**: malware e script di creazione della backdoor vengono inviati tramite mail (o simili) alla vittima
4. **Sfruttamento** della vulnerabilità per attivare lo script
5. **Installazione** della backdoor per installare il malware
6. **CnC** (Command and Control) per manipolare l’obiettivo 
7. **Azioni e obbiettivi**: l’attaccante usa l’accesso al dispositivo del bersaglio per portare a compimento l’attacco

#### Ricognizione
Attività di ricerca e raccolta di informazioni riguardanti la rete bersaglio dell'attacco. Le informazioni possono provenire sia dall'interno della rete (eventuali porte aperte, messaggi informatici, ecc.), che dall'esterno (es. informazioni trovate sui social o sui motori di ricerca). Le informazioni trovate possono essere utili per analizzare la fattibilità dell'attacco ed eventuali ulteriori diramazioni che lo stesso può prendere.

Metodi comuni di raccolta informazioni sono:
- Raccolta delle email aziendali
- Identificazione dei dipendenti tramite social media
- Raccolta delle informazioni riguardanti le pubbliche relazioni
- Analisi dei servizi che si interfacciano con la rete (es. siti web)
- Scansioni della rete, identificazione degli IP e delle porte aperte

In questa fase di solito le attività del SOC a difesa dell'attacco sono:
- Creazione di avvisi di web log e ricerca di dati storici
- Analisi degli analytics del browser
- Creazione di un playbook per identificare il comportamento e le modalità di ricognizione utilizzate
- Prioritizzare la difesa degli account analizzati dall'attaccante

#### Armamento
Le informazioni trovate vengono utilizzate per identificare falle del sistema e creare un software che le possa sfruttare per ottenere dati o danneggiare l'organizzazione. Per la creazione dell'attacco è anche possibile utilizzare attacchi già preimpostati da utenti terzi, che si adattano alle vulnerabilità del bersaglio.

Gli attacchi più pericolosi sono i cosiddetti **Zero-day attack** ()attacchi eseguiti al giorno zero), in quanto non offrono tempo sufficiente per identificare, analizzare o prepararsi a rispondere all'attacco.

L'attaccante di solito:
- Cerca online il tool di attacco più adeguato
- Prepara un documento da inviare alla vittima
- Seleziona o crea un sistema di backdoor e un'infrastruttura [CnC](#CnC)

In questa fase di solito le attività del SOC a difesa dell'attacco sono:
- Assicurarsi che le configurazioni degli IDS siano aggiornate
- Effettuare analisi complete per malware
- Impostare sistemi di identificazione di comportamenti sospetti basate sui malware attualmente conosciuti
- Identificare eventuali ,malware vecchi o costruiti su misura per la rete
- Identificare i mezzi di armamento siano più comuni in base alle varie campagne

#### Consegna
In questa fase l'attaccante trasmette il vettore dell'attacco al bersaglio. Questo  può avvenire tramite mail, dispositivi USB, sito web o altro. Spesso il codice viene mascherato per evitare i controlli di sicurezza (a discapito della velocità di esecuzione)

L'attaccante agisce tramite sistemi diretti (sito web) o indiretti (mail, chiavetta USB, interazioni nei social o siti compromessi)

In questa fase di solito le attività del SOC a difesa dell'attacco sono:
- Analizza il percorso utilizzato per la consegna
- Identifica i server, le persone e i dati bersaglio dell'attacco
- Inferisce l'intento dell'attaccante in base al suo obbiettivo
- Raccoglie le mail e i log di web per una successiva fase di ricostruzione [forense](<#Analisi Forense>)

#### Sfruttamento
L'attaccante utilizza il tool inviato per sfruttare le vulnerabilità dell'infrastruttura, attaccando specifici bersagli (che possono essere utenti, sistemi operativi o applicazioni) e prendere controllo degli stessi. L'attaccante pone particolare attenzione a questo passaggio, in quanto l'utilizzo di elementi non previsti può far scattare conseguenze indesiderate (come attacchi DoS o riavvi di sistema, che potrebbero allarmare l'organizzazione).

L'attaccante di solito:
- Utilizza i bersagli scelti
- Acquisisce o sviluppa il metodo di sfruttamento
- Utilizza un metodo di sfruttamento attivato dall'avversario per sfruttare vulnerabilità del server
- Utilizza un metodo di sfruttamento attivato dall'utente nel caso di invio del vettore tramite metodi indiretti

In questa fase di solito le attività del SOC a difesa dell'attacco sono:
- Aumentare la consapevolezza dei dipendenti ed effettuare test tramite finte spam
- Allenare gli sviluppatori al [Secure Coding](<#Secure Coding>)
- Attuare misure di [hardening](#Hardeinig) per gli endpoint
- Effettuare attività forense sugli endpoint bersagliati da un attacco

#### Installazione
L'attaccante inserisce la backdoor nel sistema per assicurargli un accesso alla rete (è importante per l'attaccante che la backdoor non faccia scattare sistemi di allarme dell'organizzazione o processi di comunicazione automatica con altri dispositivi). La backdoor deve persistere anche nel caso di riavvii della macchina nella quale è isntallata

L'attaccante di solito:
- Installa una webshell o il collegamento ad un webserver per assicurarsi un accesso
- Crea dei punti persistenti di conenssione tramite servizi, [chiavi di AutoRun], ecc.
- A volte modifica i timestamp del malware, per farlo apparire come file del Sistema Operativo

In questa fase di solito le attività del SOC a difesa dell'attacco sono:
- Configurazione corretta degli [HIPS](#HIPS)
- Determinare i requisiti di accesso utilizzati dal malware
- Effettuare un audit dell'endpoint per scoprire file creati in modo anomalo
- Determinare se il malware è già conosciuto, o se sia una variante nuova

#### CnC
In questa fase l'attaccante stabilisce una connessione con il dispositivo infettato e lo sfrutta per operare all'interno della rete. Di solito le comunicazioni avvengono tramite [IRC] (Chat di Relay tramite Internet) non autorizzate.

L'attaccante di solito:
- Avvia una comunicazione a due vie con l'infrastruttura
- Di solito opera tramite [DNS](./Tecnologie/Protocolli#DNS), web e [protocolli di email](./Tecnologie/Protocolli#Email)
- Può utilizzare un suo dispositivo per operare, o un'altra rete precedentemente infettata

In questa fase di solito le attività del SOC a difesa dell'attacco sono:
- Ricerca eventuali infrastrutture CnC
- Scopre infrastrutture CnC tramite analisi dei Malware
- Previene l'esecuzione di azioni bloccando o disabilitando al connessione CnC
- Controlla il numero di Internet Points attivi
- Aggiorna o personalizza le regole di blocco dei CnC nei [Web Proxy](<#Web Proxy>)

#### Azioni e obbiettivi
L'attaccante utilizza la CnC per navigare nella rete, trovare le informazioni bersaglio ed effettuare azioni con le stesse (esfiltrazione, cifratura, modifica, cancellazione, ecc.) o con la rete stessa (mining di bitcoin, DoS, ecc.). In questa fase l'attaccante ha accesso completo alla rete come utente infettato.

L'attaccante di solito:
- Raccoglie credenziali di utenti
- Effettua [privilege escalation](<#Privilege Escalation>)
- Effettua operazioni di ricognizione della rete
- Si muove all'interno dell'ambiente
- Raccoglie ed esfiltra dati
- Modifica, corrompe o sovrascrive i dati

In questa fase di solito le attività del SOC sono prevalentemente di tipo [forense](<#Analisi forense>):
- Definire il playbook dell'attaccante
- Identificare i dati manipolati
- Effettuare l'analisi degli alert
- Effettuare un'[analisi forense](<#Analisi Forense>) completa dei dispositivi infetti
- Catturare lo scambio di pacchetti del computer e ricreare lo storico dell'attacco
- Effettuare un'analisi dei danni subiti

#### Analisi delle intrusioni

### Diamond Model
![[diamond_model.png]]
Il modello a diamante di analisi delle intrusioni è composto da 4 parti, utilizzate per rappresentare un incidente di sicurezza o un evento di sicurezza. L'evento rappresenta un'attività effettuata in un determinato arco di tempo, limitata a passaggi predefiniti, tramite i quali un **avversario** usa le proprie **capacità** su un'**infrastruttura** per attaccare una **vittima** e ottenere determinati risultati.
- **Avversario**: Entità responsabile dell'attacco
- **Capacità**: Strumenti, conoscenze e tecnologie adoperate per portare a segno l'attacco
- **Infrastruttura**: Infrastruttura utilizzata per stabilire e mantenere una connessione con la rete bersaglio dell'attacco
- **Vittima**: Bersaglio dell'attacco

#### Meta-feature
Altri elementi fondamentali per riassumere un attacco sono:
- **Timestamp**: periodo di inizio e fine di un evento
- **Fase**: Le fasi sono le stesse della[Cyber-Kill chain](<#Cyber Kill Chain>)
- **Risultato**: Identifica cosa sia stato ottenuto dall'avversario
- **Direzione**: Indica la direzione dell'evento nel modello a diamante
- **Metodologia**: Utilizzato per classificare il tipo di evento (es. port scan, phishing, consegna di contenuti, syn flood, ecc.)
- **Risorse**: Set di elementi esterni utilizzati dall'avversario per portare a segno l'attacco (es. conoscenza del bersaglio, software, informazioni come username e password, hardware utilizzati) 


## Incident Response
Insieme di metodologie, policy e procedure, utilizzate per rispondere ad un **incidente di sicurezza** (evento con un reale effetto pregiudizievole per al sicurezza della rete e dei sistemi informativi), avendo l'obiettivo di:
- Impedire ad eventuali intrusi di operare all'interno della rete
- Minimizzare i danni apportati dall'incidente
- Riportare la situazione in regime di sicurezza

Il NIST offre una [guida per la gestione degli incidenti](https://csrc.nist.gov/pubs/sp/800/61/r2/final) che fornisce linee guida (non dipendenti dall'infrastruttura hardware e software colpita dall'attacco) per:
- Analizzare dati correlati all'incidente
- Determinare l'approccio migliore per rispondere ad ogni incidente

### CSIRC
Il primo step della guida consiste nello stabilire le capacità di risposta di un computer a seguito di incidenti di sicurezza (CSIRC) e di creare un set di [Policy](#Policy), piani e procedure a supporto. 

#### Policy
Devono includere dettagli riguardo:
- Definizione dell'impegno di gestione
- Scopi e obbiettivi delle policy
- Definizione degli incidenti di sicurezza e relativa terminologia
- Struttura organizzativa e definizione di ruoli, responsabilità e livelli di autorità
- Definizione della priorità e della gravità degli incidenti di sicurezza
- Misurazione delle prestazioni
- Report e moduli di contatto

#### Pianificazione
Gli elementi di pianificazione devono coprire le seguenti aree:
- Missione
- Strategie e obbiettivi
- Approvazione da parte di un Senior Manager
- Approccio organizzativo della risposta ad un incidente
- Metodologie comunicative della squadra di Incidente Response con il resto dell'organizzazione
- Metriche di misurazione delle capacità di risposta agli incidenti
- Come il programma venga inquadrato all'interno dell'organizzazione

#### Procedure
Le procedure devono descrivere come comportarsi durante il processo di risposta ad un incidente e devono includere:
- Processi tecnici
- Tecniche da utilizzare
- Moduli da compilare
- Checklist da seguire

### Stakeholders
Gli attori interessati (stakeholders) durante la fase di incident response sono:
- **Management**: Definiscono le policy da seguire, stabiliscono l'ammontare di risorse da utilizzare (economiche e umane) e coordinano il resto della squadra
- **Information assurance**: Provvede a modificare le impostazioni dei dispositivi di rete (quando previsto) durante le varie fasi di risposta ad un incidente
- **IT Support**: Personale con più alto livello di conoscenza della rete. SI occupa di effettuare le azioni per minimizzare l'efficacia dell'attacco e preservare dati e/o prove
- **Legali**: Revisionano policy, piani e procedure per confermare la conformità alle disposizioni normative vigenti
- **Public affairs/Media relations**: Informano la popolazione (quando previsto) delle conseguenze di eventuali esfiltrazioni di dati
- **Risorse Umane**: Prendono contromisure disciplinari quando previsto
- **Business Continuity Planner**: Si occupano di minimizzare 'impatto di un attacco informatico sulla continuità dell'attività
- **Personale di sicurezza**: Si attivano nel caso di attacco fisico all'organizzazione

### Cybersecurity Maturity Model Certification
Framework utilizzato per valutare la capacità di un'organizzazione (che opera a contatto con il Dipartimento della Difesa degli US) di proteggere dai rallentamenti la catena delle forniture o da perdite. Si compone di 5 livelli , assegnati in base al livello di sicurezza richiesto all'organizzazione.
I criteri di valutazione sono categorizzati in base a 17 domini di interesse, ognuno dei quali fornisce un valore di maturità dell'infrastruttura in base a:
- Piano di risposta all'incidente
- Identificazione e report degli eventi
- Sviluppo e implementazione di una risposta ad un'incidente dichiarato
- Effettuazione di revisioni a seguito di un incidente
- Test di risposta ad un incidente

La somma dei valori fa ottenere un punteggio finale, che rientrerà in uno dei 5 livelli previsti:
1. Non descritto
2. Il piano di risposta all'incidente rispetta i criteri del [NIST](#NIST) per identificazione, report e prioritizzazione degli eventi e analizza correttamente l'incidente per mitigare problematiche future
3. Documenta e riporta gli incidenti agli stakeholders identificati nel piano. Testa le capacità di risposta all'incidente dell'organizzazione
4. Utilizza le tecnologie, tecnologie e metodi ([TTP](#TTP)) per affinare la pianificazione e l'esecuzione dei piani di risposta. Definizione di un Centro Operativo di Sicurezza (SOC) che agevola la capacità di risposta 24/7
5. Utilizza tecniche forensi di raccolta dati sistematica dei dati per maneggiare e memorizzare dati provenienti da attività forensi. Sviluppa ed utilizza procedure di risposta manuale ed automatica a potenziali incidenti che seguono pattern conosciuti.

## Analisi forense
Anche nota come Digital Forensics, consiste nell'analizzare attività sospette, identificare le cause degli attacchi, procurare prove certe riguardo l’identità e ripristinare il sistema ad uno stato sano.
L’identificazione di un’attaccante avviene attraverso l’analisi delle tracce lasciate dallo stesso, come log e pcaps.

A seguito di un attacco è importante raccogliere prove ed informazioni riguardo l’ambito dell’attacco. La tipologia è la quantità di informazioni da raccogliere è definita spesso anche da normative (es. HIPAA per gli USA). Per questo è molto importante stabilire delle procedure ferree per il processo di analisi forense all’interno di un’organizzazione.

### Metodologia
Il processo di analisi forense è composto da 4 step:
- **Raccolta dei dati**: si identificano le fonti di dati utili per l’analisi e se ne prelevano i dati. Per massimizzare i dati raccolti, conviene sempre iniziare dai dati volatili (es. quelli localizzati 
- all’interno delle RAM)
- **Esame**: i dati vengono processati per essere leggibili (es decodifica) e vengono scartate le informazioni inutili
- **Analisi**: L’analisi permette di trarre conclusioni riguardanti l’attacco e raccogliere ed organizzare le prove trovate 
- **Documentazione**: le informazioni vengono preparate per l’inserimento in un documento finale, che permetta di riassumere i risultati ottenuti e suggerire i passaggi successivi.

Un’esempio di ordine di raccolta dati è quello di prelevare quelli memorizzati all’interno di:
1. Cache e dischi di memoria
2. Tabelle di Routing, ARP cache, tabella dei processi, statistiche del kernel, RAM
3. File temporanei di sistema
4. Media non volatili, fissi o rimuovibili
5. Logging di attività da remoto e monitoraggio dei dati
6. Interconnessioni fisiche a topologie
7. Media archiviati, registrazioni e altre forme di backup

Deve essere registrato anche il supporto dal quale è stato prelevato il dato. Durante lo scambio dei dati per l’analisi, si deve registrare per ogni passaggio da un utente all’altro:
- Chi ha scoperto e raccolto la prova
- Tutti i dettagli relativi il passaggio dei dati (orari, luoghi e persone coinvolte)
- Personale che ha accesso ai dati registrati

Questo viene effettuato per assicurare l’identificazione di possibili eventi di sabotaggio dei dati. Questo processo prende il nome di **Catena della custodia** (chain of custody).

### Prove
Le prove sono suddivise in 3 categorie, in base al grado di certezza offerto:
- **Dirette**: prove trovate in diretto possesso dell’accusato 
- **Migliori**: es. archivi di file non alterati, dispositivi di memoria utilizzati durante l’attacco
- **Corroboranti**: supportano una tesi che deriva dalle prove migliori
- **Indirette**: note anche come prove circostanziali, permettono di fare ipotesi riguardo gli avvenimenti (es la presenza certa di altri crimini effettuati dell’attaccante accusato)

Durante il processo di analisi, è sempre una buona prassi lavorare su copie (e registrare le copie) dei dati per evitare perdite accidentali.

### Documentazione
La documentazione deve includere:
- Tattiche
- Tecniche 
- Procedure
Utilizzate per portare a segno l’attacco.
Il [MITRE](#MITRE) offre un framework per analizzare questi dati: l’[ATT&CK](#ATT&CK) (Adversial Tactics, Techniques and Common Knowledge)

# Normativa
## Italia
- AGID
- [Legge 81/2001](https://www.normattiva.it/uri-res/N2Ls?urn:nir:stato:legge:2001;81)
## EU
- GDPR
- DPCM 81/21
## Internazionale
- Electronic Privacy Information Center (EPIC): Centro di ricerca non-profit per la promozione della privacy e l'apertura delle leggi e delle policy
- Convention on Cybercrime: Primo trattato internazionale a tema cybersecurity

### ISO 27000
Predispone un framework universalmente valido per predisporre le priorità di un'organizzazione, seguendo i [principi di sicurezza](<#Principi di sicurezza>)

### ISO 27001
Stabilisce i requisiti di alto livello (obiettivi) dei sistemi di sicurezza informatica di un'organizzazione e da fornire nel caso di ISMS audit (il cui superamento fornisce la prova di credibilità della sicurezza dei sistemi dell'organizzazione stessa).

### ISO 27002
Definisce come raggiungere gli obiettivi trattati nella [[#ISO 27001]] sotto i punti di vista di:
- Implementazione
- Manutenzione
- Miglioramento

## US
- Statutory law: definizione di un codice morale condiviso
- Administrative law: le FCC e FTC si interrogano sui diritti d'autore digitali
- Common law: I casi giuridici forniscono dei precedenti e le basi costituzionali per la legislazione
- FISMA (Federal Information Security Management Act): I sistemi federali sono prede molto ambite per i cybercriminali, quindi la FISMA nel 2002 ha stabilito che le agenzie federali debbano ottemperare:
	- Risk assessment
	- Inventario annuale dei sistemi informatici
	- Policies e procedure per attenuare il rischio
	- Addestramento alla consapevolezza della sicurezza
	- Testare e valutare tutti i sistemi di controllo informatici
	- Procedure di Incident Response
	- Un piani di continuità delle operazioni
- **Privacy Act:** Governa il codice di condotta per il trattamento, la conservazione e la diffusione dei dati
- **Freedom of Information Act** (FOIA): Obbliga le pubbliche autorità a fornire buone motivazioni per negare il rilascio di informazioni confidenziali. Ci sono 9 eccezioni:
	- Sicurezza nazionale
	- Regolamenti aziendali
	- Informazioni specificatamente esenti
	- Informazioni commerciali confidenziali
	- Comunicazioni inter o intra-aziendali soggette a processo deliberativo
	- Imposizioni legali che, se rilasciate, possono implicare una serie di preoccupazioni
	- Informazioni aziendali da istituzioni finanziarie
	- Informazioni geografiche e geologiche riguardanti pozzi
- **Family Education Records and Privacy** Act (FERPA): Governa l'accesso governativo a dati degli studenti in ambito scolastico
- **Children's Online Privacy Protection Act** (COPPA): Protegge la privacy dei minorenni, e in particolare i minori con eta inferiore a 13 anni, imponendo requisiti agli operatori online
- **Children's Internet Protection Act** (CIPA): Protegge i minorenni (sotto i 17 anni) dall'esposizione ad atti offensivi online
- **Video Privacy Protection Act** (VPPA): A protezione di contenuti video. Emendato nel 2003
- **Health Insurance Portability and Accountability Act** (HIPAA): Creazione di legislazione a livello nazionale per conservazione, manutenzione, trasmissione e accesso a dati relativi la salute dei cittadini. Per assicurare l'integrità viene utilizzata la firma digitale con determinati standard
- **California Senate Bill **(SB 1386): Legifera riguardo il rilascio di informazioni a seguito di security breach. Obbliga l'azienda ad informare i clienti oggetto della perdita di dati
- **Privacy policies**: Permettono di applicare le norme
- **Privacy Impact Assessment** (PIA): Assicura che le **informazioni informatiche personali** (PII) siano gestite propriamente tramite il seguente processo:
	1. Definire l'ambito della PIA
	2. Identificare i principali interessati
	3. Documentare come l'organizzazione maneggerà le PII
	4. Rivedere i requisiti legali e regolamentatori
	5. Documentare ogni possibile problematica durante la comparazione tra i requisiti e la pratiche attuale al momento
	6. Rivedere gli aggiornamenti con i principali interessati
### Finanza
- Gramm-Leach-Bliley Act (GLBA): permette all'utente di controllare come le proprie informazioni vengano utilizzate dalle aziende

### Contabilità aziendale
- Sarbanes-Oxley Act (SOX): Legifera riguardo la contabilità delle aziende con capitale d'azioni (SPA)

### Carte di credito
- Payment Card Industry Data Security Standard (PCI DSS): Set di regole contrattuali aventi l'obiettino di proteggere i pagamenti digitali durante le transazioni e dalle frodi, ponendo sanzioni elevate agli operatori che non rispettino le direttive

### Crittografia
- Regole varie: ci sono dei limiti al commercio di prodotti inerenti la crittografia in quanto potrebbero agevolare organizzazioni terroristiche. Particolare attenzione  posta alla possibilità di:
	- Tecnologie con backdoor o altre vulnerabilità alla sicurezza
	- Cittadini che utilizzino tecnologie per comunicare tramite anonimato e passare inosservati alle forze dell'ordine
	- Il livello della privacy si innalzi oltre un livello di sicurezza

### Notifica delle falle di sicurezza
- Electronic Communications Privacy Act (ECPA): Si occupa di proteggere le comunicazioni private (email, messaggi, chiamate) da intercettazioni non autorizzate, accessi e pubblicazione di dati
- Computer Fraud and Abuse Act (CFAA): Proibisce l'accesso non autorizzato a sistemi informatici e il commercio di password rubate o altre informazioni sensibili


## Generali
Raccolta di documenti non vincolanti
### ISO/IEC 27001
Si occupa della sicurezza sotto un punto di vista olistico.
### ISO/IEC 27034
Si concentra sul lato #software
### NCWF
Framework di sicurezza informatica redatto dalla NIST (National Institute of Standard and Technologies), che riassume le principali funzioni della cybersecurity, ovvero:
- Operare e manutenere
- Proteggere e difendere
- Investigare
- Raccogliere e operare
- Analizzare
- Sorvegliare e gestire
- Fornire funzionalità in sicurezza

### CIS Security Controls
Il CIS (Centro per la Sicurezza di Internet) ha sviluppato un set di controlli di sicurezza ritenuti critici per supportare le organizzazioni ai diversi livelli di risorse e expertise. Questo tipo di controlli può essere accoppiato alla [benchmarks list](https://www.cisecurity.org/cis-benchmarks) redatta sempre dalla CIS.

#### Base
Controlli da includere indipendentemente dalla dimensione e dalle risorse di un'organizzazione:
- Inventario e controllo degli asset hardware
- Inventario e controllo degli asset software
- Gestione continua delle vulnerabilità
- Uso controllato dei privilegi di amministratore
- Configurazione sicura di hardware e software
- Manutenzione, monitoraggio e analisi dei log di audit

#### Fondamentali
Controlli da implementare nel caso ci siano abbastanza risorse. Le implementazioni aggiuntive sono:
- Protezioni delle mail e della navigazione web
- Antimalware
- Limitazione delle porte di rete e dei protocolli e servizi utilizzati allo stretto indispensabile
- Capacità di recupero dei dati
- Configurazioni sicure dei dispositivi di rete
- Limiti di difesa
- Protezione dei dati
- Controllo degli accessi basato sul principio "need-to-know" (necessità di sapere)
- Controllo degli accessi wireless
- Monitoraggio e controllo degli account

#### Organizzativi
I controlli organizzativi sono consigliabili per le organizzazioni che abbiano buone risorse economiche da utilizzare in ambito Cybersecurity. Gli ulteriori controlli aggiunti sono:
- Addestramento del personale alla consapevolezza sulla sicurezza
- Sicurezza dei livello Applicazione dei software
- Gestione e risposta agli incidenti
- Penetration test e esercizi di [red team]

### CCM
La matrice dei controlli (Cloud Control Matrix) in ambito cloud è un utile strumento sviluppato dalla Cloud Security Alliance (CSA) dispone 197 controlli base da applicare su infrastrutture cloud, suddivisi in 17 domini, che coprono tutti gli aspetti della sicurezza in ambiente cloud.

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