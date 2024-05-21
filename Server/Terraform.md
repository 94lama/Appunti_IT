[Sito internet](https://www.terraform.io/)
Terraform è un servizio [IaC](<Cloud Server#IaC>) utilizzabile su tutti i provider cloud, creato da HashiCorp, che funziona sfruttando la struttura JSON per la creazione dei file e il CLI per l'immissione di input.
# Installazione
[link](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)

# Struttura
Un progetto Terraform è composto da:
```Terraform

├ terraform/
├ erraform.lock.hcl
├ main.tf
├ terraform.tfstate
└ terraform.tfstate.backup
web-app
├ main.tf
├ outputs.tf
├ terraform.tfvars
└ variables.tf
```
## main.tf
E' un file composto da un oggetto terraform che contiere la lista dei #provider, un oggetto per ogni provider in cui vengono stabilite :
```main.tf
terraform{
	backend{
		
	}
	required_providers{
		<nome_provider> = {
			region: "<regione>"
		}
	}
}
provider "<nome_provider>"{
	region: "<region>"
}
resource "<risorsa>" {
	bucket = 
}
```
Il parametro backend permette di stabilire il luogo di salvataggio del file [terraform.tfstate](#tfstate). Per evitare conflitti, #back-end viene tenuto commentato in fase iniziale.
## terraform
### tfstate

### tfvars
Importa nel progetto le variabili definite su [variables.tf](#variables.tf).
```terraform.tfvars
<chiave_1> = <valore_1>
<chiave_2> = <valore_2>
```
## variables.tf
Permette di definire le variabili del progetto.
```variables.tf
variable{
	description: "<descrizione>"
	
}
```
# Utilizzo con cloud server
## [[AWS]]
### Installazione
Installare i servizi di AWS nel pc dal seguente [link](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).

## Comandi
Installare le #dependency. Verrà create un file README.md
```sh
terraform init
```
Ricercare il server in base ai dati inseriti nel file main.tf. Terraform creerà un file chiamato [terraform.tfstate](#terraform.tfstate), che rappresenta il blueprint dell'infrastruttura
```sh
terraform plan
```
Approvare i dati trovati da Terraform. Terraform creerà un file chiamato [terraform.tfstate](#terraform.tfstate), che rappresenta il blueprint dell'infrastruttura o un file errored.tfstate nel caso il comando abbia incontrato un problema di esecuzione.
```sh
terraform apply #chiederà se confermare o meno
```
Terminare l'istanza in atto
```sh
terraform destroy #chiede conferma
```

## [[Jenkins]]
Per collegare Jenkins e Terraform si deve creare un #repository su [[Github]] del progetto Terraform e collegare Jenkins a quest'ultimo tramite #ssh-key.
Successivamente si inserisce nel repository un #jenkinsfile contenente una #pipeline di login da Jenkins al repository.
Dal Jenkinsfile si eseguiranno i comandi di Terraform
```jenkinsfile
stage('Terraform deploy'{
	steps{
		script{
			sh '''
				terraform init
				terraform plan
				terraform apply -y
			'''
		}
	}
}
```
Da terminal installare Terraform sulla macchina (cloud)
```sh
<prendere comandi>
```
Creare un sistema di autenticazione per Terraform su AWS
```Percorso
IAM > Users > terraform-user > 
```
e su Jenkins
```Percorso
Dashboard > Manage Jenkins > Credentials > System > Global credentials (unrestricted)
Type: Secret text
```
La variabile inserita su Jenkins va implementata anche nel jenkinsfile
```jenkinsfile
stage ('Terraform deploy') {
	environment{
		AWS_ACCESS_KEY_ID = credentials("<AWS_ACCESS_KEY>")
		AWS_SECRET_ACCESS_KEY = credentials("<AWS_SECRET_KEY>")
	}
}
```
Aggiornare il #repository 
```sh
git add ^^ git commit -m"<commento>" && git push
```

# Tools
## tfsec
Permette di effettuare una scansione sulla sicurezza del server, fornendo al contempo sia il grado di severità del problema, che dei link con le soluzioni agli stessi.
