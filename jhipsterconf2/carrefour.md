---
title: François Delbrayelle - JHipster Conf 2 - Carrefour : retour sur la personnalisation de JHipster pour l'entreprise (notes)
---

# Carrefour : retour sur la personnalisation de JHipster pour l'entreprise

Sujets : JHipster, CI/CD, Kubernetes, Helm, micro-services

9h45 - 10h30

Par Yoan Hoareau (Carrefour). Merci !
Par [Anthony Viard](https://twitter.com/avdev4j) (Ippon Technologies). Merci !

La vidéo complète est en ligne sur la chaîne YouTube de [Ippon Technologies](https://www.youtube.com/watch?v=OlbfgXjw5g0).

Un petit historique pour commencer :
- Carrefour (C4) cherchait une stack technique moderne et a découvert JHipster en 2016.
- En 2017 a eu lieu le premier projet monolithe (front et back séparés) développé avec JHipster chez Carrefour.
- En 2018, 3 nouveaux projets dont un en micro-services et Vert.x.
- En 2019, la core team de JHipster intervient sur le périmètre.

## Bilan de l'utilisation de JHipster

Après deux années d'utilisation, voici ce qui a été apprécié :
- L'état de l'art : la qualité est au rendez-vous, avec une prise en compte des nouveautés et frameworks récents
- [JDL studio](https://start.jhipster.tech/jdl-studio/) : un outil très pratique, gratuit et visuel
- Tests unitaires très bien générés, avec une bonne couverture de code
- Liquibase
- [jib](https://github.com/GoogleContainerTools/jib) a été également apprécié pour créer les images Docker

Il y avait ceci dit des limites à l'utilisation de JHipster dans le contexte Carrefour, parfois le code généré ne convenait pas aux besoins de par les spécificités Carrefour, un travail important sur le CI/CD Carrefour et Angular Material pas natif avec JHipster (le front utilise Bootstrap).

Comment alors s'améliorer ? Anthony et Julien Dubois interviennent pour prendre la température et aider les équipes. Plusieurs points ont été ciblés en priorité :
- Le JDL et la ré-génération (voir la pratique du [side-by-side](https://www.youtube.com/watch?v=9WVpwIUEty0) ainsi que le [talk du jour sur le sujet](side-by-side.md) pour s'en sortir)
- Liquibase et le delta avec les bases de données (utilisation d'outils comme `mvn liquibase:diff` par exemple)
- Travail sur les API REST
- Proposition d'un blueprint pour pouvoir capitaliser sur les expériences

## Blueprint Carrefour

Qu'est-ce qu'un blueprint ?

C'est une solution proposée par la communauté, c'est donc open-source. Il existe un [générateur de blueprints](https://www.jhipster.tech/modules/creating-a-blueprint/) pour en créer et permettre de personnaliser la génération (en intervenant sur certains générateurs). __Le blueprint se package en package npm.__

Il faut avant tout définir le périmètre ;
- Quelles fonctionnalités Carrefour ?
- Quels générateurs surcharger ? Notamment sur les aspects CI/CD.
- Comment gérer nos templates ?
- Se rapprocher des équipes

Le périmètre défini était "production ready", "less is more", "JHipster like" et permettait la montée en compétences.

Quel modèle choisir ? Quelle est la cible ? Quel type d'application veut-on générer ?
Une application de type starter pour les micro-services existait de base et a servi en partie de modèle pour la V1 avec d'abord du Traefik et OpenStack puis en V2 du Kubernetes avec Ingress. L'environnement est basé sur Kubernetes, Helm (pour définir des templates dans les configurations Kubernetes en fonction des environnements) et Jenkins.

Exemple de génération d'un projet monolithe chez Carrefour :
- Génération de backend Java, ajout d'un Jenkinsfile pour la CI et des charts Helm (ensemble de fichiers de configuration des templates) et un chart Helm child spécifique sans référence aux environnements
- Génération du frontend en Angular, avec aussi un Jenkinsfile et un chart Helm child
- Un dossier env charts contient un Jenkinsfile pour le CD et des charts Helm parents avec des spécificités liées aux environnements (ressources, etc)

Concernant le Jenkinsfile généré il permet plusieurs étapes dans l'intégration continue via plusieurs images Docker :
- Une pour les étapes build & tests, analyse Sonar et quality gate pour Sonarqube
- Build et push de l'image Docker de l'application à proprement parler
- Une pour gérer Helm : package et publish des charts vers Nexus
- Continuous deployment vers les environnements cibles

L'application permet à travers Jenkins de gérer le continuous deployment pour manipuler les charts Helm à travers le client Helm.

Comment cela s'intègre dans l'écosystème Carrefour ? L'application est générée via le blueprint JHipster puis poussée sur le SCM et le CI/CD prend la main pour les étapes plus classiques de build, tests unitaires, qualité, sécurité du code avec Fortify et enfin le déploiement via Helm.

## Et l'avenir ?

En bonus : Le JHipster-C4 CLI et les projets à venir. Comment utiliser le blueprint ? Avec `npm i -g generation-jhipster-c4` puis `jhipster-c4`. Cela permet de récupérer la bonne version et utiliser le blueprint en ligne de commandes. Voir l'article d'Anthony pour [ajouter un CLI à son blueprint JHipster](https://medium.com/@anth.viard/add-a-cli-to-your-jhipster-blueprint-748c4eaf6160). Ce qui n'a pas encore été fait : JHiOnline C4 et blueprint pour Angular Material.

Des contributions sur le projet JHipster ont été effectuées lors des derniers mois suite à l'expérience gagnée via Carrefour avec 8 issues et 20 pull requests mergées essentiellement sur la partie core et blueprint (proposition par exemple d'un sonar.properties utilisé par le pom, utile notamment en cas de séparation du front et du back).

Les projets JHipster Carrefour sur 2019 :
- Environ 20 développeurs et 3 lead techs
- 3 projets en cours de développement (front/back ou back seul)
- 1 projet en production micro-services avec objectif 80 % de couverture de code

Carrefour souhaite accompagner les équipes sur l'utilisation du blueprint et recueillir du feedback tout en contribuant au projet JHipster.

De nombreux chantiers sont à venir :
- Automatiser la création de l'outillage
- Tests E2E
- Secrets Vault
- Fortify et Neoload dans les pipelines Carrefour
- Déploiement automatique en production
- Versioning des micro-services (piste avec Helm pour avoir un numéro de version sur un déploiement)
- Service mesh et serverless
- JHipster as a Service
- Progressive Web App
- Vue.js
- Quarkus
- Event Driven Architecture
