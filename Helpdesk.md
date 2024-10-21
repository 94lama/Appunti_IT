Si occupa di gestire e risolvere ticket. Deve every conoscenze dei vari sistemi operativi principali ([Windows](/OS/Windows), [linux](/os/linux), software [Cisco](/os/cisco)).

Essendo un lavoro effettuabile anche in remoto (o per clienti che lavorano in remoto), è importante padroneggiare bene la CLI e i concetti di rete [VPN](/tecnologie/reti#vpn) del sistema operativo di riferimento e dei tool di accesso remoto alle macchine:
- Microsoft Remote Desktop (richiede Windows pro)
- Apple Remote Desktop (utilizzabile solo tra dispositivi Apple)
- TeamViewer
- Zoho Assist

Nel caso il dispositivo del cliente abbia installato un server SSH con OpenSSH attivo, è possibile accedere al terminale anche tramite shell e protocollo SSH (o Telnet, sebbene quest’ultimo sia sconsigliato per motivi di sicurezza).
Per dispositivi Windows è presente anche il protocollo Remote Desktop Protocol (RDP), attivabile dalle Impostazioni.

# Troubleshooting
1. Definire il problema
2. Raccogliere informazioni
3. Analizzare le informazioni
4. Scartare alcune possibili cause
5. Testare le ipotesi
6. Risolvere il problema
7. Documentare

## Metodologie
- Bottom-up: dal livello 1 Fisico as 7 Applicazione
- Top-down: dal livello 7 Applicazione all’1 Fisico
- Divide-and-conquer: Raccogli informazioni dagli utenti e fai delle ipotesi informate (Informed Guess)
- Follow-the-path: scopri il percorso del traffico ed analizzalo dalla fine alla destinazione
- Sostituzione: sostituire fisicamente i supposti componenti difettosi
- Comparazione: effettuare test uguali su macchine diverse per analizzare possibili differenze
- Educated guess (ipotesi educata): si basa sull’esperienza (educazione) del tecnico per risolvere problemi in base alle esperienze pregresse

# Ticket
Rappresenta il principale metodo di condivisione delle problematiche. Si compone di:
- ID
- Data di creazione
- Descrizione
- Utente che ha aperto il ticket
- Categoria
- Priorità 
- Status
- Creato da
- Gestito da
- aggiornamenti (includono data e specifiche)

# Gestione della rete
La gestione della rete (intesa come controllo e manutenzione) può essere gestita tramite appositi software. I software si dividono in due categorie:
- SMNP: Protocollo di gestione delle reti semplice
- RMON: Controllo della rete da remoto

Essi sono forniti in due modalità diverse:
- On-premises: sono localizzati fisicamente in server all’interno della rete, con potenza sufficiente a permettere il trattamento e l’analisi di dati per reti di medie dimensioni (tipo CAN) e possono essere dotate di strumenti di elaborazione avanzati come il ML (Machine Learning) e sono accessibili solo tramite VPN. Sono particolarmente utili nel caso siano trattati dati sensibili
- Cloud-based: permettono il monitoraggio di reti geograficamente sparse. Il servizio spesso é altamente scalabile e dotato di misure avanzate di analisi dati.

Di solito si utilizza una **network baseline** per definire il normale livello di traffico operante sulla rete.