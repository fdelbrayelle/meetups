---
title: François Delbrayelle - On Board GCP - Network / Security
---

# Network / Security

Sujets : Cloud, GCP, Réseau, Sécurité

01/10/2019 - 10h45 - 11h15

Par [Jérôme Nahelou](https://twitter.com/JNahelou) (Sfeir). Merci !

## Réseau

Même si GCP permet une abstraction du réseau, il existe bel et bien mais est configurable tout de même en déployant des composants virtuels via les interfaces.

Google est propriétaire de ses fibres optiques continentaux et d'un millier de points de connexion (cache CDN) au plus près de l'utilisateur.

Différentes offres : standard tier, premium tier (recommandé et par défaut).

GCP est organisée en régions et zones (la latence entre deux zones est estimée à moins de 5 ms). Il est possible de déployer des données sur plusieurs régions pour être au plus proche des utilisateurs.

Définir un Virtual Private Cloud Network pour plus de flexibilité. Google Cloud VPCs sont globaux, les sous-réseaux sont régionaux. GCP offre plusieurs options de connectivité : VPN, interconnexion, peering...

__Cloud DNS__ permet de gérer des zones DNS.

## Sécurité

GCP adopte un modèle de sécurisation par couche (ne pas sécuriser que le datacenter en périphérie avec un parefeu) : comment protéger chacun des éléments ?

L'approche est "trust nothing". Le chiffrement est intégré par défaut. Le Project Zero chez Google est une équipe pour détecter les failles zero day.

Une part importante est représentée par Audit Logs.

Le principe du privilège le plus petit est important.
