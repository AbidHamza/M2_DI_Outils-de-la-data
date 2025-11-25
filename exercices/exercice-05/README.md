# Exercice 05 : Monitoring avec Grafana

## 🎯 Objectifs

- Comprendre le monitoring et l'observabilité des systèmes de données
- Installer et configurer Grafana
- Créer des dashboards de monitoring
- Visualiser des métriques en temps réel
- Configurer des alertes

## 📋 Prérequis

- Python 3.8+
- Docker (recommandé) ou installation native
- Connaissances de base en monitoring

## 📦 Installation

### Option 1 : Avec Docker (Recommandé)

```bash
# Télécharger et lancer Grafana avec Docker
docker run -d -p 3000:3000 --name=grafana grafana/grafana:latest

# Accéder à Grafana : http://localhost:3000
# Identifiants par défaut : admin / admin
```

### Option 2 : Installation native

**Windows** :
1. Télécharger depuis : https://grafana.com/grafana/download?platform=windows
2. Installer le fichier .msi
3. Grafana sera accessible sur http://localhost:3000

**Linux** :
```bash
# Ubuntu/Debian
sudo apt-get install -y software-properties-common
sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
sudo apt-get update
sudo apt-get install grafana
sudo systemctl start grafana-server
```

**Mac** :
```bash
brew install grafana
brew services start grafana
```

## 📊 Données

Les données de monitoring sont générées par le script `generer_metriques.py` qui simule des métriques système (CPU, mémoire, disque, réseau, etc.).

## 🎓 Instructions

### Étape 1 : Préparation des données (1h)

1. Exécutez le script `generer_metriques.py` pour générer les données de monitoring
2. Le script crée un fichier CSV avec des métriques système simulées
3. Explorez les données générées

### Étape 2 : Installation et configuration Grafana (1h)

1. **Installer Grafana** (voir section Installation ci-dessus)
2. **Première connexion** :
   - Ouvrir http://localhost:3000
   - Identifiants par défaut : `admin` / `admin`
   - Changer le mot de passe lors de la première connexion

3. **Configurer une source de données** :
   - Aller dans Configuration > Data Sources
   - Ajouter une source de type "CSV" ou "MySQL" (selon votre choix)
   - Configurer la connexion aux données

### Étape 3 : Création de panneaux (Panels) (2h)

Créez au moins 5 panneaux différents :

1. **Graphique de ligne** : Évolution du CPU dans le temps
2. **Graphique en barres** : Utilisation de la mémoire par serveur
3. **Gauge** : Pourcentage d'utilisation du disque
4. **Stat** : Nombre total de requêtes
5. **Table** : Top 10 des serveurs par charge CPU

### Étape 4 : Création d'un dashboard complet (2h)

1. **Organiser les panneaux** :
   - Créer des lignes (rows) pour organiser
   - Grouper les métriques par catégorie
   - Ajouter des titres et descriptions

2. **Variables de dashboard** :
   - Créer une variable pour filtrer par serveur
   - Créer une variable pour la période (dernière heure, jour, semaine)

3. **Templates et répétition** :
   - Utiliser les variables pour créer des panneaux répétitifs
   - Configurer l'auto-refresh (ex: toutes les 30 secondes)

### Étape 5 : Alertes (1h)

1. **Créer des règles d'alerte** :
   - Alerte si CPU > 80%
   - Alerte si mémoire < 10% disponible
   - Alerte si disque > 90% utilisé

2. **Configurer les notifications** :
   - Configurer un canal de notification (email, Slack, etc.)
   - Tester les alertes

### Étape 6 : Export et documentation (1h)

1. **Exporter le dashboard** :
   - Exporter en JSON
   - Sauvegarder dans votre dossier de solution

2. **Créer un fichier `resultats.md`** avec :
   - Captures d'écran des dashboards
   - Explication de la configuration
   - Description des métriques surveillées
   - Configuration des alertes

## 📁 Structure attendue

```
exercice-05/
├── README.md (ce fichier)
├── donnees/
│   └── metriques.csv (généré)
├── solutions/
│   └── votre-nom/
│       ├── dashboard.json (dashboard exporté)
│       ├── screenshots/ (captures d'écran)
│       ├── resultats.md
│       └── configuration.md (optionnel)
```

## ✅ Critères d'évaluation

- [ ] Grafana installé et configuré
- [ ] Dashboard fonctionnel avec au moins 5 panneaux
- [ ] Variables de dashboard configurées
- [ ] Alertes configurées et testées
- [ ] Documentation complète avec captures d'écran
- [ ] Dashboard exporté en JSON

## 💡 Conseils

- Utilisez les templates Grafana pour vous inspirer
- Testez vos requêtes dans l'éditeur de requêtes avant de créer les panneaux
- Organisez vos dashboards de manière logique
- Utilisez des couleurs cohérentes pour les métriques
- Ajoutez des annotations pour marquer les événements importants

## 🚀 Fonctionnalités avancées (Bonus)

- Intégration avec Prometheus pour les métriques en temps réel
- Création de dashboards interactifs avec des liens entre panneaux
- Utilisation de plugins Grafana
- Configuration de sources de données multiples
- Création de dashboards partagés

## 📚 Ressources

- Documentation Grafana : https://grafana.com/docs/grafana/latest/
- Guides de démarrage : https://grafana.com/docs/grafana/latest/getting-started/
- Galerie de dashboards : https://grafana.com/grafana/dashboards/

## 🆘 Aide

Si vous êtes bloqué :
1. Consultez la documentation officielle Grafana
2. Regardez les tutoriels vidéo sur YouTube
3. Ouvrez une issue sur le dépôt GitHub

## 📤 Soumission

Suivez les instructions dans le README principal du dépôt pour soumettre votre solution.

**Durée estimée : 8 heures**

