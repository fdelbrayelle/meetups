---
title: François Delbrayelle - JHipster Conf 2 - What the heck are OAuth and OIDC? (notes)
---

# What the heck are OAuth and OIDC?

Sujets : JHipster, OAuth, OIDC

13h40 - 14h25

Par [Matt Raible](https://twitter.com/mraible) (Okta). Merci !

La vidéo complète est en ligne sur la chaîne YouTube de [Ippon Technologies](https://www.youtube.com/watch?v=Wrwa-5zx8pM).

Matt est développeur chez Okta (entreprise qui propose notamment des solutions d'authentification).

## OAuth 2.0 Overview

Pour l'authentification web, dans une authentification basique client/serveur, le serveur fait appel à un identity store pour valider les identifiants. [Fédération d'identité](https://www.ledecodeur.ch/2014/11/17/federation-identit/) avec un utilisateur qui communique avec SP et IDP. SAML 2.0 est un standard OASIS depuis 2005, un protocole de requête d'authentification. Basé sur XML (SOAP). "SAML = Web SSO".

Se pose le problème de la délégation d'identité.

> "OAuth c'est comme les cartes-clés des hôtels mais pour les applications."

Matt présente les différents termes de la terminologie OAuth :
- Acteurs
- Clients
- Serveurs d'autorisations
- Serveurs de resources
- Tokens (types : access ou refresh), OAuth ne définit pas le format d'un token)
- Scopes : 
- Consent
- Grants : implicit ("2 legged", ne supporte pas les refresh tokens), authorization code ("3 legged"), client credential, resource owner password (ne supporte pas les refresh tokens), assertion (voir SAML et SP/IDP) et device

Il y a différents canaux de flow : front (du côté du navigateur entre le propriétaire de la ressource, le client et le serveur d'autorisation) et back (entre le serveur d'autorisation, le client et le serveur de ressource).

Il y a 6 flows différents, il faut donc se poser les bonnes questions.

Quelques ressources intéressantes :
- [OAuth 2.0 Debugger](https://oauthdebugger.com)
- [OAuth 2.0 Playground](https://oauth.com/playground)

Il y a des problèmes de sécurité communs avec OAuth 2.0 :
- Trop d'entrées qui nécessitent de la validation (token hijacking avec CSRF, codes d'autorisations manquants ou tokens à travers des redirections)
- Leaking client secrets
- Unbounded & bearer tokens

__OAuth 2.0 n'est pas rétrocompatible avec OAuth 1.0 et ce n'est pas un protocole d'authentification.__ Avec OAuth 2.0 seul il n'y a pas de login et d'information à propos de l'utilisateur. Mais c'est devenu un protocole de pseudo-authentification devenu célèbre grâce à Facebook Connect et Twitter.

## Open ID Connect (OIDC)

__OpenID Connect est pour l'authentification. OAuth 2.0 est pour l'autorisation.__

Open ID Connect <-> OAuth 2.0 <-> HTTP

Il y a aussi des flows et des tokens sur OIDC. Les tokens devraient être utilisés pour créer des sessions.

En complément :
- [AppAuth](https://appauth.io/)
- [Okta Developer](https://github.com/oktadeveloper)
- [Keycloak](https://www.keycloak.org/)
- [OAuth 2.0 and OpenID Connect (in plain English)](https://www.youtube.com/watch?v=996OiexHze0)

## Et JHipster dans tout ça ?

Voir les [posts de blog](https://developer.okta.com/search/#stq=jhipster) et vidéos de Matt sur JHipster.

Support du talk sur : [https://speakerdeck.com/mraible/what-the-heck-are-oauth-and-oidc-jhipster-conf-2019](https://speakerdeck.com/mraible/what-the-heck-are-oauth-and-oidc-jhipster-conf-2019)
