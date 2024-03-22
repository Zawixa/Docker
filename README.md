# Docker

## Contexte : 
Ce projet vise à créer une application web Python utilisant Flask, avec un système de logging intégré grâce à Prometheus et Grafana. L'application Flask servira de base pour une démonstration d'intégration avec des outils de surveillance, permettant de collecter des métriques et de les afficher de manière graphique.

## Objectifs 
- Créer une application Flask conteneurisée
- Découverte de Docker avec création de conteneurs et images 
- Utilisation de Docker compose
- Découverte des outils de surveillance Prometheus et Grafana
## Conteneurs 
- Application Flask : Conteneurisée pour l'exécution de l'application Python Flask.
- Prometheus : Conteneur pour la collecte de données de monitoring et de métriques.
- Grafana : Conteneur pour afficher les données avec des tableaux de bord.  

# Etape 1 : Création de l'application conteneurisée Flask 

Pour démarrer, suivez ces étapes pour créer et conteneuriser votre application Flask :

1. **Créez un répertoire Docker :** C'est là que vous allez travailler pour construire votre application. Assurez-vous de vous positionner dans ce répertoire avant de continuer.

2. **Récupérer le fichier app.py :** Ce fichier contiendra votre application Flask. Vous le trouverez dans le répertoire git.

3. **Récupérer le fichier requirements.txt :** Ce fichier contiendra les dépendances de votre application Flask.

4. **récupérer le fichier Dockerfile :** Ce fichier spécifie comment construire votre image Docker pour l'application Flask.

Une fois que vous avez terminé, exécutez cette commande pour construire l'image à partir du Dockerfile : **sudo docker build -t app Docker**

Assurez-vous que l'image a été créée en exécutant la commande suivante : **sudo docker images**

# Etape 2 : Docker compose 

Pour orchestrer l'ensemble des conteneurs nécessaires, y compris l'application Flask, Prometheus et Grafana, suivez ces étapes :

1. **Récupéerer le Docker compose :** Ce fichier spécifiera la configuration de tous les conteneurs nécessaires

2. **Exécutez le Docker compose :** Utilisez la commande suivante pour démarrer tous les conteneurs spécifiés dans le Docker compose : **sudo docker-compose up -d**

3. **Vérifier la création de vos conteneurs :** docker ps - a  

4. **Tester la connexion aux pages web de vos conteneurs :**
      - **Application Flask :** http://votreadresseip:5000 
      - **Prometheus:** http://votreadresseip:9090
      - **Grafana :** http://votreadresseip:3000
# Etape 3 Configuration de Prometheus et Grafana : 

## Pour Prometheus : 
1. aller sur la page web de prometheus
2. aller dans la page graph
3. dans la barre de recherche "expression" taper : flask_http_request_total puis Execute
4. Tester sur votre si les metrics changent

## Pour Grafana : 

1. Connectez-vous à Grafana (nom d'utilisateur par défaut "admin" et mot de passe "admin").
2. Se rendre dans Connections > Data sources
3. Cliquez sur Ajouter Data sources
4. Choisissez Prometheus comme type de données
5. Définissez l'URL comme http://prometheus:9090 et cliquez sur Enregistrer et tester en bas.
6. Se rendre dans Dashbord > Create à Dashbord > Add Visualisation > Prometheus
7. select metrics > flask_http_request_total> run queries
8. Appuyer sur save donner un titre à votre dashbord et save
9. un graphique va apparaître dans le dashboard





