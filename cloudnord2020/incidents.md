# Et si ca tourne mal ? Recettes pour des applications résilientes

Sujets : Cloud Native

19/11/2020 - 9h45 - 10h30

Par [Christopher Maneu](https://twitter.com/cmaneu) (Microsoft). Merci !

Qu'est-ce qu'une application résiliente ?
- Capable de gérer ou anticiper la perte de données
- Exemple des liveness probes dans Kubernetes
- Résilience face aux dépendances

## Avant l'incident 

Qu'est-ce qu'on fait avant de se lancer ?
- Planifier ce qui peut mal se passer
- Se poser les bonnes questions en équipe : et si ? Identifier les dangers, évaluer les risques, préparer un plan, répeter. "From what if to failure mode analysis".
- Check-lists
- Pinnacle dive : plongée complexe à gérer
- Toujours plonger selon son niveau (expérience, profondeur, durée, ...) : changer UN paramètre à la fois

## Pendant l'incident

Quand les choses se passent mal, il y a un ordre de priorités : respirer (prendre du recul), flotabilité (comprendre ce qu'il se passe), remonter (remettre à niveau, sur pied).

Framework de priorité __TDODAR__ :
- Time (c'est aussi l'équipe)
- Diagnostics
- Options
- Decide
- Act/assign
- Review

Brownout strategies : quelles features de mon application je peux désactiver pendant une urgence ?

## Après l'incident

Discuter et faire un __post-mortem__ !