# Github Actions : enfin des pipelines accessibles aux développeurs

Sujets : GitHub Actions - DevOps

19/11/2020 - 15h45 - 16h30

Par [Antoine Méausoone](https://twitter.com/ameausoone) (Sfeir). Merci !

Un petit historique des pipelines : Scripts Ant, Jenkins, Plugins Jenkins, scripts shell, GHA !

Un répertoire `.github/workflows/<pipeline.yaml>` (plusieurs pipelines possibles).

Pipelines basés sur des events (points d'entrée). Possibilité d'utiliser des actions courantes (checkout, github-script, automation...).

Développer sa propre GitHub Action via les templates `actions/javascript` ou `actions/typescript`. Exemple de `hashicorp/vault-action`.

Problèmes de sécurité : the "left-pad" effect (une action "left-pad" a été supprimée brutalement et a cassé plein de pipelines) = fork action, the "event-stream" action (bitcoin sur les actions par exemple) = penser à dependabot ; `persist-credentials: false` pour utiliser checkout en lecture seule, set secrets, `GITHUB_TOKEN`...