MySQL è un linguaggio per la creazione e gestione di #database relazionali.
# Installazione
[link](https://dev.mysql.com/downloads/installer/)
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
### 1-to-Many
### Many-to-Many
## Errori

| Codice | Descrizione                         |
| ------ | ----------------------------------- |
| 1007   | Il database esiste già              |
| 1046   | Non hai selezionato nessun database |
|        |                                     |
# Engine
## InnoDB
Permette inserimenti, relazioni, alcune operazioni #CRUD 