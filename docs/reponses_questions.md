# Réponses aux Questions Théoriques - TP MLOps

Ce document contient les réponses aux questions théoriques du TP 1 sur la mise en place d'un projet MLOps.

---

### 1. Qu'est-ce que le MLOps ?
Le MLOps (Machine Learning Operations) combine le Machine Learning, le DevOps et l'ingénierie des données pour automatiser, versionner et fiabiliser le développement, le déploiement et la maintenance des modèles en production. Il vise à réduire le temps de mise sur le marché et à assurer un suivi continu de la performance des modèles.

---

### 2. Quelle est la différence entre Git et GitHub ?
*   **Git** est un logiciel local en ligne de commande de contrôle de version décentralisé. Il permet de suivre l'historique des modifications des fichiers sur votre propre machine.
*   **GitHub** est une plateforme cloud qui héberge les dépôts Git en ligne. Elle fournit une interface graphique, des outils de collaboration (Pull Requests, Issues) et des fonctionnalités d'intégration continue (GitHub Actions).

---

### 3. Pourquoi utilise-t-on un environnement virtuel Python ?
Un environnement virtuel Python isole les dépendances d'un projet spécifique de l'installation globale du système. Cela permet de :
1.  Éviter les conflits de versions entre les bibliothèques de différents projets.
2.  Garantir la reproductibilité de l'environnement grâce au fichier `requirements.txt`.
3.  Garder le système propre sans polluer l'interpréteur Python global.

---

### 4. Pourquoi séparer les données raw, intermediate et processed ?
Cette séparation suit le principe d'un flux de données unidirectionnel et reproductible :
*   **Raw (Brutes)** : Les données d'origine non modifiées. Elles sont immuables (lecture seule) pour pouvoir toujours revenir à l'état initial.
*   **Intermediate (Intermédiaires)** : Les données après le nettoyage lourd (valeurs manquantes, doublons). Cela évite de recalculer ces nettoyages coûteux en temps.
*   **Processed (Préparées)** : Les données prêtes pour l'algorithme (normalisées, encodées). C'est ce dossier qui alimente directement l'entraînement du modèle.

---

### 5. Quel est le rôle de MLflow ?
MLflow gère le cycle de vie complet des modèles de Machine Learning. Ses fonctionnalités principales sont :
*   Le suivi des expériences (Tracking) : enregistrement des paramètres, métriques de performance et graphiques de chaque exécution.
*   Le registre de modèles (Model Registry) : gestion centralisée des versions des modèles entraînés et de leur statut (Staging, Production, Archivé).

---

### 6. Pourquoi Docker sera-t-il utilisé dans ce projet ?
Docker permet d'encapsuler l'application (l'API de prédiction et le modèle) avec toutes ses dépendances système et Python dans un conteneur standardisé et isolé. Cela garantit que l'application s'exécutera exactement de la même manière sur n'importe quelle machine (développement, test, production).

---

### 7. Quel est le rôle de FastAPI ?
FastAPI est un framework web performant pour développer des API REST avec Python. Il sert à exposer le modèle de Machine Learning sous forme de service web. Il reçoit des requêtes contenant les caractéristiques d'une maison, valide les données, interroge le modèle et renvoie le prix estimé sous forme de réponse JSON.

---

### 8. Pourquoi un projet MLOps doit-il être versionné ?
Un projet MLOps doit être versionné (le code, les modèles et les données) pour :
1.  **Garantir la reproductibilité** : savoir retrouver l'état exact du code et des données ayant servi à concevoir un modèle spécifique.
2.  **Faciliter la collaboration** : permettre à plusieurs data scientists de travailler simultanément sans conflit.
3.  **Assurer l'auditabilité** : pouvoir expliquer les prédictions d'un modèle en production en retraçant son historique.
4.  **Permettre des retours en arrière (Rollback)** : révoquer rapidement un modèle défaillant en production au profit d'une version précédente stable.
