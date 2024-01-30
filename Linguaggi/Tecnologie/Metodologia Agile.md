## Introduzione
#agile è un metodo di lavoro in gruppi, contrapposto al metodo [[Waterfall]], definito nel 2001 nelle Wasath Mountains, Utah ad una conferenza per i metodi leggeri ( #SCRUM, #DSDM, #adaptive-software, #crystal, #extreme-programing, #driven-development, ...), basato su 12 valori, elencati nel [Manifesto agile](https://agilemanifesto.org/iso/it/manifesto.html), per agevolare la programmazione:
1. Individui e interazioni al di sopra dei processi e degli strumenti
2. Software funzionali rispetto alla documentazione completa
3. La collaborazione con il cliente è più importante della negoziazione del contratto
4. Rispondere al cambiamento piuttosto che seguire un piano.
E 12 principi:
1. Our highest priority is to satisfy the customer through early and continuous delivery of valuable software.
2. Welcome changing requirements, even late in development. Agile processes harness change for the customer's competitive advantage.---------------------------------------------------------------------
3. Deliver working software frequently, from a couple of weeks to a couple of months, with a  preference to the shorter timescale.
4. Business people and developers must work together daily throughout the project.
5. Build projects around motivated individuals. Give them the environment and support they need, and trust them to get the job done.-----------
6. The most efficient and effective method of conveying information to and within a development team is face-to-face conversation.
7. Working software is the primary measure of progress.
8. Agile processes promote sustainable development. The sponsors, developers, and users should be able to maintain a constant pace indefinitely.
9. Continuous attention to technical excellence and good design enhances agility.
10. Simplicity--the art of maximizing the amount of work not done--is essential.
11. The best architectures, requirements, and designs emerge from self-organizing teams.
12. At regular intervals, the team reflects on how to become more effective, then tunes and adjusts its behavior accordingly.
## Extreme programing
Metodologia definita da Kent Beck, Ward Cunningham (creatore del #wiki** e coniatore del termine #technical-debt***) e Ron Jeffries,

** Strumento di **editing collaborativo** 
*** Costo aggiuntivo per a futura implementazione di programmi sviluppati scegliendo l'opzione più veloce e semplice al momento.
## Toyota Production System ( #TPS)
Processo sviluppato dalla Toyota per massimizzare l'efficienza dei processi e la produzione. E' un processo produttivo *just-in-time* (la produzione inizia quando viene creato l'ordine), massimizzando l'efficienza dell'intero processo per agevolare il cliente, il lavoratore e il sistema produttivo. 
Si basa su 5 principi: Genchi genbutsu, kaizen, challenge, teamwork, respect, atti ad eliminare sprechi ( #muda), sovraccarichi ( #muri) e inconsistenze ( #mura).
#### Sistema produttivo LEAN
##### Just-in-time
Produrre solo quando l'ordine avviene (per evitare sprechi)
##### Jidoka
Fermarsi e sistemare il problema, ovvero appena si presenta un problema, esso viene segnalato, interrompendo il processo produttivo, ed un controllore raggiunge l'operatore che lo ha segnalato, e fornisce supporto per risolvere il problema.
#### Genchi genbutsu (andare all'origine)
Metodologia per risolvere i problemi
#### Kaizen (sviluppo continuo)
Alta frequenza di riunioni per controllare l'andamento dl processo
#### Challenge
#### Teamwork
#### Respect
La pulizia è parte fondamentale di un ambiente produttivo
#### Heijunka
Le componenti vengono consegnate nelle postazioni dei lavoratori seguendo l'ordine di assemblaggio. Ogni lavoratore è considerato anche un *quality checker*. Anche in caso di problemi segnalati dal cliente, essi vengono analizzati, riparati e tenuti in considerazione per il futuro sviluppo delle componenti difettose.
## [SCRUM](https://www.scrum.org/)
### Introduzione
Le metodologie **agili** sono spesso utilizzate per gestire i rischi (Mancata consegna, assenza di valore, prolungamento dei tempi di consegna).
Lo SCRUM, ideato da Jeff Sutherland, si basa su cicli di brevi intervalli di tempo, nei quali l'intero team si concentra unicamente sul lavoro, con riunioni quotidiane di aggiornamento.

#SCRUM si basa su 4 punti:
### Valori
- #### Coraggio
- #### Focus
- #### Commitment
- #### Rispetto
- #### Apertura
### Ruoli
Lo SCRUM si basa sul lavoro in team, nei quali sono stabiliti dei ruoli
#### SCRUM Master
#### Product owner
#### Stakeholders
Sono i portatori di interesse nel progetto, come dei possibili dipendenti che andranno ad utilizzare il programma
#### Sviluppatori

### Eventi
#### Planning
Periodo in cui vengono stabiliti gli obiettivi da realizzare nel ciclo
#### Review
Riunione con presentazione della demo dei risultati ottenuti nel ciclo. Nel caso 
#### Retrospettiva
Riunione tenuta dallo SCRUM Master e dagli sviluppatori, in cui vengono discussi i risultati dell'incremento
### Artefatti
#### Product backlog
Rappresenta l'intero progetto, suddiviso in blocchi separati. Viene rappresentato con un rettangolo, nella quale cima gli elementi già completati (suddivisi in piccoli blocchi).
Può essere schematizzato su una board
Nel backlog si usano **Storie** e **User persona** per schematizzare i blocchi di azioni da realizzare 
- #storia
	Rappresenta l'insieme di azioni che l'user persona compie durante la sua intera permanenza nel sito
- #user-persona
	
#### Sprint backlog
Componenti del progetto da realizzare nello sprint
#### Incremento
Rappresenta il risultato di un ciclo di programmazione

## Note

- David Heinemeier Hanson: sviluppatore di Basecamp (ora 37 Signals)
### Bibliografia
- *The pragmatic programer*, A. Hunt, D. Thomas, **Pragmatic bookshelf**
- *SCRUM: the art of doing twice the work in half the time*, J. Sutherland