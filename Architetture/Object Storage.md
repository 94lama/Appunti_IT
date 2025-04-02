Per [Object Storage](https://cloud.google.com/learn/what-is-object-storage?hl=en) si intende un'architettura di memorizzazione di dati non strutturati, tramite creazione di [unità di dati](#Unità) (oggetti) e memorizzandoli in un ambiente dati non strutturato ([*storage pool*](#Pool)).

# Unità
Un'**unità** di dati è composta da:
 - Dati
 - Metadati
 - Identificativo univoco

## Metadati
I metadati vengono utilizzati per contenere informazioni da applicare al dato nello specifico ambiente. Alcuni esempi sono:
- Permessi
- Policies

# Pool
Lo storage pool consiste in un ambiente orizzontale (non strutturato, quindi in cartelle, blocchi o altro) e interagibile tramite API RESTful, HTTP, HTTPS). Questa particolarità è la principale differenza tra Object Storage, File Storage e Block Storage, che lo rende molto facile da scalare, ma lo rende meno indicato per dati molto dinamici