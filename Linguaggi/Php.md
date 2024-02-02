# Links
-  [#Manual](https://www.php.net/manual/en/) 
### #framework 
- [[Laravel]] 
# Introduzione
La macchina per eseguire un programma in #JavaScript, #PhP  (o un qualsiasi altro linguaggio #interpretato), ne effettua la lettura, [[Traduzione]] ed  esecuzione. Il [[Protocollo di comunicazione]] tra due macchine avviene tramite messaggi di richiesta-risposta.

[[Php]] (Hyper-text Pre-Processor) è un linguaggio #interpretato, basato sul linguaggio [[C]] e scritto seguendo la metodologia [[Object-Oriented Program]], che permette di modificare un file #HTML, di scrivere stringhe di HTML al suo interno (e modificarle) e di interagire con i [[Database]].

La struttura esterna di un #codice #PhP è:
	<?php [linee di codice] ?>

Una #variabile è una [[Locazione di memoria]] che perette l'inserimento e la modifica di #dati. In PhP una variabile viene #dichiarata nel seguente modo:
	$variabile = 5;

Il linguaggio è case sensitive e per convenzione si usa la #snake_syntax (ovvero l'utilizzo dell'underscore tra le parole) per programmare.


# Terminale
PHP permette di realizzare programmi eseguibili anche da terminale.
- Eseguire un file .php all'interno del terminale:

		php file.php //esegue l'applicazione file.php
- Aprire un server locale con cui leggere il file php:

		  php -S localhost:8000

# [[Locazione di memoria]] #variabile
```
$variabile
$array = ("valore_1", 2, "valore_3");
$array_2 = ("key" => "value", "key_2" => "value_2")    //array associativo
```

- Nel caso di #stringhe, PhP può fare la #string_interpolation, ovvero l'inserimento di variabili all'interno di una stringa, solo nel caso vengano usate le virgolette (""). 
## Array
- Gli #array sono #0_based (il primo valore ha indice 0) e possono essere anche di tipo #associativo:
```
$array = ["key_1" => value_1, "key_2" => value_2];
$valore = $array["key_1"] //result: value_1
```
### #concatenazione
	Unisce due o più elementi di tipo stringa (se non sono di tipo stringa, vengono comunque considerati come tali) 
```
$variabile . $variabile_2
```
# [[Operatori]]
### #matematici 
In php i simboli degli operatori servono solo ad effettuare le operazioni. Quindi in questo linguaggio è possibile effettuare somme tra variabili int e char (che includano solo caratteri numerici).
 ```
$var + $var_2 // addizione. è anche possibile usare l'incrementatore ++
 $var - $var_2 // sottrazione 
 $var * $var_2 // moltiplicazione 
 $var / $var_2 // divisione 
 $var % $var_2 // modulo 

12 + "12" = 24;
10 + "12as3f" = 22 //L'operazione ritorna anche un messaggio di errore, dopodichè 11 (10+1)
12+"ads2" //Fatal error
```

### #confronto
	== //doppia ugualianza
	=== //tripla ugualianza
	>= //maggiore o uguale
	<= minore o uguale
	!= //diverso (previa conversione a stringa)
	!== // non identico

Restituiscono valori #booleani 

### #logici
	&& // #and 
	|| // #or

## #selezione 
ln tutti i casi, il comando #break interrompe il ciclo

### #if 
	if(condizione){istruzione}
	condizione ?? istruzione //forma concentrata del ternary operator

#### #else-if
	elseif(condizione){iterazione}

#### #else
	else{istruzione}

#### #switch 
	switch($variabile){
		case $variabile == condizione_1:
			istruzione_1;
			break;
		case $variabile == condizione_2:
			istruzione_2;
		default:
			istruzione_n;
		};

### #for
	for(contatore; condizione; incremento){
		istruzione;
	};

#### #while 
	while(condizione){
		istruzione;
	};

#### #foreach
Viene usato solamente per gli #array ed esegue un ciclo #for per ogni suo elemento

	foreach($array as $key => $value){
		istruzione;
	};
	
	foreach($array as &$value){
		istruzione;
	};
# [[Funzioni]]
E' possibile creare una #user-function  tramite il comando **function** (le funzioni in Php hanno solo #scope #locale):

	function nomeFunzione($var_1, $var_2){
		istruzioni;
		};

- Php crea una copia dei parametri dichiarati in una nuova locazione di memoria temporanea. Per evitare questo procedimento, si può anteporre il carattere **&** al parametro di cui non si voglia creare la copia temporanea.

		$var_1 = 5;
		$var_2 = 2;
		
		function sottrai(&$num_1, $num_2 = 0){ //inserendo $num_2 = 0, nel caso il parametro non venga dichiarato durante l'evocazione della funzione, sarà utilizzato il valore 0 di default
			$num_1 -= $num_2;
			};
	
		sottrai($var_1, var_2);
		echo $var_1 //Risultato: 3

- Come in [[JavaScript]], è possibile inserire un parametro di quantità variabile anteponendo **...** al nome della variabile:

		function nome_funzione(...$var){
			foreach($var as $key => $value){
				istruzioni;
			};
		};
- E' possibile effettuare un' #iterazione su una variabile tramite

		$var = 1;
		$var += 1; //Risultato: 2
		$var ++ //Ritorna var e ne incrementa il valore di 1
		++ $var //Incrementa il valore di var di 1 e ne ritorna il valore
		$var -- //Ritorna var e ne riduce il valore di 1
		-- $var //Decrementa il valore di var di 1 e ne ritorna il valore
## #callback

	function nome_funzione(...$nums){
		$variabile = array_reduce($nums, $callback)
	};

##  Funzioni #built-in

### #ctype
tipologie: - [ctype_​alnum](https://www.php.net/manual/en/function.ctype-alnum.php "ctype_​alnum"), [ctype_​alpha](https://www.php.net/manual/en/function.ctype-alpha.php "ctype_​alpha"), [ctype_​cntrl](https://www.php.net/manual/en/function.ctype-cntrl.php "ctype_​cntrl"), [ctype_​digit](https://www.php.net/manual/en/function.ctype-digit.php "ctype_​digit"), [ctype_​graph](https://www.php.net/manual/en/function.ctype-graph.php "ctype_​graph"), [ctype_​lower](https://www.php.net/manual/en/function.ctype-lower.php "ctype_​lower"), [ctype_​print](https://www.php.net/manual/en/function.ctype-print.php "ctype_​print"), [ctype_​punct](https://www.php.net/manual/en/function.ctype-punct.php "ctype_​punct"), [ctype_​space](https://www.php.net/manual/en/function.ctype-space.php "ctype_​space"), [ctype_​upper](https://www.php.net/manual/en/function.ctype-upper.php "ctype_​upper"), [ctype_​xdigit](https://www.php.net/manual/en/function.ctype-xdigit.php "ctype_​xdigit")
```
#ctype_upper - Controlla se una #stringa ha tutti i caratteri in #minuscolo 
```
### stampa 
Visualizza nella #console l'elemento desiderato.
```
echo $variabile    //converte il dato in stringa e lo stampa
var_dump($variabile)    //stampa il dato ed il tipo del dato e dei suoi eventuali figli
print_r($variabile)    //stampa il dato ed il tipo del dato
```
### count
Ritorna la #lunghezza della variabile #array o di un #oggetto #enumerabile
### implode
#unire i vari elementi di un' #array
### unset
#ripristina la #variabile scelta
### array_reduce
Applica il #callback a tutti gli elementi dell' #array, ritornando un singolo valore

	array_reduce(array $array, $callback, $initial = null)
### in_array(key->value)
vede se l'array include l'elemento selezionato
### strlen
Ritorna la #lunghezza della #stringa
### readline
Richiede un #input dall'utente, fornendo il parametro come messaggio inziale

### parse_url()
### Escaping
Per escaping si intende la rimozione di caratteri da una variabile. #Laravel effettua automaticamente l'escaping nel caso si utilizzi la sintassi di #Blade 
- **htmlspecialchars()** effettua l' #escaping dei caratteri speciali da una variabile
- **htmlentities()**
### `$_POST`

### `$_SERVER`
Oggetto predefinito che contiene dati sulla #sessione in corso:
- 'REMOTE_ADDR' - Indirizzo #ip del #client
### exec()
### shell_exec()
Esegue un comando nello **shell** del server
```
$output = shell_exec("ping -c 4" .$ip);
```
### system()
### pass_through()
### pcntl_exec()
```
pcntl_exec(string $path, array $args = [] $env_)
```
## [[Object-Oriented Program]]
### Introduzione
Php è un linguaggio (così come #JavaScript) che permette la programmazione in [OOP][Object-Oriented Program], ovvero di strutturare i codice in blocchi, che servono ad istanziare un nuovo oggetto. Questi blocchi prendono il nome di #classi.

```
class Object {
	public $attr_1; //definisco gli attributi rendednoli pubblici (altrimenti il programma ritorna un errore)
	public $attr_2;
	private $attr_3; //il comando private non permette l'accesso alla variabile se non dall'interno della classe stessa
	function __construct($valore){$this => attr_2 = $valore;} //il nome è definito dal linguaggio per default
	public function salute(){echo "Ciao, $this->$attri_1"}
};
$user = new Object("val_2"); //Quando inizializzo l'oggetto, richiamo automaticamente il metodo __construct
var_dump($user); //result: object(Object)#1 (3) {["attr_1"] -> NULL ["val_2"] -> valore ["attr_3"] -> NULL
$user->salute() //result: "Ciao, NULL"
```


La classe, che contiene al suo interno i vari attributi, viene costruita tramite il costruttore (funzione che valorizza gli attributi)
Per convenzione le #classi si creano in un file separato, utilizzando terminologia in **inglese**, con la parola al **singolare** e avente **prima lettera maiuscola**.

### Metodo / attributo #statico
Sono metodi o attributi di una classe richiamabili anche nel caso non si sia attribuita la classe ad un oggetto:

```
class Object {
	static public $count;
	static public function function_name(){
		echo "test";
	};
	public function count(){
		self:: $count ++; //self permette di richiamare un attributo della classe per ogni oggetto della classe (non riferita all'oggetto specifico)
	}
};
Object::print(); //result: "test"
echo Object::$count; //result: UNDEFINED (se $count = 0 -> result: 0)
$user = new Object;
echo Object::$coun; //result: 1
```

### Ereditarietà
L' #ereditarietà è la possibilità di una classe di ereditare la struttura (metodi e attributi) da un'altra classe (in Php solo una classe).
Nel caso metodi/attributi sono dipendenti da una o più variabili, essi devono essere richiamati anche nella definizione della classe ereditaria:

```
class User{
	public $user;
	public $password;
	public function construct($user, $pass){
		$this -> user = $user;
		$this -> password = $pass;
	};
	public function salute(){istruzioni;}; //il metodo viene ereditato automaticamente da Student
};
class Student extends User{
	public $subjects;
	public function __construct($username, $password, $subject){
		parent:: __construct($username, $password);
		$this -> subjects = $subject;
	};
};
$student = new Student("user", "password", "subjects");
```

Qualora un metodo o una proprietà vengano dichiarate sia nella classe ereditaria (figlia) che ereditata (genitore), la classe ereditaria avrà il nuovo metodo sovrascritto rispetto a quello precedente.
### Modificatori d'accesso
#### public
L'attributo può essere richiamato dall'esterno
#### protected
L'attributo può essere richiamato dalla classe stessa e dalle classi derivate
#### private
L'attributo può essere richiamato solo dalla classe stessa


### Astrazione
Una classe #astratta è una classe che rappresenta un concetto astratto e serve per stabilire le regole su come le classi figlie devono essere implementate.  La classe astratta non può successivamente essere istanziata.
```
abstract class Manichino{
	public $braccia;
	
	abstract public function funzione(){
		istruzioni;
	}
	
	public function __construct(Braccia $braccia){
		$this-> braccia = $braccia;
	}
}
```
E' possibile astrarre anche i metodi, che in questo caso avranno l'obbligo di essere dichiarati nelle funzioni figlie
```
abstract Sub_User extnds User{
	public function funzione(){  //nel caso non venga dichiarata, il programma ritorna un errore
		istruzioni;
	}
}
```
### Dependency injection
la #dependency-injection permette di far dipendere il funzionamento di una classe da un'altra classe.
```
class Braccio{
		public function nome_funzione(){
			echo "questa è una dependaency injection";
		}
	}
	$braccia = new Braccia();
	$oggetto = new Manichino($braccia); //Object composition
	$oggetto->braccia->nome_funzione() //result: "questa è una dependency injection"
```
### Tratti (traits)
Un #tratto è una porzione di codice non correlata a ciò che la classe rappresenta.
```
trait Nome_tratto{
	public function funzione_2(){
		echo "funzione numero 2";
	}
}
$oggetto->funzione_2; //result: "funzione numero 2"
```

### Object composition
L' #object-composition è la possibilità di creare proprietà di oggetti di tipo array.
```
class Object{
	public $var;
	public function __construct(...$var){
		$this->var = $var;
	}	
}
$object = Object("var_1", "var_2");
var_dump($object); //result: 
```
# Secure authentication
In PHP, per ovviare ad eventuali rischi di #broken-authentication, è necessario tenere a mente una serie di precauzioni:
- Utilizzo di sistemi di sicurezza aggiornati
- Autenticazione e gestione corretta delle #sessione 
- Implementare la rotazione del #session-id  e seguito di login riusciti
- Verificare la correttezza dell'autenticazione (non solo per gli aspetti funzionali dell'applicazione)
- Implementare una politica efficiente in materia di password
- Implementare la sicurezza del controllo degli accessi perimetrali
- Assicurarsi che anche le API implementino un controllo di sicurezza coerente
## [Broken OAuth]( #broken-oauth)
#oauth
### Scenari d'attacco
#### Reindirizzamento ad URI non sicuri
#### Controlli sulla mancanza di stato
Il protocollo usa un parametro di stato che funge da #csrf-token. Qualora non si usi questo metodo, il processo risulta vulnerabile a #csrf attack
#### Flusso di codice non sicuro
Senza un supporto da un server, è impossibile per un sito web memorizzare dati in modo sicuro
## Broken access control

# Librerie
## [Firebase JWT](https://github.com/firebase/php-jwt)
Permette di creare un #jwt
```
 composer require firebase/php-jwt
```
