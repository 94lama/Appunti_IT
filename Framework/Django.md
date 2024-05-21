# Introduzione
[Django](https://www.djangoproject.com/) un #framework di  [[Python]] per gestire il #back-end di applicazioni #web

# Installazione
Si può installare Django sulla macchina da #terminale, tramite 
```sh
python -m pip install -e django/ 
```
	WINDOWS:
	py -m pip install -e django\
Da qui in poi sarà possibile avviare un progetto in Dhjango tramite il comando
```sh
django-admin startproject <project_name>
```
	django-admin permette di inizializzare un progetto con annessa un'area di controllo dedicata per l'admin
	user: admin password: admin

# Comandi
I comandi, scritti in [[Python]], possono essere eseguiti anche da #terminale anteponendo il comando ```python```, ad esempio: 
```
python manage.py runserver
``` 
## Avviare il server
```python
manage.py runserver
```
	Per uscire dal server premere Ctrl+C
## Aggiungere una nuova funzionalità
Ogni #feature ha una #directory dedicata, la cui creazione è automatizzata tramite comando
```python
manage.py startapp <nome_funzionalità>
```
### settings.py
Andare poi su **settings.py** ed aggiungere la directory su INSTALLED_APPS:
```settings.py
INSTALLED_APPS = [
...
"<nome_funzionalità>.apps.<NomeFunzionalita>Config",
]
```
	la classe <NomeFunzioanlita>Config viene creato automaticamente
### views.py
Aggiungere la vista in ```<nome_progetto>/views.py```. Se la funzionalità è strutturata:
```python
from django.urls import include, path

urlpatterns = [
	...
	path("<nome_funzionalita>/", include("<nome_funzionalita>.urls"))
]
```
Se è semplice, invece:
```python
import <nome_funzionalita>.views as nome_funzionalita_view

urlpatterns = [
	path(path("<nome_funzionalita>/", nome_funzionalita_view.index)
]
```
### urls.py
Contiene tutte le #Routes del modulo. E' possibile creare delle rotte parametriche tramite il [[RegEx]], tramite il modulo **re_path**.
```urls.py
from django.urls import path, re_path
from . import views

urlpatterna = [
	path ('', views.index, name="index"),
	path('sub-route/<int:parameter>/'),
	re_path(r"^parametric/", views.parametric_route)
]
```
	path: si utilizza più comunemente per le rotte. Nel caso di rotte parametriche si segue l'esempio di sub-route. Le variabili possono essere:
		- int
		- slug
	re_path: si utiliza nel caso di rotte parametriche per cui è necessario utilizzare RegEx
### models.py
Creare una nuova classe basata su ```django.db.models.Model``` e definirne la struttura.
Esempio
# Struttura
Una volta inizializzato il progetto, verrà creata automaticamente un file ```manage.py``` ed una cartella avente il nome del progetto:
```Progetto
project_name
├ project_name
|	├ __init__.py
|	├ settings.py
|	├ urls.py
|	├ asgi.py
|	├ wsgi.py
|	└ nome_feature
|		├ migrations
|		├ __init__.py
|		├ admin.py
|		├ apps.py
|		├ models.py
|		├ tests.py
|		├ views.py
|		└ urls.py
├ manage.py
└ db.sqlite3 # Se il progetto utilizza mysqlite per gestire il #database
```

# Librerie
Ogni libreria in Django viene rappresentata da un #modulo.
## built-in
### Django-admin
Permette di creare un #admin ed una pagina di controllo dedicata. L'admin avrà permessi da #superuser 
```sh
python manage.py createsuperuser
```
	Il terminale chiedera' di inserire dati aggiuntivi:
	Username: <username>
	Email: <email>
	Password: <password>
	Confirm password: <password>
