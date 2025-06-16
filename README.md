# Infrastructure Microservices – Docker Compose

Ce dépôt contient le fichier `docker-compose.yml` permettant d’orchestrer l’ensemble de l’infrastructure pour vos microservices :  
- 3 APIs FastAPI (chacune avec sa propre base PostgreSQL)
- 1 broker RabbitMQ
- 1 interface PgAdmin pour la gestion des bases de données

---

## Prérequis

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

---

## Structure des services

- **api1, api2, api3** : Microservices FastAPI (chacun dans son propre dossier ou image)
- **db1, db2, db3** : Bases de données PostgreSQL, une par microservice
- **rabbitmq** : Broker de messages pour la communication asynchrone
- **pgadmin** : Interface web pour gérer les bases PostgreSQL

---

## Lancement de l’infrastructure

1. Clonez ce dépôt :
   ```bash
   git clone <url-du-repo-infra>
   cd <nom-du-repo>
   ```

2. Assurez-vous que les dossiers ou images des APIs sont accessibles selon la configuration du `docker-compose.yml`.

3. Lancez l’ensemble des services :
   ```bash
   docker compose up --build
   ```

4. Accédez aux interfaces :
   - **API 1** : [http://localhost:8001](http://localhost:8001)
   - **API 2** : [http://localhost:8002](http://localhost:8002)
   - **API 3** : [http://localhost:8003](http://localhost:8003)
   - **PgAdmin** : [http://localhost:5050](http://localhost:5050)  
     - Email : `admin@admin.com`  
     - Mot de passe : `admin`
   - **RabbitMQ Management** : [http://localhost:15672](http://localhost:15672)  
     - User : `user`  
     - Password : `password`

---

## Connexion des bases dans PgAdmin

Dans PgAdmin, ajoutez chaque base de données :
- **Host** : `db1`, `db2`, `db3`
- **Port** : `5432`
- **User** / **Password** / **Database** : selon la configuration du service concerné

---

## Arrêt de l’infrastructure

```bash
docker compose down
```

---

## Personnalisation

- Modifiez les variables d’environnement dans le `docker-compose.yml` selon vos besoins.
- Ajoutez ou retirez des microservices en adaptant le fichier.

---

## Notes

- Chaque microservice doit être buildé ou accessible via une image Docker.
- Les volumes Docker assurent la persistance des données
