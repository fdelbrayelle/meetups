---
title: François Delbrayelle - JHipster Conf 2 - Keynote - Dernières nouvelles du projet et retours d'expérience clients (notes)
---

# Keynote - Dernières nouvelles du projet et retours d'expérience clients

Sujet : JHipster

9h00 - 9h40

Par [Julien Dubois](https://twitter.com/juliendubois) (Microsoft). Merci !
Par [Pascal Grimaud](https://twitter.com/pascalgrimaud) (Ippon Technologies). Merci !

La vidéo complète sur les projets et réussites est en ligne sur la chaîne YouTube de [Ippon Technologies](https://www.youtube.com/watch?v=LfpV34seu10).

Julien présente la JHipster Conf, les sponsors et les tracks en deux langues avec les programmes : une matinée plutôt orientée inspiration et une après-midi plus technique. Il y aura des retours d'expérience de clients utilisant JHipster comme la Société générale et Carrefour.

## Quelles nouvelles sur JHipster ?

Il y a __plus de 100000 installations par mois__ (2 millions au total), 90000 visiteurs uniques mensuels sur le site web du projet, plus de 1 million de téléchargements pour jhipster-registry sur Docker Cloud, 14000+ étoiles sur GitHub, plus de 500 contributeurs, plius de 10000 tickets et pull requests (dont environ 50 tickets ouverts actuellement).

Il y a des co-leaders en plus de Julien qui sont Pascal Grimaud et Deepu K Sasidharan. De nouveaux membres de l'équipe core sont arrivées (environ 25 au total). Il y a aussi des responsables par "streams".

La campagne Open Collective est un énorme succès avec un budget de près de $30.000 par an. Le système de bug bounties (100, 200, 300 ou $500) fonctionne très bien et facilite la progression du projet, motive les contributeurs.

L'an passé le [JHipster Artwork](https://github.com/jhipster/jhipster-artwork) avait été annoncé à la première JHipster Conf. Le logo de JHipster a évolué : c'est maintenant le noeud papillon et une famille de personnes (plus inclusif).

Des tutoriels gratuits sont disponibles sur [Google Cloud Shell](https://github.com/jhipster/jhipster-guides/blob/master/guides/00_setting_up_your_environment.md).

__JHipster 6__ est sorti il y a quelques semaines. Le but est de rester sur une livraison majeure par an. De nombreuses mises à jour et nouveautés sont arrivées : Spring Boot, Spring Security, Angular, React, ... en dernière version, JDK 11, HTML5 pushstate, FakerJS...
 
Une autre grosse nouveauté est la stabilisation du [blueprint officiel Vue.js](https://github.com/jhipster/jhipster-vuejs) : prêt à l'utilisation, plus rapide en développement que Angular et React et des discussions sont ouvertes pour l'intégrer dans le générateur principal.

## Roadmap

Il y a plusieurs objectifs sur l'année.

Migration vers une configuration entièrement JDL pour les applications et les entités et donc plus de fichiers `.yo-rc` et `jhipster/*.json`, configuration centralisée et plus cohérente, moins de manières de configurer = moins de code à maintenir. De nouvelles fonctionnalités JDL sont prévues.

Un plugin [Prettier](https://github.com/jhipster/prettier-java) (outil de formattage de code le plus populaire côté client) pour Java est également en cours de développement. Deux niveaux : en sortie de JHipster et aussi possible en installation sur le projet (prise en charge à la sauvegarde).

JHipster supporte d'autres technologies côté serveur : JHipster Kotlin, Micronaut, Quarkus, JHipster .NET, NodeJS... De nouveaux objectifs apparaissent : intégrer les nouvelles équipes, améliorer le support Open API et les tests end-to-end.

Il y a également eu la __migration de l'intégration continue de JHipster vers Azure DevOps__ : plus rapide et puissante (10 builds en parallèle, builds journaliers plus complexes), gratuit, déploiement automatique sur Azure prévu...

Il y a des améliorations sur le Cloud avec des améliorations sur Kubernetes, Helm et Istio. Deux voies se présentent : utiliser Spring Kubernetes et Spring Cloud ou devenir "Kubernetes native" et dépendre de la plate-forme et ses extensions (Istio). Le support de Redis est nécessaire pour avoir un cache distribué prêt pour le cloud. Des discussions sont ouvertes pour un support du serverless avec un "JHipster Function".

## Projets et réussites sur JHipster

Pascal prend le relais.

Qu'en est-il chez Ippon et leurs clients ?

Quelques mots sur Ippon : spécialisé en digital, cloud et data, environ 17 ans d'existence, 400 collaborateurs environ, 38M€ de chiffre d'affaires, 5 continents et une practice JHipster depuis environ un an qui permet 1 jour de R&D par mois, des stagiaires JHipster, missions JHipster et des évènements/meetups. Il y a même eu un tour de France de JHipster avec de nombreux évènements.

Quelques réussites chez des clients :
- __Tessi__ (plate-forme de gestion du courrier avec 500 à 1000 utilisateurs en simultané, haute disponibilité entre 8h et 20h, beaucoup de données) avec une architecture micro-services (jusqu'à 7 services), du blue/green deployment avec Jenkins et Ansible
- __Manpower__ (Direct Recrutement) en mode Discovery to Delivery avec 4 développeurs et 1 architecte, première version en production en un mois du [site](https://www.direct-recrutement.fr), architecture micro-services, PostgreSQL, Keycloack, AWS
- __Galeries Lafayette__ (Ship from Store) pour un [projet from scratch Discovery to Delivery](https://www.youtube.com/watch?v=nG0ShHD7RQE) et du time to market en production après 10 semaines après 8 semaines de développement, architecture monolithe, PostgreSQL, Google Cloud Platform : ajouter liens
- __Horizon__ (client USA) pour des applications Spring Boot uniquement pour des API - solutions possibles : Maven Archetype, Spring Initializr ou JHipster. Il existe un module JHipster pour générer des micro-services, sans frontend et avec des configurations supplémentaires
- __Carrefour__ pour un JHipster "entreprise" avec un blueprint C4 (questions similaires au générateur, personnalisation du frontend, de la configuration et génération des Jenkinsfiles) et un générateur personnalisé (Helm chart, configuration Kubernetes)

Il y a officiellement [282 entreprises qui utilisent JHipster à ce jour](https://www.jhipster.tech/companies-using-jhipster/) et il existe également un [showcase](https://www.jhipster.tech/showcase/).
