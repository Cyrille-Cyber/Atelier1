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

### Équipe
Ndeye Absa FALL
Cyrill TCHINDA
