# House Price Prediction using MLOps

[![Python Version](https://img.shields.io/badge/python-3.11%2B-blue.svg)](https://www.python.org/)
[![MLflow](https://img.shields.io/badge/MLflow-Tracking-orange.svg)](https://mlflow.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-Framework-green.svg)](https://fastapi.tiangolo.com/)
[![Docker](https://img.shields.io/badge/Docker-Container-blue.svg)](https://www.docker.com/)

Ce projet présente un flux de travail MLOps complet pour la prédiction des prix de l'immobilier, en intégrant le versionnement du code, des données, l'entraînement traçable, la conteneurisation et le déploiement d'API.

---

## Objectif du Projet

L'objectif principal est de construire et de déployer un modèle de prévision robuste des prix des maisons en appliquant les meilleures pratiques de l'ingénierie MLOps. Le système est conçu pour être reproductible, testable, conteneurisé et prêt pour la production.

---

## Technologies Utilisées

- **Python (3.11+)** : Langage principal du projet.
- **Pandas & Numpy** : Manipulation, nettoyage et transformation des données.
- **Scikit-learn & XGBoost** : Conception, entraînement et validation des modèles de régression.
- **MLflow** : Suivi des expériences, enregistrement des hyperparamètres, des métriques et gestion du registre de modèles.
- **FastAPI** : Framework de création d'API REST ultra-rapide pour exposer le modèle en temps réel.
- **Docker** : Conteneurisation de l'API pour un déploiement standardisé et portable.
- **Kubernetes** (Futur) : Orchestration des conteneurs pour une mise à l'échelle en production.

---

## Architecture Générale du Dépôt

Voici l'organisation de l'arborescence du projet conforme aux standards de l'industrie :

```text
house-price-mlops/
├── api/                  # Code de l'API FastAPI et routeurs
├── configs/              # Fichiers de configuration (hyperparamètres, chemins, variables)
├── data/                 # Répertoires de stockage des données
│   ├── raw/              # Données brutes (invariables, non modifiées)
│   ├── intermediate/     # Données nettoyées mais non transformées
│   └── processed/        # Données prêtes pour l'entraînement du modèle
├── docker/               # Fichiers Docker (Dockerfiles, docker-compose.yml)
├── docs/                 # Documentation technique (architecture.md, etc.)
├── mlflow/               # Configuration et artéfacts locaux de MLflow
├── models/               # Emplacement des modèles entraînés localement (PKL, Joblib)
├── notebooks/            # Notebooks Jupyter pour la recherche et l'exploration de données
├── src/                  # Code source du pipeline (ingestion, processing, training)
├── tests/                # Tests unitaires et d'intégration (Pytest)
├── requirements.txt      # Liste des dépendances Python requises
├── README.md             # Documentation principale du projet
└── .gitignore            # Fichiers et dossiers exclus du contrôle de version Git
```

---

## Rôle et Organisation des Données

### Tableau des Répertoires de Données

| Dossier | Rôle |
| :--- | :--- |
| **raw** | Stockage des données brutes, d'origine et immuables. Ce dossier ne doit jamais être modifié directement pour garantir la reproductibilité. |
| **intermediate** | Stockage des données nettoyées de manière préliminaire (suppression des doublons, correction des valeurs manquantes et aberrantes) mais non encore transformées pour le modèle. |
| **processed** | Stockage des données transformées, normalisées et prêtes pour l'entraînement (encodage, sélection de caractéristiques). C'est le jeu de données final pour le modèle. |

---

## Rôle des Dossiers dans l'Architecture MLOps

| Dossier | Rôle dans l'architecture MLOps |
| :--- | :--- |
| **models/** | Contient les versions locales des modèles entraînés et sauvegardés sous forme de fichiers binaires (pickle, joblib, etc.) avant leur enregistrement officiel. |
| **mlflow/** | Stocke les configurations locales, les fichiers de suivi d'expériences (runs, métriques, hyperparamètres) et les fichiers de tracking de MLflow. |
| **docker/** | Contient les Dockerfiles, configurations et fichiers de composition pour conteneuriser l'API et ses dépendances pour un déploiement uniforme. |
| **api/** | Héberge le code de l'interface de programmation (FastAPI) pour exposer le modèle sous forme de service web et répondre aux requêtes en temps réel. |
| **tests/** | Regroupe les tests automatisés (tests unitaires, tests d'intégration) pour valider le code d'ingestion, de traitement et de l'API. |
| **configs/** | Centralise les fichiers de configuration (hyperparamètres du modèle, variables d'environnement, configurations de pipeline) pour éviter de coder en dur. |

---

## Démarrage Rapide

### 1. Cloner le projet
```bash
git clone https://github.com/naval0506/house-price-mlops.git
cd house-price-mlops
```

### 2. Configurer l'environnement virtuel
```bash
python3 -m venv venv
source venv/bin/activate  # Sur Linux/macOS
# ou
.\venv\Scripts\activate  # Sur Windows
```

### 3. Installer les dépendances
```bash
pip install -r requirements.txt
```

---

## Auteurs

- **Valkely** - *Étudiant en L3 IAD (Intelligence Artificielle et Décision)* - [valkely02@gmail.com](mailto:valkely02@gmail.com)
