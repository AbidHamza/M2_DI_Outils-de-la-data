# Exercice 01 : Apache Superset - Analyse des Ventes
## Solution de Mounirou Cisse

### 📋 Résumé de l'exercice
Création d'un dashboard d'analyse des ventes e-commerce 2024 avec Apache Superset.

---

## 🎯 Objectifs atteints

- [x] Installation et configuration de Superset via Docker
- [x] Génération des données de ventes (200 lignes)
- [x] Création de la base de données SQLite
- [x] Connexion de Superset à la base de données
- [ ] Création du dataset dans Superset
- [ ] Création des 6 charts requis
- [ ] Assemblage du dashboard
- [ ] Configuration des filtres

---

## 🔧 Installation et Configuration

### Étapes réalisées

1. **Génération des données**
   ```bash
   python3 generer_donnees.py
   ```
   - 200 lignes de ventes générées
   - Période : 2024-01-02 à 2024-12-30
   - 35 produits différents
   - 24 clients différents

2. **Création de la base SQLite**
   ```bash
   python3 creer_base_donnees.py
   ```
   - Base `ventes.db` créée avec succès
   - Table `ventes` avec index optimisés

3. **Installation de Superset**
   ```bash
   docker run -d -p 8088:8088 \
     -e "SUPERSET_SECRET_KEY=..." \
     --name superset apache/superset
   ```
   - Container Docker créé et démarré
   - Base de données Superset initialisée
   - Compte admin créé (admin/admin)
   - Interface accessible sur http://localhost:8088

---

## 📊 Analyses et Insights

### Vue d'ensemble des données
- **Période analysée** : Janvier à Décembre 2024
- **Nombre de transactions** : 200
- **Nombre de produits** : 35
- **Nombre de clients** : 24
- **Catégories** : Electronique, Mobilier, Education

### Prochaines étapes

1. **Se connecter à Superset** (http://localhost:8088)
   - Username: admin
   - Password: admin

2. **Connecter la base de données**
   - Aller dans Data > Databases > +Database
   - Choisir SQLite
   - URI: `sqlite:////app/donnees/ventes.db`
   - Note: Le fichier ventes.db doit être copié dans le container Docker

3. **Créer le dataset**
   - Data > Datasets > +Dataset
   - Sélectionner la table `ventes`
   - Configurer les types de colonnes

4. **Créer les charts**
   - CA par mois (Bar Chart)
   - Évolution des ventes (Line Chart)
   - Répartition par catégorie (Pie Chart)
   - Top 10 produits (Table)
   - Activité par client (Bar Chart horizontal)
   - KPIs (Big Number)

5. **Créer le dashboard**
   - Assembler tous les charts
   - Ajouter des filtres (période, catégorie)
   - Organiser la mise en page

---

## 🎨 Structure du Dashboard (à créer)

### Section 1 : Vue d'ensemble
- KPI : CA Total
- KPI : Nombre de transactions
- KPI : Panier moyen

### Section 2 : Évolution temporelle
- Chart : CA par mois
- Chart : Évolution des ventes

### Section 3 : Analyse produits
- Chart : Répartition par catégorie
- Chart : Top 10 produits

### Section 4 : Analyse clients
- Chart : Activité par client

---

## 📈 Insights clés (à compléter après analyse)

### Tendances identifiées
- À compléter après création du dashboard

### Catégories performantes
- À compléter après analyse

### Produits phares
- À compléter après analyse

### Comportement clients
- À compléter après analyse

---

## 🚀 Recommandations (à compléter)

### Actions commerciales
- À définir après analyse des données

### Optimisations
- À définir après analyse

---

## 📝 Notes techniques

### Configuration Docker
- Container : `superset`
- Port : 8088
- Image : `apache/superset:latest`
- Variable d'environnement : SUPERSET_SECRET_KEY configurée

### Base de données
- Type : SQLite
- Fichier : `donnees/ventes.db`
- Table : `ventes`
- Colonnes : date, produit, categorie, quantite, prix_unitaire, client_id, montant_total

### Commandes utiles
```bash
# Vérifier le status du container
docker ps

# Accéder aux logs
docker logs superset

# Redémarrer le container
docker restart superset

# Copier la base de données dans le container (si nécessaire)
docker cp donnees/ventes.db superset:/app/donnees/ventes.db
```

---

## ✅ Checklist de progression

- [x] Environnement Python configuré
- [x] Données générées
- [x] Base de données créée
- [x] Superset installé et fonctionnel
- [x] Structure de solution créée
- [ ] Base de données connectée à Superset
- [ ] Dataset configuré
- [ ] Charts créés
- [ ] Dashboard assemblé
- [ ] Filtres configurés
- [ ] Screenshots capturées
- [ ] Dashboard exporté (JSON)
- [ ] Documentation finalisée

---

## 📅 Date de réalisation
- **Début** : 25 novembre 2025
- **Fin** : En cours

---

## 👤 Auteur
**Mounirou Cisse**
