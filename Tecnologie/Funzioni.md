E'  una porzione di codice riutilizzabile, che può essere chiamata in vari punti del nostro codice.
Ci sono due tipi di funzioni: #built-in, ovvero precostruite all'interno del linguaggio,  e #user-function, ovvero definite dall'utente.

	function nomeFunzione(parametri formali){
		istruzioni;
	};

Una funzione può contenere uno o più #parametri, che si definiscono #formali durante la dichiarazione della funzione, e #reali quando la funzione viene evocata.

La porzione di codice in cui è visibile una variabile si chiama #scope, che può essere #globale, se si trova all'esterno della funzione (e non è utilizzata come parametro), o #locale se si trova all'interno

## #callback
si usa quando si vuole passare una funzione come parametro di una seconda funzione

## Trasformazione di una serie di istruzioni in funzione
la #funzionalizzazione di una serie di istruzione avviene tramite 3 step: **estrapolazione** (1), **incapsulamento** (2) ed **astrazione** (3):

1. Uso il nome della variabile finale come nome della funzione
2. copio e incollo le istruzioni all'interno della funzione
3. Sostituisco le variabili con parametri formali parlanti
