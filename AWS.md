# Introduzione
Servizio di #coud-server
# Creazione di un nuovo server
- free tier eligible: permette di avere un periodo di uso gratuito
## Instance type
Ubuntu
## Key pair (login)
Inserire una chiave di protezione (consigliata protezione ED25519)
## Network settings
### Firewall
Permette di impostare le #porte aperte e le chiavi
- 0.0.0.0 indica una porta aperta a tutti
## Storage
AWS ha un programma di pagamento basato sullo spazio utilizzato per tempo utilizzato (calcolato in ore). I primi 30GB sono gratuiti per i primi 12 mesi
# Server
Di norma si utilizzano più server per progetto. Su AWS i server devono essere localizzati nella stessa regione 
- Pipeline (collega il server aperto al pubblico alla piattaforma di versionamento)
- Deploy (server pubblico)
# Installazione di [[Docker]]
prendere script da sito di docker in base al sistema operativo che si è installato nel server
Durante l'installazione, nel caso si utlilizzi una memoria di piccole dimensioni, il server potrebbe andare in stato di #anger (sovraccarico). Per evitare ciò si utilizza lo #swap, ovvero una partizione (o file), situato nell'hard disk, che lavora come estensione della RAM.
## Installazione di [[Jenkins]]
Installo Jenkins (vedi file di Jenkins)
## Installazione di un database
## PostGres
Si può installare da container Docker
# Utilizzo
## Ridurre lo spazio utilizzato
Per ridurre lo spazio utilizzato, si deve creare un nuovo volume da uno #snapshot
# Attenzione
- Nel caso si voglia aprire una nuova porta dal server, la si deve anche segnalare nella piattaforma di AWS