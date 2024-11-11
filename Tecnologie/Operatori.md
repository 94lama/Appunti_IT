links: [[Php]] 
## #matematici 
- #addizione
- #sottrazione
- #moltiplicazione
- #divisione
- #modulo

## #confronto 
Restituiscono valori #booleani 
- Maggiore o uguale
- Minore o uguale
- Uguale
- Doppia uguaglianza
- Tripla uguaglianza
- Diverso

## Logici
- AND: restituisce true solo se entrambi gli operandi sono true
- OR: restituisce true se almeno uno dei due operandi è true
- NOT: restituisce true se il valore è false

Teorema di #Bohm-Jacopini: Qualsiasi problema può essere risolto tramite tre costrutti: 
	- #sequenza
	- #selezione
	- #iterazione

## #selezione (Cicli) 

- #if: effettua l'istruzione se la condizione è verificata
- #else-if : si concatena all' #if per inserire una variante avente anch'essa una condizione
- #else : parte finale del #ciclo if-else, che esegue un'istruzione nel caso tutte le selezioni precedenti abbiano dato come risultato false
- #switch: Verifica se la variabile rientra in una serie di opzioni ed in caso esegue l'istruzione relativa alla prima opzione che risulta true 
- #for: Esegue un'istruzione fino a quando il contatore impostato non rende vera la condizione
- #while: Esegue un'istruzione fino a quando il contatore impostato non rende vera la condizione
# Matematica booleana
## Somma booleana
Si effettua sostituendo la cifra 1 nel caso ci sia almeno un 1 tra i due valori e 0 nel caso non ci sia, ovvero:
```
1 + 0 = 1
0 + 1 = 1
0 + 0 = 0

Quindi
1100 +
0101 =
_______
1101
```

## Moltiplicazione booleana
Si effettua sostituendo la cifra 1 nel caso entrambi i valori siano 1 e 0 in tutti gli altri caso, ovvero:
```
1 + 0 = 0
0 + 1 = 0
0 + 0 = 0
1 + 1 = 1

Quindi
1100 +
0101 =
_______
0100
```