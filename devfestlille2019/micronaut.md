---
title: François Delbrayelle - DevFest Lille 2019 - Micronaut, le framework JVM ultra-light du futur (notes)
---

# Micronaut, le framework JVM ultra-light du futur

Sujets : Architecture microservices, serverless

15h10 - 15h40

Par [Olivier Revial](https://twitter.com/pommedouze) (Stack Labs). Merci !

/!\ La vidéo complète devrait bientôt être en ligne sur la chaîne YouTube du [GDG France](https://www.youtube.com/user/francegdg).

Reprend le meilleur de Spring, Grails et Spring Boot :
- injection de dépendances
- auto-configuration
- découverte de services

Sans les points moins bien, et donc :
- en limitant la réflexion et des proxies
- avec une meilleure empreinte mémoire
- avec un temps de démarrage largement amélioré

En Kotlin et en Java : Micronaut se base sur les processeurs d'annotations et en Groovy sur les transformations AST.
Micronaut se base sur la compilation AOT (pas de réflexion).
La JVM est toujours gérée mais la cible est surtout les applications natives via GraalVM (et donc possible seulement si pas de réflexion au runtime).

Outil `mn` en ligne de commandes pour manipuler Micronaut.

Micronaut est cloud-native.

Outil [siege](https://github.com/JoeDog/siege) pour auditer les requêtes et plus encore.

En résumé :
- jeune mais évolue beaucoup
- container ready
- serverless
- certains composants peuvent manquer mais devraient arriver
- support GraalVM partiel car projet GraalVM expérimental
- projet qui risque de tirer la communauté dans le bon sens pour les temps de démarrage notamment

Support des démos sur [http://github.com/orevial/hello-micronaut](http://github.com/orevial/hello-micronaut)
