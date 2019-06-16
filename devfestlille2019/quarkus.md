---
title: François Delbrayelle - DevFest Lille 2019 - De Java à un exécutable natif : GraalVM et Quarkus changent la donne (notes)
---

# De Java à un exécutable natif : GraalVM et Quarkus changent la donne

Sujets : JVM, Java, architecture microservices, serverless

15h40 - 16h40

Par [Emmanuel Bernard](https://twitter.com/emmanuelbernard) (Red Hat) et [Guillaume Smet](https://twitter.com/gsmet_) (Red Hat)

/!\ La vidéo complète devrait bientôt être en ligne sur la chaîne YouTube du [GDG France](https://www.youtube.com/user/francegdg).

Stack open-source pour Java : cloud-native, microservices, serverless. Approche [twelve-factor](https://en.wikipedia.org/wiki/Twelve-Factor_App_methodology), scalabilité.

__Synchronisation du code lors du run (hot replace).__

Extensions Quarkus : `mvn quarkus:list-extensions` (simplement un ajout de dépendances dans le pom).
Hibernate ORM avec Panache mais aussi Hibernate Validator, Resteasy, CDI... Hibernate Search + Elasticsearch intégrés récemment.

Configuration unifiée dans un seul fichier standard, typiquement la préconisation est de tout placer dans le `application.properties`.

L'annotation `@QuarkusTest` fait démarrer Quarkus pour les tests unitaires.

## Pourquoi Quarkus ?

Du monolithe aux microservices (scale to 1) aux fonctions (scale to 0).
Exemple : 1 monolithe ~ 20 microservices ~ 200 functions.
Besoin d'isoler les microservices ?
La vérité cachée à propos de Java et des containers, on n'est (n'était ?) pas bons jusqu'à aujourd'hui : temps de démarrage, mémoire...

Pour les fonctions serverless d'autres langages que Java sont aujourd'hui mieux adaptés : Node, Go voire Python.

Principaux avantages de Quarkus :
- __temps de démarrage ultra rapide__
- __Taille RSS (Resident Set Size ~ RAM)__ : Quarkus + GraalVM = 13 Mo ; Quarkus + OpenJDK = 74 Mo ; Cloud-native stack traditionnelle : 150 Mo
- basé sur les standards
- configuration unifiée
- 0 configuration externe
- compilation native
- unifie programmation impérative et réactive
- joie du développeur
- "supersonic subatomic Java"
- le meilleur des bibliothèques et des standards

Pour les microservices la taille mémoire compte plus que le temps de démarrage. C'est l'inverse pour les fonctions.

## GraalVM

Elimination du code mort d'où la taille réduite de l'exécutable natif. Le côté obscur : chargement des classes dynamique.

Un framework au démarrage :
- parse les fichiers de configuration
- scanne le classpath
- construit les objets du métamodèle

Le travail n'est réalisé qu'une fois : moins de mémoire, moins de temps de démarrage, limite la réflexion et les proxies dynamiques.

Observabilité : prêt pour ([OpenAPI et Swagger UI](https://quarkus.io/guides/openapi-swaggerui-guide), métriques avec Prometheus possible, health...) notamment grâce à Eclipse Microprofile.
