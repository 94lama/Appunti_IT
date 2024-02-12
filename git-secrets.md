# Introduzione
# Installazione
Scaricare il file dal sito e poi da Powershell:
```Powershell
./install.ps1
```
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
 