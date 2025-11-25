# Exercice 06 : Apache Airflow - Orchestration de workflows

## 🎯 Objectifs

- Installer Apache Airflow
- Créer des DAGs (Directed Acyclic Graphs)
- Orchestrer des pipelines de données
- Monitorer l'exécution des tâches
- Maîtriser l'orchestration de workflows

## 📋 Prérequis

- Python 3.8+
- Docker (recommandé) ou installation native

## 📦 Installation

### Option 1 : Avec Docker Compose (Recommandé)

```bash
# Télécharger docker-compose.yml
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
source airflow-env/bin/activate

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

## 🎓 Instructions

### Étape 1 : Configuration initiale

1. **Accédez à Airflow** : http://localhost:8080
2. **Explorez l'interface** :
   - DAGs : Liste des workflows
   - Graph View : Vue graphique
   - Task Instances : Historique
   - Admin : Configuration

### Étape 2 : Premier DAG simple

Créez un DAG qui :

1. **Tâche 1** : Génère un fichier CSV avec des données
2. **Tâche 2** : Lit le CSV et calcule des statistiques
3. **Tâche 3** : Sauvegarde les statistiques en JSON
4. **Tâche 4** : Envoie un log de confirmation

**Structure** : Tâche 1 → Tâche 2 → Tâche 3 → Tâche 4

### Étape 3 : DAG avec dépendances complexes

Créez un DAG qui :

1. **Extraction** (en parallèle) :
   - Tâche 1 : Télécharger depuis API
   - Tâche 2 : Lire fichier CSV
   - Tâche 3 : Extraire de base de données

2. **Transformation** (en parallèle après extraction) :
   - Tâche 4 : Nettoyer données API
   - Tâche 5 : Nettoyer données CSV
   - Tâche 6 : Nettoyer données DB

3. **Agrégation** :
   - Tâche 7 : Fusionner toutes les données
   - Tâche 8 : Calculer métriques

4. **Chargement** :
   - Tâche 9 : Sauvegarder dans warehouse
   - Tâche 10 : Générer rapport

### Étape 4 : Gestion d'erreurs

1. **Configurez les retries** :
   - Retries automatiques
   - Délais entre retries

2. **Callbacks** :
   - on_failure_callback
   - on_success_callback

### Étape 5 : Variables et connexions

1. **Variables Airflow** :
   - Créez des variables
   - Utilisez-les dans vos DAGs

2. **Connexions** :
   - Configurez une connexion DB
   - Utilisez-la dans vos tâches

### Étape 6 : Scheduling

1. **Configurez le scheduling** :
   - Quotidien
   - Hebdomadaire
   - Expression cron

2. **Testez le déclenchement**

## 📁 Structure attendue

```
exercice-06/
├── README.md (ce fichier)
├── dags/
│   ├── simple_dag.py
│   ├── complex_dag.py
│   └── monitoring_dag.py
└── solutions/
    └── votre-nom/
        ├── dags/ (vos DAGs)
        ├── screenshots/
        └── resultats.md
```

## ✅ Critères d'évaluation

- [ ] Airflow installé et fonctionnel
- [ ] Au moins 3 DAGs créés
- [ ] Dépendances correctement configurées
- [ ] Gestion d'erreurs implémentée
- [ ] Variables et connexions utilisées
- [ ] Scheduling configuré
- [ ] Documentation complète

## 💡 Conseils

- Placez vos DAGs dans le dossier `dags/`
- Utilisez des IDs de tâches descriptifs
- Documentez vos DAGs
- Testez en mode debug
- Utilisez XComs pour passer des données

## 📚 Ressources

- Documentation Airflow : https://airflow.apache.org/docs/
- Tutoriels : https://airflow.apache.org/docs/apache-airflow/stable/tutorial/
- Exemples : https://github.com/apache/airflow/tree/main/airflow/example_dags

## 🆘 Aide

Si vous êtes bloqué :
1. Consultez la documentation
2. Regardez les DAGs d'exemple
3. Ouvrez une issue sur le dépôt GitHub

## 📤 Comment soumettre votre solution

### Étapes pour pousser votre exercice sur GitHub

1. **Créez votre dossier de solution** :
   ```bash
   cd exercice-06
   mkdir -p solutions/votre-nom/dags
   cd solutions/votre-nom
   ```

2. **Copiez vos DAGs** dans le dossier `dags/`
3. **Prenez des captures d'écran** de vos DAGs dans Airflow
4. **Créez un fichier `resultats.md`**

5. **Ajoutez et commitez** :
   ```bash
   git add solutions/votre-nom/
   git commit -m "Solution exercice 06 - Votre Nom"
   git push origin main
   ```

**Important** : N'oubliez pas de remplacer "votre-nom" par votre vrai nom !
