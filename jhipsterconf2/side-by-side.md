---
title: François Delbrayelle - JHipster Conf 2 - JHipster side-by-side in practice (notes)
---

# JHipster side-by-side in practice

Sujets : JHipster

16h35 - 17h20

Par [David Steiman](https://twitter.com/theonlyscrippi) (K-TEL Communications GmbH). Merci !

/!\ La vidéo complète devrait bientôt être en ligne sur YouTube.

Il y a un côté obscur de JHipster : les applications personnalisées ont un besoin constant de changements de code qui peuvent être mal regénérés. L'an passé Antonio Goncalves a donné un [talk](https://www.youtube.com/watch?v=9WVpwIUEty0) à la JHipster Conf 2018 pour parler de l'approche side-by-side. L'idée est d'étendre les fichiers générés dont on a besoin = peu ou pas de changements dans les fichiers générés.

On rentre dans le vif du sujet tout de suite avec une démo d'une application monolithique pour gérer des groupes de musique :
- Import d'entités de base pour commencer
- Dans l'interface on peut bien ajouter des groupes et des morceaux et voter pour eux
- Création d'une nouvelle interface BandExtendedRepository héritant de BaseRepository avec une méthode spécifique
- Possibilité d'étendre même les ressources REST

Derrière le side-by-side :
- Permet la personnalisation du code généré par l'héritage
- Regénération/upgrade de JHipster plus sûrs
- Que faire en cas de grands changements des conceptions fonctionnelles ?

Penser également aux blueprints corporate pour les stacks techniques spécifiques et pour implémenter des spécifications métiers corporate.
