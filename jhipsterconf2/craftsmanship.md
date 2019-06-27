---
title: François Delbrayelle - JHipster Conf 2 - JHipster Craftsmanship & TDD (notes)
---

# JHipster Craftsmanship & TDD

Sujets : JHipster, qualité, software craftsmanship, tests

17h25 - 18h10

Par [Hippolyte Durix](https://twitter.com/hdurix) (Ippon Technologies). Merci !

/!\ La vidéo complète devrait bientôt être en ligne sur YouTube.

Les TDD sont au coeur du software craftsmanship.

Hippolyte part de la pyramide de tests pour la granularité des tests automatisés et leur intégration dans JHipster :
- Tests unitaires : __JUnit 5__ et __Jest__
- Tests d'intégration : __Spring Boot Test__, base de données embarquée (via Docker par exemple) et __Jest__ mais différences TU/TI assez flou côté front
- Tests end-to-end (E2E) : __Protractor__ côté back et front

Qu'est-ce que le TDD ?
- Développer des features par les tests
- Les 3 étapes : écrire un test KO, écrire le code pour que le test soit OK, refactoriser

En guise de démo, Hippolyte crée une application web de prise de notes en Vue.js en TDD tout en passant par JHipster. L'application gère des Todo avec des attributs Label, Description et DueDate.

Hippolyte vante les mérites de la notation "Gherkin" avec le [Given-When-Then](https://martinfowler.com/bliki/GivenWhenThen.html) dans les tests unitaires ainsi que la possibilité de faire du test asynchrone en JavaScript avec async-await.
