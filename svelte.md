---
title: François Delbrayelle - BBL AXA - Des applications Front rapides et légères avec Svelte
---

# Des applications Front rapides et légères avec Svelte

Sujets : Svelte, front

10/09/2019 - 12h45 - 13h30

Par [Jérôme Boukorras](https://twitter.com/itupix) (AXA). Merci !

## Encore un framework JavaScript ?

Et oui, créé par [Rich Harris](https://twitter.com/rich_harris) mais pas de grosse entreprise derrière le framework.

## Comment ça fonctionne un framework JavaScript ?

Avant : un site traditionnel avec un serveur qui envoie des données au navigateur et on ajoute un peu de JavaScript et de CSS.
Depuis quelques temps on fait des SPA (single page applications).

## En quoi Svelte est différent ?

Moins de lourdeur et de dépendances externes.

## Découverte de Svelte en live coding

Dans le package.json on remarque déjà 2 choses :
- [Rollup](http://rollupjs.org/guide/en/) (créé également par Rich Harris) est utilisé plutôt que Webpack
- Svelte est en devDependencies et non dependencies

Les composants .svelte ont 3 parties : le style, le JavaScript et un template HTML un peu comme sur les composants monofichier de Vue.js. Les styles peuvent être scopés.
Les stores sont présents nativement et très facilement gérables.
La [documentation](https://svelte.dev/) est très bien fournie avec beaucoup d'exemples.
Jérôme nous montre ensuite un exemple d'application simple consommant une API ([personnages Marvel](https://developer.marvel.com/)).

## Cas d'utilisation

La version 3 est sortie.
Svelte est plutôt adapté à des petites applications mais un acteur de la grande distribution a récemment mis en production une grosse application e-commerce écrite avec ce framework.

## Conclusion

Pour les futurs projets pourquoi ne pas ajouter Svelte dans le comparatif ?

Questions : Peut-on tester les applications Svelte simplement ? Il faut des librairies externes.