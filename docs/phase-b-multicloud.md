# Phase B2 — Semaine 4 (multi-cloud)

## Tableau

|Besoin|AWS|Azure|GCP|
|-|-|-|-|
|VM|EC2| Azure Virtual Machines|Google Compute Engine|
|Stockage objet|S3|Azure Blob Storage|Google Cloud Storage|
|DNS|Route 53| Azure DNS|Google Cloud DNS|
|CI|CodeBuild| Azure DevOps|Google Cloud Build|

## Question

Pourquoi utiliser **GitHub Actions** plutôt qu’installer Jenkins sur sa propre VM ? (5 lignes)



GitHub Actions est un service cloud déjà géré, donc il ne nécessite pas d’installation ni de maintenance serveur.

Contrairement à Jenkins, il n’y a pas besoin de configurer une VM ou gérer les mises à jour manuellement.

Il est directement intégré à GitHub, ce qui facilite l’automatisation des tests et déploiements.

Il est aussi plus rapide à mettre en place et scalable automatiquement selon la charge.

Enfin, il réduit les coûts et les risques liés à la gestion d’une infrastructure CI/CD interne.



