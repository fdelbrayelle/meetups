---
title: François Delbrayelle - JHipster Conf 2 - Programmation réactive avec JHipster, c'est parti ? (notes)
---

# Programmation réactive avec JHipster, c'est parti ?

Sujets : JHipster, programmation réactive

15h20 - 16h05

Par [Christophe Bornet](https://twitter.com/cbornet_) (CDiscount). Merci !

/!\ La vidéo complète devrait bientôt être en ligne sur YouTube.

Il est d'abord important de __distinguer concurrent (en concurrence sur un même CPU) et parallèle (plusieurs CPU par exemple)__. Concurrence : threads vs boucle événementielle (pendant longtemps les threads ont été préférés).

Pourquoi faire de la boucle événementielle ?
- Pour la __scalabilité__ : avoir moins de threads et donc moins de RAM utilisée : voir `java -XX:+PrintFlagsFinal -version | grep ThreadStackSize`, 1 Mo de RAM réservée par Thread ; impact des changements de contexte (réel ?)
- __Accès concurrent__ aux ressources partagées simplifié

Penser programmation asynchrone avec :
- Callbacks -> "callback hell", "pyramid of doom"
- Future puis CompletableFuture pour des objets de cardinalité 1, pas de streams
- RxJava1/Observable pour des streams mais pas de back pressure (en gros : ce qui permet qu'un publisher ne suralimente pas des subscribers) non-bloquante
- Reactive Streams : streams avec back pressure non-bloquante

Les Reactive Streams utilisent le modèle Pub/Sub (publisher/subscriber) : la librairie Reactor avec les Mono/Flux ou Spring 5 avec les APIs réactives basées sur Reactor.

Les premiers pas dans JHipster :
- Première tentative : wrapper les RequestMapping dans Mono/Flux sur une application Spring WebMVC, ça n'a pas marché on ne peut pas mélanger WebMVC et WebFlux dans la même application. Tout le code doit être écrit en réactif. Bloquer est devenu interdit dans certains pools de threads. __Du coup refactoring Big Bang !__
- L'option réactive est en cours de développement : `yo jhipster --experimental` puis choisir application réactive dans type d'application. Peu de contributeurs, voir l'issue [TODO : Reactive/Webflux support #7608](https://github.com/jhipster/generator-jhipster/issues/7608).

Ce qui change en réactif dans JHipster :
- L'authentification réactive : Spring Security -> Reactive Spring Security, ReactiveSecurityContextHolder @EnableWebFluxSecurity, etc... JWT, HTTP Session c'est OK mais __OAuth 2.0 et OIDC tout reste à faire__ (contributions acceptées et récompensées).
- Accès aux bases de données réactif : Reactive Spring Data OK (réactif et non réactif peuvent cohabiter), MongoDB OK, Cassandra OK, Couchbase OK, ... Pour __SQL TODO__ : JDBC est bloquant, on peut contourner en wrappant dans un pool de threads, JPA/Hibernate reposent sur JDBC et donc sont bloquants, ADBC et R2DBC en cours de développement avec drivers pour PostgreSQL, MS SQL, MySQL, performances pas très bonnes pour le moment et ce ne sont pas des ORM. Objectif JHipster pour l'instant UserRepository sans support pour les relations pour le moment.
- Autres fonctionnalités OK : ressources statiques, CORS, entêtes HTTP de contrôle de cache, gestion langue/locale, gestion utilisateur, actuateurs, métriques, etc.
- Autres fonctionnalités KO : audit, cache, swagger-ui

Prochaines étapes :
- __rendre le code "production ready" et sortir de l'expérimental__ (supprimer le code d'audit, étudier le cache réactif et probablement le supprimer pour le moment, désactiver le générateur d'entités, supprimer swagger-ui)
- __développer les options manquantes__ (SQL, OAuth 2.0, OIDC, Elastic Search, Kafka, WebSockets)
- développer le générateur d'entités réactives (avec/sans DTO, avec/sans service, tests, paginations) : __gros morceau__

À explorer :
- Coroutines et Fibers & Continuations (JVM [Project Loom](../devfestlille2019/fibers-continuations.md))
- Protocoles avec un bon support du streaming (gRPC et RSocket)

Retour d'expérience sur le développement d'applications réactives :
- Courbe d'apprentissage difficile
- Pile d'appels cryptique
- Pas de debug pas à pas
