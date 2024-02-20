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
## commit
Esistono delle [convenzioni](Conventional%20commit) per effettuare il #commit, visibili su [conventional commit](https://www.conventionalcommits.org/en/v1.0.0/)
```sh
git commit
```
Opzioni
```sh
-m "<commento>"
```
## merge
E' 'na roba brutta da evitare quando possibile.
### Fast-forward
Il parametro #fast-forward è attivo di default 
```sh
git merge --no-ff
```
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
# Conventional commits

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

