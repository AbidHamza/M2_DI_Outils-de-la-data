# Exercice 06 : Apache Airflow - Orchestration de workflows

## 🎯 Objectifs

- Comprendre l'orchestration de workflows de données
- Installer et configurer Apache Airflow
- Créer des DAGs (Directed Acyclic Graphs)
- Gérer les dépendances entre tâches
- Monitorer l'exécution des pipelines

## 📋 Prérequis

- Python 3.8+
- Docker (recommandé) ou installation native
- Connaissances de base en Python

## 📦 Installation

### Option 1 : Avec Docker (Recommandé)

```bash
# Télécharger docker-compose.yml depuis Airflow
curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.7.0/docker-compose.yaml'

# Initialiser la base de données
docker-compose up airflow-init

# Démarrer Airflow
docker-compose up -d

# Accéder à l'interface : http://localhost:8080
# Identifiants : airflow / airflow
```

### Option 2 : Installation native

```bash
# Créer un environnement virtuel
python -m venv airflow-env
source airflow-env/bin/activate  # Linux/Mac
# ou
airflow-env\Scripts\activate  # Windows

# Installer Airflow
pip install apache-airflow

# Initialiser la base de données
airflow db init

# Créer un utilisateur admin
airflow users create \
    --username admin \
    --firstname Admin \
    --lastname User \
    --role Admin \
    --email admin@example.com

# Démarrer le serveur web
airflow webserver --port 8080

# Dans un autre terminal, démarrer le scheduler
airflow scheduler
```

## 📊 Contexte

Vous devez créer un pipeline ETL complet qui :
1. Extrait des données depuis plusieurs sources
2. Transforme et nettoie les données
3. Charge les données dans une destination finale
4. Envoie un rapport par email

## 🎓 Instructions

### Étape 1 : Configuration initiale (1h)

1. **Installer Airflow** (voir section Installation)
2. **Accéder à l'interface web** : http://localhost:8080
3. **Explorer l'interface** :
   - DAGs : Liste des workflows
   - Graph View : Vue graphique des dépendances
   - Task Instances : Historique d'exécution
   - Admin : Configuration

### Étape 2 : Premier DAG simple (2h)

Créez un DAG qui :

1. **Tâche 1** : Génère un fichier CSV avec des données aléatoires
2. **Tâche 2** : Lit le CSV et calcule des statistiques
3. **Tâche 3** : Sauvegarde les statistiques dans un fichier JSON
4. **Tâche 4** : Envoie un email avec les résultats (simulé avec un log)

**Structure du DAG** :
```python
# Tâche 1 → Tâche 2 → Tâche 3
#              ↓
#          Tâche 4
```

### Étape 3 : DAG avec dépendances complexes (3h)

Créez un DAG plus complexe qui :

1. **Extraction** :
   - Tâche 1 : Télécharger des données depuis une API (simulée)
   - Tâche 2 : Lire un fichier CSV local
   - Tâche 3 : Lire des données depuis une base SQLite

2. **Transformation** (en parallèle après extraction) :
   - Tâche 4 : Nettoyer les données de l'API
   - Tâche 5 : Nettoyer les données CSV
   - Tâche 6 : Nettoyer les données SQLite

3. **Agrégation** :
   - Tâche 7 : Fusionner toutes les données nettoyées
   - Tâche 8 : Calculer des métriques agrégées

4. **Chargement** :
   - Tâche 9 : Sauvegarder dans un Data Warehouse (simulé)
   - Tâche 10 : Générer un rapport

**Structure du DAG** :
```
Tâche 1 ─┐
Tâche 2 ─┼─→ Tâche 4 ─┐
Tâche 3 ─┘    Tâche 5 ─┼─→ Tâche 7 → Tâche 8 → Tâche 9 → Tâche 10
         └─→ Tâche 6 ─┘
```

### Étape 4 : Gestion des erreurs et retry (1h)

1. **Configurer les retries** :
   - Ajouter des retries automatiques en cas d'échec
   - Configurer les délais entre retries

2. **Gestion d'erreurs** :
   - Implémenter des callbacks on_failure
   - Envoyer des alertes en cas d'échec

3. **Tests** :
   - Tester le comportement en cas d'échec
   - Vérifier les retries

### Étape 5 : Variables et connexions (1h)

1. **Variables Airflow** :
   - Créer des variables pour stocker des configurations
   - Utiliser les variables dans vos DAGs

2. **Connexions** :
   - Configurer une connexion à une base de données
   - Utiliser la connexion dans vos tâches

### Étape 6 : Scheduling et triggers (1h)

1. **Scheduling** :
   - Configurer l'exécution quotidienne
   - Configurer l'exécution hebdomadaire
   - Utiliser des expressions cron

2. **Triggers manuels** :
   - Tester le déclenchement manuel
   - Utiliser les paramètres de configuration

### Étape 7 : Documentation et monitoring (1h)

1. **Documentation** :
   - Ajouter des docstrings aux DAGs
   - Documenter chaque tâche
   - Créer un fichier `resultats.md`

2. **Monitoring** :
   - Configurer des alertes
   - Créer un dashboard de monitoring
   - Exporter les logs

## 📁 Structure attendue

```
exercice-06/
├── README.md (ce fichier)
├── dags/
│   ├── simple_dag.py
│   ├── complex_dag.py
│   └── monitoring_dag.py
├── scripts/
│   ├── extract_data.py
│   ├── transform_data.py
│   └── load_data.py
├── donnees/
│   └── (fichiers générés)
└── solutions/
    └── votre-nom/
        ├── dags/ (vos DAGs)
        ├── resultats.md
        └── screenshots/ (captures d'écran)
```

## ✅ Critères d'évaluation

- [ ] Airflow installé et fonctionnel
- [ ] Au moins 3 DAGs créés (simple, complexe, monitoring)
- [ ] Dépendances correctement configurées
- [ ] Gestion d'erreurs et retries implémentée
- [ ] Variables et connexions utilisées
- [ ] Scheduling configuré
- [ ] Documentation complète

## 💡 Conseils

- Placez vos DAGs dans le dossier `dags/` d'Airflow
- Utilisez des opérateurs Python pour la flexibilité
- Testez vos DAGs en mode debug avant de les activer
- Utilisez les XComs pour passer des données entre tâches
- Documentez vos DAGs avec des docstrings

## 🚀 Fonctionnalités avancées (Bonus)

- Utilisation de Docker Operators
- Intégration avec des APIs externes
- Utilisation de Sensors pour attendre des conditions
- Création de plugins personnalisés
- Déploiement en production

## 📚 Ressources

- Documentation Airflow : https://airflow.apache.org/docs/
- Tutoriels : https://airflow.apache.org/docs/apache-airflow/stable/tutorial/
- Exemples de DAGs : https://github.com/apache/airflow/tree/main/airflow/example_dags

## 🆘 Aide

Si vous êtes bloqué :
1. Consultez la documentation officielle
2. Regardez les DAGs d'exemple fournis avec Airflow
3. Ouvrez une issue sur le dépôt GitHub

## 📤 Soumission

Suivez les instructions dans le README principal du dépôt pour soumettre votre solution.

**Durée estimée : 10 heures**

