---
title: François Delbrayelle - JHipster Conf 2 - JHipster avec Google Cloud (notes)
---

# JHipster avec Google Cloud

Sujets : JHipster, Google Cloud Platform

11h25 - 12h10

Par [Ludovic Champenois](https://twitter.com/ludoch) (Google). Merci !

## Historique

Un rappel de ce qui existe aujourd'hui sur GCP est proposé. L'aspect serverless computing fait partie intégrante de Google Cloud.

La présentation se concentre plutôt sur Google Cloud Platform standard (depuis 2009), notamment basé sur Google App Engine (GAE). Depuis trois couches se sont créées : Cloud Functions (functions), App Engine (apps) et Cloud Run (containers). Les trois tournent sur le même socle de base.

__On ne peut pas faire de serverless sur JHipster aujourd'hui__ même si en théorie on pourrait. Cloud Functions est une plate-forme pour le serverless et est donc event-driven.

L'environnement App Engine standard pour des applications web hautement scalables voire serverless. La grosse nouveauté de juin 2019 est le runtime Java 11. Pas besoin de s'embêter avec une version mineure de type "update", Google s'en occupe.

Cloud Run pour utiliser serverless dans les containers. On paie ce que l'on consomme avec App Engine. Très utilisé avec des milliards de requêtes par jour. Le plus gros client est snap.

Google App Engine a créé le monde serverless que l'on connaît aujourd'hui. Le mot "App Engine" a disparu petit à petit pour être remplacé par le terme "serverless". La stack a beaucoup évolué depuis 2009. Google App Engine a évolué en tant que Platform as a Service.

## Google App Engine runtime Java 11

[gVisor](https://github.com/google/gvisor) est un user-space kernel écrit en Go qui se met entre une application et l'OS et délégue les syscalls au kernel ou les émule. C'est une sandbox basée sur la virualisation mais ce n'est pas une VM et ne nécessite pas de changements dans la JVM.

On peut utiliser GAE Java 11 Unrestricted pour travailler avec le runtime Java 11. On envoie un fat jar ou une collection de jars à GAE. En écoute sur le port 8080. Éventuellement on renseigne l'entrypoint (proche de l'instruction ENTRYPOINT sur un Dockerfile). Les API publiques Google Cloud sont utilisées. Possibilité d'utiliser en live Cloud Debugger et Cloud Profiler. Le fichier de configuration "app.yaml" de GAE permet de renseigner le runtime, l'entrypoint, si besoin des options de scaling.
GAE maintient une image de base (Ubuntu LTS) ainsi qu'une OpenJDK 11 (LTS aussi). Une application déployée en 2019 héritera automatiquement des mises à jour des couches d'images. GAE Java 11 Beta sorti en juin 2019.

Dans Google Cloud Run par contre on donne directement l'image Docker par exemple grâce à [Jib](https://github.com/GoogleContainerTools/jib) dans JHipster : `./mvnw install appenginejava11:deploy jib:build -Pprod,prod-gae,swagger,no-liquibase -Dimage=gcr.io/jhipster-project/myimage` (le plugin appenginejava11 permet aussi de déconstruire un fat jar) et la déployer dans Cloud Run avec `gcloud beta run deploy --image gcr.io/jhipster-project/myimage --platform managed`.

> Google Jib ou "je suis un développeur Java, j'ai pas envie de m'occuper de Dockerfiles..." :)

Jib propose un build optimisé, par exemple avec ce Dockerfile :

```
FROM gcr.io/distroless/java
COPY target/dependencies /app/dependencies
COPY target/resources /app/resources
COPY target/classes /app/classes
ENTRYPOINT java -cp /app/dependencies/*:/app/resources:/app/classes my.app.Main
```

Jib vs Docker :
- Au premier build la taille est identique
- Rebuild sans changement, Jib gagne
- Rebuild avec changements, Jib gagne largement

Jib est parfait pour Cloud Run qui a besoin d'un container.

Ludovic propose une démo avec JHipster :
- Un projet JHipster de base avec quelques entités
- La commande `jhipster gae` permet d'ajouter des fichiers de configuration pour GAE (pour Java 8 et Java 11) via des options (instance class, scaling, nombre d'instances, ...), cela a pour effet de lancer plusieurs commandes `gcloud`
- Déploiement dans Cloud App Engine avec `./mvnw install appenginejava11:deploy`
- Le site est bien déployé à l'URL suivante : http://jhipster-2019-6-dot-openjdk11.appspot.com
- On peut debug en temps réel dans GCP (en ajoutant l'agent de debug dans le "app.yaml"). Les sources sont pour l'instant sur la machine. Possibilité d'utiliser Bit Bucket, GitHub... pour uploader les sources et débuguer.
- Passage dans Cloud Run : nouvelle instance à créer pour le service en se basant sur une image Docker (via jib) en choissant les options dont la mémoire allouée. Un évènement d'exécution est créé dans gVisor.