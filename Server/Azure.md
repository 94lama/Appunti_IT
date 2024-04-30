[Documentazione](https://learn.microsoft.com/it-it/azure/?product=popular)
# Introduzione
Servizio offerto da #Microsoft, che offre servizi #SaaS, #IaaS e #PaaS. Tramite l'utilizzo si #windows-server e #system-center, permette di ottenere un sistema di #cloud-ibrido.
# Bastion
#bastion è il gestore delle connessioni di Azure (incluse le Virtual Machines, tramite protocollo [SSH](<Protocolli di comunicazione#SSH>) o [RDP](<Protocolli di comunicazione#RDP>)).

# Macchina virtuale
## [Creare una macchina virtuale](https://learn.microsoft.com/it-it/azure/virtual-network/quick-create-portal)

# [IAM](https://learn.microsoft.com/it-it/azure/active-directory/fundamentals/introduction-identity-access-management)
La #IAM, o Identity Access Management è un servizio web che aiuta a controllare in modo sicuro l'accesso alle risorse di Azure tramite l'assegnazione di ruoli. L'utilizzo di autenticazione a 2 fattori ( #2FA) con sistema proprietario permette di evitare problemi di clonazione delle #sessione. 
L'accesso avviene tramite #token di accesso, che riassume le credenziali di accesso e le autorizzazioni (mentre [[AWS]] separa questa procedura in 2 momenti).
## Termini
- user
- gruppo
- ruolo
- #policy
- oggetto identity-provider
## Federazione
Servizio che consente l'accesso temporaneo alle risorse tramite password già utilizzate altrove (es. password aziendali).
### Outside organization
Sono tutti gli utenti che non possiedono un account AWS, ma possono comunque accedere a determinate risorse del cloud (es. tramite specifici user e password). Non fanno parte dell'organizzazione principale e devono essere sempre segnati.
## Ruoli
### [Tenant](https://learn.microsoft.com/it-it/entra/fundamentals/introduction-identity-access-management)
Rappresenta un'azienda. Viene trattato come "raggruppamento" di utenti, regole ecc..
#### [Configurazione di un tenant](https://learn.microsoft.com/it-it/entra/external-id/customers/quickstart-tenant-setup)

### Utente
#### Gruppi
Il funzionamento dei gruppi è simile a quello di [[Linux]].
### Amministratore del servizio
### Amministratore IAM
Gestore delle #policy di accesso tramite #IAM. Queste possono essere preconfigurate, o impostate tramite file (di solito #JSON) 
## [Tipologie di accesso](https://docs.aws.amazon.com/it_it/IAM/latest/UserGuide/introduction_identity-management.html#AccessControlMethods)
### MFA
E' possibile implementare un meccanismo di Autenticazione a Multi-Fattore ( #mfa) tramite #IAM.
### SSO
Il Single Sign-ON ( #SSO) è una tipologia di accesso che permette di richiedere una minore quantità di dati durante il login di un utente, qualora si stia effettuando il secondo (o più) accesso al sistema.
## ABAC
Attribute-Based Access Control ( #ABAC) è un meccanismo di gestione delle autorizzazioni tramite utilizzo di Attributi ( #tag)
