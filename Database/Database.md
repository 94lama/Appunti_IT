# Introduzione
I dati hanno bisogno di un contesto per essere considerati informazione. per far ciò si utilizzano i database.
Un #database è una raccolta di dati organizzati e memorizzati in una o più tabelle, dove ogni elemento è descritto in una riga (o #record), mentre ogni #attributo è indicato in una specifica colonna.
Una #colonna (di solito la prima) deve essere riservata ad un valore univoco, di norma identificato con l'ID, denominato #chiave-primaria. Come #ID è spesso utilizzato un numero intero positivo #incrementale.
I database sono gestiti da un Motore di Database, ovvero un #software che consente di rappresentare, memorizzare e manipolare le tabelle. Alcuni esempi di motori db sono: [[informatica/Database/MySQL]], [[SQLite]], entrambi i quali utilizzano [[informatica/Linguaggi/MySQL]] come linguaggio, [[PostGres]].
#DBMS (DataBase Management System). A loro volta possono essere #relazionali o non relazionali. I primi, denominati #RDBMS (Relational DataBase Management System), sono organizzati a tabelle mentre i secondi, sono rappresentati da #oggetti e di norma sono più veloci dei primi.

Un comando impartito al database si chiama #query.
# Struttura dei dati
I dati possono essere strutturati per massimizzare la velocità in lettura o scrittura.
Per rendere un database #normalizzato bisogna rispettare i seguenti parametri:
- Vincolo di integrità referenziale: Attributo di una tabella che permette di collegare il campo con uno o più campi di un'altra tabella ( #foreign-key )
- #primary-key: non può essere nulla, dev'essere univoca
un database #normalizzato è più lento in scrittura, ma più veloce in lettura

## SQL
Tipologia di database più comunemente utilizzato per memorizzare i dati in maniera **strutturata** in gruppi (tabelle) di dati normalizzati (aventi attributi comuni, rappresentati dalle colonne). Di solito viene utilizzato per memorizzare numerosi dati di piccola dimensione (numeri, testi, date, o oggetti aventi proprietà in uno dei formati precedentemente elencati).
Tra i più comuni database relazionali di tipo SQL ci sono:
- [MySQL](./MySQL)
- [MariaDB](https://mariadb.com/kb/)
- [PostgreSQL](https://www.postgresql.org/)

## File storage

## Block storage
## Object storage
E' un metodo di memorizzazione dei dati di tipo **non strutturato** tramite l'[utilizzo di oggetti](https://cloud.google.com/learn/what-is-object-storage?hl=en). Ogni oggetto deve possedere 3 proprietà:
- **Dati**
- **Metadati**, ovvero le proprietà dell'oggetto 
- **Identificatore**

## NoSQL
Abbreviazione di *Not Only SQL* (ovvero non solo SQL), è un tipo di database non relazionale, che permette di registrare dati in formato coppia **chiave-valore** all'interno di un ambiente orizzontale (ovvero non suddiviso in gruppi come cartelle, ecc.).

# Manipolazione dei dati
Ci sono 4 tipologie di #query:
## DDL
## 


# Software per la visualizzazione
[TablePlus](https://tableplus.com/) è un software che permette di connettersi ad un database a fare operazioni su di esso

