# Introduzione
[MySQL](https://www.mysql.com/it/) è un Relational [[Database]] Management System ( #dms) #relazionale, che lavora utilizzando il linguaggio #SQL.
# Installazione
[link](https://dev.mysql.com/downloads/installer/)
# Connessione al server
Su terminal:

| comando | descrizione |
| ------- | ----------- |
| -u      | user        |
| -p      | password    |
# Comandi
I comandi originariamente dovevano essere scritti in MAIUSCOLO. Successivamente questa pratica è diventata opzionale.

Creazione di un #database 
```MySQL
CREATE DATABASE <nome_database>;
```
	CREATE DATABASE IF NOT EXISTS <nome_database>; # Permette di evitare l'errore nel caso il database esiste già
Usare un #database 
```MySQL
USE <nome_database>;
```
Creazione di una #tabella (per vedere le [tipologie di dati](https://www.html.it/pag/31909/mysql-tipo-dei-dati/) o le [parole riservate](https://www.html.it/pag/31910/mysql-parole-riservate/))
```MySQL
CREATE TABLE <nome_tabella> (
<nome_colonna_1> <tipologia_dati> <parola_riservata>, 
<nome_colonna_2> <tipologia_dati>
);
```
	TIPOLOGIE DI DATI
	- char(<lunghezza>) # stringa di lunghezza fissa
	- varchar(<lunghezza_max>) # stringa di lunghezza variabile
	- int # numero intero compreso tra -2147483648 e +2147483647
	- float(i,d) # creazione di un numero decimale, avente i cifre intere e d decimali
	- decimal # Numero composto da una parte intera e 2 cifre decimali
	- datetime # dato composto da una data ed un orario
	- timestamp (<tipologia>)
	PAROLE RISERVATE (O MODIFICATORI DI COLONNA)
	- AUTO_INCREMENT
	- BINARY
	- DEFAULT
	- NOT NULL
	- PRIMARY KEY
	- FOREIGN KEY
	- UNIQUE
	- UNSIGNED # utilizzabile per dati numerici. Corrisponde al modulo del numero (sempre positivo)
	- ZEROFILL # utilizzabile per dati numerici. Permette di inserire degli zeri all'inizio del numero, in modo tale da avere numeri con lunghezza uguale
Per popolare una tabella
```MySQL
INSERT INTO <tabella> (<nome_colonna_1>, <nome_colonna_2>...)
VALUES (<valore_1>, <valore_2>) (<valore_1>, <valore_2>);
```
Aggiornare un record
```MySQL
UPDATE <database>.<tabella> WHERE <condizioni>
```
## Query
Selezionare determinate colonne di una tabella
```MySQL
SELECT <colonna> FROM <tabella>;
```
	Se <colonna> = *, si seleziona l'intera tabella
Selezionare un determinato record da una tabella in base ad un parametro
```MySQL
SELECT <colonna_1>, <colonna_2> FROM <tabella> WHERE <colonna> <operazione>; 
```
	OPERAZIONE:
	- BETWEEN <min> AND <max> # Ritorna parametri compresi tra due valori
	- ORDER BY [ASC, DESC] # Ordina i risultati in ordine ascendente o discendente
	- LIKE <pattern> # Trova i parametri che rientrano nel pattern
### LIKE

| Pattern | Descrizione                               |
| ------- | ----------------------------------------- |
| _       | Carattere qualsiasi                       |
| %       | Presenza di uno o più caratteri qualsiasi |
```MySQL
SELECT * FROM <table> WHERE <colonna> LIKE "_a%d"
```
	La query selezionerà tutti i record che abbiano (nella colonna selezionata) la seconda lettera "a" e "d" come ultima lettera.
## Relazioni
**ATTENZIONE**
Per creare relazioni tra tabelle, MySQL utilizza [[#InnoDB]] per la definizione delle tabelle
```MySQL
CREATE TABLE IF NOT EXISTS <tabella> (<colonne>) engine = InnoDB;
```
Per stabilire le relazioni si utilizza la #foreign-key 
### 1-to-1
```MySQL
CREATE TABLE <tabella> (
<colonne>
FOREIGN KEY(<colonna>) REFERENCES <tabella>(<colonna>)
);
```

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

## Join
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
| Comando                                        | Descrizione                                             |
| ---------------------------------------------- | ------------------------------------------------------- |
| not null                                       | Imposta il valore come impossibile da essere nullo      |
| PRIMARY KEY(chiave)                            | Imposta la #primary-key                                 |
| FOREIGN KEY(chiave) REFERENCES tabella(chiave) | Imposta il dato come #foreign-key                       |
| INT                                            | Numero intero                                           |
| auto_increment                                 | Imposta automaticamente il dato in maniera incrementale |
| check(condizione)                              | Verifica se i campo rispetta la condizione impostata)   |
| CHAR(lungh.)                                   | Dato di tipologia Stringa e lunghezza fissa lungh.      |
| VARCHAR(lungh.)                                | Dato di tiologia Stringa e lunghezza lungh.             |

## Altri comandi utili
- index: Definisce l'indice della tabella
- show index /g: mostra gli indici della tabella riga per roga (senza /g li mostra in tabella semplice)
- describe table: mostra la tabella table
- order by: ordina i record mostrati (desc li ordina in ordina decrescente)
- max(chiave): seleziona il parametro più grande
# Engine
## InnoDB
Permette inserimenti, relazioni, alcune operazioni #CRUD 
# Viste
Sono delle tabelle virtuali definite da #query. Si utilizzano per salvare e richiamare più velocemente le ricerche (si può fare per le ricerche più effettuate ad esempio).

	CREATE VIEW table_name as SELECT table1.key1, table2.key2;
Si possono visualizzare i dati tramite:

	SELECT * from table_name*
# Esempi di queries

	CREATE Table directors (id int auto_increment,name VARCHAR(40), surname VARCHAR(40), PRIMARY KEY(id));
	INSERT INTO directors(name, surname) VALUES ("Stanley", "Kubrick"),
	("Quentin", "Tarantino");