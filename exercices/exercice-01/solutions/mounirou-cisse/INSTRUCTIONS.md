# Instructions pour accéder à Superset

## 🚀 Accès à l'interface

1. **Ouvrir un navigateur** et aller à : http://localhost:8088

2. **Se connecter avec les identifiants** :
   - Username : `admin`
   - Password : `admin`

---

## 📊 Étapes suivantes pour compléter l'exercice

### 1. Connecter la base de données SQLite

**Important** : La base de données doit être accessible depuis le container Docker.

#### Option A : Copier la base dans le container
```bash
docker cp exercices/exercice-01/donnees/ventes.db superset:/app/donnees/ventes.db
```

#### Option B : Monter le volume (nécessite de recréer le container)
```bash
docker rm -f superset
docker run -d -p 8088:8088 \
  -e "SUPERSET_SECRET_KEY=JxuJWylZvjpVBNxsZ//FQUItQDDLE0zfPX5OPVaRnbLT7rMxZyHwCD+3" \
  -v $(pwd)/exercices/exercice-01/donnees:/app/donnees \
  --name superset apache/superset

# Réexécuter l'initialisation
docker exec -it superset superset db upgrade
docker exec -it superset superset fab create-admin --username admin --firstname Admin --lastname User --email admin@example.com --password admin
docker exec -it superset superset init
```

### 2. Dans Superset : Ajouter la base de données

1. Cliquer sur **Data** (menu du haut) → **Databases**
2. Cliquer sur **+ Database** (en haut à droite)
3. Sélectionner **SQLite**
4. Dans le champ **SQLAlchemy URI**, entrer :
   ```
   sqlite:////app/donnees/ventes.db
   ```
5. Cliquer sur **Test Connection**
6. Si succès, cliquer sur **Connect**

### 3. Créer le Dataset

1. Aller dans **Data** → **Datasets**
2. Cliquer sur **+ Dataset**
3. Sélectionner :
   - Database : votre base SQLite
   - Schema : (laisser vide pour SQLite)
   - Table : `ventes`
4. Cliquer sur **Create Dataset and Create Chart**

### 4. Configurer le Dataset

1. Dans la vue du dataset, vérifier les types de colonnes :
   - `date` → Temporal (Date)
   - `produit` → String
   - `categorie` → String
   - `quantite` → Numeric
   - `prix_unitaire` → Numeric
   - `client_id` → String
   - `montant_total` → Numeric

2. Si nécessaire, ajouter une colonne calculée :
   - Nom : `montant_total`
   - Expression SQL : `quantite * prix_unitaire`
   - Type : Numeric

### 5. Créer les Charts

#### Chart 1 : CA par mois (Bar Chart)
1. Chart Type : **Bar Chart**
2. Time Column : `date`
3. Time Grain : **Month**
4. Metrics : `SUM(montant_total)`
5. Titre : "Chiffre d'affaires mensuel 2024"

#### Chart 2 : Évolution des ventes (Line Chart)
1. Chart Type : **Line Chart**
2. Time Column : `date`
3. Time Grain : **Month**
4. Metrics : `COUNT(*)`
5. Titre : "Évolution du nombre de ventes"

#### Chart 3 : Répartition par catégorie (Pie Chart)
1. Chart Type : **Pie Chart**
2. Dimension : `categorie`
3. Metrics : `SUM(montant_total)`
4. Titre : "Répartition du CA par catégorie"

#### Chart 4 : Top 10 produits (Table)
1. Chart Type : **Table**
2. Columns : `produit`, `categorie`
3. Metrics : `SUM(montant_total)`, `SUM(quantite)`, `COUNT(*)`
4. Sort : `SUM(montant_total)` DESC
5. Row Limit : 10
6. Titre : "Top 10 des produits"

#### Chart 5 : Activité par client (Bar Chart horizontal)
1. Chart Type : **Bar Chart**
2. Dimension : `client_id`
3. Metrics : `SUM(montant_total)`
4. Orientation : Horizontal
5. Row Limit : 10
6. Titre : "Top 10 clients"

#### Chart 6 : KPIs (Big Number)
Créer 3 charts séparés :

**KPI 1 - CA Total**
1. Chart Type : **Big Number**
2. Metric : `SUM(montant_total)`
3. Titre : "CA Total 2024"

**KPI 2 - Nombre de transactions**
1. Chart Type : **Big Number**
2. Metric : `COUNT(*)`
3. Titre : "Transactions"

**KPI 3 - Panier moyen**
1. Chart Type : **Big Number**
2. Metric : `AVG(montant_total)`
3. Titre : "Panier Moyen"

### 6. Créer le Dashboard

1. Aller dans **Dashboards**
2. Cliquer sur **+ Dashboard**
3. Nom : "Analyse des Ventes 2024"
4. Cliquer sur **Edit Dashboard**
5. Ajouter tous les charts créés
6. Organiser la mise en page :
   - Ligne 1 : Les 3 KPIs côte à côte
   - Ligne 2 : CA mensuel + Évolution des ventes
   - Ligne 3 : Répartition par catégorie + Top produits
   - Ligne 4 : Top clients

### 7. Ajouter les filtres

1. En mode édition du dashboard, cliquer sur **Filter** (icône d'entonnoir)
2. Ajouter un filtre pour **date** :
   - Type : Time Range
   - Default : Last year
3. Ajouter un filtre pour **categorie** :
   - Type : Filter Select
   - Column : categorie
4. Appliquer les filtres à tous les charts

### 8. Finaliser

1. **Sauvegarder** le dashboard
2. **Tester** les filtres
3. **Prendre des screenshots** de :
   - Dashboard complet
   - Chaque chart individuellement
   - Utilisation des filtres
4. **Exporter le dashboard** :
   - ⋮ (menu) → Export → Export to JSON
   - Sauvegarder dans `solutions/mounirou-cisse/dashboard_export.json`

---

## 📸 Screenshots à capturer

Placer les screenshots dans `solutions/mounirou-cisse/screenshots/` :

1. `01-vue-ensemble.png` - Dashboard complet
2. `02-kpis.png` - Zone des KPIs
3. `03-ca-mensuel.png` - Chart CA mensuel
4. `04-evolution-ventes.png` - Chart évolution
5. `05-repartition-categories.png` - Pie chart catégories
6. `06-top-produits.png` - Table top produits
7. `07-top-clients.png` - Chart top clients
8. `08-filtres.png` - Dashboard avec filtres appliqués

---

## 🔧 Commandes utiles

### Voir les logs du container
```bash
docker logs superset
```

### Redémarrer Superset
```bash
docker restart superset
```

### Arrêter Superset
```bash
docker stop superset
```

### Relancer Superset
```bash
docker start superset
```

### Supprimer complètement Superset
```bash
docker rm -f superset
```

---

## ❓ En cas de problème

### La base de données n'est pas trouvée
→ Vérifier que le fichier a bien été copié dans le container avec la commande `docker cp`

### Erreur de connexion
→ Vérifier que le chemin est bien `/app/donnees/ventes.db` dans le container

### Les colonnes ne s'affichent pas correctement
→ Rafraîchir le dataset : Data → Datasets → ⋮ → Edit → Refresh columns

---

**Bon travail !** 🎉
