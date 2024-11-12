# Bare-metal
Hypervisor di tipo 1 che non necessita di un #OS alla base. Offre performance maggiori, grazie al minore carico di utilizzo.
# Hosted
Hypervisor di tipo 2, che si appoggia su un sistema operativo (es. [Hyper-V](Windows.md#Hyper-V))

## Virtual machine
Utilizzo di un Hypervisor per connettere il sistema operativo virtualizzato all'infrastruttura hardware.
## Container
Utilizzo di un apposito Container Engine, ovvero un software che permette di collegare uno o più container (ognuno dei quali rappresenta una macchina a se stante) al Sistema Operativo in uso. [Docker](./software/Docker) è l'esempio più famoso di software per containerizzazione.

# Software di virtualizzazione

## [VirtualBox](**https://www.virtualbox.org/**)
Software di [virtualizzazione di tipo 2](#hosted) open-source prodotto da Oracle
### Nuovo
Ci sono due possibili metodi per creare un nuovo ambiente virtuale:
- Scaricare un file ISO da cui prendere i settaggi
- Selezionare Tipo e Versione del #OS da installare (il software prende in automatico tipo e versione dal Nome, se combacia con una versione)
Dopodichè verrà richiesta la quantità di risorse da allocare alla macchina virtuale (sarà possibile modificarli)
### Impostazioni
#### Generale
#### Sistema
Da qua è possibile  modificare le risorse allocate alla macchina virtuale
#### Archiviazione
Si possono scegliere le immagini di base ( #iso), da utilizzare come base della macchina virtuale.
1. Cliccare sul disco blu
2. Selezionare Scegli/crea un disco ottico virtuale
3.  Cliccare su Aggiungi
4. Selezionare il file desiderato
5. Cliccare su Scegli per finalizzare la scelta

### Linux
#### [Debian](**https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/**)
Settaggi consigliati:
2048Mb
1 CPU
- Disco fisso virtuale: 30GB
##### Installazione
Cliccare sullo schermo (o premere ctrl (Destro))
- Graphical install: Tipologia user-friendly
###### Software selection
Debian desktop environment, GNOME e standard system utilities sono i software indispensabili per utilizzare Debian
###### GRUB Boot loader
Permette di 



## VMwareWorkstation

# Alternative
## VDI
La Virtual Desktop Interface è una tipologia alternativa di virtualizzazione di una macchina. Non rientra in nessuna delle due versioni precedenti in quanto il Sistema Operativo è effettivamente installato in un server (può essere virtualizzato) ed è reso disponibile all'utente tramite l'utilizzo di Software appositi, o piattaforme web (come [AWS](../server/aws)).

# Security
I problemi di sicurezza relativi l'utilizzo di macchine virtuali possono essere:
- VM sprawl: quando l'utilizzo di molte macchine virtuali comporta un'uso eccessivo di spazio rispetto al necessario