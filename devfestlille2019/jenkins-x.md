---
title: François Delbrayelle - DevFest Lille 2019 - Il faut sauver le soldat Jenkins ! (notes)
---

# Il faut sauver le soldat Jenkins !

Sujets : Jenkins, CI/CD, Kubernetes

14h00 - 15h00

Par [Nicolas de Loof](https://twitter.com/ndeloof) (Cloudbees)

/!\ La vidéo complète devrait bientôt être en ligne sur la chaîne YouTube du [GDG France](https://www.youtube.com/user/francegdg).

Le marketing de Cloudbees a préféré que le talk soit nommé "Jenkins X : Vers un Jenkins cloud-native", et pour cause !

Kubernetes sur Jenkins c'est une option mais pas tout Jenkins X.

Jenkins X n'est pas :
- Jenkins pour Kubernetes
- une variable avec plug-ins etc
- un projet complètement à part

Projet faisant partie de la [CD foundation](https://cd.foundation). Possibilité de l'installer classiquement ou serverless.

C'est une boîte à outils nécessaire __pour les applications modernes cloud-native__. L'un des avantages de Jenkins X : il pré-assemble ces outils.

Nicolas nous fait assez rapidement une démo :
`jx create cluster gke` ou `jx install` si cluster existant.
Jenkins reste un monolithe. Prow est utilisé pour la CI (pour gérer les webhooks github).
Config as code.
Github as UI.
Pipeline engine : rétrocompatibilité avec Jenkins classique via un Jenkinsfile (Jenkinsfile runner). Autre option pour le pipeline engine avec Tekton (Jenkins-x.yaml).
GitOps : "git as single source of truth". Automatisation du workflow sur git (par __pull requests__).

Extrait de la démo :
- `jx version`
- `jx create quickstart # lien avec le github, choix du quickstart`
- `jx get build logs`
- `jx get applications`
- `kubectl get services`
- `jx cloudbees`
