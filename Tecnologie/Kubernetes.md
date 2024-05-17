[Documentazione](https://kubernetes.io/it/docs/concepts/overview/what-is-kubernetes/) 
# Introduzione
Kubernetes è un software per l'orchestrazione, la gestione e il coordinamento automatico dei sistemi informativi, di solito utilizzato come complementare di [Docker.
Funziona tramite [#Kubelet] e [#Pod]
# Kubelet
Rappresenta l'area operativa di Kubernetes (di solito è sovrapponibile all'intero progetto in [Docker])
## Environment
### Green
Contiene tutti gli aggiornamenti da testare, rilasciare o in fase di sviluppo. L'accesso avviene solo tramite rete locale
### Blue
Contiene l'applicazione ufficiale, con accesso aperto al pubblico.
### Deploy
E' possibile effettuare sia il #rollout (la pubblicazione di una nuova versione del software), che il #rollback (ovvero la pubblicazione di una versione precedente del software)
### Self-healing
Kubernetes riavvia i container di [[Docker]] che si bloccano, sostituisce i container e termina quelli che non rispondono agli #health-check
# Pod
Rappresenta un singolo nodo all'interno della [#Kubelet]
# [[Cybersecurity]]
Kubernetes possiede più di 90 certificazioni .
Il software permette di
- Memorizzare e gestire informazioni sensibili (password, token OAuth, chiavi SSH)