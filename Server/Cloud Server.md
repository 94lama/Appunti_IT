# Introduzione
La tecnologia *cloud* è stata ideata per astrarre l'infrastruttura, ovvero spostare l'attenzione dall'infrastruttura stessa alle informazioni. 
Un cloud server è una rete diffusa a livello globale di #server, localizzati spesso in apposite strutture chiamate #data-center, che permettono di avere un accesso costante ai dati contenuti al suo interno. Nel caso di data center momentaneamente non disponibile, è possibile migrare i dati in un altro data center, grazie a costanti #backup effettuati tra #server limitrofi.
Le caratteristiche principali di un servizio in cloud sono:
- Disponibilità di accesso al servizio 24/7
- Accesso multi-dispositivo.
I principali #provider (Hosting Service Provider) di servizi cloud server sono [[AWS]], [[Azure]] e [[Google Cloud]].
Gli altri attori coinvolti nell'utilizzo di un cloud service sono:
- Cliente amministratore (Cloud Broker), ovvero l'amministratore dei servizi cloud sotto l'aspetto dell'utilizzo (es. server completo o solo #storage) e dell'intermediazione tra #provider e cliente finale;
- Cliente finale (Cloud Consumer).
## Benefici
- Stoccaggio efficiente dei dati
- Risparmio economico
- Utilizzo appropriato delle risorse
- Alta affidabilità dei servizi
- Gestione e manutenzione dell'hardware gestita dal provider
- Adattabilità delle risorse in base alla quantità e qualità necessaria al momento d'uso
- Alta scalabilità
# Cloud Computing
La definizione di #cloud-computing è stabilita dal #NIST (National Institute of Standards and Technology) e comprende 5 caratteristiche essenziali, 3 modelli di servizio e 4 modelli di distribuzione. L'obiettivo è quello di fornire ed ottimizzare aspetti quali la velocitò d'accesso, integrità dei dati e sicurezza.
## Storia
La Gartner nel 2017 (anno in cui il 75% delle aziende adottava un modello bivalente, improntato a garantire il mantenimento della qualità dei servizi e un'innovazione costante volta all'efficienza) aveva analizzato alcune tendenze e predetto la diffusione a livello globale del cloud. L'innovazione, in realtà, è stata velocizzata di molto dal covid.
Nel 2019 sono state identificate 7 tendenze nel mondo cloud:
- Hybrid e multi cloud
- Edge Computing: distribuzione e decentralizzazione del sistema informativo, con l'obiettivo di ottimizzare le opportunità fornite dai dati raccolti dagli oggetti connessi alla rete (esempio #IoT)
- Intelligent cloud: si trattano i dati presenti in cloud tramite #intelligenza-artificiale  e #machine-learning
- #PaaS e architetture Cloud Native: Utilizzo di #intelligenza-artificiale tramite modelli pre-istruiti all'interno del cloud per innovare prodotti e servizi al fine di sfruttare economie di scala nell'apprendimento sui dati
- Cloud culture e organization: trend relativo agli specialisti IT, corrispondente all'apparizione di nuove figure (Cloud Specialist e Cloud Architect), addette alla gestione degli ambienti in cloud
- Security e Cyberintelligence: adattamento al nuovo #GDPR
- Agile, DevOps e IT Automation
## Caratteristiche
### On Demand Self Service
Possibilità di richiedere i servizi (o la variazione degli stessi) in maniera autonoma, senza l'intermediazione dell'Internet Service #provider o comunque di terzi.
Sia in caso di Virtual Machine, che di Virtual Private Datacenter, è fondamentale che siano utilizzabili e modificabili tutte e 3 le principali risorse di una macchina, ovvero **storage**, **RAM** e **CPU**, sia per adattarsi alle esigenze dello specifico utente, che per disattivarsi automaticamente quando non utilizzate. 
### Broad Network Access
- Accessibilità virtuale (multi-dispositivo, quali mobile, pc, server)
- disponibile 24/7
- indipendentemente dal luogo da cui ci si connette
- con possibilità di scambiare grandi moli di dati
### Resource Pooling
Raggruppamento delle risorse IT (storage, processori, macchine virtuali ecc.), effettuato in maniera tale da poter servire dinamicamente un numero variabile di utenti, a seconda delle loro richieste #TODO Rivedere slides 53-54
Alcune pratiche che si possono utilizzare sono:
- condivisione delle risorse a più utenti
- possibilità di abbassare le risorse (o interromperle) nel caso di inattività ad uno specifico utente al fine di bilanciare la banda
-  #multi-tenancy, ovvero condivisione di partizione virtuale, utilizzabile da più utenti
- #multi-istanza (contrapposto alla multi-tenancy), ovvero la messa a disposizione di più risorse, suddivise tra i vari utenti
### Rapid elasticity
Possibilità di scalare (verso l'alto o verso il basso) velocemente le risorse
### Measured services
Possibilità di monitorare con precisione dati come:
- le risorse utilizzate
- le risorse inutilizzate
- elaborazione
- larghezza di banda
- account attivi
Indispensabile al fine di poter applicare il modello #pay-per-use.
### Vantaggi
- **Agilità e flessibilità**: E' più facile rendere l'azienda scalabile rispetto ai cambiamenti del mercato;
- **Riduzione del time-to-market**: La riduzione dei costi di gestione delle infrastrutture aumenta la competitività dell'azienda
- **Riduzione dei costi**
- **Sicurezza e affidabilità**
## Modelli di servizio
Ci sono 3 tipi di modelli di business per gli applicativi: Saas, PaaS e IaaS
![[Pasted image 20240415140801.png]]
### SaaS
Il modello #SaaS (Software as a Service), consiste nel fornire al cliente un prodotto pronto all'uso (es. Adobe package, **Office 365**, G-suite, SalesForce, Amazon Web Services, iCloud) comprensivo di programmi manutentivi e aggiornamenti. La tipologia è nata a seguito della migrazione lato cloud dei vari servizi. E' composto da:
- software (disponibile in remoto o in locale)
- ambiente di storage per i dati
- sistema di abbonamento per poter fruire del servizio
Ci sono due categorie di servizio SaaS:
- Linea di servizi alle Imprese: soluzioni di business offerte alle imprese
- Orientato al Cliente: 
#### Caratteristiche
- Eventuali fatturazioni sono emesse in archi temporali predefiniti (mensili, annuali, ecc.),
- Spesso le applicazioni sono eseguite online
- Fornitura e manutenzione sono a carico del #provider 
- Accessibile da qualsiasi dispositivi con connessione ad [[Internet]] tramite dati d'accesso
- I dati dell'azienda cliente possono essere trovati sul server del fornitore di servizi**non sempre accettabile per ragioni di privacy**
- E' indispensabile imporre misure di sicurezza che proibiscano al fornitore di servizi di accedere ai dati in caso di separazione delle due parti
- Utilizzo del servizio tramite API
#### Rischi
- Software incompleto: Può capitare che un software SaaS, a causa di controlli meno rigorosi, venga rilasciato senza i beta test necessari
### PaaS
Il #PaaS, ovvero Platform as a service, consiste nel mettere a disposizione dell'utente la piattaforma da utilizzare per sviluppare, testare e distribuire i applicazioni software. Un esempio è Google Cloud Platform (che include Google App Engine) e Microsoft Azure.
Il cliente in questo caso non ha controllo dell'infrastruttura, ma solo delle applicazioni distribuite ed eventualmente della configurazione dell'ambiente-hosting delle applicazioni. In generale gli ambienti PaaS sono composte essenzialmente da un'infrastruttura di base (OS, server, archiviazione) e dei #middleware di connessione dell'infrastruttura stessa.
A ciò si aggiungono risorse di sviluppo (linguaggi di programmazione, database e container).
#### aPaaS
Application Platform as a Service, 
#### iPaaS
Integration Platform as a Service, ovvero un PaaS che punta ad ottimizzare l'integrazione dei servizi cloud (esempio AnyPoint) e rendere superflui i #middleware
### IaaS
Nel #PaaS, o Platform as a Service, il servizio messo a disposizione è l'infrastruttura, ovvero uno #storage, un #server, un sistema di #networking e un sistema di visualizzazione. Esempi di #IaaS sono [[Azure]], [[AWS]] e [[Google Cloud]].
Tutti i servizi #IaaS sono accessibili unicamente tramite riga di comando.
### Sottomodelli
Sono modelli non standardizzati dal #NIST, ma comunque utilizzati (a volte) per categorizzare le tipologie di servizi
#### DaaS
Data as a Service ( #DaaS), ovvero un modello che offre dati. E' una sottocategoria del #IaaS, specializzata nella trasmissione dei dati.
![](https://lh7-us.googleusercontent.com/slidesz/AGV_vUd47uLlgO7kYS1-5oC-s6gdZSaLzLLINpiBijSedukre1m3HFjqTu23iVzVj9zO49CG-_OzYOhsNiHdG3acdcSa7Eeh5k-ErskruY34xO-o7jJ7bnGQfO2MFF8Kc4AaKwpUCOwKydeHf-pkdIQYjkZaZj06eOarlT3bpa_LVsfbxg=s2048?key=RHfRp77HVKkYRhqghLXE6Q)
Un esempio di applicazione del DaaS è un software per trasportare dei dati dallo #storage all'ambiente di elaborazione (es. #machine-learning) al cliente (es. meccanismo che collega la visualizzazione di foto di Google Maps con StreetView)
##### STaaS
Lo #STaaS, ovvero Storage as a Service, 
#### HaaS
#HaaS, o Hardware as a Service, è la messa a disposizione dei soli componenti #hardware al cliente (ad esempio utilizzato per il mining).
### Servizi
#### IaC
#IaC: Infrastructure as a Code. Alcuni esempi sono: [[Terraform]]
## Modelli di distribuzione
Nel caso si debba decidere quale modello utilizzare, è necessario effettuare un'analisi preliminare che tenga conto delle attrezzature esistenti già in possesso dell'azienda, del budget a disposizione, del tipo di dati che verranno trattati, da eventuali vendor con cui iniziare un rapporto, ecc.
### Private cloud
Servizio di cloud computing erogato da un'azienda (o da un provider esterno) che asservisce unicamente un'azienda (di solito la stessa che eroga il servizio). Il mantenimento dei dati all'interno dell'azienda stessa, permette di aumentare la **privacy** e la **sicurezza** del sistema rispetto ad un ambiente pubblico.
La proprietà e la gestione **possono** essere effettuati dall'azienda stessa, o da enti terzi.
#### Gestione
- OpenStack
- VMWare
- Microsoft System Center
- Altri prodotti per unificare e gestire le risorse
- Può esistere in seno all'organizzazione o fuori sede (inteso come dislocazione e/o gestione separata per le varie sedi)
- Presenza di un'interfaccia self-service per la gestione e il monitoraggio dei servizi
- Automatizzazione della gestione di tutte le risorse
- Governance e sicurezza personalizzate in base ai requisiti specifici dell'azienda
#### Vantaggi
- Sicurezza
- Privacy
- Governance
- Minimizzazione delle risorse inutilizzate
- Facilità di previsione del carico massimo di utenti
### Public cloud
Servizio di cloud computing fruibile dal pubblico. Di solito è offerto secondo il modello #pay-per-use che garantisce elevate prestazioni, scalabilità e assenza di costi di manutenzione, al costo di un minore controllo dell'infrastruttura sotto il punto di vista delle policy di sicurezza.
#### Caratteristiche
- Il #provider deve garantire il rispetto dei requisiti di sicurezza del [[#Data center]] e deve esistere nei locali del #provider del cloud
- App di business innovative, per applicazioni che vanno da #crm (Customer Relationship Management)
- Nel caso di recessione dell'accordo tra cliente e #provider da parte del secondo, il #provider deve permettere alla controparte di poter migrare tutti i dati entro un determinato periodo di tempo (di solito 2 mesi)
### Hybrid cloud
Versione ibrida tra [[#Public cloud]] e [[#Private cloud]], utilizzata per ovviare a particolari esigenze di sicurezza e/o ottimizzazione delle strutture a disposizione dell'azienda. Rappresenta una via di mezzo tra il [[#Public cloud]] e [[#Private cloud]] anche se, quando si crea un servizio ibrido, è possibile che ci sia una mancanza di consistenza operativa
#### Annotazioni
- E' necessario garantire l'interoperabilità dei propri server nel cloud ( #cluster)
- La sicurezza rappresenta uno dei nodi critici
- Si può utilizzare durante il periodo di migrazione da server privato a cloud pubblico per ottimizzare le risorse (o qualora l'azienda non voglia più effettuare investimenti per la gestione di progetti di breve durata)
#### Caratteristiche
- Può essere di proprietà
- Esiste nei locali del #provider del cloud (sia esso #provider pubblico, o azienda che offre il servizio)
- Gestito da un business, un'università, organizzazione, azienda o combinazione di essi
### Community cloud
Può essere erogato da un'azienda o da un service provider, che permette l'accesso ad un gruppo ristretto di organizzazioni che condividono alcune caratteristiche, come livelli di sicurezza, norme legali, ecc. Il sistema può essere gestito da una delle aziende del gruppo, o da un provider esterno.
Questa tipologia di cloud è stata una diretta evoluzione del modello [[#Hybrid cloud]], al fine di collegare in maniera efficace le istanza private con quelle pubbliche sia in termini di affidabilità, che di sicurezza.
Può essere identificato sia come branca del [[#Public cloud]], in quanto accessibile dal pubblico (sebbene ristretto alla community), che [[#Private cloud]] in quanto rispetta le caratteristiche di sicurezza e privacy.
Sotto termini pratici, la definizione di Community Cloud dipende dal significato che si attribuisce al termine Community. Di solito come Community si intende un raggruppamento di aziende e/o enti.
#### Esempi di utilizzo
- Testing di prodotti di alto profilo.
- Condivisione di ambiente sicure per Organizzazioni governative diffuse nel territorio

# Clienti
A parte il cliente singolo, nel caso di cliente rappresentato da un'azienda, è possibile categorizzarle in base alla dimensione. In base alla categoria di cliente, a volte è preferibile utilizzare determinate tecnologie piuttosto che altre.
![[Pasted image 20240415163500.png]]
### Startup
Sono piccole aziende con ridotte capacità economica. Per ottimizzare i costi, spesso si preferisce utilizzare strumenti #SaaS, in quanto permettono di avere un prodotto da utilizzare immediatamente ad un prezzo non troppo elevato (si risparmiano soldi rispetto alla creazione di un sistema personalizzato #IaaS o #PaaS)
### Software house
Sono imprese che agevolano l'implementazione dell'informatica all'interno di aziende, tramite la creazione di software, app, infrastrutture ecc. personalizzate.
Di solito utilizzano servizi #PaaS per creare velocemente servizi scalabili, sempre connessi, integrati con i servizi più diffusi e con la possibilità di offrire servizi di alta qualità.
### PMI
Azienda già consolidata che, a volte, possiede già una struttura IT privata e dalle maggiori possibilità economiche. Di solito utilizzano strutture #IaaS privato o ibrido
### Grande azienda
Possiede spesso #data-center, creata durante un processo di crescita disorganica, avvenuta utilizzando, ad esempio, diversi sistemi operativi o linguaggi. Spesso gestiscono i dati in maniera totalmente privata, spostando quindi l'attenzione verso la #sicurezza dell'infrastruttura, la possibilità di accesso mobile e sempre disponibile, la collaborazione.
# Gestione
Il data center alloca una parte di risorse all'utente e ne monitora l'utilizzo per emettere fatture relative unicamente alla porzione di risorse utilizzate e al tempo di utilizzo (pay-per-use).
Le due metodologie di utilizzo di #cloud-server sono:
- #scale-up, ovvero impostare l'allocazione minima di risorse per poi aumentare progressivamente
- #scale-down, ovvero l'utilizzo sovrabbondante di risorse, per poi rimuovere la porzioni inutilizzata.
Ognuna di queste metodologie ha i suoi punti positivi e negativi. In generale, grazie al bilanciamento del carico reattivo, non ci sono sostanziali differenze riguardo la gestione dei server dal punto di vista di installazione delle dipendenze, ecc.
## Costi
I costi di manutenzione sono sempre a carico del #provider.
## IAM
L' #IAM (Identity Access Management), è una particolare tipologia di utenti, a cui viene assegnata in maniera predefinita una particolare tipologia di permessi. 
# Cloud Storage
In un ambiente aziendale totalmente orientato verso servizi cloud, è possibile rimuovere l'hard disk nelle varie macchine, utilizzando il #server cloud come memoria centralizzata, sia per i file da salvare, che per i software installati (che possono essere richiesti tramite accesso ad un catalogo) e gestendo una politica di #backup dei dati (di solito più volte al giorno) tramite crittografia con chiave digitale.
Si parla di Cloud Storage nel caso in cui lo "spazio disco" utilizzato è separato dallo #storage primario.

Anche il cloud #storage può essere classificato in base ai [[#Modelli di distribuzione]] e può essere [[#Public cloud]], [[#Private cloud]] o [[#Hybrid cloud]] e ha la possibilità di gestire la dimensione (di solito variando il piano tariffario). La differenza in questo caso è vincolata alla localizzazione dei server e alla platea di utenti a cui è consentito l'accesso ai dati.
Di solito è accessibile a seguito di un processo di #login.
## Archiviazione
### Formati di archiviazione
#### File storage
Un #file-level-storage deve rispettare due punti essenziali:
- Tutti i dati vengono conservati sotto forma di **file** completi 
- I file vengono conservati in una struttura gerarchica e vengono richiamati tramite percorso ( #tree-folder)
#### Block Storage
E' un modello flessibile e logicamente strutturato, in cui i dati sono divisi in blocchi di dati uguali dimensioni, ognuno dotato di un proprio indirizzo. Gli indirizzi delle celle fisiche vengono astratti, rendendo irrilevante l'effettiva localizzazione delle celle. Questo li rende particolarmente appetibili a contenere #database e in generale applicazioni che lavorano con dati strutturati.
Un esempio di archiviazione in Block Storage è lo storage del CERN di Ginevra, gestito dalla Huawei.
#### Object Storage
Formato di archiviazione che memorizza i file come oggetti (inclusi i metadati) e li dota di un numero di identificazione univoco, che può essere utilizzato per la sua amministrazione. La **modifica** del file avviene tramite creazione di una copia contenente le modifiche apportate. Questo rende questo tipo di archiviazione ottimo per la creazione di #backup, o comunque archivi destinati alla sola lettura di file.
Un esempio di Object Storage è quello utilizzato da Swisscom realizzata da Ctera, ovvero un sistema di storage dotato di sistema di #backup esterno, stoccaggio di file multipiattaforma e possibilità di effettuare #snapshot.

### Hardware
#### HDD
Gli Hard Disk Drive o #hdd, sono elementi destinati all'immagazzinamento di dati, che permettono scrittura, lettura, modifica e cancellazione degli stessi ( #CRUD). Sono caratterizzati da un costo basso e da una minore velocità di lettura rispetto agli #ssd
#### SSD
I Solid State Drive, o #ssd, sono strumenti di immagazzinamento dati più recenti rispetto agli #hdd, caratterizzati da maggiori costi, minore spazio a disposizione e una maggiore velocità di lettura.
### CDMI
Il #CDMI, ovvero Cloud Development Management Interface, è una tecnologia che ha permesso di stabilire il #STaaS
### Architettura
Il cloud storage possiede tutte le caratteristiche principali del #cloud-computing
- La metodologia d'accesso è definita dal #provider. Di norma avviene tramite protocolli #FTP (File-Transfer Protocol) o #http 
Le modalità di fruizione sono 3: #TODO 29
#### Application Cloud
Es. Dropbox, La struttura dello #storage è nascosta all'utente.
#### Computer Cloud
Il servizio consiste in un server virtuale, la cui struttura è nascosta all'utente.
#### Network Storage Cloud
L'utente è visto come utente locale e l'ambiente viene rappresentato come  fosse una #directory a tutti gli effetti.

# [[Cybersecurity]]

## GDPR
Il testo che regolamenta la sicurezza dei Cloud Server è il GDPR (General Data Protection Regulation, 2016/679). In linea generale si devono garantire due tipologie di requisiti: fisici e tecnologici. Il testo, adottato nel 2016, inizialmente riguardava unicamente i dati posseduti in territorio comunitario. Successivamente, venne modificato per includere anche tutti quei provider che trattino dati relativi ai cittadini comunitari
## Data center
Un #data-center deve rispettare determinati requisiti di privacy, in base alla localizzazione fisica dello stesso. In generale, il provider si assume la responsabilità riguardo aspetti come:
- Preservare la riservatezza
- integrità e la disponibilità dei dati
Al contempo, parte della responsabilità ricade anche sull'utente, in particolare riguardo:
- #TODO slide 11

### Sicurezza Fisica (passiva)
Si deve puntare a minimizzare i rischi, che possono essere dovuti a:
- furti
- accessi non autorizzati
- possibilità  di recuperare rapidamente dati a seguito di problemi

Alcune
- Monitoraggio dell'accesso tramite riprese video
- Controllo dell'accesso tramite identificazione e limite di tempo di accesso
- Smaltimento sicuro dei dischi in caso di guasto o sostituzione
- Porte di accesso blindate
- Misure di protezione da eventuali danni (es. interruzione improvvisa di corrente)
- Continuo aggiornamento in ambito di sicurezza dei dipendenti
### Sicurezza Logica (attiva)
- Accesso protetto ai dati sensibili per gli utenti con accesso #intranet
- Rispetto della normativa relativa al trattamento dei dati
- Tracciamento tramite file di #log delle operazioni effettuate
- Crittazione dei dati #at-rest e #in-transit
- Pseudonomizzazione
- Garantire che tutti i dati siano soggetti a backup frequenti (sia lato #provider che cliente)
### Stato dei dati
I dati possono essere classificati in base al loro stato:
- #at-rest: dato salvato sul server, ma non attualmente utilizzato
- #in-transit: dato in stato di movimento (sia #intranet che #internet, che tra dispositivi direttamente collegati tra loro)
- #in-use: dato attualmente utilizzato da un operatore, un cliente o un'applicazione (salvato nella RAM della macchina. In caso di streaming, il dato in-use è l'applicazione, non il file di per se)
#### #at-rest 
Nonostante non siano utilizzati nel momento preso in considerazione, è sempre consigliato proteggerli tramite #crittografia, per evitare il caso in cui il dato venga visualizzato o prelevato da utenti malevoli. Per questo motivo, conviene crittografare anche i dispositivi che contengono i dati stessi, specialmente nel caso non siano salvati nello storage (es. smartphone, chiavetta USB).
- Sicurezza fisica
	- Utilizzo di programmi di criptazione (es. VeraCrypt)
- Sicurezza logica
	- Utilizzo di funzionalità di auto-encryption dei principali #DBMS open-source
	- Utilizzo di protocolli S/MIME o PGP per l'archivio #email
#### #in-use 
Le vulnerabilità più comuni per questo tipo di dati sono lo #spectre ed il #meltdown
#### #in-transit
I dati in transito possono essere intercettati da un utente terzo. Gli attacchi più comuni sono:
- #man-in-the-middle  - interposizione dell'attaccante tra cliente e #server 
- #eavesdropping - cattura di singoli pacchetti di trasmissione
E' quindi necessario utilizzare metodi di protezione dei dati, come:
- Utilizzo di protocolli sicuri (es. #https)
- Uso di protocolli di trasmissione sicura certificati da una delle Certification Authorities (CA) ( #SSL, #TLS)
- Uso di data encryption #end-to-end
## Cloud Storage
Si deve garantire:
- Continuità dei servizi
- Privacy e sicurezza dei dati
- Reperibilità dei dati, anche in caso di guasto del server
Quindi, è necessario che sussistano determinate caratteristiche, ovvero:
- Sistemi anti-intrusione efficienti
- Meccanismi di #backup e #mirroring robusti ed implementabili tramite soluzioni [#RAID](https://it.wikipedia.org/wiki/RAID) (Redundant Array of Indipendent Disks)
- Utilizzo di meccanismi (implementabili tramite utilizzo di software commerciali o open source, tipo DFS o Robocopy), che permetta di recuperare i file anche in caso di rottura del server, manomissione o [failover](https://it.wikipedia.org/wiki/Failover) del servizio per attività di manutenzione o prevenzione/gestione di attacchi.


## Firewall
Un #firewall è un meccanismo di difesa basato sul diniego di accesso a determinate connessioni. Può essere definito sia tramite #whitelist, che #blacklist e può colpire sia protocolli, che indirizzi #IP.
Le #policy sono relative prevalentemente alla protezione dell'infrastruttura e alle pratiche di #disaster-recovery.
### IDS
Denial System, o #IDS è un meccanismo di difesa, che si attua prima del #firewall. Il suo scopo è analizzare i pacchetti in arrivo e, in caso di pacchetti sospetti o proibiti, menda una notifica #ping al moderatore (che può essere sia umano, che automatizzato). La risposta può essere un blocco automatico del pacchetto, oppure una sospensione dello stesso 
### IPS
Prevent System, o #IPS è un meccanismo di difesa, che si attua prima del #firewall, dopo l'attuazione dell'[[#IDS]].
## Valutazione dei rischi
