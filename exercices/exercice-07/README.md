# Exercice 07 : dbt (data build tool) - Transformation SQL

## 🎯 Objectifs

- Installer et configurer dbt
- Créer des modèles de transformation SQL
- Implémenter des tests de qualité
- Générer de la documentation automatique
- Maîtriser la transformation de données moderne

## 📋 Prérequis

- Python 3.8+
- PostgreSQL ou SQLite installé
- Connaissances SQL avancées

## 📦 Installation

```bash
# Installer dbt (choisir selon votre base)
pip install dbt-postgres  # Pour PostgreSQL
# ou
pip install dbt-sqlite    # Pour SQLite

# Vérifier l'installation
dbt --version
```

## 📊 Données

Utilisez la base de données de l'exercice 02 ou créez-en une nouvelle.

## 🎓 Instructions

### Étape 1 : Configuration du projet

1. **Initialiser un projet dbt** :
   ```bash
   dbt init m2_di_project
   cd m2_di_project
   ```

2. **Configurer `profiles.yml`** dans `~/.dbt/profiles.yml` :
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

3. **Tester la connexion** :
   ```bash
   dbt debug
   ```

### Étape 2 : Modèles de base

Créez des modèles dans `models/` :

1. **Staging** (`models/staging/`) :
   - `stg_customers.sql` : Nettoyage table clients
   - `stg_orders.sql` : Nettoyage table commandes
   - `stg_products.sql` : Nettoyage table produits

2. **Intermediate** (`models/intermediate/`) :
   - `int_order_items.sql` : Jointure commandes et produits
   - `int_customer_orders.sql` : Agrégation par client

3. **Marts** (`models/marts/`) :
   - `dim_customers.sql` : Dimension clients enrichie
   - `dim_products.sql` : Dimension produits
   - `fct_orders.sql` : Fait des commandes

### Étape 3 : Macros

Créez des macros réutilisables dans `macros/` :

1. **Macro pour formater les dates**
2. **Macro pour calculer les pourcentages**
3. **Macro pour les calculs de croissance**

### Étape 4 : Tests

1. **Tests de base** :
   - `not_null` : Vérifier absence de valeurs nulles
   - `unique` : Vérifier unicité
   - `accepted_values` : Vérifier valeurs acceptées
   - `relationships` : Vérifier relations

2. **Tests personnalisés** :
   - Créez des tests SQL personnalisés
   - Testez les règles métier

3. **Exécuter les tests** :
   ```bash
   dbt test
   ```

### Étape 5 : Documentation

1. **Documenter les modèles** :
   - Ajoutez des descriptions
   - Documentez les colonnes
   - Ajoutez des exemples

2. **Générer la documentation** :
   ```bash
   dbt docs generate
   dbt docs serve
   ```

### Étape 6 : Seeds et sources

1. **Créer des seeds** :
   - Fichiers CSV de référence
   - Charger avec `dbt seed`

2. **Définir des sources** :
   - Définir les tables sources
   - Documenter les sources
   - Utiliser `source()` dans les modèles

### Étape 7 : Pipeline complet

1. **Exécuter le pipeline** :
   ```bash
   dbt run
   ```

2. **Vérifier les résultats** dans la base de données

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
│   └── seeds/
└── solutions/
    └── votre-nom/
        ├── m2_di_project/ (votre projet)
        └── resultats.md
```

## ✅ Critères d'évaluation

- [ ] Projet dbt configuré
- [ ] Au moins 8 modèles créés
- [ ] Macros réutilisables
- [ ] Tests configurés et passés
- [ ] Documentation complète
- [ ] Pipeline fonctionnel

## 💡 Conseils

- Suivez les conventions dbt
- Organisez en couches logiques
- Testez régulièrement
- Documentez au fur et à mesure
- Utilisez Jinja templates

## 📚 Ressources

- Documentation dbt : https://docs.getdbt.com/
- Tutoriels : https://docs.getdbt.com/tutorial
- Best practices : https://docs.getdbt.com/guides/best-practices

## 🆘 Aide

Si vous êtes bloqué :
1. Consultez la documentation
2. Regardez les exemples
3. Ouvrez une issue sur le dépôt GitHub

## 📤 Comment soumettre votre solution

### Étapes pour pousser votre exercice sur GitHub

1. **Créez votre dossier de solution** :
   ```bash
   cd exercice-07
   mkdir -p solutions/votre-nom
   cd solutions/votre-nom
   ```

2. **Copiez votre projet dbt** complet
3. **Générez la documentation** et sauvegardez-la
4. **Créez un fichier `resultats.md`**

5. **Ajoutez et commitez** :
   ```bash
   git add solutions/votre-nom/
   git commit -m "Solution exercice 07 - Votre Nom"
   git push origin main
   ```

**Important** : N'oubliez pas de remplacer "votre-nom" par votre vrai nom !
