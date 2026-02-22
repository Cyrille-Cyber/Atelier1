# Atelier1_entrepot_de_donnees

## Étape 1 – Jeu de données

Nous avons choisi un jeu de données de parties classées de **League of Legends**.  
Ce dataset contient plus de 100 000 parties, avec des statistiques in‑game détaillées pour chaque joueur et chaque équipe :

- kills, deaths, assists  
- gold gagné  
- dégâts infligés  
- objectifs pris (tours, dragons, barons)  
- champion joué  
- rôle et lane  

## Étape 2 – Architecture technique

Nous avons mis en place une architecture décisionnelle ELT basée sur Docker Compose.

### Extract / Load
- **MySQL** est utilisé pour stocker les données brutes du jeu de données League of Legends.
- Les fichiers CSV seront importés dans des tables MySQL via phpMyAdmin.

### Transformation
Nous utilisons **Jupyter Notebook** pour réaliser les transformations :
- nettoyage des données brutes,
- séparation en tables normalisées (match, team_stats, player_stats),
- chargement dans un schéma final.

### Visualisation
La visualisation pourra être ajoutée lors de l’atelier 3 (Metabase ou Notebook).

### Lien vers le jeu de données
https://drive.google.com/drive/u/0/folders/1gLSw0RLjBbtaNy0dgnGQDAZOHIgCe-HH  (2024)

### Présentation du dataset
Le dataset contient des statistiques in‑game détaillées :
- kills, deaths, assists  
- gold gagné  
- dégâts infligés  
- objectifs pris (tours, dragons, barons)  
- champion joué, rôle, lane  
- statistiques d’équipe (victoire, kills totaux, objectifs)

##Étape 3 - Modèle relationnel

Voici le schema ERD destiné à stockés les données du jeu de données, nous tenons à ce que vous sachiez que le dataset qui a été
choisi était très lourd c'est pour celà on a pris les données principales seulement pour faire le ERD

<img width="2048" height="1236" alt="image" src="https://github.com/user-attachments/assets/e589f8cd-14bc-4382-beed-10572e366699" />


# Atelier2_entrepot_de_donnees

## Étape 1 – Modélisation dimensionnelle

Voici notre schéma dimensionnel 

![alt text](image.png)


# Atelier3_entrepot_de_donnees
## Étape 3 — Centralisation des logs

Pour centraliser les logs de tous les services , nous avons intégré Dozzle, une interface légère permettant de visualiser en temps réel les logs Docker.

### Intégration dans docker-compose

```yaml
dozzle:
  image: amir20/dozzle:latest
  container_name: dozzle
  ports:
    - "9999:8080"
  volumes:
    - /var/run/docker.sock:/var/run/docker.sock
  restart: always

/Exemple d’erreur visualisée/

Pour tester la centralisation, nous avons volontairement provoqué une erreur de connexion MySQL depuis Jupyter :
from sqlalchemy import create_engine
import pandas as pd

engine_test = create_engine("mysql+pymysql://root:FAUX_MDP@mysql:3306/lol_dw_db")
pd.read_sql("SHOW TABLES;", engine_test)

![alt text](image-1.png)


## Étape 4 — Documentation

### Prérequis

- Docker
- Docker Compose
- Python 3.10
- pip + packages :
  - pandas
  - sqlalchemy
  - pymysql
  - matplotlib
  

### Lancement complet de la stack
Apres integration de DOZZLE dans le conteneur :

```bash
docker compose down 
docker compose up -d

ensuite on y accede via le navigateur en tapant : http://localhost:9999/

### Valeurs configurables
Dans docker-compose.yml :

Ports MySQL : 3310:3306

Ports Jupyter : 8888:8888

Ports Dozzle : 9999:8080

Mot de passe MySQL : root

Noms des bases : lol_raw_db, lol_dw_db, lol_model_db

### les points de vigilance pour l'ajout de service
-Toujours exposer les ports nécessaires

-Toujours monter /var/run/docker.sock pour les outils de logs

-Vérifier les dépendances (depends_on)

-Redémarrer la stack après modification 

### Équipe
Ndeye Absa FALL
Cyrill TCHINDA
