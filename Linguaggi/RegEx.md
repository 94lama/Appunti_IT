RegEx è un linguaggio utilizzato per comparare elementi di testo con specifici parametri. I parametri sono definiti tramite **espressioni**. Un valido strumento per validare le espressioni scritte in RegEx è [regexr.com](https://regexr.com/)

# Caratteri speciali
Le espressioni possono essere corredate da determinati caratteri, che permettono di coprire un più ampio spettro di casistiche tramite l'uso di una singola espressione. 

| Carattere | Descrizione                                                                                           |
| --------- | ----------------------------------------------------------------------------------------------------- |
| .         | Ogni singolo carattere                                                                                |
| *         | Il carattere precedente può essere presente da zero a più volte                                       |
| \|        | E' presente il carattere precedente o quello successivo                                               |
| \[  \]    | Include una lista o un range di caratteri da verificare                                               |
| (  )      | Delimita una sezione                                                                                  |
| ?         | Il carattere precedente può essere incluso una volta o non incluso                                    |
| +         | Il carattere precedente è presente almeno una volta                                                   |
| ^         | Inizio della riga (se inserito all'inizio dell'espressione)                                           |
| $         | Fine della riga (se inserito alla fine dell'espressione)                                              |
| \         | Il simbolo successivo è un semplice simbolo, che non verrà utilizzato per le espressioni di cui sopra |

# Utilizzo nei framework
## [[Django]]
In Django, nel caso si utilizzi il metodo **re_path**, si devono porre alcune attenzioni al modo in cui si scrive la stringa RegEx [link](https://www.webforefront.com/django/regexpdjangourls.html).
