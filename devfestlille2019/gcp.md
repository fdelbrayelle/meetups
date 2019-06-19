---
title: François Delbrayelle - DevFest Lille 2019 - Comment la GCP m'a permis de sauver ma prod chez Mamie (notes)
---

# Comment la GCP m'a permis de sauver ma prod chez Mamie

Sujets : GCP, cloud

17h20 - 18h20

Par [Sylvain Nieuwlandt](https://twitter.com/an0rak_dev) (Sfeir). Merci !

/!\ La vidéo complète devrait bientôt être en ligne sur la chaîne YouTube du [GDG France](https://www.youtube.com/user/francegdg).

Retour d'expérience sur un incident de production détecté à distance, dans un moment inopportun, sans moyen d'intervenir... a priori ;)

Intérêts de GCP :
- coûts sensiblement réduits
- temps de maintenance réduit (temps, personnes)
- aucun impact sur le code métier
- facile de logger/débugger la prod sans interruption
- facile d'intervenir même avec un smartphone (avec l'application CloudConsole sur Android/iOS)
- facile de monter/scaler une infra

Conseils :
- hoster sur plus d'une région
- garder un maximum d'opérations dans la GCP (gratuit)
- utiliser le minimum de ressources
- se préparer à scaler ou avoir un DRP (disaster recovery plan)

SLA 99.9 % (sur l'infra hors PostgreSQL pour cet exemple, etc).

Stackdriver Debugger : ajout de logs à chaud en prod sans redéployer. Debug pas à pas possible également.
