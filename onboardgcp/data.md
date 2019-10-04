---
title: François Delbrayelle - On Board GCP - Data et Stockage SQL
---

# Data

Sujets : Cloud, GCP, Data, Bases de données

01/10/2019 - 14h00 - 14h30

Par [Vincent Dolez](https://twitter.com/dolez_v) et [Aurélien Allienne](https://twitter.com/sn0rks) (Sfeir). Merci !

Le stockage ?

__Persistent Disk__ pour gérer et sizer l'espace disque.

__Cloud Storage__ pour le stockage de larges objets binaires, possibilité de brancher à un Pub/Sub, faire du machine learning... Les fichiers sont organisés en bucket au nom unique. Différentes classes de stockage (multi-régional, régional, nearline, coldline et bientôt icecold).

## Stockage SQL

__Cloud SQL__ est un RDBMS managé (MySQL, PostgreSQL et bientôt Microsoft SQL Server). Réplication de données automatique, haute disponibilité...

Différences entre scaling vertical (plus de taille) ou horizontal (plus de serveurs) ?

__Cloud Spanner__ est pensé pour scaler horizontalement. Réplication synchrone globale (multi-continents), forte consistence des données... Répond au théorème CAP : Spanner garantit les trois contraintes (cohérence, disponibilité et tolérance au partitionnement). Spanner prend le meilleur du relationnel et du non-relationnel.

__Cloud Memorystore__ est un data store pour Redis.

__Cloud Datastore__ pour scaler horizontalement du NoSQL.

__Cloud Bigtable__ pour scaler du pétabyte (base de données NoSQL serverless).
