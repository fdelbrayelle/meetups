# Optimiser son déploiement Spring Boot dans le cloud

Sujets : Spring Boot

19/11/2020 - 14h40 - 15h25

Par [Julien Dubois](https://twitter.com/juliendubois) (Microsoft). Merci !

Comment exécuter Spring Boot dans le cloud ?
- Les machines virtuelles (par ex : Azure VMs) ; tout doit être installé/maintenu par l'utilisateur
- Support de Spring Boot installable en tant que service Ubuntu
- Container Docker (ce qu'utilise https://start.jhipster.tech aujourd'hui)
- Utiliser JIB pour faire une image docker sans Docker ou utiliser [Buildpacks.io](https://buildpacks.io/)
- Kubernetes : Azure Container Instance ou Azure App Service ou bien au sein d'un cluster (Azure Kubernetes Services)

Spring Cloud Function

Spring Boot starters pour Azure (fruit de 4 ans de collaboration avec VMware)

Quels outils et libs sont disponibles ?

Comment déployer automatiquement ?

Comment monitorer/sécuriser sa prod ?

Spring Boot doit suivre les 12Factors, logs en sortie standard...