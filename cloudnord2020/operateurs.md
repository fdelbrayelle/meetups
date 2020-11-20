# Les opérateurs Kubernetes : opérer des services Cloud Native à grande échelle

Sujets : Kubernetes, Cloud Native

19/11/2020 - 13h45 - 14h30

Par [Horacio Gonzalez](https://twitter.com/LostInBrittany) (OVHCloud). Merci !

Operating Kubernetes : easier said than done.

C'est quoi "opérer" des micro-services ? Derrière un simple déploiement déclaratif en YAML ?
Utiliser un package manager comme Helm. Les charts Helm c'est de la configuration. Opérer c'est plus que des installations et upgrades.
Comment automatiser les opérations humaines ?
Un contrôleur Kubernetes c'est une boucle de contrôle qui vérifie l'état courant et l'état désiré et fait les changements désirés.
Définitions de ressources personnalisées en utilisant l'API étendue de Kubernetes avec les CRD.
Kubebuilder pour construire des APIs Kubernetes avec des CRD.
Catalogue d'opérateurs libres sur [operatorhub.io](operatorhub.io).
OVHcloud utilise Harbor Operator (registry docker d'images mais aussi de charts Helm).