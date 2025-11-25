# Requêtes SQL - Exercice 01
## Mounirou Cisse

Ce fichier contient les requêtes SQL utilisées pour l'analyse des ventes dans SQL Lab (si utilisé).

---

## 📊 Requêtes d'exploration

### 1. Vue d'ensemble des données
```sql
-- Aperçu de la table ventes
SELECT * FROM ventes LIMIT 10;
```

### 2. Statistiques générales
```sql
-- Chiffre d'affaires total et nombre de transactions
SELECT 
    COUNT(*) as nombre_transactions,
    SUM(montant_total) as ca_total,
    AVG(montant_total) as panier_moyen,
    MIN(date) as date_debut,
    MAX(date) as date_fin
FROM ventes;
```

### 3. Analyse par catégorie
```sql
-- CA et nombre de ventes par catégorie
SELECT 
    categorie,
    COUNT(*) as nb_transactions,
    SUM(montant_total) as ca_total,
    AVG(montant_total) as panier_moyen,
    SUM(quantite) as quantite_totale
FROM ventes
GROUP BY categorie
ORDER BY ca_total DESC;
```

### 4. Top produits
```sql
-- Top 10 des produits par CA
SELECT 
    produit,
    categorie,
    COUNT(*) as nb_ventes,
    SUM(quantite) as quantite_totale,
    SUM(montant_total) as ca_total,
    AVG(prix_unitaire) as prix_moyen
FROM ventes
GROUP BY produit, categorie
ORDER BY ca_total DESC
LIMIT 10;
```

### 5. Analyse temporelle
```sql
-- CA par mois
SELECT 
    strftime('%Y-%m', date) as mois,
    COUNT(*) as nb_transactions,
    SUM(montant_total) as ca_mensuel,
    AVG(montant_total) as panier_moyen
FROM ventes
GROUP BY strftime('%Y-%m', date)
ORDER BY mois;
```

### 6. Analyse clients
```sql
-- Top 10 clients par CA
SELECT 
    client_id,
    COUNT(*) as nb_achats,
    SUM(montant_total) as ca_total,
    AVG(montant_total) as panier_moyen,
    SUM(quantite) as articles_achetes
FROM ventes
GROUP BY client_id
ORDER BY ca_total DESC
LIMIT 10;
```

---

## 🔍 Requêtes avancées

### 7. Analyse croisée produits-clients
```sql
-- Produits les plus populaires auprès des meilleurs clients
SELECT 
    v.produit,
    v.categorie,
    COUNT(DISTINCT v.client_id) as nb_clients,
    SUM(v.montant_total) as ca_total
FROM ventes v
WHERE v.client_id IN (
    SELECT client_id
    FROM ventes
    GROUP BY client_id
    ORDER BY SUM(montant_total) DESC
    LIMIT 5
)
GROUP BY v.produit, v.categorie
ORDER BY ca_total DESC;
```

### 8. Saisonnalité
```sql
-- Analyse par trimestre
SELECT 
    CASE 
        WHEN CAST(strftime('%m', date) AS INTEGER) BETWEEN 1 AND 3 THEN 'T1'
        WHEN CAST(strftime('%m', date) AS INTEGER) BETWEEN 4 AND 6 THEN 'T2'
        WHEN CAST(strftime('%m', date) AS INTEGER) BETWEEN 7 AND 9 THEN 'T3'
        ELSE 'T4'
    END as trimestre,
    COUNT(*) as nb_transactions,
    SUM(montant_total) as ca_total
FROM ventes
GROUP BY trimestre
ORDER BY trimestre;
```

### 9. Panier moyen par catégorie et mois
```sql
-- Évolution du panier moyen par catégorie
SELECT 
    strftime('%Y-%m', date) as mois,
    categorie,
    AVG(montant_total) as panier_moyen,
    COUNT(*) as nb_transactions
FROM ventes
GROUP BY strftime('%Y-%m', date), categorie
ORDER BY mois, categorie;
```

### 10. Concentration des ventes
```sql
-- Répartition 80/20 : Top produits générant 80% du CA
WITH ca_par_produit AS (
    SELECT 
        produit,
        SUM(montant_total) as ca_produit
    FROM ventes
    GROUP BY produit
),
ca_cumule AS (
    SELECT 
        produit,
        ca_produit,
        SUM(ca_produit) OVER (ORDER BY ca_produit DESC) as ca_cumule,
        (SELECT SUM(ca_produit) FROM ca_par_produit) as ca_total
    FROM ca_par_produit
)
SELECT 
    produit,
    ca_produit,
    ROUND(ca_cumule * 100.0 / ca_total, 2) as pct_ca_cumule
FROM ca_cumule
WHERE ca_cumule <= ca_total * 0.8
ORDER BY ca_produit DESC;
```

---

## 📈 Requêtes pour les métriques du dashboard

### Métrique 1 : CA Total
```sql
SELECT ROUND(SUM(montant_total), 2) as ca_total FROM ventes;
```

### Métrique 2 : Nombre de transactions
```sql
SELECT COUNT(*) as nb_transactions FROM ventes;
```

### Métrique 3 : Panier moyen
```sql
SELECT ROUND(AVG(montant_total), 2) as panier_moyen FROM ventes;
```

### Métrique 4 : Nombre de clients uniques
```sql
SELECT COUNT(DISTINCT client_id) as nb_clients FROM ventes;
```

### Métrique 5 : Quantité moyenne par transaction
```sql
SELECT ROUND(AVG(quantite), 2) as quantite_moyenne FROM ventes;
```

---

## 🎯 Requêtes pour les filtres

### Filtre par période (exemple)
```sql
-- Ventes du mois d'avril 2024
SELECT *
FROM ventes
WHERE strftime('%Y-%m', date) = '2024-04';
```

### Filtre par catégorie (exemple)
```sql
-- Ventes de la catégorie Electronique
SELECT *
FROM ventes
WHERE categorie = 'Electronique';
```

### Filtre combiné (exemple)
```sql
-- Electronique en avril 2024
SELECT *
FROM ventes
WHERE categorie = 'Electronique'
AND strftime('%Y-%m', date) = '2024-04';
```

---

## 📝 Notes

Ces requêtes peuvent être utilisées dans :
- **SQL Lab** de Superset pour l'exploration de données
- **Custom SQL** lors de la création de datasets virtuels
- **Exploration manuelle** de la base de données

**Astuce** : Superset permet de sauvegarder ces requêtes dans SQL Lab pour une réutilisation ultérieure.

---

**Auteur** : Mounirou Cisse  
**Date** : 25 novembre 2025
