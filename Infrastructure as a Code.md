Metodologia nata con l'avvento del cloud hosting per 3 motivi principali:
# Environment Drift
Ovvero cambio di #environment 
# Consistency

# Idempotenza
# Tipologia di infrastruttura
## Muteveole
Permette di applicare in tempo reale le modifiche apportate al codice.
## Immutevole
Crea un nuovo sistema, andando ad eliminare il modello precedente ogni volta che il codice viene modificato.
# Approccio
## Imperativo
Si definisce il metodo di creazione dell'output.
## Dichiarativo
Si definisce il risultato da ottenere, senza considerare il metodo. Permette un maggior controllo del flusso (e richiede una maggiore conoscenza della composizione della struttura). E' da preferire all'[approccio imperativo](#Imperativo).
# Software
## [[Terraform]]
Sistema di configurazione dell'infrastruttura in cloud.
## [Ansible](https://www.ansible.com/)
Serve per configurare il sistema
## [NixOs]
Sfrutta un approccio funzionale
## [Chef]
