# Workshop-postgreSQL-docker
The purpose of this project is to create a postgreSQL database with a docker image

## Prérequis

-   Avoir `docker` et `docker-compose` installés sur votre ordinateur
-   Avoir une connaissance de base de SQL

## Etape 1 : Télécharger l'image PostgreSQL

Créez un nouveau répertoire pour votre workshop et utilisez la commande suivante pour télécharger l'image PostgreSQL :

`docker pull postgres`

## Etape 2 : Créer un fichier `docker-compose.yml`

Dans le répertoire de votre workshop, créez un fichier `docker-compose.yml` avec le contenu suivant :

```yml
version: '3'
services:
    db:
        image: postgres
        environment:
            - POSTGRES_USER: myuser
            - PO STGRES_PASSWORD: mypassword
            - POSTGRES_DB: mydb
        ports:       - "5432:5432"
        volumes:       
        - pgdata:/var/lib/postgresql/data
``` 

Ce fichier définit un service nommé `db` qui utilise l'image PostgreSQL téléchargée à l'étape 1. Il définit également les variables d'environnement pour l'utilisateur, le mot de passe et la base de données à utiliser. Il expose également le port 5432 pour que vous puissiez vous connecter à la base de données à l'aide d'un client externe.

## Etape 3 : Lancer la base de données

Utilisez la commande suivante pour lancer la base de données :

`docker-compose up -d`

Cela lancera le service `db` défini dans le fichier `docker-compose.yml`.

## Etape 4 : Se connecter à la base de données

Vous pouvez maintenant vous connecter à la base de données en utilisant un client SQL tel que `psql`. Utilisez la commande suivante pour vous connecter :

`psql -h localhost -U myuser -d mydb`

## Etape 5 : Exercices

1.  Créez une table nommée "users" avec les colonnes "id", "username" et "email".
2.  Insérez des données dans la table "users".
3.  Sélectionnez tous les utilisateurs de la table "users".
4.  Mettez à jour l'email d'un utilisateur en utilisant son nom d'utilisateur.
5.  Supprimez un utilisateur en utilisant son nom d'utilisateur.

## Etape 6 : Arrêter la base de données

## Bonus Part

1. Try to find a way to keep your work when you quit your docker compose
