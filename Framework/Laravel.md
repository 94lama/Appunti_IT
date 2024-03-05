# Introduzione
[Laravel](https://laravel.com/)è un #framekork (ovvero un'insieme di librerie) di [[Php]], che serve per gestire le richieste #http lato #server.

![[Pasted image 20230913102025.png]]

Laravel segue la logica del *Separation of concern*, ovvero ogni oggetto deve avere uno scopo ben specifico

{{pattern mvc}}
# View
### web.php
Il file web.php contiene le #Routes (rotte) del sito.
```
Route::get('/', function(){return view('home')})
Route::get('/', [PublicController::class, 'homepage']); //nel caso si usino i Controller
```
Nel caso si usi la seconda metodologia (consigliato), si deve anche inserire in cima al file la stringa:

  ```
use App\Http\Controllers\PublicControllers //si può anche fare click con il tasto destro del mouse nella classe presente nel metodo get e selezionare import class <-----(controllare)
```

Definisce cosa deve essere inviato al #client. 
{{view HTML}}
{{modello interazione con il database}}

# Controller
Serve a contenere la logica effettiva.
```
php artisan make:controller PublicController //crea un controller per la categoria Public del sito nella directory /app/Http/Controllers
```
Si devono creare almeno due controllers: uno per i file pubblici ed uno per quelli protetti. Si possono creare anche dei controller specifici per elementi che richiedono più azioni disponibili (es. get e post).

#patch - permette di modificare solo un elemento dell'oggetto ----------------------------

All'interno del file si possono ridefinire le funzioni di visualizzazione delle pagine:

	 ---
# Comandi da #terminale 
### [Composer](https://getcomposer.org/)
E' un gestore di pacchetti ( #package-manager ) per il linguaggio #PhP, La lista delle #librerie è indicata su **composer.json**  
### Artisan
I comandi sono da inserire nel #terminale con il prefisso "php" (es. php artisan serve).
Laravel lavora principalmente per #array #associativo 

|comando|azione|
|-|-|
|artisan|ritorna una lista dei comandi eseguibili da artisan|
|artisan serve|rende temporaneamente il nostro computer un server per far funzionare il sito|
|artisan make:elemento nomeElemento*|crea una componente da riutilizzare all'interno del progetto|
|artisan make:mail nome_della_mail|crea un prortotipo di mail, correlata ad un destinatario ed un messaggio|
|artisan migrate|effettuo le migrazioni per il database|
|artisan migrate:fresh|ricarica da zero tutte le ttabelle
|artisan migrate:rollback|torna alla situazione precedente all'ultimo comando lanciato|
|artisan migrate:status|controlla lo stato delle migrazioni|
|artisan migrate:stash|annulla le migrazioni effettuate|
|artisan route:list|permette di avere una lista di tutte le route disponibili nell'app|
|artisan optimize:clear|Pulisce la cache di Laravel|
|artisan tinker|permette di verificare dal terminal se gli elementi selezionati tramite php sono effettivamente relazionati al #database|  
|artisan db seed|crea un database di paretnza utilizzando i #seeders pre-impostati dall'utente|
|artisan migrate:fresh --seed|combina il "fresh" e il "db seed"|
|artisan route:list|mostra tutte le route dell'app|
|artisan make:middleware|crea un middleware (nel percorso /app/Http/Middleware)|
#### Elemento
Può essere:
- component
- view
- mail
- model
	- model -mc -  creerà automaticamente una migration ed un controller
	- model -mcr - migration, controller, resources
# Installazione

Scaricare Composermodel
```
composer global require laravel/installer
laravel new app_name
```
### Collegare il progetto a github
```
git init -b main
git add .
git commit -m 'Progetto inizializzato'
git remote add origin REMOTE-URL
git remote -v
git push origin main
```
### Collegare il progetto al #database 
1. aprire il file #nascosto  #env
2. inserire i dati:
	1. DB_CONNECTION
	2. DB_HOST
	3. DB_PORT
	4. DB_DATABASE 
	5. DB_USERNAME
	6. DB_PASSWORD
	**nota!** i dati non verranno pushati su #git 
#### Migrazioni
Le #migration sono dei file in cui viene definito come devono essere fatte le tabelle

|funzione|descrizione|
|-|-|
|up()|consente di definire i campi della singola tabella tramite la #dependency-injection del metodo Blueprint|

Per effettuare le migrazioni si usa il comando in bash:
```
artisan migrate
```
Le migrazioni, una volta create, vengono effettuate una volta sola (se si creano più file migrate il comando **migrate** lavora solo sui file che non sono ancora stati processati).
#### Memorizzazione
Per memorizzare i dati, abbiamo bisogno di:
- Un'area di input per recepire i dati (form)
- una funzione che elabori i dati e li invii al server
- una funzione che memorizzi i dati nel database

vd. [Invio di mail] ---collegare

Dopo aver ricevuto i dati dal #form, creo un #Model, che mi permetterà di trasformare le variabili #php in dati pronti per essere registrati nel database. Per popolare il Modello, basta creare una nuova istanza dello stesso all'interno del Controller da cui prendere i dati, e aggiungere le proprietà desiderate:

**Controller**
```
$nome_model = new NomeModel;
$nome_model->proprietà = $variabile_proprietà; //si può anche usare request(input->nome_input)
```

Per prendere i dati dal model, si usa il metodo **all()**:
```
$nome_model = NomeModel::all() //NomeModel ritorna il dato sotto forma di #collection
```
Una #collection è un'array di oggetti, su cui si può utilizzare una serie di [metodi statici](#metodo-statico) di Laravel.
la classe Model è gestita dalla libreria #Eloquent ORM (Object Relational Mapper).

##### Metodi
|nome|effetto|
|-|-|
|fillable|definisce le variabili che possono essere inserite nel Model (protected)|
|create|definisce un'array con i parametri che possono essere inseriti nel Model comparandoli con i fillable|
# Struttura
A parte la cartella #public, tutte le cartelle sono nascoste al client

|cartella|descrizione|
|-|-|
|app|contiene tutte le risposte alle richieste #http|
|public|l'unica cartella accessibile al browser|
|resurces|contiene tutto ciò che è relativo al front-end|
|views|contiene i file php (prevalentemente in linguaggio html) delle pagine da visualizzare**|
|routes|contiene i messaggi di #risposta alle richieste del #client|
|vendor|contiene tutte le librerie necessarie per Laravel|
** Nella cartella può anche essere inclusa una sottocartella chiamata **components**, che include le componenti HTML utilizzate (es. Head, Navbar, Footer). Le classe vanno create seguendo la metodologia delle [funzionalizzazione](Funzioni.md).
### /app
#### /HTTP
##### /Controllers
Sono presenti le varie classi dei controllers
### /resources
#### Descrizione
Contiene i file da implementare nel progetto (es. #css e #javascript. I file possono avere come contenuto la #direttiva **@import** dei file da importare. I file sono contenuti in cartelle nominate in base alla tipologia di file che contengono.
 
 	@import './bootstrap'; //css
	import 'bootstrap'; //js

Una volta importati, è possibile inserire i file nel progetto (in versione #minificata ) tramite #npm

	npm build dev

|cartella|
|-|
|/js|
|/css|

Contiene all'interno tutti i collegamenti per i file #CSS del progetto.

Contiene all'interno tutti i collegamenti per i file #JavaScript  del progetto. 
IMPORTANTE - Se si utilizza #npm, dopo aver preparato le librerie, si deve eseguire il comando

	npm run build //crea due nuovi file (css e js) minificati su public/build/assets

Successivamente, per far leggere i file ai documenti HTML, basta inserire nei file .blade.php il seguente codice

	@vite(['resources/css/app.css', 'resources/js/app.js']) //si possono anche aggiungere altri file da leggere

#### /views
##### /components
Contiene i componenti, richiamabili nelle viste tramite il comando

	<x-percorso 'valore'=$valore ></x-percprso>
dove **percorso** rappresenta il percorso della vista (all'interno della cartella components) da visualizzare, con **.** al posto di **/** (es. "nome_cartella.nome_vista")

### /vendor

|cartella|descrizione|
|---|---|
|.env|contiene il file di configurazione del progetto|
|.gitignore|file che contiene la lista delle cartelle che non deve essere inviata alla repository|
|composer.json|contiene la lista delle librerie utilizzate dal progetto|
|composer.lock|contiene  ---riprendere la lezione----|

### /models

##### Metodi predefiniti
| metodo | descrizione |
| ---- | ---- |
|  |  |
### /Providers
#### AppServiceProvider
Viene usata per condividere piccoli dati3
# #Comandi

### Classi

|classe|azione|
|---|---|
|Route::[metodo]|metodo statico - [get, push, put, delete]|

#### Route
Da utilizzare sul file **routes/web.php**

|metodo|azione|
|---|---|
|get([url], function (){return view([percorso file])}|rende temporaneamente il nostro computer un server per far funzionare il sito|
|view("URI", contenuto)|metodo di get(), che permette di ritornare la "vista" slezionata|
|compact("variabile")|Permette di utilzzare lo stesso nome sia per la variabile inviata che per quella ricevuta| 
|route('variabile')|ritorna l' #URI della rotta della variabile da web.php
|abort(errore)|metodo posto dopo il return, lancia l'errore specificato nel caso il return non si attivi (es. abort(404));|
|currentRouteName()|restituisce una stringa contenente il valore name() della route corrente|
|currentRoute()|restituisce l'oggetto della route corrente|

```
Route::get('/', function(){
	return view('homepage', $value as $key); //invia il file chiamato homepage.blade.php
})

Route::get('/', function(){
	return $element = [  //invia la variabile di tipo array $element
		'key' => $value,
	];
})
```
##### Rotta parametrica
```
Route::get('/URI/{parametro}', [class_name::class, 'metodo'])->name('metodo'.'parametri_da_inserire')
```
### Comandi con Blade
#### #direttiva
|metodo|azione|
|---|---|
|@dd($variabile)|stampa su schermo la variabile (se non è in HTML la ritornerà come testo|
|@foreach($array as $varaibile)|inizia a selezionare la parte di codice su cui applicare il ciclo|
|@endforeach|indica la chiusura della porzione di codice su cui applicare il ciclo|
|@import "file_da_importare"|importa il file_da_importare all'interno del file| 
|@vite(['resources/css/app.css', 'recources/js/app.js']) |prende i file presenti in public/build/assets e li inserisce all'interno del componente|
|@js($valore)|Rende la variabile leggibile anche da JavaScript|
|{{}}|Permette di inserire una variabile previo #escaping |
|{{!! !!}}|Permette di inserire una variabile senza escaping|

#### #componente
I componenti in #Blade vanno create su un nuovo file **nome_componente.blade.php**, dove sarà presente il codice da ripetere e la stringa posizionale **{{$slot}}** per indicare il punto in cui verrà inserito il codice della singola pagina su cui applicare il componente stesso.
Per inserire il componente nella pagina, basta contornare il codice con il #tag **x-nome_componente**. E' possibile creare anche un #tag-autoconcludente, ovvero un tag che possiede lo slash direttamente nel tag di apertura (ed. img).

E' possibile inserire molteplici variabili all'interno dei tag **x** tramite gli attributi
Nel caso l'attributo venga evocato, ma non richiamato nelle singole pagine #Blade, il programma ritornerà #errore. Per ovviare al problema, si può inserire il #coalescing-operator **?? "valore_default"** dopo la variabile. Nel caso si voglia richiamare un valore composto, sarà sufficiente anteporre **:** al nome dell'attributo, per poi dichiarare il nome della variabile da richiamare senza l'uso delle parentesi graffe:
 ```
<x-layout variabile="valore" ?? "" :variabile_composta="$valore_composto" /> //sovrascriverà la variabile "variabile" con il valore specificato
```
### Invio di mail
#### Creo una nuova pagina per il form di invio
1. creo una nuova route nella cartella /routes
2. creo il relativo controller su /app/http/controllers, dentro la quale la funzione di invio del messaggio dal form deve essere di tipo **Request** (classe preimpostata, da inserire tramite #dependency-injection  )
3. creo la pagina da visualizzare

#### Preparo il form
1. Creo un modulo di form base
2. il div form dovrà avere attributo **method="POST"** e **action={{route('email')}}**
3. aggiungo la direttiva **@csrf** (cross site request forgery), che aggiungerà un input nascosto contenente un token univoco che permetterà di sorpassare i filtri del server per le mail non pre-impostate
4. Per rendere i dati da inviare riconoscibili da Laravel, forniamo un attributo **name** con un valore univoco per tutti i campi che contengono valori da inviare (@csrf ha attributo nome preimpostato)
5. aggiunge la nuova route "email" in /routes/web.php

#### Preparo il messaggio da inviare
#### Configuro la mail da cui inviare il messaggio
Laravel non può inviare mail, deve quindi affidarsi a servizi di terzi (come [mailtrap](https://www.mailtrap.io) )
#### Invio la mail
1. creo una funzione per l'invio della mail su PublicController
2. Inserisco la classe per l'invio della mail
3. ritorno la pagina da visualizzare una volta inviata la mail e un alert per confermare l'invio della mail
```
return redirect() ->route('uri_da_visualizzare')->with('message', 'contennuto_del_messaggio');
```
Successivamente si inserisce nella pagina di ritorno un alert da visualizzare se il valore 'message' non sia vuoto:
```
@if(session()->has('message'))
	{alert({session('message')})};
@endif
```
#### Invio di file al server
Per inviare file al server bisogna aggiungere l'attributo 
 ```
ecntype="multipart/form-data"
```
Al form, per permettergli di convertirli in codice binario e di salvarli in /storage/app/public. Per decidere la cartella di memorizzazione, si usa il metodo **store**, con il quale si indica il percorso dove salvare il file (il cui valore sarà ritornato dal metodo store).
```
$img = $request->input('name')_>store('public/')
```
Per rendere la nuova cartella public, si può creare un #link tramite #artisan 
```
php artisan storage:link
```
così da poter avere una variabile *Storage::url($movie->img)*, da poter inserire come path del file. Nel caso non si inserisca nessun file, l'input avrà valore ***null***, il quale non permetterà di evocare il metodo Storage e ritornerà errore. Per ovviare al problema, si può usare un ciclo #if per fornire un valore di default nel caso non venga fornito dall'utente.
#### Richiesta di dati dal server
```
$item = ClassName::find($id) //trova l'elemento con l'id desiderato
```
### Validazione dei dati
1. Creare una richiesta tramite
```
php artisan make:request NomeRequest
```
2. Apro il file e creo un metodo rules
```
public rules():array{return ['parametro_1'=>'required|min:2|max:300']}
```
3. Sostituisco NomeRequest tramite #dependency-injection a nel metodo store() del Controller che gestisce gli elementi da inserire nel form (in questo modo nel caso di dati non accettati, il programma di default ricaricherà la pagina, azzerando tutti i campi)
```
public function store(NomeRequest $request)
```
4. Nel caso io voglia mostrare gli errori all'utente, devo aggiungere un metodo error() nel form (HTML) ed un metodo messages() alla classe che gestisce i dati del form
### #API
Sand tube, VIRT (view Inertial Laravel Tailwind)

### #CRUD - Create, Read, Update, Delete
1. Creo il #database
2. Mi connetto al db
3. Effettuo le #migration
4. creazione del #model che gestirà la il database
5. Gestione dei campi da inserire
#### Create
1. Creo il form in HTML su cui inserire i dati
2. Collego i vari input tramite attributo **name** al #Model
#### Read
1. Creo una rotta **nome_rotta.index**
2. Creo un metodo all'interno del Controller, che legge i file dal [db](#database) e li ritorna come variabile php

		$nome_variabile = $nome_database->all(); //oppure
		$nome_variabile = NomeModello::orderBy('parametro', 'desc/asc')->get(); //query builder

	Tramite #model-binding è possibile automatizzare la funzione di ricerca dell'oggetto nel database
#### Update
1. Creo una rotta ed un metodo che mi permettano di accedere alla vista del form di modifica dell'elemento
2. Digito le modifiche
3. Ricevo le modifiche tramite #dependency-injection  Request e le passo ad un secondo metodo che mi permette di inviare le modifiche al server e di ritornare ad una pagina del sito con le modifiche apportate

Nel **Controller**

	public function edit(Item $item){return view('form_modifica', compact('element'));} //metodo che porta alla pagina di modifica dell'elemento
	public function update(Request $$request, Item $item){
		$item->update('property' => $request->input('property')]); //aggiorno il database
		return to_route('rotta') //ritorno alla vista deisderata
	}
Su **web.php**

	Route::get('/{item}/edit', [ItemController::class, 'edit'])->name('item.edit');
	Route::put('/updated/{item}', [ItemController::class, 'update', 'movie'])->name('index.update');
#### Delete

### #seeders - database/seeders
Sono comodi per avere dei dati di default nel database (anche nel caso di utilizzo di **artisan migrate:fresh**) in fase di test

### Factories
Permettono di popolare automaticamente le tabelle con contenuti composti da 
- #### valori decisi da noi

		'valore'=>valore,
- #### valori scelti da un'array

		$array = ['valore1', 'valore2', 'valore3'];
		foreach($array as $valore){
			Model::create(['valore'=>$valore]);
		};
- #### valori casuali

		dasd
	
# Librerie
## [Fortify](https://laravel.com/docs/10.x/fortify#:~:text=Laravel%20Fortify%20is%20a%20frontend,%2C%20email%20verification%2C%20and%20more.) - Autenticazione
Laravel #Fortify ci permette di lavorare con le autenticazioni e la creazione di account
#### Installazione
1. Si digita il comando in bash
```
composer require laravel/fortify
php artisan vendor:publish --provider="Laravel\Fortify\FortifyServiceProvider"
```
	Il comando copierà dei file da vendor/ nella cartella principale del progetto
	- Actions/Fortify/ - si trovano le categorie di validazione
	- providers/
	- -
2. E' necessario effettuare una migrazione
```
php artisan migrate
```
3. Si apre il file **config/app.php** e si inserisce la stringa

```
App\Providers\FortifyServiceProvider::class,
```
	all'interno della sezione **providers**. Ciò permetterà di aggiungere i metodi di Fortify nel nostro progetto, ovvero **register()** e **boot()** (boot si attiverà all'apertura dell'app)
4. Ora possiamo accedere alle funzioni di autenticazione, registrazione
##### Registrazione
1. Aprire **AppServiceProvider.php** e aggiungere a boot il metodo 
```
Fortify::registerView(function(){return view('auth.register');});
Fortify::loginView(function(){return view('auth.login');});
```
2. Creo un file **register.blade.php** all'interno di **auth/**, che conterrà il form di registrazone
--------- SE NON SONO LOGGATO AUTH::USER=null -------------------------
@auth / @endauth == @if(Auth::user!=null) / @endif
@guest / @endguest == @if(Auth::user == null) / @endif
Laravel cripta in SHA1
## [LiveWire](https://laravel-livewire.com/)
#live-wire è una libreria #full-stack di Laravel, ideta da Caleb Porzio per realizzare piattaforme reattive, basate su [interazioni]( #interazione), ovvero l'attivazione di funzioni in base ad attività effettuate dall'utente (es. click), gestite da [[JavaScript]].
Una delle principali differenze tra Laravel e LiveWire è che il primo si basa sulle #Routes, mentre il secondo sui [componenti](#compoente). L'assenza di Routes è permessa dal [routing implicito](routing-implicito).
**La versione 2.x richiedeva di iinserire all'interno dell'app.blade
```
@livewirestyles
```
#### Componente
Il #componente è costituito da un file HTML/Blade e una classe PHP/Laravel. Classe e pagina sono strettamente correlati 

- Si installa con il comando
```
composer require livewire/livewire 
```
- la creazione può essere effettuata tramite
```
php artisan make:Livewire nome_componente
```
- può essere importato nelle pagine web tramite
```
<livewire:nome_componente /> //attiva la funzione quando viene lanciato l'evento
<livewire:nome_componente.live /> //attiva la funzione ogni volta che avviene un evento nel componente
```
- Le direttive possono essere inserite come funzioni nel componente e richiamate su Blade tramite

	<tag wire:evento="nome_funzione" />
- Le locazioni di memoria sono visibili nella console del #developer-tools, tramite comando 
```
Livewire.all())
```
- ##### Stato
	- L'insieme dei valori di tutti gli attributi in un dato momento si chiama #stato
	- Il periodo di tempo che va dalla renderizzazione del componente al ricaricamento della pagina (o di una nuova pagina), si chiama #life-cycle
- Nel form per impedire il ricaricamento della pagina
```
<form wire:submit.prevent="store" > //su livewire 2
<form wire:submit="store" > //da livewire 3
```
	- Nel caso si vogliano resettare i campi dopo l'invio, basta aggiungere nel #componente LiveWire
```
$this->reset();
```

|Metodo Livewire|Descrizione|
|-|-|
|mount()|inizializza le proprietà del componente ogni volta che viene chiamato|
|reset()|resetta i campi del form|
|render($elemento)|renderizza solo l'elemento selezionato, senza dover ricaricare la pagina|
|validateOnly()|Permette di validare solo il campo selezionato|
|pluck('colonna')|trasforma una collection in un array della colonna selezionata|
|slug('key_space_substitute')|effettua lo #slug dell'elemento selezionato|

- In Livewire 2  
#### Metodi wire:
|Metodo|descrizione|
|-|-|
|navigate|Permette di collegare una route ad un componente (es. per single-page web-app)|
|dispatch||

## MessageBox

attributes (#)

	#[on(nome_metodo)] 
## [TNT-search](https://github.com/teamtnt/laravel-scout-tntsearch-driver) - Ricerca parole
#### Installazione
- Terminal

		composer require laravel/scout
		php artisan vendor:publish --provider="Laravel\Scout\ScoutServiceProvider"
		composer require teamtnt/laravel-scout-tntsearch-driver
- config/app.php

		'providers' => [
		TeamTNT\Scout\TNTSearchScoutServiceProvider::class,
		],
- FrontController
- .env

		SCOUT_DRIVER=tntsearch

##### POSSIBILI ERRORI
Controllo:

	php artisan scout:status
- Non legge i dati

		php artisan scout:flush "App\Models\announcement"
		php artisan scout:import "App\Models\announcement"
## [Socialite](https://laravel.com/docs/10.x/socialite)
#socialite è un pacchetto proprietario che permette l'autenticazione tramite #oauth con Facebook, Twitter, LinkedIn, Google, GitHub, GitLab, BitBucket, Slack.
### Installazione
```
composer require laravel/socialite
```
### Configurazione client
```
'github' => [
'client_id' => env('GITHUB_CLIENT_ID'),
'client_secret' => env('GITHUB_CLIENT_SECRET'),
'redirect' => 'http://example.com/callback-url',
],
```

# Middleware
Laravel include un metodo per creare un #middleware all'interno della classe **Route** 

|middleware|descrizione|
|-|-|
|Auth::|Vede se l'utente è autenticato|

Una volta creato un Middleware (tramite #artisan), aggiorno la lista dei #middleware su Kernel (app/Http/Middleware) nella proprietà **$middlewareAliases**
# #Eloquent #ORM 
Laravel gestisce le interazione con il #database tramite la libreria Eloquent ORM (Object-Relational Mapper).
## [[Relazioni]]
### #1-n 
1. Aggiunta di una colonna per la #foreign-key (FK)
```
php artisan make:
```
2. Aggiungo al metodo **up()** della #migration un vincolo di integrità referenziale
```
$table->unsignedBigInteger('user_id')->after('id')->default(1) //il metodo after si usa se si vuole specificare la posizione nella tabella
$table->foreign('user_id')->references('id')->on('users');
```
3. Aggiungo al metodo down() della stessa #migration per gestire l'eliminazione del dato dalle tabelle
```
$table->drop('user_id')
$table->
```
4. Aggiorno i #fillable e il metodo #create del Model 
5. Effettuo la migrazione
```
php artisan migrate
```
#### Lettura della #foreign-key
1. Apro il modello di riferimento
2. creo una funzione con il nome della tabella  originale della [FK]( #foreign-key )
	1. La #foreign-key collega il dato a più elementi
```
public function table_names(){return $this->hasMany(ModelName::class);} //nel caso di relazione 1-1, non si usa il metodo hasMany
```
	1. La #foreign-key collega il dato ad un solo elemento
```
public function table_name(){return $this->belongsTo(ModelName::class);}
```
1. Per richiamare l'elemento indicato dalla #foreign-key (l'intero oggetto), basta utilizzare il metodo table_name/table_names come fosse una proprietà (ovvero senza parentesi).
2. Aggiorno le #migration, #request, #Model e #Controller, in modo tale da avere la #foreign-key indicata in maniera corretta
	Nel caso il progetto sia già online, è consigliato creare una nuova migration tramite
	1. Terminal
```
php artisan makemigration add_nome-tabella_chiave_to_nome-tabella_table.php
```
		2. Nel nuovo file
```
public function up():void{ //void viene utilizzato quando la funzione non ritorna alcun valore
	Schema::table('nome_tabella', function (Blueprint $table){
		$table->unsignedBigInteger('director_id');
		$table->foreign('tabella_chiave')->references('chiave')->on('tabella')
	})
}
```
1. Implemento nel #Model un metodo che colleghi la #foreign-key alla tabella di riferimento
2. aggiungere eventuale #input nel form e coppia key=>value
### #n-n 
Per modellare le relazioni n-n, si usa una tabella intermedia, detta #tabella-pivot,  dove ogni riga rappresenterà la singola relazione tra gli oggetti, rappresentati dalle #foreign-key.

La tabella si chiamerà automaticamente **tabella1_tabella2**
All'interno della #migration, si potranno inserire le #foreign-key nel seguente modo

Dal terminale
```
php artisan make:migration create_table1_table2_table 
```
Nella migration appena creata

 ```
$table->foreignId('table1_id')->constrained(); //crea automaticamente la colonna ed il vincolo relativo
$table->foreignId('table2_id')->constrained();
```
#### Convenzioni
##### #migration
- Il comando #artisan per creare la tabella deve contenere la parola chiave **create**
- Entrambi i nomi delle tabelle coinvolte al singolare in ordine alfabetico
- Terminare il nome con la parola **table** 
- I valori da inserire corrispondono alle #foreign-key 

##### #Model 
- I nomi delle tabelle sono indiati al plurale
```
public function tables2 () {return $this->belongsToMany(Model_2::class);} //La funzione si inserisce in entrambi i modelli
```
##### #HTML 
- Devo indicare nell'attributo **name** il valore come #array
```
<input action="nome_parametro[]" />
```
##### #Controller

	$
# Clonare un progetto Laravel
1. Clonare il progetto da GitHub
	Su [[Github]] vengono pushati tutti i file, tranne quelli elencati su .gitignore, ciò vuol dire che sarebbe impossibile clonare il file correttamente su un secondo computer.
	
		git clone
 2. Si installa Composer
	Si sfrutta il file composer.json con il seguente comando sul terminale:

		composer install (oppure "composer update" per ottenere la versione aggiornata delle librerie)

per poi aggiornare il file nascosto #env (anch'esso non pushato in automatico da #git) tramite il terminale:

	cp .env.example .nuove_nome (di solito .env)
	php artisan key:generate  (per impostare la key univoca del progetto)
	
# #plugin utili in Visual Studio
- Laravel Snippets
- Laravel Blade formatter
- Laravel Blade Snippets
- PHP Namespace Resolver (by Mehedi Hassan)
- Bootstrap Intellisense
# [Messa online]( #online)
Un #server è una macchina dotata di almeno una scheda di memoria, una #RAM, e un #processore, dotato di un programma di gestione delle richieste #http.

Mettere online un progetto significa inserire all'interno di questa macchina l'app. I server hanno molteplici macchine, aventi potenze di calcolo diverse (spesso selezionabili tramite servizi in abbonamento).

### Programmi di gestione per le richieste #http 
Sono suddivisi in due #stack: LAMP e LEMP
#### LAMP
L = Linux
A = [Apache](https://httpd.apache.org/)
M = [[MySQL]]
P = [[Php]] (utile perchè è un linguaggio lato server)
#### LEMP
L = Linux
E = [NGINX](https://www.nginx.com/) (enginext)
M = [[MySQL]]
P = [[Php]]

#### [Forge](https://forge.laravel.com/)
Permette di gestire i server, collegandosi ad una piattaforma di gestione del #server (es. [DigitalOcean](https://www.digitalocean.com/))
Per creare sito saranno necessari alcuni dati:
- Root Domain (in questo caso nome_gruppoh89.demohackademy.it)
- Project Type (nel nostro caso PHP/Laravel/Synphony)
- Aliases (nel nostro caso rimane vuoto)
- Web Directory (nel nostro caso /public)
- PHP Version
- Database Name (nel nostro caso nome_gruppoh89)
Per indicare il progetto da lanciare a Forge, è possibile collegare una #repository di [[Github]], inserendo anche il #branch da cui recuperare i dati
##### Deployments
Contiene la voce **Deployment Scripts**, ovvero un'insieme di #script che Forge eseguirà ogni volta che viene modificato il progetto

	cd/percorso_progetto
	git pull origin SFORGE_SITE_BRANCH
	
	// $FORGE_PHP artisan serve
	npm run build

	(flock -w 10 9 || exit 1
		echo 'Restarting FPM...'; sudo -S service $FORGE_PHP_FPM reload) 9>/tmp/fpmlock
	if [ -f artisan ]; then
		$FORGE_PHP artisan migrate --force //il force viene usato per 
	fi
##### Site Environment
Contiene il file .env da inserire all'interno del server (preso da .env.example), denominato **Deployment Script**

	APP_ENV=production //indica lo stato dell'applicazione
	APP_DEBUG=false //se true mostra l'errore, se false mostra l'errore 500
Se si clicca su **Deploy Now** il server esegue gli script indicati nel **Deployment Script**

- E' possibile avviare i deploy da remoto tramite link fornito da Forge 
##### Commands
Contiene un terminal per eseguire dei comandi da eseguire *una tantum*. Alla prima messa online del sito, si devono lanciare i seguenti comandi

	npm i //$FORGE_NPM i
 	$FORGE_COMPOSER install
	$FORGE_PHP artisan key:generate
	$FORGE_PHP artisan storage:link

E' possibile entrare nel server anche da #git-bash
##### SSL
Se si clicca su **Obtain Certicifate**, Forge genera automaticamente un certificato #ssh, per rendere il protocollo **https**

# [[Cybersecurity]]
## CVE
### 2021-3129 - #remote-code-execution
Ignition, prima della versione 2.5.2, permetteva ad un attaccante di eseguire codice arbitrario all'interno del programma tramite i comandi **file_put_content()** e **file_get_content()** se il sito web è in #debug-mode.
La debug mode permetteva agli utenti di sfruttare una variabile non dichiarata per inserire del codice malevolo all'interno del #log.
L'attacco avviene tramite un file **.phar** (PHP ARchive) #phar-deserialization-vulnerability e consiste nell'inserire un file phar all'interno del server che, una volta attivato, crea e apre un file php, tramite file_get_contents("<link del file php>") che permette di inserire dati all'interno del #log
#### Note
- file_put_content() inserisce un file
- file_get_content() legge un file

# Altro
## Policies
## Open-AI e Chat-GPT
### Reti neurali
Una #rete-neurale è un modello matematico predittivo, il cui funzionamento è bassato sul cervello umano. 
### Prompt design
Branca che studia le metodologie di input per effettuare richieste ad una #intelligenza-artificiale.
#### Peso dei comandi
```Midjourney
::<valore> # create an explosion::2 in a city::6
```

## Gate
Sono delle funzioni che determinano se un utente è autorizzato o meno ad effettuare una determinata azione. Ricevono come primo parametro il nome del gate, seguito da la funzione da eseguire ogni volta che il Gate viene evocato
**File: AuthServiceProvider.php**
```
use App\Models\Post;
use App\Models\User;
use Illuminate\Support\Facades\Gate;

// Register any authentication / authorization services.

public function boot(): void
{
Gate::define('update-post', function (User $user, Post $post) {
return $user->id === $post->user_id;
});
}
```
