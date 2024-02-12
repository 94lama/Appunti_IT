Software scritto con linguaggio [[Java]], che permette di automatizzare la #pipeline di un progetto.
# Installazione
```shell
sudo apt-get install jenkins 
```


Accedo al server tramite browser alla porta 8080.
```browser
<indirizzo_ip>:8080
```
Apparirà una pagina con un form di login, dove si dovrà inserire la password di Jenkins del server (la si trova salvata in un file all'interno del server)
```browser
Username: admin
Password: <password>
Confirm password: <password>
```

# Pagina di comando
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

# Collegamenti
## [[SonarQube]]
Una volta creato il #token per il login, scaricare il #plugin di integrazione con SonarQube (SonarQube Scanner):
- Manage Jenkins->Plugins
- selezionare SonarQube Scanner
- Ricaricare la pagina per completare l'installazione
- Andare su Manage Jenkins->Credentials.>System->Global credentials (unrestricted)
