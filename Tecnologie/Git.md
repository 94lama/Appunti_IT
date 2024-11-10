# Installazione
## Linux
```sh
sudo apt install git-all
```
# Comandi

# Conventional commits
I [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/) sono delle regole, ideate dai developers di Angular, per facilitare la code review e la lettura delle history dei commits. I principi cardine dei commits sono:
- Per l'implementazione dei conventional commits su un progetto già esistente, è consigliabile applicarlo inizialmente solo su alcune branches, con i type più utilizzati e senza le sezioni opzionali.
- Devono essere atomiche, ovvero limitate ad una singola implementazione e deve essere applicabile e revertabile senza modifiche al resto del progetto. Buona prassi è aggiungere dei test ai commit per verificarne l'efficacia.
- Le parole devono essere scritte in minuscolo ed essere espresse al presente

Per attuarli non servono tool esterni a git stesso, anche se sono disponibili tool di supporto (come, ad esempio, dei linter).
Alcuni progetti che utilizzano i git commits sono ad esempio Vue e Angular.

Il comportamento in caso di merge dipende dalla politica del team.
## header
```
type(scope): description
```
	Lo scope è opzionale

### type
E' un label di solito in caratteri minuscoli (convenzione che può variare da progetto a progetto), utilizzato per categorizzare il commit

| type     | descrizione                                                                                                   |
| -------- | ------------------------------------------------------------------------------------------------------------- |
| build    | apporta modifiche al processo di build (es. ai file .config)                                                  |
| chore    | categoria generica, utilizzata a volte per attività di configurazione                                         |
| ci       | per le modifiche di continuous integration                                                                    |
| docs     | modifiche alla documentazione                                                                                 |
| feat     | introduzione di nuove funzionalità                                                                            |
| fix      | per la correzione di bug                                                                                      |
| refactor | usato per il refactoring del codice                                                                           |
| revert   | usato come support al messaggio già offerto dal ```<br>git revert``` nel caso di revert parziali di un commit |
| style    | per le modifiche stilistiche del progetto (es formattazione da tab a spazi)                                   |
| test     | per la modifica di classi di test                                                                             |

### scope
Valore opzionale, inserito tra parentesi, non molto regolato dalle regole base dei conventional commits, ma da definire in base alle preferenze del team. Ad esempio si può orientare lo scope verso:
- a

### description
Breve descrizione delle modifiche. Deve essere scritta tutta in minuscolo (a parte nel caso siano presenti nomi) e senza punto finale.

### body
(opzionale) Permette di inserire messaggi aggiuntivi al commit, come la motivazione, il contesto, le scelte tecniche, ecc.

### footer
(opzionale) Contiene delle informazioni, presentate come coppia ```chiave:valore```, separate dal carattere ```-```.
Sono particolarmente utili ad esempio per referenziare eventuale supporto alla parte del codice oggetto del commit.

## semantic versioning
Nel caso di implementazione di semantic versioning, il numero di versione può essere stabilito dal tipo di commit utilizzato.
I commits possono essere suddivisi in base all'impatto che hanno sul progetto in:
- major
- minor
- patch

La tipologia di categorizzazione è a discrezione del team, ma una buona base di partenza può essere la seguente:
### major
Indicate con il simbolo **!** tra lo scope (o il type in assenza di scope) e  **:**. Vengono utilizzati per commits di tipo:
- breaking change

### minor
- feat

### patch
- build
- chore
- ci
- docs
- fix
- perf
- refactor
- style
- test

## Plugins
Esistono dei plugin di supporto dei git commits per i vari IDE.
# rules