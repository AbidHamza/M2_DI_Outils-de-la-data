# Atelier 03 : Projet complet - Stack moderne de données

## 🎯 Objectifs

- Intégrer plusieurs outils de la stack moderne
- Créer un pipeline de données complet
- Mettre en place le monitoring
- Déployer une solution production-ready

## 📋 Prérequis

- Tous les exercices précédents complétés
- Docker installé
- Connaissances en architecture de données

## 🎓 Instructions

### Contexte du projet

Vous devez créer une stack complète de données pour une application e-commerce qui inclut :
- Collecte de données en temps réel
- Stockage dans un data warehouse
- Transformation avec dbt
- Orchestration avec Airflow
- Monitoring avec Grafana
- Dashboard analytique

### Phase 1 : Architecture (2h)

1. **Dessiner l'architecture** :
   - Schéma complet du système
   - Flux de données
   - Technologies choisies
   - Justifications des choix

2. **Planifier l'implémentation** :
   - Liste des composants
   - Dépendances entre composants
   - Ordre d'implémentation

### Phase 2 : Infrastructure (3h)

1. **Docker Compose** :
   - Créer un fichier docker-compose.yml
   - Configurer PostgreSQL (data warehouse)
   - Configurer Airflow
   - Configurer Grafana
   - Configurer les services nécessaires

2. **Réseau et volumes** :
   - Configurer les réseaux Docker
   - Créer les volumes persistants
   - Configurer les variables d'environnement

### Phase 3 : Collecte de données (3h)

1. **Génération de données** :
   - Créer un générateur de données en temps réel
   - Simuler des événements e-commerce
   - Streamer les données vers Kafka (ou file)

2. **Ingestion** :
   - Configurer l'ingestion dans PostgreSQL
   - Créer les tables de destination
   - Valider l'ingestion

### Phase 4 : Transformation (3h)

1. **Pipeline dbt** :
   - Créer les modèles staging
   - Créer les modèles intermediate
   - Créer les modèles marts
   - Configurer les tests

2. **Intégration Airflow** :
   - Créer un DAG pour orchestrer dbt
   - Configurer les dépendances
   - Tester l'exécution

### Phase 5 : Monitoring (2h)

1. **Grafana** :
   - Configurer la connexion à PostgreSQL
   - Créer des dashboards de monitoring
   - Configurer des alertes

2. **Métriques** :
   - Métriques de pipeline (succès/échec)
   - Métriques de données (volume, qualité)
   - Métriques business (ventes, clients)

### Phase 6 : Dashboard analytique (3h)

1. **Créer un dashboard** :
   - KPIs principaux
   - Graphiques de tendances
   - Analyses approfondies

2. **Intégration** :
   - Connecter au data warehouse
   - Mettre à jour automatiquement
   - Rendre interactif

### Phase 7 : Documentation et déploiement (2h)

1. **Documentation** :
   - Architecture documentée
   - Guide d'installation
   - Guide d'utilisation
   - Troubleshooting

2. **Déploiement** :
   - Instructions de déploiement
   - Configuration de production
   - Monitoring en production

## 📁 Structure attendue

```
atelier-03/
├── README.md (ce fichier)
├── docker-compose.yml
├── architecture/
│   ├── diagramme.png
│   └── architecture.md
├── infrastructure/
│   ├── docker/
│   └── config/
├── data_generator/
│   └── generator.py
├── dbt_project/
│   └── (projet dbt complet)
├── airflow/
│   └── dags/
├── grafana/
│   └── dashboards/
└── solutions/
    └── votre-nom/
        └── (votre solution complète)
```

## ✅ Critères d'évaluation

- [ ] Architecture complète et justifiée
- [ ] Infrastructure Docker fonctionnelle
- [ ] Pipeline de données complet
- [ ] Monitoring opérationnel
- [ ] Dashboard analytique fonctionnel
- [ ] Documentation complète
- [ ] Solution production-ready

## 💡 Conseils

- Commencez simple, complexifiez progressivement
- Testez chaque composant individuellement
- Utilisez Docker pour l'isolation
- Documentez au fur et à mesure
- Pensez à la scalabilité

## 🚀 Fonctionnalités avancées (Bonus)

- Streaming en temps réel avec Kafka
- Machine Learning intégré
- CI/CD pour le déploiement
- Multi-environnements (dev, staging, prod)
- Backup et recovery

## 📤 Soumission

Suivez les instructions dans le README principal du dépôt pour soumettre votre solution.

**Durée estimée : 15 heures**

