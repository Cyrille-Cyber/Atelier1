# Atelier1_entrepot_de_donnees

### Équipe
Ndeye Absa FALL
Cyrille TCHINDA

## Étape 1 – Jeu de données
Dataset: 2024 LoL Esports Match Data
Source: https://drive.google.com/drive/u/0/folders/1gLSw0RLjBbtaNy0dgnGQDAZOHIgCe-HH  (2024)

## Étape 2 – Architecture technique

Nous avons mis en place une architecture décisionnelle ELT basée sur Docker Compose.

- Base de données : PostgreSQL 15
- Stockage brut : table raw_lol_esports
- Transformation : requêtes SQL
- Modèle relationnel normalisé

### Visualisation
La visualisation pourra être ajoutée lors de l’atelier 3 (Metabase ou Notebook).

### Lien vers le jeu de données
https://drive.google.com/drive/u/0/folders/1gLSw0RLjBbtaNy0dgnGQDAZOHIgCe-HH  (2024)

### Présentation du dataset
Nous avons choisi un jeu de données de parties classées de **League of Legends**.  
Le dataset contient 122 388 lignes correspondant aux statistiques détaillées 
des matchs e-sport League of Legends 2023-2024.

Chaque ligne représente un joueur dans une partie.
Les principales variables utilisées :
- gameid (identifiant du match)
- league
- year
- teamname
- playername
- champion
- kills, deaths, assists
- totalgold
- total_cs
- visionscore

Après nettoyage (suppression des lignes sans playerid),
101 500 participations valides ont été intégrées dans le modèle relationnel.

### Modèle relationnel
Le schéma ci-dessous représente le modèle relationnel normalisé utilisé pour l'analyse des données League of Legends
<img width="824" height="705" alt="ERD_LoL_Atelier1" src="https://github.com/user-attachments/assets/cf3434df-2e46-4da8-8bf2-920f66c61771" />
