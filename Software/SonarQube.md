[Link](https://www.sonarsource.com/products/sonarqube/enterprise-edition/?gads_campaign=SQ-Hroi2-PMax&gads_ad_group=Global&gads_keyword=&gad_source=1&gclid=Cj0KCQiAoKeuBhCoARIsAB4WxtfxGej9zg5zzjbkcut3KWp9PhhLbt7-A5dmL76rA5dlN9HTkAoBivMaAjceEALw_wcB)
# Installaizone
## Immagine Docker
Carico l'immagine da DockerHub
```sh
docker pull sonarqube
```
Creo i container
```sh
docker volume create --name sonarqube_data
docker volume create --name sonarqube_extensione
docker volume create --name sonarqube_logs
```
Inizializzo il container
```sh
docker run -d --name sonarqube -p 9000:9000 -v sonarqube_data:/opt/sonarqube/data -v sonarqube_extensions:/opt/sonarqube/extensions -v sonarqube_logs:/opt/sonarqube/logs <image_name>
```
	Esempio di immagine: sonarqube:9.9-community
Dopo questo passaggio, si potrà accedere alla porta 9000 a SonarQube con le credenziali
```Credenziali
user: admin
password: admin
```
# Collegamento a [[Jenkins]]
Creazione di un #token