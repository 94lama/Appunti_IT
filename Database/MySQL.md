## Introduzione
[MySQL](https://www.mysql.com/it/) è un Relational [[Database]] Management System ( #dms) #relazionale, che lavora utilizzando il linguaggio #SQL.
## Installazione
## Connessione al server
Su terminal:

|comando|descrizione|
|-|-|
|-u|user|
|-p|password|

|Tipologia di dato|Descrizione|
|-|-|
|varchar|stringa piccola (max 255 caratteri)|
|int|numero intero|
|text|stringa lunga|

|Comando|Descrizione|
|-|-|
|SELECT|seleziona 
|UNION|ritorna un risultato che comprende i dati delle colonne selezionate (da usare con select)|


	winpty mysql -u-nome_user -p
	mysql show databases; //mostra i database
	use nome_database; //aprire il database
	show tables; //mostrare le tabelle del database
	describe nome_tabella; //mostra la struttura della tabella
	create database nome_database; // crea un nuovo database
	drop database nome_database; // cancella il database
	create table nome_tabella (nome_proprietà tipo_dato, nome_2, tipo_dato, ..., primary_key(nome_proprietà)); // crea nuova tabella
	select nome_elemento from nome_tabella; //seleziona l'elemento dal database (* seleziona tutti gli elementi)
	drop table nome_tabella; //cancella la tabella selezionata
	quit //esce dal database

### Join
Variante del prodotto cartesiano di più tabelle (che mostra tutte le possibili combinazioni tra i file)
![[SQL Join.png]]

	SELECT key1, key2, key3 from table1, table2 where table1_fk == table2_pk;
	SELECT key1, key2, key3 from table1, table2 inner JOIN on table1_fk == table2_pk;
Le JOIN possono essere effettuate in varie maniere diverse, in base alla tipologia di inclusione dei dati delle tabelle:
- INNER - ritorna solo i dati presenti contenuti in entrambe le tabelle
- LEFT - ritorna i dati presenti in entrambe le tabelle e quelli presenti solo nella prima tabella
- RIGHT - ritorna i dati presenti in entrambe le tabelle e quelli presenti solo nella seconda tabella
- 
# Tipologie di dati
|Comando|Descrizione|
|-|-|
|not null|Imposta il valore come impossibile da essere nullo|
|PRIMARY KEY(chiave)|Imposta la #primary-key|
|FOREIGN KEY(chiave) REFERENCES tabella(chiave)|Imposta il dato come #foreign-key|
|INT|Numero intero|
|auto_increment|Imposta automaticamente il dato in maniera incrementale|
|check(condizione)|Verifica se i campo rispetta la condizione impostata)|
|CHAR(lungh.)|Dato di tipologia Stringa e lunghezza fissa lungh.|
|VARCHAR(lungh.)|Dato di tiologia Stringa e lunghezza lungh.|

## Altri comandi utili
- index: Definisce l'indice della tabella
- show index /g: mostra gli indici della tabella riga per roga (senza /g li mostra in tabella semplice)
- describe table: mostra la tabella table
- order by: ordina i record mostrati (desc li ordina in ordina decrescente)
- max(chiave): seleziona il parametro più grande
# Viste
Sono delle tabelle virtuali definite da #query. Si utilizzano per salvare e richiamare più velocemente le ricerche (si può fare per le ricerche più effettuate ad esempio).

	CREATE VIEW table_name as SELECT table1.key1, table2.key2;
Si possono visualizzare i dati tramite:

	SELECT * from table_name*
# Esempi di queries

	CREATE Table directors (id int auto_increment,name VARCHAR(40), surname VARCHAR(40), PRIMARY KEY(id));
	INSERT INTO directors(name, surname) VALUES ("Stanley", "Kubrick"),
	("Quentin", "Tarantino");