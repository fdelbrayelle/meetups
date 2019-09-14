---
title: François Delbrayelle - Sfeir Lunch 3 - Improve your workflow with GCP Cloud Build - Faire cohabiter Java et Haskell en douceur
---

# Improve your workflow with GCP Cloud Build - Faire cohabiter Java et Haskell en douceur

Sujets : GCP, CI/CD, Haskell, programmation fonctionnelle

12h30 - 13h15

Par [Aurélien Allienne](https://twitter.com/sn0rks) (Sfeir) et [Julien Debon](https://twitter.com/Sir4ur0n) (Décathlon). Merci !

## Talk 1 - Improve your workflow with GCP Cloud Build

__Cloud Build__ est un outil d'intégration continue qui simplifie les opérations de build.
Aurélien part d'un projet Python simple avec Flask déployé sur une cloud function.
Il faut ajouter un fichier "cloudbuild.yaml" à la racine du projet avec la bonne configuration sur GitHub pour communiquer avec GCP et trigger un évènement. Cela fonctionne également sur GitLab.
Cloud Build est un peu comme GitLab CI et basé sur des images Docker.
Il n'existe pas de templates prêts pour Cloud Build et son fichier de configuration : cela représente un léger inconvénient par rapport aux pipelines Groovy sur Jenkins où on peut les mutualiser.

## Talk  2 - Faire cohabiter Java et Haskell en douceur

Julien prend l'exemple d'une application de calcul des prix chez un client de la grande distribution sur lequel il a mené avec son équipe une migration itérative de code Java vers des fonctions Haskell.
La programmation fonctionnelle est assez limitée avec Java 8 et même avec Vavr en termes de pattern matching, de génériques et puis une méthode n'est pas une fonction.
Pourquoi Haskell parmi les autres comme F# ? C'est celui qui paraissait le plus fonctionnel pour son équipe.
L'équipe a utilisé [Scientist4j](https://github.com/rawls238/Scientist4J) de GitHub pour les refactorings.

Les plus :
- (+) Bien adopté par l'équipe
- (+) Opportunité pour l'entreprise

Les moins :
- (-) Concepts avancés
- (-) Beaucoup de pratique

Conclusion : Il s'agit là globalement d'une bonne expérience surtout qu'une autre équipe fait maintenant du Haskell dans l'entreprise.