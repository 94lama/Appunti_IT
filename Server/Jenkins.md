Software scritto con linguaggio [[Java]], che permette di automatizzare la #pipeline di un progetto.
# Installazione
Qualora la macchina non abbia installato [[Java]], è necessario installarlo:
```bash
sudo apt update
sudo apt install fontconfig openjdk-17-jre
java -version
openjdk version "17.0.8" 2023-07-18
OpenJDK Runtime Environment (build 17.0.8+7-Debian-1deb12u1)
OpenJDK 64-Bit Server VM (build 17.0.8+7-Debian-1deb12u1, mixed mode, sharing)
```
Poi sarà possibile installare Jenkins:
```shell
sudo apt-get install jenkins 
```
Accedo al server tramite browser alla porta 8080.
```browser
<indirizzo_ip>:8080
```
Recupero la password di Jenkins
```sh
cat /var/lib/jenkins/secrets/initialAdminPassword
```
	Copiare la password mostrata
Apparirà una pagina con un form di login, dove si dovrà inserire la password di Jenkins appena copiata
```browser
Username: admin
Password: <password>
Confirm password: <password>
```
# Pagina di comando
## Struttura
```Dashboard
|- <nome_progetto>
|-- Configuration
|--- General
|--- Source Code Management
|--- Build Environment
|--- Build Steps
|--- Post-build Actions
```
## People
## Build history
Mostra i #job effettuati nel tempo (il job è l'esecuzione di una singola #pipeline)
## New item
### Freestyle project
Permette di creare l'automatizzazione di un processo qualsiasi.
#### Source Code Management
Permette di scegliere la fonte del codice da trattare (ad esempio Git)
- Per il collegamento con GitHub, Jenkins accetta solo la chiave ssh
- Poll CRM permette di impostare il periodo tra due esecuzioni della pipeline
- 

### Pipeline
## Manage Jenkins
### Credentials
#### Systems
Permette di configurare le variabili di sistema. Una volta inserite, Jenkins le renderà non più visibili (né dalla pagina, né da eventuali log di sistema).
### Nodes
Permette di gestire i nodi di Jenkins
#### New node
Permette di creare un nuovo nodo. Dati richiesti:
- Nome
- Descrizione
- Numero di esecutori
- root remota della directory
- #label (come fosse un tag)
- Modalità di utilizzo
- Metodo di inizializzazione
- Proprietà

## Configure
### Build Steps
Permette di costruire la #pipeline tramite blocchi di codice. I blocchi possono contenere varie tipologie di comandi (es. comandi di #terminale, variabili, ecc.). 
# Configurazione
## [[Docker]]

Acquisire i permessi di docker per l'user jenkins
```sh
sudo usermod -aG docker jenkins
```
Riavviare Jenkins
```sh
sudo service jenkins restart
```
Rieffettuare il login

Se si usa #AWS, seguire i [passaggi dedicati](AWS#Installazione%20di%20Docker)
## https

## VPN

# Agent
Modalità di esecuzione di #nodo su una macchina in remoto. Viene utilizzato per nascondere gli elementi contenuti nella pipeline #agent da quella principale.
```sh

```
# Pipeline  syntax
E' possibile utilizzare Jenkins tramite file (**jenkinsfile**), selezionando [Pipeline](#pipeline) durante la pagina di creazione di nuovo elemento. Il #jenkinsfile è un file costruito con metodo orientato agli oggetti, dove è presente un unico elemento **pipeline**, che contiene i vari settaggi
```jenkinsfile
pipeline {
	agent <agent>
	stages {
		stage('<nome_stage>'){
			steps{
				script {
					<codice>
					withCredentials[<credenziali>] {
						<codice>
					}
				}
			}
		}
	}
}
```
Sulla piattaforma di Jenkins, è possibile creare degli #snippet di codice da utilizzare nel #jenkinsfile su Dashboard-><nome_progetto>->
# Collegamenti
## [[SonarQube]]
Una volta creato il #token per il login, scaricare il #plugin di integrazione con SonarQube (SonarQube Scanner):
- Manage Jenkins->Plugins
- selezionare SonarQube Scanner
- Ricaricare la pagina per completare l'installazione
- Andare su Manage Jenkins->Credentials.>System->Global credentials (unrestricted)
