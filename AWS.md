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
## Collegamento al server da terminale
```sh
ssh ubuntu@<indirizzo_ip_server> -i <user_ssh>
```
# Installazione di [[Docker]]
prendere script da sito di docker in base al sistema operativo che si è installato nel server
Durante l'installazione, nel caso si utlilizzi una memoria di piccole dimensioni, il server potrebbe andare in stato di #anger (sovraccarico). Per evitare ciò si utilizza lo #swap, ovvero una partizione (o file), situato nell'hard disk, che lavora come estensione della RAM.

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
## Installazione di [[Jenkins]]
Installo Jenkins (vedi file di Jenkins)
## Installazione di un database
## PostGres
Si può installare da container Docker
# Utilizzo
## Apertura di un immagine di Docker
Le immagini possono essere cercate sul [link](https://hub.docker.com/)

mongo/express
```sh
docker pull mongo-express
```
Oppure, seguendo l'esempio di Simone:
```sh
docker run --network api-net --name database -v /var/lib/postgresql/data:/var/lib/postgresql/data -e POSTGRES_PASSWORD=password -e POSTGRES_USER=api -e POSTGRES_DB=api -d postgres:14
```
## Ridurre lo spazio utilizzato
Per ridurre lo spazio utilizzato, si deve creare un nuovo volume da uno #snapshot
# Attenzione
- Nel caso si voglia aprire una nuova porta dal server, la si deve anche segnalare nella piattaforma di AWS