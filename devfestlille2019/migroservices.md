---
title: François Delbrayelle - DevFest Lille 2019 - Des microservices aux migroservices (notes)
---

# Des microservices aux migroservices

Sujets : Architecture microservices, DevOps, CI/CD...

10h00 - 11h00

Par [François Teychené](https://twitter.com/fteychene) (Saagie). Merci !

/!\ La vidéo complète devrait bientôt être en ligne sur la chaîne YouTube du [GDG France](https://www.youtube.com/user/francegdg).

## C'est quoi un microservice ?

Il faut commencer par parler des monolithes : ça coûte et c'est lourd mais ça répond très bien à la plupart des besoins.

## Quels problèmes on cherche à résoudre avec les microservices ?

Un __monolithe est extrêmement lourd et complexe à faire évoluer__. Lorsque l'on cherche à faire évoluer une application c'est complexe.
Quand doit-on livrer et mettre tout le monde d'accord quand l'application devient trop grosse et difficile à faire évoluer ?

Être __scalable__ (pouvoir faire augmenter le nombre d'instances facilement).

L'image "evolution of software architecture" est présentée (spaghettis > lasagnes > raviolis > ?) :

![Evolution of software architecture](evolution-architecture.png)

Martin Fowler parle aussi des [microservices](https://martinfowler.com/articles/microservices.html) sur son site.

L'idée est de diviser le monolithe en petites parties avec maillage pour communiquer entre elles.

Netflix est pionnier sur l'utilisation des microservices.

Gestion de la complexité : essentielle, obligatoire, accidentelle (d'après Arnaud Lemaire).

Interactions : multiplication de complexité. L'idée des microservices est de séparer les complexités. Et de travailler sur les scopes fonctionnels en travaillant sur les types de complexité : moins de complexité essentielle, plus de complexité obligatoire et moins de complexité accidentelle.

Dès lors on peut se demander comment résister aux microservices ?

## Constats à l'adoption

Plusieurs questions se posent rapidement une fois les microservices adoptés :
- Comment scoper un service ?
- Quelle bonne taille ?
- Comment un microservice est-il couplé ?
- Comment les microservices doivent-ils communiquer ?

On s'aperçoit vite qu'on a des __"migroservices"__. Il faut accepter que les microservices c'est pas facile.

Il est __nécessaire de changer d'état d'esprit__ pour les adopter.

Besoin de connaître un écosystème important de technologies. Ceci dit les maîtriser ne permettra pas pour autant de bien gérer ses microservices.

Les microservices ce n'est pas une bataille technique.

Prendre une partie d'une application en couches ("lasagnes") pour en extraire des microservices ça ne fait que déplacer le problème et ajouter du __chaos__.

## Comment s'en sortir ?

__Il faut que chaque microservice réponde à une problématique métier__. C'est important de différencier les frontières techniques et fonctionnelles (plus importantes).
Se pose la problématique des liens entre microservices. L'échec n'est pas une option. Le réseau n'est pas fiable (pire source d'entropie d'un système). 

L'un des principaux problèmes est le recovery. L'idée du __circuit breaker__ est intéressante mais que doit-on renvoyer comme valeur fonctionnelle en cas d'erreur ?
Le format des messages compte autant que la manière de communiquer entre microservices.

Protocoles maîtres : format - actions - échanges. Est-ce synchrone ? Asynchrone ? Peut-on réduire le nombre d'appels ?
Un microservice reste une application à part entière, parfois avec des données partagées. Qui est responsable de la donnée ? De mettre à jour le schéma ?

Idée de faire porter la base de données à un monolithe ? Mauvaise idée. Essayer de ne pas partager la donnée entre systèmes. L'idée n'est pas pour autant d'avoir une base de données par service mais au moins de séparer les tables par microservices.

Comment concevoir son workflow métier ?
Un monolithe coûtera toujours moins cher que des microservices étant donné qu'il faut plusieurs instances.
Et si on parle de V1 -> V2, de blue/green, de canary ou d'A/B testing ? Oui mais besoin de maîtriser son réseau à la perfection.

Solutions possibles :
- Service discovery (simple) avec sôzu par exemple ; la plupart des technologies de type service mesh comme Istio se basent là dessus.
- Orchestrateur : tout le monde pense à Kubernetes mais non en fait il n'est pas forcément nécesaire d'avoir des containers. Possibilité avec Jenkins + Ansible. Nécessité d'automatiser l'orchestration.

Problématique de monitorer : comment trouver le microservice en cause dans les logs ?
Dans la définition de Martin Fowler il faut automatiser la totalité de la chaîne.

En résumé :
- Pas là pour dire que les microservices il ne faut pas en faire. Attention il ne faut pas s'enflammer sur le gain qu'ils apportent. Investissement lourd et important. Savoir ce que l'on fait.
- Se poser les bonnes questions : Qu'est-ce que l'on y gagne ? Qu'est-ce que les utilisateurs y gagnent ?
- Voir [tweet du 14/07/2O18](https://twitter.com/Maziar/status/1047344181239316480) : il faut des microservices pour résoudre les monolithes, il faut Docker pour les microservices, il faut Kubernetes pour Docker.
- Bounded context, loosely coupled, ownership, small & focused, protocal portability, automation.
- Si besoin d'être sur le même langage : pas forcément les microservices.
