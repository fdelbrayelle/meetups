---
title: François Delbrayelle - On Board GCP - Introduction to the Cloud - Cloud, on board online
---

# Introduction to the Cloud - Cloud, in board online

Sujets : Cloud, GCP

01/10/2019 - 09h45 - 10h25

Par [Didier Girard](https://twitter.com/DidierGirard) (Sfeir). Merci !

GCP c'est un ensemble de services que l'on va pouvoir sélectionner en fonction des besoins.

__Il y a aujourd'hui un besoin de performance.__

Pendant des années quand on avait besoin de puissance on mettait un processeur en plus...
Plutôt que de faire du scale up on fait plutot du scale out au point d'arriver à du serverless (on ne sait plus sur combien de machines on exécute notre code).

Il y a 3 gros cloud providers qui ont plus ou moins les mêmes fonctionnalités : GCP, AWS et Azure.

## Pourquoi GCP ?

Google a travaillé sur plusieurs innovations majeures ces dernières années dont les caractéristiques sont accessibles sur le net : Google File System, MapReduce, BigTable, Borg (projet sur la containerisation ayant déclenché Kubernetes), Dremel (pour comprendre le fonctionnement de BigQuery), Kubernetes, TensorFlow...

Hadoop a été créé notamment pour répondre aux problématiques big data qui sont surtout parties de chez Google.

On est passé d'un monde physique/on-premise à un monde virtualisé puis dans le cloud (serverless, DevOps). Autrement dit d'un monde basé sur la configuration utilisateur, maintenu et managé à un monde totalement automatisé.

Il s'agit de 7 produits cloud avec 1 milliard d'utilisateurs (Google, Android, Chrome, Maps, Play, YouTube, Mail). Tout est container derrière.

Il y a de multiples raisons de basculer sur le cloud :
- Optimiser les coûts d'infrastructure et scaler : l'argument économique est très défensif selon Didier. C'était surtout vrai aux débuts du cloud. Il vaut mieux basculer sur le cloud pour créer de la valeur.
- Gagner de la valeur des données pour prédire les possibilités business.
- Construire de nouvelles applications et expériences.
- Se connecter à des plate-formes business de services et partenaires.
- Rendre les équipes productives avec des mobiles et périphériques sécurisés.

Pendant ce temps, l'IT se modernise à différentes vitesses (années, mois, semaines).

## Qu'est-ce que je peux faire avec GCP ?

Les services offerts par le cloud computing sont :
- Compute : louer de la puissance, de l'élasticité (pour s'adapter et scaler dans des containers = c'est l'utilisateur qui crée les images)
- Network : load-balancing (on ne connaît pas le nombre de machines, pas à le gérer), configurer les réseaux, le DNS...
- Storage : Cloud Storage, Cloud SQL, Cloud Bigtable...
- Database/big data : BigQuery, Cloud Pub/Sub...
- AI/ML : Cloud ML, reconnaissance de parole...
- Analytics/opérations/outils

## Basculer sur le cloud

Il faut prévoir un planning. Il y a différents types de cloud plans.
