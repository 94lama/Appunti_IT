[DevProxy](https://learn.microsoft.com/en-us/microsoft-cloud/dev/dev-proxy/get-started?tabs=automated&pivots=client-operating-system-linux) è un software open source sviluppato da Microsoft per intercettare ed analizzare le chiamate http effettuate da un dispositivo. Il software si avvia come processo in shell, ed è terminabile tramite comando Ctrl+C

# Linux
## Installazione
Per installare DevProxy digitare il comando
```sh
bash -c "$(curl -sL https://aka.ms/devproxy/setup.sh)"
```
	RISPOSTA:

Per installare il certificato SSL
```sh
# Export Dev Proxy root certificate
openssl pkcs12 -in ~/.config/dev-proxy/rootCert.pfx -clcerts -nokeys -out dev-proxy-ca.crt -passin pass:""

# Install the certificate
sudo cp dev-proxy-ca.crt /usr/local/share/ca-certificates/
# Update certificates
sudo update-ca-certificates
```
	RISPOSTA:
	info    8 error responses loaded from devproxy-errors.json
	 info    Dev Proxy API listening on http://localhost:8897...
	 info    Dev Proxy Listening on 127.0.0.1:8000...
	
	Hotkeys: issue (w)eb request, (r)ecord, (s)top recording, (c)lear screen
	Press CTRL+C to stop Dev Proxy

Riavviare il profilo (dalla home del profilo)
```sh
source ~/.bashrc
```

Per avviare una sessione di DevProxy, digitare il comando
```sh
devproxy
```

Premere "Ctrl+C" per terminare la sessione in sicurezza.

## Intercettazione richieste
Per simulare una chiamata scrivere
```sh
curl -ix http://localhost:8000 https://jsonplaceholder.typicode.com/posts
```
	RISULTATO:
	req   ╭ GET https://jsonplaceholder.typicode.com/posts
	 api   ╰ Passed through

# Windows
## Installazione
```PowerShell
(Invoke-WebRequest https://aka.ms/devproxy/setup.ps1).Content | Invoke-Expression
```


## Intercettazione richieste

# Generali
## Configurazione
Per configurare DevProxy tramite [file](#devproxyrc.json) apposito (in formato JSON) basta digitare il comando
```sh
devproxy config
```

### devproxyrc.json
#### urlsToWatch
Chiave che contiene la lista degli indirizzi URL da monitorare.

### devproxy-errors.json
File che contiene i messaggi di log degli errori ricevuti dal server.
```devproxy-errors.json
{
  "$schema": "https://raw.githubusercontent.com/microsoft/dev-proxy/main/schemas/v0.20.0/genericrandomerrorplugin.schema.json",
  "errors": [
    {
      "request": {
        "url": "https://jsonplaceholder.typicode.com/*"
      },
      "responses": [
        {
          "statusCode": 429,
          "body": {
            "message": "Too Many Requests",
            "details": "The user has sent too many requests in a given amount of time (\"rate limiting\")."
          },
          "headers": {
            "Retry-After": "@dynamic"
          }
        }
      ]
    }
  ]
}
```

### Opzioni

| Opzione                  | Descrizione                                                         |
| ------------------------ | ------------------------------------------------------------------- |
| --failure-rate \<numero> | Indica il numero massimo di chiamate prima di terminare la chiamata |

## Documentazione
Per agevolare la creazione di una documentazione dell'app che si sta sviluppando, possono tornare utili alcuni plugin, in base alla tipologia di report che si vuole ottenere:
- **MarkDown**: Il plugin MarkdownReporter genera un report delle chiamate in formato Markdown
- **JSON**
- **Plain text**

### MarkdownReporter
Per attivare il plugin, basta inserire nel file di configurazione i seguenti parametri
```devproxyrc.json
"plugins": [
	{ "name": "ExecutionSummaryPlugin", "enabled": true, "pluginPath": "~appFolder/plugins/dev-proxy-plugins.dll" },
	{
	  "name": "MarkdownReporter",
	  "enabled": true,
	  "pluginPath": "~appFolder/plugins/dev-proxy-plugins.dll"
	}
],
"urlsToWatch": [
	<URL da monitorare>
]
```

Avviare DevProxy tramite comando
```sh
devproxy --record --summary-group-by messageType
```

In automatico il software creerà un file  chiamato "PluginName_MarkdownReporter.md"

