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
# Manipolazione dei dati
Ci sono 4 tipologie di #query:
## DDL
## 

# Software per la visualizzazione
[TablePlus](https://tableplus.com/) è un software che permette di connettersi ad un database a fare operazioni su di esso

