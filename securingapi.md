---
title: François Delbrayelle - Ch’ti JUG - Securing your API - From basics to beyond
---

# Securing your API - From basics to beyond

Sujets : API, sécurité, OAuth2, OIDC, JWT, OWASP

12/09/2019 - 19h00 - 20h00

Par [Alexandre Faria](https://twitter.com/lusoalex_) (Décathlon). Merci !

Les API sont partout. Elles sont prises pour cible par les attaquants (dans le top 10 du prochain draft OWASP).

Quels sont les risques ? Vol d'identité, indisponibilité du service, pénalités financières...

Quelques actions basiques à appliquer : HTTPS, headers, véifier le [top 10 OWASP](https://www.owasp.org/index.php/Top_10-2017_Top_10) (le dernier rapport date de 2017),

Alexandre nous propose un rapide exemple d'injection via une API en JavaScript et en Java.

L'une des premières bonnes pratiques est de mettre en place une brique dédiée pour authentification autorisation avec Identity Provider d'une part et d'autre part une API management.

## Brique d'authentification et d'autorisation

Il est nécessaire de bien faire la différence entre authentification et autorisation et accessoirement entre un code HTTP 401 et un code HTTP 403.
Il faut utiliser FIDO et 2FA, les captcha...

Mais surtout aujourd'hui les incontournables sont OAuth 2 et Open ID Connect (OIDC) qui est une extension de OAuth2.
Ces standards permettent la génération de tokens d'accès.
Les grands rôles de OAuth2 sont :
- le client ou l'applicartion qui consomme l'API
- le resource server (qui héberge l'API)
- le resource owner (la donnée reste la propriété de l'utilisateur)
- l'autorisation server (Identity Provider)

Différents flows possibles selon le cas d'utilisation (SPA, application mobile...).
Attention à distinguer symétrique et asymétrique HS vs RSA. Quand il y a un shared secret en symétrique on va pouvoir déchiffrer par brute force
Penser à utiliser les states de OAuth2 quel que soit le flow utilisé.
Restreindre les scopes (= consentements) stockés dans les tokens.
La notion d'audience permet de définir le périmètre d'un token (par exemple à une API A, B ou C).

# API management

C'est la première chose à mettre en place en termes de sécurité : on y place les consommateurs et les différentes API.
[Gravitee.io](https://gravitee.io/) est un exemple d'API management.

Une API management permet :
- L'utilisation d'une API Key : à elle seule ne permet pas d'être sécurisé
- De poser des limites : utiliser l'outil [wrk](https://github.com/wg/wrk) pour benchmarker des API et leurs URL via HTTP
- La gestion des CORS
- La gestion d'un circuit breaker
- De faire du A/B testing
- De l'observabilite (mesures)

Liens proposés par Alexandre :
- [JSON Web Tokens](jwt.io)
- [Démos du talk sur le GitHub d'Alexandre](https://github.com/lusoalex/talk-api-security)
- [jwtcrack](https://github.com/ojensen5115/jwtcrack)

Liens que j'ajoute en complément :
- [Sécuriser une API REST : tout ce qu’il faut savoir ](https://blog.octo.com/securiser-une-api-rest-tout-ce-quil-faut-savoir/)
- [Securing REST APIs](https://developer.okta.com/blog/2019/09/04/securing-rest-apis)

