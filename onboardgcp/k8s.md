---
title: François Delbrayelle - On Board GCP - Containers and Kubernetes
---

# Containers and Kubernetes

Sujets : Cloud, GCP, Containers, Kubernetes

01/10/2019 - 13H15 - 

Par [Antoine Méausoone](https://twitter.com/AMeausoone) et [Sylvain Nieuwlandt](https://twitter.com/an0rak_dev) (Sfeir). Merci !

Compute Engine pour l'IaaS. App Engine pour le PaaS. Kubernetes entre deux ?

Antoine rappelle la différence entre virtualisation et containers.

Pourquoi utiliser les containers ? "Build once, run everywhere".

## Kubernetes et GKE

Kubernetes c'est la solution d'orchestration de containers développée par Google en Go. À l'origine était le projet Borg il y a une dizaine d'années.

Avantages de Kubernetes :
- Portable
- Haute disponibilité
- Élasticité (un cluster dans une zone, une région, multi-zones... ; load-balancing ; auto-scaling...)

Google Kubernetes Engine (GKE) est un cluster qui gère et lance les containers. Des services complémentaires existent : Google Cloud Build et Google Container Registry.

Sylvain et Antoine montrent une démo.

GKE On-Prem : sur son infrastructure mais géré par Google.

Anthos (annoncé au dernier Cloud Next) : ensemble de services open-source "write once, deploy in any cloud".

## Serverless Compute

__App Engine__, plate-forme de PaaS utilisable pour le serverless avec une limitation à certaines versions de Java, Python, Node, Go...

__Cloud Run__ est un service serverless pour les containers et bâti sur Knative.

__Cloud Function__ est une plate-forme de serverless computing event-driven. Le moyen le plus simple de lancer du code dans le cloud.

__Cloud Tasks__ est une file de tâches asynchrone (garantie que le message sera délivré).

__Cloud Scheduler__ pour les jobs cron.

Nouvelle démo sur une application en Go déployée sur Cloud Run. Commande `gcloud app deploy app.yaml`.
