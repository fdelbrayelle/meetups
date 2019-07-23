---
title: François Delbrayelle - JHipster Conf 2 - Angular, React, Vue.js : il n'en restera qu'un (notes)
---

# Angular, React, Vue.js : il n'en restera qu'un

Sujets : JHipster, Angular, React, Vue.js

14h30 - 15h15

Par [William Marques](https://twitter.com/wylmarq) (Ippon Technologies). Merci !
Par [Christopher Dionisio](https://twitter.com/chris_dns) (Ippon Technologies). Merci !
Par [Sahbi Ktifa](https://twitter.com/sahbiktifa) (Malt). Merci !
Par [Pierre Besson](https://twitter.com/pibesson) (Ippon Technologies). Merci !

D'abord un petit historique des frameworks front dans JHipster est fait :
- AngularJS était le premier a être intégré, puis ensuite __Angular__ depuis février 2017.
- __React__ : feature majeure de JHipster 5 au printemps 2018.
- __Vue.js__ : blueprint avec JHipster 6 depuis le printemps 2019, pas (encore) dans le générateur principal.

Points communs :
- Langage : c'est __TypeScript__ qui a été choisi (le gros intérêt c'est que l'on n'a pas besoin de Babel pour transpiler vers ES5)
- Module bundler : __Webpack__ avec une configuration modularisée et exposée
- __Folder-by-feature__ avec une plus grande modularité et une navigation facilitée
- Tests automatisés E2E avec __Protractor__ (principalement pour Angular mais aussi utilisé sur React et Vue.js) et tests unitaires avec __Jest__ (avant c'était Karma)

Différences :
- Dans Angular : composants utilisés (@Componant avec un sélecteur, un template et une feuille de style), templates externes, directives, injection de dépendances...
- Dans React : composants également avec une différence syntaxique (Facebook a fait le choix de ne pas séparer le HTML et la logique en créant JSX) et l'importance du DOM virtuel
- Dans Vue.js : composants AUSSI avec des différences, il n'y a pas de JSX mais la notion de single-file component avec template, la librairie est légère et il y a une certaine rapidité d'exécution

Gestion de l'état :
- Dans Angular : passer des services (singletons @Injectable) ou en Redux-like avec NgRx (pour écouter sur le store en passant via les Observables)
- Dans React : grosse nouveauté de 2019 (version 16.8) avec les Hooks et setState() ou bien Redux
- Dans Vue.js : VueX (inspiré de Elm) ou Redux (out-of-the-box mais ne connaît pas le contexte Vue)

Routing :
- Dans Angular : on définit des routes constituées d'URL, un composant associé et des données (lazy loading par modules, gestion des rôles par les guards et déclaration des routes par module)
- Dans React : à peu près équivalent avec une balise JSX <Route ...> avec en particularités une gestion des rôles via le PrivateRouteComponent et du lazy loading par modules (admin + entités)
- Dans Vue.js : VueRouter (on définit les routes associées aux composants) avec en particularités la gestion d'attributs customs sur les routes et du lazy loading par défaut par Path/Composant

HTTP :
- Dans Angular : HttpClient (service injectable) qui fonctionne via des Observables (et non des Promises), la possibilité d'annuler les requêtes une fois lancées et des notions de flux réactifs
- Dans React : Axios (librairie externe) et fonctionnement via des Promises (et non des Observables), utilisation très simple 
- Dans Vue.js : idem que React

Outils de développement :
- Dans Angular : Augury compatible Chrome/Firefox, permet de voir l'arbre des composants, les routes, les injections...
- Dans React : React DevTools + Redux DevTools
- Dans Vue : Vue DevTools

Déploiement :
- Tout pareil (déployer les fichiers statiques sur un serveur)

Une démo est faite en générant 3 applications identiques fonctionnellement (entités notamment) sur les 3 frameworks pour comparer ce qui est généré et les performances (temps de build webpack, taille des bundles avec webpack-bundle-analyzer, rapports de performance en production avec les DevTools, les métriques et duo Puppeteer/Lighthouse sur la page d'accueil et les pages d'entités).

Résultats :
- Temps de build : vainqueur Angular
- Taille du bundle : vainqueur Vue.js (où il y a beaucoup plus de lazy loading)
- Performances : round 1 home page (avantage Vue.js notamment pour les temps de chargement), round 2 entités (à peu près équivalent)

Finalement le grand vainqueur semble être clairement Vue.js même s'il faut rester pragmatique et que c'est à chacun de se faire sa propre idée en pesant les avantages et inconvénients de chacun de ces 3 frameworks qui restent tous excellents.

## Angular

- (+) TypeScript fourni de base
- (+) Familier pour les développeurs Java
- (+) Programmation réactive (RxJs)
- (+) All-in-one (HTTP, Routeur...)
- (-) Volumineux
- (-) Moins performant (potentielle amélioration avec Ivy)

## React

- (+) DOM virtuel
- (+) JSX
- (+) Rapide
- (+) Communauté
- (-) Prise en main simple pour les petites applications, plus compliquée sur les conséquentes

## Vue

- (+) Vainqueur des benchmarks
- (+) Single File Component
- (+) Montée en compétences facile
- (+) Vue 3 (qui doit bientôt sortir) ?
- (-) Peu de variété en contributeurs mis à part la core team
- (-) Vue 3 ?

Conclusion - Pourquoi JHipster propose ces 3 frameworks :
- Parce que c'est hype
- Pour proposer du choix
- Pour pouvoir comparer les solutions

L'avenir dans JHipster : continuer d'étudier les statistiques, observer la dynamique de chaque framework, amélioration continue... Au final les 3 frameworks sont tous de très bons choix et permettent de faire grosso-modo la même chose.
