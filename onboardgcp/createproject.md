---
title: François Delbrayelle - On Board GCP - Create a project on GCP
---

# Create a project on GCP

Sujets : Cloud, GCP

01/10/2019 - 10h25 - 10h45

Par [Sébastien Friess](https://twitter.com/SebastienFriess) (Sfeir). Merci !

L'unité de base sur GCP c'est le projet, qui contient des ressources (par exemple : une base de données).

On peut organiser des dossiers contenant des projets. L'organisation est le noeud racine contenant l'ensemble des ressources où l'on définit des stratégies de sécurité.

La hiérarchie est la suivante : Organisation > Dossiers > Projets > Ressources.

Une stratégie plus restrictive passe devant une stratégie moins restrictive.

Il y a 4 façons d'intéragir avec la GCP :
- GCP Console : c'est bien mais en tant que développeur on a besoin d'outils d'automatisation, d'où les points suivants
- Cloud Shell et Cloud SDK (CLI)
- Cloud Console Mobile App (Android et iOS)
- REST-based API (pour les applications custom)

GCP Console :
- Console centralisée pour toutes les données projet
- Outils pour les développeurs
- Organiser les projets et les droits

Google Cloud SDK : inclut les outils CLI (`gcloud`, `bq`...).

L'application mobile Cloud Console Mobile App permet aussi de manager tout cela.

Les API RESTful (utilisent OAuth 2.0) : un peu le Swagger de GCP.

Il existe des librairies clientes : Cloud Client Libraries (gérée par la communauté)...

__Cloud Identity__ permet d'intégrer les dossiers cloud et on-premise dans une plate-forme IDaaS (IDentity as a Software). SSO qui supporte SAML 2.0, OAuth 2.0 et OpenID. Détecte les activités suspectes. C'est une plate-forme indépendante pour héberger et gérer des identités. Les droits sont gérés avec Cloud Console IAM. Il existe des comptes de service (service accounts).

Questions à se poser pour chaque action : qui ? pour faire quoi ?

3 types de rôle IAM : primitif, prédéfini et personnalisé.

Bonnes pratiques :
- Assigner des droits à des groupes plutôt qu'à des personnes
- Créer des groupes par ressources et chaque équipe
- Préférer des petits groupes pour des droits fins
- Éviter d'imbriquer des répertoires
