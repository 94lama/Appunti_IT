# Introduzione
# Installazione
Clonare il repository dal [sito](https://github.com/awslabs/git-secrets.git) e poi eseguire da Powershell:
```Powershell
./install.ps1
```
	NB. la directory .git-secrets/ dovrà contenere solo due file: git-secrets e git-secrets.1
Per installarla sul nostro repository
```bash
git secrets --install
```
Per renderla globale invece:
```bash
git secrets --register-aws
```

# Comandi
Per inizializzare una ricerca parametrica
```bash
git secrets --commit_msg_hook -- <parametro>
```
```parametri

```
Per eseguire una scansione del codice
```shell
git secrets --scan
```
 