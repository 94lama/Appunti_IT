[link](https://www.aquasec.com/products/trivy/), [GitHub](https://github.com/aquasecurity/trivy)
# Introduzione
Aqua trivy è u software utilizzato per effettuare il controllo delle #immagine  utilizzate nel progetto. E' possibile utilizzarlo tramite #immagine di [[Docker]], per collegarlo alla #pipeline di messa online del progetto (es. tramite [[Jenkins]]).
# Avviare una scansione
```shell
trivy <target> [--scanners <scanner1,scanner2>] <subject> 
```
Eseguire un'analisi su un immagine [[Docker]] all'interno di una #pipeline in [[Jenkins]]
```shell
trivy image {DOCKER_HUB_USER}/devops-api 
```
Il comando ritorna una tabella (in [[MarkDown]]) delle #vulnerabilità dell'immagine selezionata con annessa la #CVE ed il relativo grado di vulnerabilità. Il #report è da analizzare anche in base alla tipologia di vulnerabilità e all'uso che si fa dell'immagine stessa.