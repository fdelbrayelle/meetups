---
title: François Delbrayelle - On Board GCP - Compute et IaaS
---

# Compute et IaaS

Sujets : Cloud, GCP, Compute, IaaS

01/10/2019 - 11h15 - 12h00

Par [Tanguy Baudrin](https://twitter.com/TanguyBaudrin) et [Jérôme Nahélou](https://twitter.com/JNahelou) (Sfeir). Merci !

## Compute

IaaS construit pour l'ère du cloud avec Compute Engine. Groupes d'instance managés qui vont scaler horizontalement la flotte de machines (CPU, charge HTTP, métriques custom...).

Google propose une facturation avec réduction sur volume au fil du temps.

Il existe des Preemptible VMs totalement sans état (beaucoup moins cher, mais Google peut arrêter les machines sans prévenir...). Ce sont des machines temporaires (moins de 24h).

__Cloud GPU__ est pratique pour du machine learning par exemple.

## IaaS

Plusieurs raisons d'automatiser l'infrastructure : répétition, déployer de plus en plus vite, solutions scalables, grosses architectures...

Sur la GCP c'est possible de créer des images de base.

Utiliser __Cloud SDK__ (commande `gcloud init` pour l'initialiser). Plusieurs commandes utiles : `gcloud`, `gsutil`, `bq` et `kubectl`.

La philosophie est "Infrastructure as a code". Le Deployment Manager est accessible via Cloud Console. Un fichier texte de configuration est uploadé dans Deployment Manager et les ressources sont provisionnées dans GCP.

Deployment Manager (gratuit, serverless, intégré à GCP, APIs discovery/driven) vs Terraform (open-source, multi plate-formes, Terraform Cloud).

Cloud Marketplace permet de trouver des solutions prêtes à déployer (par exemple on peut chercher un load-balancer "F5").

Retour du client de Jérôme sur la mise en place de l'IaaS au sein du pôle infrastructure chez Adeo.
