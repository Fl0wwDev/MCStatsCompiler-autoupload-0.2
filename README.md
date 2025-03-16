# MCStatsCompiler

## Description

Ce projet vise à traiter un ensemble de fichiers de statistiques générés par des joueurs de Minecraft et à produire des statistiques formatées de manière lisible.

## Avertissement

Ce projet a été initialement codé pour mon propre usage, mais j'ai décidé de le partager au cas où il pourrait être utile à quelqu'un d'autre. Il est encore en cours de développement et nécessite une certaine connaissance de Python.

Le script est destiné à être exécuté sur votre propre ordinateur et non sur un serveur. Il pourrait être exécuté sur un serveur, mais cela nécessiterait probablement quelques adaptations.

## Modules

Actuellement, ce projet comporte deux "modules". Note : les deux modules sont désormais dans le même fichier Python, **main.py**.

### Module principal

Ce module traite les fichiers de statistiques vanilla (au format JSON) situés dans le dossier "stats". Il propose actuellement deux fonctionnalités :
- Un classement (affiché uniquement en console pour l'instant) de la statistique souhaitée. Par exemple, `minecraft:play_time` pour le temps de jeu de chaque joueur.
- Un "meilleur-et-pire" (affiché uniquement en console pour l'instant) pour un joueur donné. Cela indique la position du joueur dans chaque classement de statistiques individuelles.

### Module Cobblemon

Ce module traite les fichiers de statistiques générés par le mod Cobblemon (au format JSON) situés dans le dossier "cobblemonplayerdata". Il propose actuellement trois fonctionnalités liées :
- Un classement des joueurs ayant capturé le plus de Cobblemons. Le classement est exporté dans un fichier Excel.
- Le même principe pour les Cobblemons Shiny. Le classement est ajouté dans le même fichier Excel.
- Le même principe pour les Cobblemons Légendaires. Le classement est ajouté dans le même fichier Excel.

## Exécution des scripts

### 1. Installation

Pour exécuter les scripts, commencez par télécharger ce dépôt. Vous avez besoin d'une installation valide de Python ainsi que des bibliothèques requises. Voici les bibliothèques qui ne sont pas installées par défaut avec Python :

`pandas, numpy, configparser, openpyxl, paramiko, excel2img, requests`

Vous pouvez les installer tous en même temps avec la commande suivante `pip install -r requirements.txt`.

### 2. Modifier la configuration

Un seul fichier de configuration est à modifier : **config.ini**.
Lisez-le et modifiez-le si nécessaire en fonction de vos besoins.

### 3. Mettre à jour usercache.json

Tous vos fichiers de données doivent être nommés [uuid].json, où [uuid] correspond à l'UUID Minecraft du joueur. Pour utiliser les noms d'utilisateur des joueurs, vous devez mettre à jour le fichier **data/usercache.json**. Il vous suffit de le télécharger depuis votre serveur (il se trouve normalement à la racine du dossier) et de le placer dans ce répertoire. Si vous utilisez l'option FTP (voir ci-dessous), le script récupérera automatiquement ce fichier (pas besoin de le mettre à jour manuellement).

### 4. Fichiers d'entrée

Vous avez le choix entre quatre méthodes pour importer les fichiers de données : manuel, local, FTP ou SFTP. Par défaut, l'option "manuel" est activée dans la configuration.
- **manuel** : ajoutez manuellement tous les fichiers dans les dossiers appropriés du dossier "data" du projet.
- **local** : si vous exécutez un serveur sur votre machine locale, indiquez simplement le chemin du dossier principal dans la configuration.
- **ftp** : utilisez une connexion FTP vers un serveur distant.
- **sftp** : utilisez une connexion SFTP vers un serveur distant.

Si vous utilisez l'option manuelle, déposez les fichiers dans les sous-dossiers appropriés du dossier **data** (stats, usercache...). Pour les autres options, suivez les instructions dans la configuration. Remarque : le mode local est encore en cours de développement.

### (Module Cobblemon uniquement) 5a. Préparer output.xlsx

Si vous souhaitez utiliser la fonctionnalité de classement du module Cobblemon, vous devez préparer le fichier **output.xlsx**. Adaptez simplement le tableau à votre nombre de joueurs prévu (par exemple, si vous attendez 20 joueurs, vous pouvez opter pour un tableau de 5x4 ou 10x2). Vous pouvez également modifier le titre, les couleurs et les éléments de mise en forme. Assurez-vous simplement de garder trois colonnes Excel par classement et de commencer dans la cellule **B3**.

N'oubliez pas d'adapter le fichier de configuration à vos modifications, notamment le nombre de lignes et de colonnes. Les sous-titres du tableau peuvent également être configurés ici.

### (Module Cobblemon uniquement) 5b. Préparer Pokemon.csv

Si vous utilisez le classement "Cobblemons Légendaires" (désactivé par défaut), vous pouvez modifier **Pokemon.csv**. Ce n'est pas obligatoire, mais si vous souhaitez définir quels Pokémons sont considérés comme légendaires pour le classement, vous pouvez le faire ici.

### 6. Exécuter le script

Vous pouvez maintenant exécuter le script **main.py** avec votre installation Python.

### Problèmes fréquents
1. Ce script utilise des chemins locaux, assurez-vous donc de l'exécuter depuis le bon dossier ! Si vous obtenez des erreurs liées aux fichiers JSON, il est probable que le script ne les trouve pas.
2. Ce script n'est pas automatique, vous devez le lancer toutes les heures ou minutes pour qu'il fonctionne. Mais vous pouvez utiliser le gestionnaire de tâches de Windows pour qu'il soit exécuté automatiquement.


---

# English Version


# MCStatsCompiler

This project aims at taking a bunch of stats data file generated from Minecraft players and outputing nicely formatted statistics.

## Disclaimer

This was coded for my own use originally, but I've decided to share it in case it can be useful to someone else. It is still work in progress, and requires some knowledge of Python.

The script is intended to be executed on your own computer and not on a server. It could be executed on a server, but it probably requires a little adaptation.


## Modules
For now, there are 2 "modules" in this project. Note: the 2 modules are now in the same Python file main.py

### Main module
This module takes vanilla stats files (json format) that can be found in the folder "stats". It has currently 2 features: 
- A leaderboard (console printed-only for now) of the desired statistic. For example, `minecraft:play_time` for the play time of each player.
- A "best-and-worst" (console printed-only for now) for the desired player. This gives the position of the player in each of the leaderboards of individual stats.

### Cobblemon module
This module takes statistics files generated by the Cobblemon mod (json format) that can be found in the folder "cobblemonplayerdata". It has currently 3 (related) features:
- A leaderboard of the players who caught the most Cobblemons. The leaderboard is output on an Excel sheet.
- Same for the most Shiny Cobblemons. The leaderboard is output on the same Excel sheet.
- Same for the most Legendary Cobblemons. The leaderboard is output on the same Excel sheet.


## Running the scripts

### 1. Installation
In order to run the scripts, start by downloading this repo. You need a valid installation of Python, as well as the required libraries. Here are the libraries that are not installed by default with Python:

`pandas, numpy, configparser, openpyxl, paramiko, excel2img, requests`

You can install them all at once with the following command `pip install -r requirements.txt`

### 2. Edit the config
There is 1 config to edit, **config.ini**.
Read it, and if needed, edit it based on what you want.

### 3. Update usercache.json
All of your data files should be named [uuid].json, where [uuid] is the Minecraft UUID of the player. In order to work with the usernames of the players instead, you need to update the file **data/usercache.json**. Simply download it from your server (it should be at the root folder) and put it there. If you use the FTP setting (see below), the script will go and file the file for you (no need to update it manually then).

### 3. Input files 
You have the choice between 4 options to input data files: manual, local, ftp or sftp. In the config, manual is by default.
- manual: upload manually all the files in the relevant folders in the data folder of the project
- local: you have a server on your local machine/computer, in this case simply give the path to the main folder in the config.
- ftp: use an ftp connection to a distant server
- sftp: use an sftp connection to a distant server

If you use the manual option, drop the files in the appropriate subfolders in the **data** folder (stats, usercache...). If you use other options, follow the instructions in the config. Note: the local mode is still WIP.

### (Cobblemon module only) 5a. Prepare output.xlsx
If you intend on using the leaderboard feature of the Cobblemon module, you need to prepare the **output.xlsx** file. Simply adapt the table to your desired number of players (for example, if you expect 20 players, you can for example have a 5x4 table or a 10x2 table). You can also change the title, the colors and other formatting elements. Just make sure to keep 3 Excel columns per leaderboard column, and start it in the cell B3 (see example in the image below).

Don't forget to adapt the config file to your changes, especially the number of rows and columns if you have changed them! The subtitles of the table can also be configured there.

![Cobblemon example](images/cobblemon_example.PNG)

### (Cobblemon module only) 5b. Prepare Pokemon.csv
If you intend on using the "Most Legendary Cobblemons" Leaderboard (which is disabled by default), you can edit **Pokemon.csv**. This is not needed, but if you want to change which pokémons are considered as legendary for the leaderboard, it is done there.

### 6. Run the script
You can now run the **main.py** script of the module with your Python installation.

### Frequent problems
1. This script uses local paths, so make sure that you are executing the Python script from the folder! If you get errors related json files, it's probably that the script couldn't find it.
2. This script is not automatic; you need to run it every hour or minute for it to work. But you can use Windows Task Manager to have it run automatically.