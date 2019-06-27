---
title: François Delbrayelle - JHipster Conf 2 - JHipster et Kafka : un mix détonnant ! (notes)
---

# JHipster et Kafka : un mix détonnant !

Sujets : JHipster, Kafka

18h15 - 19h00

Par [Florent Ramière](https://twitter.com/framiere) (Confluent). Merci !

/!\ La vidéo complète devrait bientôt être en ligne sur YouTube.

## Qu'est-ce que Kafka ?

Il faut d'abord se poser la question de ce que l'on fait, ce que l'on manipule et comment. Les silos expliqués par le concept de "Data Gravity". Kafka est un moyen de casser des silos qui nous empêchent d'aller vite. LinkedIn est à l'origine de Kafka qui s'est aperçu que son architecture était chaotique. Pourquoi ne pas utiliser ActiveMQ ou des alternatives qui existaient avant ? En un mot : la __volumétrie__. Par exemple 4 millions de messages environ transitent sur Netflix par seconde. Kafka est une plate-forme contenant entre autre des clusters, Kafka Connect, Kafka Streams et KSQL : publish & subscribe, store & ETL et process.

Voir l'article [Turning the database inside-out with Apache Samza](https://www.confluent.io/blog/turning-the-database-inside-out-with-apache-samza/).

Propriétés importantes en Kafka : immutabilité, consistence, durabilité, résilience, scalabilité...

Il existe aussi un modèle de maturité pour Kafka :
- Apprendre Kafka
- Aller en production avec
- Répondre à un besoin critique
- "Break slice"
- "Stream everything"

Il est également nécessaire de comprendre la business value et où l'on se situe avec son projet de manière macro dans un système donné.

Voir également le talk sur les [patterns et anti-patterns Kafka à Devoxx](https://www.youtube.com/watch?v=rp537D69CYw)