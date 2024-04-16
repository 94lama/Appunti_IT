# Introduzione
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
## Cloud Computing
La definizione di #cloud-computing è stabilita dal #NIST (National Institute of Standards and Technology) e comprende 5 caratteristiche essenziali, 3 modelli di servizio e 4 modelli di distribuzione. L'obiettivo è quello di fornire ed ottimizzare aspetti quali la velocitò d'accesso, integrità dei dati e sicurezza.

La Gartner nel 2017 (anno in cui il 75% delle aziende adottava un modello bivalente, improntato a garantire il mantenimento della qualità dei servizi e un'innovazione costante volta all'efficienza) aveva analizzato alcune tendenze e predetto la diffusione a livello globale del cloud. L'innovazione, in realtà, è stata velocizzata di molto dal covid.
Nel 2019 sono state identificate 7 tendenze nel mondo cloud:
- Hybrid e multi cloud
- Edge Computing: distribuzione e decentralizzazione del sistema informativo, con l'obiettivo di ottimizzare le opportunità fornite dai dati raccolti dagli oggetti connessi alla rete (esempio #IoT)
- Intelligent cloud: si trattano i dati presenti in cloud tramite #intelligenza-artificiale  e #machine-learning
- #PaaS e architetture Cloud Native: Utilizzo di #intelligenza-artificiale tramite modelli pre-istruiti all'interno del cloud per innovare prodotti e servizi al fine di sfruttare economie di scala nell'apprendimento sui dati
- Cloud culture e organization: trend relativo agli specialisti IT, corrispondente all'apparizione di nuove figure (Cloud Specialist e Cloud Architect), addette alla gestione degli ambienti in cloud
- Security e Cyberintelligence: adattamento al nuovo #GDPR
- Agile, DevOps e IT Automation
### Caratteristiche
- **On Demand Self Service**, ovvero la possibilità di richiedere i servizi (o la variazione degli stessi) in maniera autonoma, senza l'intermediazione di service provider o terzi 
- **Broad Network Access**, ovvero l'accessibilità virtuale (multi-dispositivo)
- **Resource Pooling**, ovvero il raggruppamento delle risorse IT (storage, processori, macchine virtuali ecc.), effettuato in maniera tale da poter servire dinamicamente un numero variabile di utenti, a seconda delle loro richieste
- **Rapid elasticity**, in modo tale da poter scalare (verso l'alto o verso il basso) velocemente le risorse
- **Measured services**, ovvero la possibilità di monitorare con precisione le risorse utilizzate, per poter applicare il modello pay-per-use
### Modelli di servizio
Ci sono 3 tipi di modelli di business per gli applicativi: Saas, PaaS e IaaS
![[Pasted image 20240415140801.png]]
#### SaaS
Il modello #SaaS (Software as a Service), consiste nel fornire al cliente un software pronto all'uso (es. Adobe package, **Office 365**, G-suite) comprensivo di programmi manutentivi e aggiornamenti. La tipologia è nata a seguito della migrazione lato cloud dei vari servizi. E' composto da:
- software (disponibile in remoto o in locale)
- ambiente di storage per i dati
- sistema di abbonamento per poter fruire del servizio
#### PaaS
Il #PaaS, ovvero Platform as a service, consiste nel mettere a disposizione dell'utente la piattaforma da utilizzare per sviluppare, testare e distribuire i servizi. . Un esempio è Google Cloud Platform
#### IaaS
Nel #PaaS, o Platform as a Service, il servizio messo a disposizione è l'infrastruttura, ovvero uno #storage, un #server, un sistema di #networking e un sistema di visualizzazione. Esempi di #IaaS sono [[Azure]], [[AWS]] e [[Google Cloud]].
Tutti i servizi #IaaS sono accessibili unicamente tramite riga di comando.
#### Sottomodelli
- DaaS
- HaaS
- IaC: Infrastructure as a code
### Modelli di distribuzione
#### Private cloud
Servizio di cloud computing erogato da un'azienda (o da un provider esterno) che asservisce unicamente l'azienda stessa.
#### Community cloud
Può essere erogato da un'azienda o da un service provider, che permette l'accesso ad un gruppo ristretto di organizzazioni che condividono alcune caratteristiche, come livelli di sicurezza, norme legali, ecc. Il sistema può essere gestito da una delle aziende del gruppo, o da un provider esterno.
#### Public cloud
Servizio di cloud computing
#### Hybrid cloud
Versione ibrida tra [[#Public cloud]] e [[#Private cloud]], utilizzata per ovviare a particolari esigenze di sicurezza e/o ottimizzazione delle strutture a disposizione dell'azienda.

## Clienti
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
# Storage
In un ambiente aziendale totalmente orientato verso servizi cloud, è possibile rimuovere l'hard disk nelle varie macchine, utilizzando il #server cloud come memoria centralizzata, sia per i file da salvare, che per i software installati (che possono essere richiesti tramite accesso ad un catalogo) e gestendo una politica di #backup dei dati (di solito più volte al giorno) tramite crittografia con chiave digitale.
# [[Cybersecurity]]
Il testo che regolamenta la sicurezza dei Cloud Server è il GDPR.
