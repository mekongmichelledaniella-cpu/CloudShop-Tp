# Phase C — Semaine 5 (pipeline DevOps)

## Schéma de votre pipeline

```
Code local → git push → GitHub Actions → tests → docker build
```

Indiquez :
 où ça **s’arrête** si un test échoue ?
le pipeline s’arrête immédiatement à l’étape des tests, Le build Docker ne se lance pas, et le code n’est pas déployé.
 Qu’est-ce qui reste **manuel** chez vous ?
Écriture du code backend Flask, API
Push du code sur GitHub (git push)
Configuration initiale du projet (Dockerfile, repo GitHub)
Lancement initial de l’instance ou du service cloud 
Correction des erreurs après feedback des tests


## Questions

1. DevOps en une phrase :Le DevOps est une approche qui combine développement et opérations pour automatiser le déploiement, améliorer la collaboration et accélérer la livraison des applications.
2. Deux objectifs mesurables du DevOps :Réduire le temps de déploiement entre le code et la production
Diminuer le taux d’échec des déploiements grâce à l’automatisation des tests
3. Ce qui reste manuel dans **votre** TP :
le développement du code source
les commits et push GitHub
certaines configurations initiales (serveur, Docker, environnement)
la correction des erreurs détectées par la CI