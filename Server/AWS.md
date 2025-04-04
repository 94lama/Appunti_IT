[Documentazione](https://docs.aws.amazon.com/)
# Introduzione
Servizio di [[Cloud]] gestito da Amazon, prodotto leader nel campo #IaaS.
# Server
Di norma si utilizzano più server per progetto. Su AWS è consigliabile utilizzare i server  localizzati nella stessa regione di utilizzo. I prezzi variano in base alla localizzazione scelta. Di solito per prove, conviene utilizzare il data server ue-east-1 (per motivi legati ai costi e alla documentazione).
- Pipeline (collega il server aperto al pubblico alla piattaforma di versionamento)
- Deploy (server pubblico)
## Creazione di un nuovo server
- free tier eligible: permette di avere un periodo di uso gratuito
### Instance type
Ubuntu
### Key pair (login)
Inserire una chiave di protezione (consigliata protezione ED25519)
### Network settings
#### Firewall
Permette di impostare le #porte aperte e le chiavi
- 0.0.0.0 indica una porta aperta a tutti
### Storage
AWS ha un programma di pagamento basato sullo spazio utilizzato per tempo utilizzato (calcolato in ore). I primi 30GB sono gratuiti per i primi 12 mesi
## Collegamento al server da terminale
```sh
ssh ubuntu@<indirizzo_ip_server> -i <user_ssh>
```

# VPC
L'Amazon Virtual Private Cloud è una rete privata ed isolata all'interno del Cloud AWS, che richiede un range di indirizzi [IPv4](Protocolli di comunicazione#IPv4) o [IPv6](Protocolli%20di%20comunicazione.md#IPv6 di comunicazione#IPv6>) e permette di scegliere un range #cidr in base alle necessità.
E' possibile scegliere in quale datacenter utilizzare in base all'***Availability Zone***, ovvero l'insieme di server AWS utilizzabili dall'utente, in base alla posizione geografica dello stesso.
## Tipologie di VPC
- Hardware VON
- Direct Connect
- VPN CloudHub
- Software VPN
## Subnet
### Private subnet
Sottorete accessibile solo all'interno della VPC. Esempi sono:
- Data Store
- Batch processing
- Server Back-end
### Public subnet
Sottorete accessibile anche dall'esterno della VPC. Esempi sono:
- Applicazione Web
## UI
### IP Address
### Elastic Network Interfaces
### Route tables
### Network Address Translation
### DHCP
Dynamic Host Configuration Protocol
### DNS
Domain Name System. E' un servizio a pagamento utilizzabile tramite Route 53.
### VPC Peering
### VPC Endpoints
### VPC Flow logs

# IAM
La [#IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html), o Identity Access Management è un servizio web che aiuta a controllare in modo sicuro l'accesso alle risorse di AWS tramite l'assegnazione di ruoli. E' il [Domain controller](<Reti#Domain controller>) di AWS.
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
## Policy
[Policy simulator](https://signin.aws.amazon.com/signin?redirect_uri=https%3A%2F%2Fpolicysim.aws.amazon.com%2Fhome%2Findex.jsp%3Fstate%3DhashArgs%2523%26isauthcode%3Dtrue&client_id=arn%3Aaws%3Aiam%3A%3A015428540659%3Auser%2Fpolicysim&forceMobileApp=0&code_challenge=L5HWMe5DQvLufKnzOFmJ-VuKOkHeX_OG1h2ymBEYJp4&code_challenge_method=SHA-256)
# EC2
L'Elastic Compute Cloud (o EC2), è il servizio di virtualizzazione di AWS, che permette di creare macchine virtuali, utilizzabili per impostare database, siti web, ecc.
Ogni #istanza si basa si un sistema operativo virtualizzato, creato tramite [[#AMI]] e può essere collegata ad un [[#S3]] e ad uno o più #snapshot.
## AMI
O Amazon Machine Image, sono dei file, preimpostati da Amazon, utilizzati come immagine per impostare le  macchine virtuali dell'EC2.
### Amazon Linux 2
Il #package-manager predefinito è
```sh
sudo yum
```
### Amazon Linux 2023
Il #package-manager predefinito è
```sh
sudo dnf
```
### Windows
Utilizzare una porta [RDP](<Protocolli%20di%20comunicazione.md#RDP di comunicazione#RDP>) invece che [SSH](<Protocolli%20di%20comunicazione.md#SSH di comunicazione#SSH>) per la connessione. Per connettersi al server remoto è necessario  scaricare il file preposto alla connessione da remoto o tramite il #software Connessione da Remoto nel caso si utilizzi [[Windows]] mentre, nel caso si utilizzi [[iOs]], sarà necessario scaricare un software apposito.
#### [Connettersi](https://docs.aws.amazon.com/it_it/AWSEC2/latest/WindowsGuide/connecting_to_windows_instance.html)

## [Tipo di istanza](https://docs.aws.amazon.com/it_it/AWSEC2/latest/UserGuide/instance-types.html)
### t2
Consigliata per applicazioni web a basso traffico, database di piccole o medie dimensioni.
#### micro
Istanza idonea al piano gratuito.
### r5
Consigliata per DAS, ovvero Database ad alte prestazioni e cache di memoria distribuite
### proton
Chip creato nativamente da AWS per aumentare di molto le prestazioni di una macchina (non è un'istanza generica, ma può essere attivato all'interno di AWS) tramite una gestione automatica delle risorse ( #backup inclusi).
## Ciclo di vita
![[Pasted image 20240502095612.png]]
### Attiva
### Arresta
### Termina
Quando si chiede di terminare un' #istanza [[#Attiva]], AWS effettua un controllo di eventuali collegamenti ad altri servizi di AWS (ad esempio S3) e, in caso questi esistano, bloccherà la terminazione dell'istanza. Per questo motivo conviene [arrestare](#Arresta) l'istanza prima di terminarla.
## Utilizzo
### PuTTY
1. Inserire indirizzo IP o nome Host dell'EC2 con cui ci si vuole connettere
2. andare su ssh/auth/credentials e aprire il file .ppk con le credenziali
3. Inizializzare il programma e accedere come **ec2-user**
### [Inizializzazione di LAMP](https://docs.aws.amazon.com/it_it/AWSEC2/latest/UserGuide/ec2-lamp-amazon-linux-2.html)
### Installazione di [[Docker]]
prendere script da sito di Docker in base al sistema operativo che si è installato nel server
Durante l'installazione, nel caso si usi una memoria di piccole dimensioni, il server potrebbe andare in stato di #anger (sovraccarico). Per evitare ciò si utilizza lo #swapfile, ovvero una partizione (o file), situato nell'hard disk, che lavora come estensione della RAM.
```sh
sudo fallocate -l 4G /swapfile 
```
```sh
sudo dd if=/dev/zero of=/swapfile bs=1M count=4096 

```
```sh
sudo chmod 600 /swapfile 
```
```sh
sudo mkswap /swapfile 
```
```sh
sudo swapon /swapfile
```
```sh
sudo nano /etc/fstab
```
	Inserire la seguente riga:
	/swapfile none swap sw 0 0
Per installare Docker su Ubuntu bisogna scrivere nel terminale:
```sh
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
```
Imposta il repository Docker apt
```sh
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```
Installa i pacchetti di Docker
```sh
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
Verifica che l'installazione ha avuto successo
```sh
sudo docker run hello-world
```
### Installazione di [Jenkins](../software/jenkins) su AWS
Installo Jenkins (vedi file di Jenkins)
### Installazione di un database
### Deploy
### Apertura di un immagine di Docker
Le immagini possono essere cercate su [Docker hub](https://hub.docker.com/)
#### Esempi
mongo/express
```sh
docker pull mongo-express
```
Oppure, seguendo l'esempio di Simone:
```sh
docker run --network api-net --name database -v /var/lib/postgresql/data:/var/lib/postgresql/data -e POSTGRES_PASSWORD=password -e POSTGRES_USER=api -e POSTGRES_DB=api -d postgres:14
```

#### Caricare le impostazioni del server da immagine Docker
E' possibile automatizzare il caricamento di un server partendo da un'immagine [[Docker]].
```sh
ssh ubuntu@<indirizzo_ip> -i ${SSH_CREDNTIALS} -o StrictHostKey=no << EOF
	docker container stop <nome> || true && \
	docker container rm <nome> || true && \
	docker container run -d --network <nome_network> --name <nome> -p <porta>:<porta> \
	-e <variabile_ambiente>=<valore> \
	${DOCKER_USER}/<nome_immagine>:latest && \
	exit
	EOF
```
	EOF (End Of File è un placeholder per indicare quale sia l'ultima riga del comando)
	L'algoritmo <dato> || true && viene utilizzato per far continuare il processo anche nel caso il comando dia errore (es. se non ci sono container da imterroompere)
	\ viene utilizzato per proseguire con le istruzioni nella riga successiva
### Ridurre lo spazio utilizzato
Per ridurre lo spazio utilizzato, si deve creare un nuovo volume da uno #snapshot
## Snapshot

# EKS
Elastic Kubernetes Services implementa [[Kubernetes]] all'interno di AWS.
# S3
Il Simple Storage Service è il servizio di #storage  principale di Amazon, fruibile tramite [http](<Protocolli%20di%20comunicazione.md#HTTP di comunicazione#HTTP>). Alcuni punti di forza del servizio sono:
- Possibilità di memorizzare un numero illimitato di oggetti in un bucket
- Oggetti fino a 5TB
- Durability e disponibilità del 99,9%
- Endpoint HTTP/S
- Altamente scalabile, affidabile, veloce
- Tool di stima del costo mensile - [AWS Simple Monthly Calculator](https://calculator.aws/#/), calcolati in base a
	- #storage 
	- numero di richieste
	- trasferimento dati
## Bucket
E' il #container utilizzato da S3 per memorizzare i dati. Ogni account può possedere massimo 100 bucket, i cui nomi devono essere univoci a livello globale.
```Bucket URL
http://<nome_bucket>.s3.amazonaws.com/<Object_key>
```
	Object key: data/
	versioning
## Glacier
Servizio a pagamento utilizzato in coppia con [[#S3]], utilizzato per recuperare dati (anche grandi) entro 3-5 ore per definire il ciclo di vita dei dati del bucket.

## API
AWS offre delle [API](https://docs.aws.amazon.com/AmazonS3/latest/API/Type_API_Reference.html) per interagire con i servizi S3, suddivise in Actions e Data types.

### Actions

### Data types

### Tools di terze parti
- [s5cmd](../Software/s5cmd)

# Dynamo DB
Database non relazionale #nosql.
```Dymano
{
TableName: "Music",
KeySchema: [
	{
		AttributeName: "Artist",
		AttributeDefinition: "Definition"
	}
	]
}
```
AWS fornisce un'interfaccia per l'inserimento di dati nel database, utilizzabile per evitare di inserire i dati tramite codice.
# [RDS](https://docs.aws.amazon.com/it_it/AmazonRDS/latest/UserGuide/Welcome.html)
Il Relational Database Service (RDS) permette di effettuare #backup cross-region. Permette di utilizzare linguaggi di gestione dei #database come:
- [[informatica/Database/MySQL|MySQL]]
- [[Informatica/Database/MariaDB|MariaDB]]

# AWS CLI
Command-Line Interface si usa per immettere comandi ad AWS direttamente da terminale.
## Installazione
Per effettuare l'accesso bisogna creare una chiave di accesso dalla console di AWS (Navbar -> utente -> Credenziali di sicurezza -> Chiavi di accesso -> Crea chiave di accesso)
## Configurazione
```sh
aws configure
```
	AWS Access Key ID - inserire la chiave
	AWS Secret Access Key - inserire la chiave segreta 
	Default region name - Inserire oil codice della regione in cui si opera (es. us-east-1) 
	Default output format - JSON

# Amazon VPC
Servizio di virtual private #cloud di Amazon.

# Attenzione
- Nel caso si voglia aprire una nuova porta dal server, la si deve anche segnalare nella piattaforma di AWS
# Indirizzi IP utili
| Dominio | Tipo | Porte | Destinazione |
| ---- | ---- | ---- | ---- |
| GitHub | SSH | 22 | 140.82.121.0/24 |
| Pubblico IPv4  |  |  | 0.0.0.0/0 |
| Pubblico PIv6 |  |  | ::/0 |
