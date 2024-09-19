# Introduzione
E' un linguaggio di programmazione #compilato (ovvero che gira in modo statico) ad #alto-livello, creato per funzionare su più dispositivi possibile e ottimizzare la memoria.

La possibilità di utilizzare Java su più dispositivi grazie alla Java Virtual Machine ( #jvm), ovvero una macchina virtuale che traduce il linguaggio nel linguaggio della specifica macchina su cui viene utilizzato (ogni macchina ha un suo specifico pacchetto di traduzione in #bytecode).

I file scritti in Java hanno estensione FileName.java e deve contenere una classe con lo stesso nome del file:
```
FileName.java
class FileName{
	public static void main(String[] args {})
}
```

# Classi
Almeno una classe deve avere un punto di entrata (ovvero un punto da cui far partire l'esecuzione). Il punto d'entrata è una funzione main().
- Le classi vanno dichiarate in #pascal-case

# Funzioni
Sono composte da 5 elementi:
1. keyword per la visibilità: public
2. keyword per l'occupazione di memoria: static, runtime
3. tipo di ritorno della funzione: void
4. nome della funzione ( #pascal-case, in inglese, parlante)

|Nome|Descrizione|
|-|-|
|public|visibilità pubblica|
|static|effettua il controllo a compile time|
|dynamic|effettua il controllo a runtime|
## Metodi
### main
```
public static void main(String[] args){
	System.out.println(x:"stringa da stampare"); //Libreria System, sistema interno out, metodo println, valore x
}
```
# Dati
La dichiarazione di dati viene effettuata utilizzando il #camel-case.
## Interi
|tipo|spazio|dimensione|
|-|-|-|
|long|8 B|+- 9 quantilioni|
|int|4 B| +- 2 miliardi|
|short|2 B|+- 32768|
|byte|1 B|+- 128|
## Float
|tipo|spazio|dimensione|
|-|-|-|
|float|4 B|7 cifre decimali|
|double|8 B|15 cifre decimali|

Nel caso si superi il dettaglio consentito, il programma arrotonderà il risultato.
## Literals
| tipo  | descrizione        |
| ----- | ------------------ |
| long  | 40000000000000000L |
| float | 0.52F              |
## Char
Definiti da **'**
## Array
Gli array sono collezioni di dati di un singolo tipo e a dimensione fissa.
```
int[] arrayName = new int[lunghezza]; //crea una nuova array di int
int[] arrayName = {1,2,3,4,5}; //metodo alternatio per dichiarare un'array
```
# Operatori logici

|simbolo|operatore|
|-|-|
|&|and|
# Casting
Il #casting è la conversione di tipo di un parametro. Si effettua se il valore viene tradotto da una tipologia che può essere riprodotta nella seconda (es. da da **byte** a **short**). Avviene se la seconda tipologia occupa uno spazio uguale o maggiore della prima.
## Esplicito
```
int number = 23;
double number = (double) number;
```
## Implicito
```
int number = 23;
double number = number;
```
# Type Inference
Presente dalla versione 10, permette di memorizzare dati senza la necessità di indicare la tipologia di dato.
```
var score = 10; 
```
# Oggetti
## Oggetti predefiniti
### String
Sono una sequenza di stringhe (caratteri UNICODE), delimitati dal simbolo **"**. In Java le stringhe sono rappresentate come oggetti immutabili (per modificarle bisogna salvare la nuova stringa in una nuova locazione di memoria).
- Per unire più stringhe, è possibile concatenarle tramite il simbolo **+**
#### Metodi
|Nome|Descrizione|
|-|-|
|length|Ritorna la lunghezza della stringa|
|substring(x, y)|Ritorna la stringa inclusa dal carattere x all'y (incluso x ed escluso y)|
|equals(x)|Verifica se la stringa è uguale ad x (case sensitive)|
|equalsIgnoreCase(x)|Verifica se la stringa è uguale ad x|
### Arrays
Classe che gestisce elementi di tipo array
#### Metodi
|Nome|Descrizione|
|-|-|
|copyOf(x)|Crea una copia dell'array x|
|equals(x)|Verifica se l'array è uguale ad x|
