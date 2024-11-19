# Hash
Meccanismo di alterazione controllata dei dati, che consiste nell'applicare un algoritmo al dato stesso. Le caratteristiche principali dell'hasing sono:
- Univocità del risultato, in modo tale che dati simili diano risultati sempre diversi
- Ripetibilità del risultato, ovvero lo stesso dato sottoposto allo stesso algoritmo di has, deve dare sempre lo stesso risultato
- Controllo della dimensione del risultato

Nonostante teoricamente possano garantire l'assenza di modifica di un dato sia in casi accidentali, che intenzionali, è consigliato evitare di utilizzarlo come meccanismo di difesa per eventi appartenenti al secondo caso. 

## MD5
Algoritmo sviluppato da Ron Rivest, consistente in una funzione con risultato da 128-bit. L'algoritmo è da considerarsi come datato e da non usare, se non quando strettamente necessario.

## SHA-1
Sviluppato dalla [NSA](https://www.nsa.gov/), che genera un risultato di 160-bit, leggermente più lento del [[#MD5]].

## SHA-2
Sviluppato dalla [NSA](https://www.nsa.gov/) come evoluzione del [[#SHA-1]]. Genera un risultato di 256-bit

## SHA-3
Sviluppato dalla [NSA](https://www.nsa.gov/) come evoluzione del [[#SHA-2]], considerato come attuale standard di sicurezza per gli algoritmi di hashing. E' possibile ottenere un risultato di lunghezza:
- 224-bit
- 256-bit
- 384-bit
- 512-bit

# Crittografia
Gli algoritmi di criptazione servono a proteggere un messaggio, applicandogli un algoritmo per renderlo incomprensibile e utilizzare un secondo algoritmo per far tornare il messaggio criptato nella sua condizione originale.

Questo meccanismo sfrutta anche un elemento esterno, chiamato **chiave**, che conferisce un ulteriore valore di complessità alla cifratura nel caso non si sia in possesso dell'elemento. I protocolli di cifratura possono essere:
- Simmetrici quando si utilizza una chiave unica per cifrare e codificare il messaggio
- Asimmetrici, quando la chiave di criptazione è diversa da quella di decriptazione

## Simmetrica
La criptazione simmetrica utilizza chiavi corte (40-256 bit, ma per considerare una connessione sicura si consiglia di utilizzare una chiave di minio 128-bit) per fornire un meccanismo veloce di criptazione dei dati (viene spesso usata per cifrare i messaggi dei protocolli, come nelle [VPN](Reti.md#vpn)). Si basa sull'utilizzo di una chiave pre-condivisa per gestire la protezione dei dati.

### Block ciphers
I **cifrari a blocchi**  sono elementi utilizzati per scomporre il dato da cifrare (può essere un **plaintext** o un intero file)  e lo ricomporlo in un blocco di **ciphertext** (testo cifrato) da 128-bit. Il file risultante avrà un formato specifico (es. .7z)

#### 3DES
Utilizza il metodo [DES](#des) 3 volte consecutive per creare ogni blocco. Nonostante sia una miglioramento del DES, nel caso lo si voglia utilizzare, è preferibile farlo per dati aventi lunghezza di vita molto breve. Dal 2023 è deprecato.

#### AES
Advanced Encryption Standard, si basa sull'utilizzo di **ciphertext** da almeno 128-bit per proteggere i dati. Le dimensioni disponibili sono:
- 128-bit
- 192-bit
- 256-bit

#### DES
Simile all'[AES](#aes), ma utilizza blocchi di **ciphertext** da 64-bit. Considerato un metodo obsoleto.

#### RC4
Il Rivest Cipher 4 è un algoritmo di cifratura inventato nel 1987 e molto popolare fino a qualche anno fa quando, dopo aver trovato molte vulnerabilità, è da considerarsi obsoleto.

##### Algoritmo
[Fonte](https://it.wikipedia.org/wiki/RC4)

```pseudo-code
for i = 0 to 255
  S[i] = i
next
j = 0
for i = 0 to 255
  j = (j + S[i] + key[i mod keylength]) mod 256
  swap (S[i], S[j])
next
```
Una volta effettuato il passaggio precedente:
```pseudo-code
i = 0
j = 0
for l = 0 to len(input)
    i = (i + 1) mod 256
    j = (j + S[i]) mod 256
    swap (S[i], S[j])
    output[l] = S[(S[i] + S[j]) mod 256] XOR input[l]
next
```
### Stream cipher
Tramite questo metodo di cifratura, ogni singolo bit (o byte) del plaintext viene crittografato in un blocco a se stante. Questo consente una maggiore velocità del processo.

#### A5

#### SEAL
Metodo di criptazione dei dati più rapido tra le alternative con metodo simmetrico del [AES](#aes). Utilizza una chiave a 160-bit e ha un impatto contenuto sulla CPU comparato agli altri metodi.

## Asimmetrica
Utilizza due chiavi per gestire la criptazione e la decriptazione dei dati. Le chiavi sono più lunghe rispetto al metodo simmetrico (512 - 4096 bit), portando l'intero processo ad essere più lento, ma sicuro, in quanto è necessario l'uso di entrambe le chiavi per completare con successo l'algoritmo. Per questo di solito viene utilizzato per proteggere dati singoli, come dati di accesso bancari o per la firma digitale di file.

Negli algoritmi con chiave asimmetrica è possibile utilizzare entrambe le chiavi per cifrare il testo e la controparte per decriptarlo, rendendo possibili le comunicazioni da entrambe le parti. Di solito una delle due chiavi viene resa pubblica, mentre l'altra rimane al proprietario, permettendo una comunicazione sicura con chiunque voglia.

Nel caso la chiave privata risulti compromessa, è necessario creare una nuova coppia di chiavi.

- Confidenzialità per entrambi i lati
- Autenticazione tramite chiave privata
- Integrità da entrambi i lati

#### DH
Il Diffie-Helman è un algoritmo di cifratura che consente a due dispositivi tra loro sconosciuti di creare una chiave di criptazione concordata ed utilizzarla per stabilire una connessione sicura all'interno di una rete non protetta. 

La creazione della chiave avviene previo scambio di dati ottenuti tramite operazioni con numeri di grandi dimensioni (che costituiranno le rispettive chiavi private), che avviene in una connessione sicura (di solito [IPsec](Protocolli.md#ipsec) o [VPN](Reti.md#vpn)).
Una volta ricevuti i dati, questi vengono combinati con quelli inviati, in modo tale da ottenere una chiave condivisa uguale, senza averla di fatto comunicata.

L'assenza della necessità di dover condividere la chiave fornisce un ulteriore livello di sicurezza alla comunicazione.

Le chiavi utilizzabili sono da:
- 512-bit
- 768-bit
- 1024-bit
- 1536-bit
- 2048-bit
- 3072-bit
- 4096-bit

#### DSA
Il Digital Standard Algorithm è l'algoritmo di cifratura utilizzato come standard secondo la DSS (Standard di Firma Digitale). Permette di creare una chiave pubblica tramite lo schema di firme [ElGamal](#elgamal).
E' strutturalmente simile al [[#RSA]], ma consente di ottenere chiavi che richiedano dalle 10 alle 40 volte il tempo di verifica a parità di tempo utilizzato per creare la chiave.

#### ECC
Anche noto come Elliptic Curve Cryptography (curve di cifratura ellittica), è un algoritmo utilizzato per l'implementazione di più algoritmi di fila. Il vantaggio che offre è la possibilità di utilizzo di chiavi dalle dimensioni più ridotte.

DImensione chiavi:
- 224-bit o maggiore

#### ECDSA
L'Elliptic Curve Digital Signature Algorithm è una variante del [[#DSA]], che permette di fornire strumenti di autenticazione, non ripudio, efficienza computazionale e ridotte dimensioni del file cifrato.

#### ElGamal
Algoritmo di criptazione che si basa sullo scambio di chiavi tramite algoritmo [[#Diffie-Helman]]. Lo svantaggio di questo algoritmo è la grande dimensione dei file cifrati (circa il doppio del plaintext di partenza). Per questo motivo è consigliato l'utilizzo solo nel caso di messaggi brevi (es. scambio di chiavi segrete).

Lunghezza chiave:
512-bit
1024-bit

#### RSA
L'algoritmo di Rivest-Shamir-Adleman è uno dei primi algoritmi di criptazione e tuttora molto utilizzato. Si basa sull'utilizzo di numeri primi di grandi dimensioni per la creazione delle chiavi. E' tuttora considerato abbastanza sicuro, qualora vengano utilizzate chiavi abbastanza lunghe e venga utilizzato accoppiato alle ultime implemetnazioni.

## smistare
#### PFS
E' una proprietà di un protocollo di criptaggio, ovvero un sistema che definisce come, quando e dove deve essere utilizzato un algoritmo di #crittografia.
