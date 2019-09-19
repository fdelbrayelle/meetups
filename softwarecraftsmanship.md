---
title: François Delbrayelle - BBL AXA - L’impact du mouvement software craftsmanship sur la qualité logicielle
---

# L’impact du mouvement software craftsmanship sur la qualité logicielle

Sujets : Software craftsmanship, qualité, clean code|architecture|coder|agile, tests

19/09/2019 - 12h45 - 13h45

Par [Arthur Magne](https://twitter.com/ArthurMagne) (Promyze). Merci !

## C'est quoi le software craftsmanship ?

- Responsabilité
- Autonomie
- Amélioration continue
- Échange et partage
- Satisfaction du client

C'est une pratique en pleine explosion, un mouvement qui pousse un état d'esprit.

## L'historique

- 1992 : "What Is Software Design?" (Jack W. Reeves)
- 1999 : "The Pragmatic Programmer" (Andrew Hunt et David Thomas)
- 2001 : "Software Craftsmanship" (Pete McBreen)
- 2001 : [Manifeste Agile](http://manifesteagile.fr/index.html) qui mise plutôt sur l'humain que sur la technique
- 2008 : Craftsmanship over Execution (Markus Gärtner)
- 2009 : [Manifesto for Software Craftsmanship](http://manifesto.softwarecraftsmanship.org/) qui remet la technique sur le devant de la scène
- 2014 : "The Software Craftsman: Professionalism, Pragmatism, Pride" (Robert C. Martin)
- 2008, 2011, 2017 et 2019 : Livres "Clean Code|Coder|Architecture|Agile"

## Et 10 ans plus tard ?

Il y a une communauté vivante :
- Groupes (JUG...)
- Meetups
- BBL
- Coding dojos
- Conférences

## Qualité logicielle, c'est quoi ?

Elle se retrouve dans trois grands domaines : l'architecture, les tests et le clean code.

### Architecture

- pair programming
- code review
- coding dojo
- lectures diverses

### Tests

Il en existe différents types selon les besoins : unitaires, d'intégration, IHM...
Arthur nous présente un graphique montrant la __corrélation entre un nombre de tests élevé et un nombre de bugs faible__.
La couverture de code c'est bien mais __attention à la pertinence du contenu des tests__.
Le tests de mutation permettent génération de mutants ([Stryker](https://stryker-mutator.io/) pour JavaScript par exemple, ils existent aussi pour Java et d'autres langages).
Le GitHub [awesome-mutation-testing](https://github.com/theofidry/awesome-mutation-testing) recense les frameworks de tests de mutation.

### Clean code

- TDD first
- Pas de commentaire, code simple (KISS, DRY)
- Code smells (voir le livre "Clean Code")

Il y a une __corrélation entre le nombre de bugs et les code smells__. La dette technique est détectée notamment avec SonarQube.

## Constats et tendances

L'étude ["Le coefficient développeur"](https://stripe.com/reports/developer-coefficient-2018) de 2018 sur la qualité logicielle montre que __les développeurs passent 42 % de leur temps à la maintenance__.
L'impact de la dette technique sur les développeurs est énorme : découragement, lenteur, perte de créativité, érosion des compétences...
Pourquoi la dette augmente ? À cause de certaines règles, parfois de nouvelles technologies, des différences de niveaux dans l'équipe...

La tendance actuelle est à la réduction du risque, des coûts et à la valorisation de la qualité logicielle.

__Attention à la poudre aux yeux :__
- SonarQube tout seul ce n'est pas (forcément) faire de la qualité
- Docker et Jenkins ce n'est pas (forcément) faire du DevOps
- JIRA n'est pas (forcément) agile, etc

## Comment favoriser la qualité ?

- Valoriser actions positives
- Définir une stratégie collaborative
- Ajouter du fun avec la "gamification"

Arthur travaille sur et avec la plate-forme collaborative [Themis](https://promyze.com/themis/) développée par sa société Promyze.

## En synthèse

- Les pratiques évoluent
- Il y a une hétérogénéité des équipes et des entreprises en terme de qualité logicielle
- Il faut diffuser les pratiques pour ne pas voir toujours les mêmes personnes aux Meetups