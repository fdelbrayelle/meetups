---
title: François Delbrayelle - Serverless et sécurité, ce qu’il faut comprendre
---

# Serverless et sécurité, ce qu’il faut comprendre

Sujets : Serverless, sécurité, OWASP

19h30 - 20h30

Par [Steve Houël](https://twitter.com/SteveHouel) (Ippon). Merci !

Steve a créé [daSWAG](https://www.daswag.tech/), un générateur d'application web serverless.

## La sécurité et nous ?

> La sécurité c'est pour les autres. Je n'ai pas le budget...

Pourtant les statistiques parlent : le plus gros coût d'une attaque c'est la productivité.

La sécurité et le cloud public, un mariage parfait !
On parle de modèles de partage de sécurité. AWS garantit le niveau le plus haut possible. Plus solide que du "on premise".

## Qu'est-ce que le serverless ?

Même si le terme porte à confusion il y a bien des serveurs physiques derrière mais pas besoin de les gérer, ni même d'y penser ou encore de provisionner en infrastructure. L'idée est de ne payer que ce que l'on utilise. Pour simplifier le serverless c'est du BaaS (backend as a service) et du FaaS (function as a service) = on déploie des fonctions et non des applications. Et enfin le serverless est basé sur les évènements.

Les bénéfices ?
- __Coût__ opérationnel réduit
- BaaS coût réduit de développement
- FaaS coût scaling
- __Optimisation du code__ primordiale pour éviter les dépenses inutiles d'argent
- __Plus écologique__ en termes de consommation de ressources

Les inconvénients ?
- "Vendor lock in"
- Problèmes de sécurité : comment gérer la gouvernance ?
- Implémentation : durée d'exécution, temps de démarrage, tests, packaging, versioning
- Difficulté pour tester, même si des frameworks comme [LocalStack](https://github.com/localstack/localstack) permettent d'émuler des appels nombreux. Notion de [alias shifting](https://docs.aws.amazon.com/fr_fr/lambda/latest/dg/lambda-traffic-shifting-using-aliases.html) proche du canary release pour choisir d'utiliser de tel ou tel environnement.

Certains langages ne sont pas adaptés au serverless (Java ou .NET C# par exemple). __Il est préférable d'utiliser Node, Go ou Python sur du serverless.__ Il y a peu de développeurs compétents dans ces domaines.

## Et la sécurité dans tout ça ?

Les responsabilités ne sont pas les mêmes que sur d'autres architectures. Pas besoin de gérer la sécurité au niveau OS car pas d'accès depuis les fonctions. Le FaaS s'occupe de la partie OS, des VMs, des containers, des BDDs...

Dangers :
- Surface d'attaque agrandie
- Complexité de cette surface d'attaque
- Complexité du système dans son ensemble (AWS Lambda, Amazon DynamoDB, Amazon API Gateway, Amazon Kinesis...)

Les risques principaux sont connus et sont recensés notamment par le [Top 10 OWASP](https://www.owasp.org/index.php/Top_10-2017_Top_10) (le dernier disponible en ligne semble dater de 2017).

Il existe également un [top 12 des risques critiques pour le serverless](https://www.puresec.io/serverless-security-top-12-csa-puresec) édité par Puresec.

Top 10 serverless :
- __Injection de données__ dans les fonctions
- __Authentification cassée__ : il faut des rôles privilégiés pour chaque fonction même si elles sont nombreuses et éviter l'authentification faible
- __Configuration de déploiement non sécurisée__ : par exemple avec un flag qui rend public un bucket S3 (qui sont très crawlés par des personnes mal intentionnées)
- __Rôles et permissions IAM__ : ne donner que les rôles minimaux aux fonctions
- __Monitoring et logs inadéquats__ : manque de réponses aux incidents en temps réel
- __Dépendances tierces non sécurisées__ : penser aux méthodes comme le OWASP dependency check dans maven, npm audit...
- __Stockage des informations sensibles__ : attention aux variables d'environnement (possibilité de chiffrer l'information)
- __DDoS__ : limite d'exécutions concurrentes, serverless apporte de la haute disponibilité et scalabilité, régler les timeouts bas
- __Manipulation du flow d'exécution__
- __Mauvaise gestion des erreurs et exceptions__ : les options de debug pas à pas pour serverless sont limitées et plus complexes

En conclusion, il vaut mieux prévenir que guérir :
- Choisir le privilège moindre (plugin [serverless-puresec-cli](https://github.com/puresec/serverless-puresec-cli/) : scanne les fonctions et détecte les bonnes policies à mettre en place) : AWS IAM
- Logs et piste d'audit : AWS Cloudtrail et AWS Cloudwatch
- Outils d'observabilité comme Datadog notamment pour analyser les logs AWS Cloudtrail
- Éviter les DDoS : bien gérer les timeouts (pas 15 minutes par exemple si on sait que notre fonction s'exécute en moyenne en 30 ms => plutôt 50 ms), côté API Gateway pour gérer les quotas, penser au monitoring
- Utiliser AWS Config for Compliance pour détecter les problèmes avant qu'ils ne surviennent avec notamment des règles sur les rôles