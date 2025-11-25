# Exercice 07 : dbt (data build tool) - Transformation de données

## 🎯 Objectifs

- Comprendre le concept de transformation de données avec SQL
- Installer et configurer dbt
- Créer des modèles de données
- Implémenter des tests de qualité
- Générer de la documentation automatique

## 📋 Prérequis

- Python 3.8+
- PostgreSQL ou SQLite installé
- Connaissances SQL avancées

## 📦 Installation

### Installation de dbt

```bash
# Installer dbt (choisir selon votre base de données)
pip install dbt-postgres  # Pour PostgreSQL
# ou
pip install dbt-sqlite    # Pour SQLite (plus simple pour débuter)

# Vérifier l'installation
dbt --version
```

### Configuration

1. **Créer un profil dbt** dans `~/.dbt/profiles.yml` :

```yaml
m2_di_project:
  outputs:
    dev:
      type: postgres  # ou sqlite
      host: localhost
      user: votre_user
      password: votre_password
      port: 5432
      dbname: m2_di_db
      schema: public
  target: dev
```

2. **Initialiser un projet dbt** :
```bash
dbt init m2_di_project
cd m2_di_project
```

## 📊 Données

Utilisez la base de données créée dans l'exercice 02 ou générez de nouvelles données avec le script fourni.

## 🎓 Instructions

### Étape 1 : Configuration du projet (1h)

1. **Initialiser le projet dbt**
2. **Configurer la connexion** à votre base de données
3. **Tester la connexion** : `dbt debug`
4. **Explorer la structure** du projet dbt

### Étape 2 : Modèles de base (2h)

Créez des modèles SQL pour :

1. **staging** (couche de staging) :
   - `stg_customers.sql` : Nettoyage de la table clients
   - `stg_orders.sql` : Nettoyage de la table commandes
   - `stg_products.sql` : Nettoyage de la table produits

2. **intermediate** (modèles intermédiaires) :
   - `int_order_items.sql` : Jointure commandes et produits
   - `int_customer_orders.sql` : Agrégation par client

3. **marts** (couche business) :
   - `dim_customers.sql` : Dimension clients enrichie
   - `dim_products.sql` : Dimension produits
   - `fct_orders.sql` : Fait des commandes

### Étape 3 : Macros et fonctions réutilisables (2h)

1. **Créer des macros** :
   - Macro pour formater les dates
   - Macro pour calculer les pourcentages
   - Macro pour les calculs de croissance

2. **Utiliser les macros** dans vos modèles

### Étape 4 : Tests de qualité (2h)

1. **Tests de base** :
   - `not_null` : Vérifier l'absence de valeurs nulles
   - `unique` : Vérifier l'unicité
   - `accepted_values` : Vérifier les valeurs acceptées
   - `relationships` : Vérifier les relations entre tables

2. **Tests personnalisés** :
   - Créer des tests SQL personnalisés
   - Tester les règles métier

3. **Exécuter les tests** : `dbt test`

### Étape 5 : Documentation (1h)

1. **Documenter les modèles** :
   - Ajouter des descriptions aux modèles
   - Documenter les colonnes
   - Ajouter des exemples

2. **Générer la documentation** : `dbt docs generate`
3. **Visualiser la documentation** : `dbt docs serve`

### Étape 6 : Seeds et sources (1h)

1. **Créer des seeds** :
   - Fichiers CSV de référence
   - Charger avec `dbt seed`

2. **Définir des sources** :
   - Définir les tables sources
   - Documenter les sources
   - Utiliser `source()` dans les modèles

### Étape 7 : Pipeline complet (2h)

1. **Créer un pipeline complet** :
   - Modèles staging → intermediate → marts
   - Tests à chaque étape
   - Documentation complète

2. **Exécuter le pipeline** : `dbt run`
3. **Vérifier les résultats** dans la base de données

## 📁 Structure attendue

```
exercice-07/
├── README.md (ce fichier)
├── m2_di_project/
│   ├── dbt_project.yml
│   ├── models/
│   │   ├── staging/
│   │   ├── intermediate/
│   │   └── marts/
│   ├── macros/
│   ├── tests/
│   ├── seeds/
│   └── docs/
└── solutions/
    └── votre-nom/
        ├── m2_di_project/ (votre projet)
        ├── resultats.md
        └── documentation/ (docs générées)
```

## ✅ Critères d'évaluation

- [ ] Projet dbt configuré et fonctionnel
- [ ] Au moins 8 modèles créés (staging, intermediate, marts)
- [ ] Macros réutilisables implémentées
- [ ] Tests de qualité configurés et passés
- [ ] Documentation complète générée
- [ ] Pipeline complet fonctionnel

## 💡 Conseils

- Suivez les conventions de nommage dbt
- Organisez vos modèles en couches logiques
- Testez régulièrement avec `dbt test`
- Documentez au fur et à mesure
- Utilisez les Jinja templates pour la flexibilité

## 🚀 Fonctionnalités avancées (Bonus)

- Utilisation de packages dbt
- Création de snapshots pour l'historisation
- Utilisation de hooks pour l'orchestration
- Intégration avec Airflow
- Déploiement en production

## 📚 Ressources

- Documentation dbt : https://docs.getdbt.com/
- Tutoriels : https://docs.getdbt.com/tutorial
- Best practices : https://docs.getdbt.com/guides/best-practices

## 🆘 Aide

Si vous êtes bloqué :
1. Consultez la documentation officielle dbt
2. Regardez les exemples de projets dbt
3. Ouvrez une issue sur le dépôt GitHub

## 📤 Soumission

Suivez les instructions dans le README principal du dépôt pour soumettre votre solution.

**Durée estimée : 11 heures**

