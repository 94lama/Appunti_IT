# Introduzione
[Semgrep](https://github.com/semgrep/semgrep) è un software #SAST, sviluppato da Meta nel 2009 con l'obiettivo di avere un software veloce, ed efficace (punta ad ottenere falsi positivi piuttosto che falsi negativi).
# Installazione
1. Install Semgrep CLI

```
# For macOS
$ brew install semgrep

# For Ubuntu/WSL/Linux/macOS
$ python3 -m pip install semgrep

# To try Semgrep without installation run via Docker
$ docker run -it -v "${PWD}:/src" semgrep/semgrep semgrep login
$ docker run -e SEMGREP_APP_TOKEN=<TOKEN> --rm -v "${PWD}:/src" semgrep/semgrep semgrep ci
```

2. Run `semgrep login` to create your account and login to Semgrep.
Logging into Semgrep gets you access to:

- [Semgrep Supply Chain](https://semgrep.dev/products/semgrep-supply-chain): A dependency scanner that detects reachable vulnerabilities in third party libraries
- [Semgrep Code's Pro rules](https://semgrep.dev/products/semgrep-code): 600+ high confidence rules written by Semgrep's security research team
- [Semgrep Code's Pro engine](https://semgrep.dev/products/pro-engine/): An advanced code analysis engine, designed to detect complex vulnerabilities, and reduce false positives

3. Go to your app's root directory and run `semgrep ci`. This will scan your project to check for vulnerabilities in your source code and its dependencies.
    
4. Try writing your own query interactively with `-e`. For example, a check for Python == where the left and right hand sides are the same (potentially a bug): `$ semgrep -e '$X == $X' --lang=py path/to/src`
# [semgrep rules](https://github.com/semgrep/semgrep-rules)
Sezione di #semgrep adibita alla collezione di regole, categorizzate per linguaggio di programmazione. I linguaggi inclusi sono:
- [[Python]]
- [[Php]]
- [[JavaScript]]
- [[Java]]
# Funzionamento
Per imparare il funzionamento di semgrep, è possibile visualizzare il [sito](https://semgrep.dev/learn) .

semgrep effettua la scansione e successivamente crea un file **semgrep.txt**, dove riporta il risultato dell'analisi (presente anche nel #terminale).
# Linguaggio semgrep
Verificare la possibile presenza di valori (va bene sia se sono presenti che nel caso non lo siano)
```semgrep
...
```
Definire una variabile
```semgrep
$VAR_NAME
```

## Tainted mode
```semgrep
rules:
- id: request.cookies[...]
	mode: taint
	pattern sources:
	- pattern:
```
Per verificare se il dato viene immesso in un particolare elemento
```semgrep
pattern-sink:
```
Per verificare la presenza di un tentativo di sanifica del dato dopo essere stato identificato, è possibile escluderlo dalle segnalazioni tramite
```semgrep
- patter-sanitize:
	- pattern:
```
Per verificare le il dato viene immesso in un sink 