# M2 DI - Outils de la Data

Ce dépôt contient les ressources pédagogiques pour le cours **Outils de la Data** du Master 2 en Data Intelligence.

## 📚 Contenu

- **Slides de cours** : Présentation complète sur les outils de la data
- **Exercices pratiques** : Exercices open source pour mettre en pratique les concepts
- **Ressources** : Documentation et liens utiles

## 🎯 Objectifs du cours

Ce cours vise à :
- Comprendre l'écosystème des outils de la data
- Maîtriser les outils essentiels pour le traitement et l'analyse de données
- Apprendre à choisir les bons outils selon le contexte
- Mettre en pratique les concepts à travers des exercices

## 📁 Structure du dépôt

```
.
├── slides/                          # Présentations du cours
│   ├── index.html                   # Version HTML pour projection (Reveal.js)
│   ├── cours-outils-data.md         # Version Markdown originale
│   ├── cours-outils-data-format-word.md  # Version optimisée pour Word/PDF
│   └── INSTRUCTIONS_CONVERSION.md   # Guide de conversion Word/PDF
├── exercices/                       # Exercices pratiques (autonomes)
│   ├── exercice-01/                 # Pandas (1h) - données générées
│   ├── exercice-02/                 # SQL (1h) - base de données générée
│   ├── exercice-03/                 # Pipeline ETL (2h)
│   ├── exercice-04/                 # Apache Spark (2h) - données générées
│   ├── exercice-05/                 # Grafana (8h) - métriques générées
│   ├── exercice-06/                 # Apache Airflow (10h)
│   ├── exercice-07/                 # dbt (11h)
│   ├── atelier-01/                  # Dashboard analytique (14-16h)
│   ├── atelier-02/                  # Machine Learning Pipeline (15-17h)
│   └── atelier-03/                  # Stack moderne complète (15h)
├── ressources/                      # Documentation et ressources
└── README.md                        # Ce fichier
```

**Total estimé : 40-42 heures de travail**

## 🚀 Démarrage rapide

### Visualiser les slides

**Option 1 : Version HTML (pour projection)**
1. Ouvrir `slides/index.html` dans un navigateur web
2. Utiliser les flèches pour naviguer entre les slides
3. Appuyer sur `F` pour le mode plein écran
4. Appuyer sur `S` pour le mode présentateur

**Option 2 : Version Word/PDF**
1. Consulter `slides/INSTRUCTIONS_CONVERSION.md` pour les instructions
2. Convertir `slides/cours-outils-data-format-word.md` en Word ou PDF
3. Utiliser Pandoc, LibreOffice ou Word pour la conversion

### Exécuter les exercices

Chaque exercice est **autonome** et contient :
- Un fichier `README.md` avec les instructions détaillées
- Un script `generer_donnees.py` pour créer les données nécessaires (si applicable)
- Toutes les instructions pour installer et utiliser les outils requis
- Des exemples de code et de solutions

**Important** : Tous les exercices sont conçus pour être complétés de manière autonome. Les données sont générées automatiquement via les scripts fournis.

## 🛠️ Technologies utilisées

- **Reveal.js** : Pour les présentations interactives
- **Python** : Pour les exercices pratiques
- **Jupyter Notebook** : Pour certains exercices interactifs

## 📝 Licence

Ce projet est sous licence MIT - voir le fichier [LICENSE](LICENSE) pour plus de détails.

## 📤 Comment soumettre vos réponses aux exercices

### Méthode 1 : Fork et Pull Request (Recommandé)

1. **Forker le dépôt** :
   - Cliquez sur le bouton "Fork" en haut à droite de cette page
   - Cela crée une copie du dépôt dans votre compte GitHub

2. **Cloner votre fork** :
   ```bash
   git clone https://github.com/VOTRE_USERNAME/M2_DI_Outils-de-la-data.git
   cd M2_DI_Outils-de-la-data
   ```

3. **Créer une branche pour votre travail** :
   ```bash
   git checkout -b nom-prenom-exercice-01
   # Exemple : git checkout -b jean-dupont-exercice-01
   ```

4. **Travailler sur l'exercice** :
   - Allez dans le dossier de l'exercice (ex: `exercices/exercice-01/`)
   - Créez un dossier avec votre nom : `exercices/exercice-01/solutions/votre-nom/`
   - Placez vos fichiers de solution dans ce dossier
   - Suivez les instructions dans le README de l'exercice

5. **Ajouter et commiter vos changements** :
   ```bash
   git add .
   git commit -m "Solution exercice 01 - Votre Nom"
   ```

6. **Pousser vers votre fork** :
   ```bash
   git push origin nom-prenom-exercice-01
   ```

7. **Créer une Pull Request** :
   - Allez sur votre fork sur GitHub
   - Cliquez sur "Compare & pull request"
   - Remplissez le formulaire avec votre nom et le numéro de l'exercice
   - Soumettez la Pull Request

### Méthode 2 : Ajout direct dans le dépôt (si vous avez les droits)

1. **Cloner le dépôt** :
   ```bash
   git clone https://github.com/AbidHamza/M2_DI_Outils-de-la-data.git
   cd M2_DI_Outils-de-la-data
   ```

2. **Créer votre dossier de solution** :
   - Créez un dossier dans `exercices/exercice-XX/solutions/votre-nom/`
   - Placez vos fichiers de solution dedans

3. **Pousser vos changements** :
   ```bash
   git add .
   git commit -m "Solution exercice XX - Votre Nom"
   git push origin main
   ```

### Structure de soumission attendue

Pour chaque exercice, créez un dossier avec votre nom dans le dossier `solutions/` :

```
exercices/
└── exercice-01/
    ├── README.md
    ├── donnees/
    └── solutions/
        ├── jean-dupont/
        │   ├── solution.py
        │   ├── resultats.md
        │   └── README.md (optionnel - explication de votre approche)
        └── marie-martin/
            ├── solution.py
            └── resultats.md
```

### 📋 Checklist avant de soumettre

- [ ] J'ai lu et compris les instructions de l'exercice
- [ ] Mon code est commenté et lisible
- [ ] J'ai testé mon code et il fonctionne
- [ ] J'ai créé un dossier avec mon nom dans `solutions/`
- [ ] J'ai ajouté un fichier `resultats.md` ou `README.md` expliquant ma solution
- [ ] Mon commit message est clair et contient mon nom

## 🤝 Contribution

Les contributions sont les bienvenues ! N'hésitez pas à :
- Proposer de nouveaux exercices
- Améliorer la documentation
- Corriger les erreurs

## 📧 Contact

Pour toute question, ouvrez une issue sur ce dépôt.

