# Comandi
## Inizializzazione di un progetto
Clonare un progetto da una #repository esistente
```shell
git clone <url>
```
Inizializzare un progetto esistente su una repository esistente
```shell
git add remote origin < 
```
## pull
# Struttura
## Branches
Le #branch sono delle ramificazioni del progetto.

| nome | utilizzo |
| --- | ----- |
| main | programma in fase di produzione |
| release | programma in fase di staging pronto al #deploy |
| development | codice in fase di sviluppo |
| features | indica la singola feature da implementare |
# Deploy keys
Contiene tutte le chiavi utilzzate per effettuare i deploy
# [git-secrets](https://github.com/awslabs/git-secrets)
Genera una nuova sotto-cartella di .git chiamata **secrets**.
```bash
providers = git secrets --aws-provider
patterns = (<pattern_da_controllare>)
patterns = (<secondo_patterna_da_controllare)
allowed = <stringa_permessa>)
```
Aggiornare i secrets
```bash

```
Scansionare i file in base ai secrets impostati
```bash
git secrets --scan <percorso>
```
# Terminologia
|termine|descrizione|
|-|-|
|pair programing|metodologia di programmazione nella quale i developers lavorano contemporaneamente, ma su file diversi per evitare conflitti|

