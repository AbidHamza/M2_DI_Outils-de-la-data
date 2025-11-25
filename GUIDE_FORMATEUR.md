# Guide du Formateur - Outils de la Data

**Formateur : Abid Hamza**

## 📋 Vue d'ensemble

Ce dépôt contient tous les matériaux pédagogiques pour le cours "Outils de la Data" du Master 2 Data Intelligence.

## 📁 Structure du dépôt

```
.
├── slides/                    # Présentations du cours
│   ├── cours-outils-data.md  # Version Markdown (éditable)
│   └── index.html            # Version HTML pour projection (Reveal.js)
├── exercices/                 # Exercices pratiques
│   ├── exercice-01/          # Manipulation Pandas
│   ├── exercice-02/          # Analyse SQL
│   ├── exercice-03/          # Pipeline ETL
│   ├── exercice-04/          # Apache Spark
│   ├── atelier-01/           # Dashboard analytique (projet complet)
│   └── atelier-02/            # Machine Learning Pipeline (projet complet)
├── ressources/                # Documentation et ressources
└── README.md                  # Documentation principale
```

## 🎯 Utilisation des slides

### Option 1 : Version HTML (Reveal.js) - Recommandée pour projection

1. Ouvrir `slides/index.html` dans un navigateur web
2. Utiliser les flèches du clavier pour naviguer
3. Appuyer sur `F` pour le mode plein écran
4. Appuyer sur `ESC` pour voir la vue d'ensemble
5. Appuyer sur `S` pour le mode présentateur (avec notes)

**Avantages** :
- Navigation fluide
- Transitions animées
- Mode présentateur avec notes
- Fonctionne hors ligne (CDN Reveal.js)

### Option 2 : Version Markdown

Le fichier `slides/cours-outils-data.md` peut être :
- Converti en PDF avec Pandoc
- Converti en PowerPoint/LibreOffice
- Utilisé directement dans des éditeurs Markdown

**Conversion en PDF** :
```bash
pandoc slides/cours-outils-data.md -o slides/cours-outils-data.pdf
```

**Conversion en PowerPoint** :
```bash
pandoc slides/cours-outils-data.md -o slides/cours-outils-data.pptx
```

**Conversion en LibreOffice** :
```bash
pandoc slides/cours-outils-data.md -o slides/cours-outils-data.odp
```

## 📚 Organisation du cours

### Séquence recommandée

1. **Cours théorique** (2-3h)
   - Présentation des slides
   - Explication des concepts
   - Démonstrations

2. **Exercices pratiques** (4-6h)
   - Exercice 01 : Manipulation Pandas (1h)
   - Exercice 02 : Analyse SQL (1h)
   - Exercice 03 : Pipeline ETL (2h)
   - Exercice 04 : Apache Spark (2h)

3. **Ateliers projets** (14-16h)
   - Atelier 01 : Dashboard analytique (14-16h)
   - Atelier 02 : Machine Learning Pipeline (15-17h)

### Planning suggéré

**Semaine 1** :
- Cours théorique (slides 1-5)
- Exercices 01 et 02

**Semaine 2** :
- Cours théorique (slides 6-10)
- Exercices 03 et 04

**Semaine 3-4** :
- Ateliers projets
- Présentations des projets étudiants

## 🎓 Utilisation des exercices

### Pour chaque exercice

1. **Présentation** (10 min)
   - Expliquer les objectifs
   - Présenter le contexte
   - Montrer la structure attendue

2. **Travail en autonomie** (selon durée de l'exercice)
   - Les étudiants travaillent individuellement ou en binômes
   - Support disponible si besoin

3. **Correction et discussion** (15-20 min)
   - Présenter une solution
   - Discuter des différentes approches
   - Répondre aux questions

### Suivi des étudiants

Les étudiants doivent :
1. Forker le dépôt
2. Créer un dossier `solutions/votre-nom/` dans chaque exercice
3. Pousser leurs solutions via Pull Request

Vous pouvez :
- Examiner les Pull Requests
- Donner des feedbacks
- Valider les solutions

## 💡 Conseils pédagogiques

### Pour les slides

- **Rythme** : Ne pas aller trop vite, laisser le temps de comprendre
- **Interactivité** : Poser des questions, faire participer
- **Exemples** : Utiliser des exemples concrets et pertinents
- **Schémas** : Expliquer les diagrammes en détail

### Pour les exercices

- **Progression** : Commencer par les exercices simples
- **Aide** : Être disponible pour les questions
- **Corrections** : Montrer plusieurs approches possibles
- **Feedback** : Donner des retours constructifs

### Pour les ateliers

- **Encadrement** : Suivre régulièrement l'avancement
- **Milestones** : Définir des jalons intermédiaires
- **Présentations** : Organiser des présentations des projets
- **Évaluation** : Évaluer le code, la documentation, la présentation

## 🔧 Personnalisation

### Modifier les slides

1. Éditer `slides/cours-outils-data.md` (format Markdown)
2. Pour la version HTML, modifier directement `slides/index.html`
3. Tester la présentation avant le cours

### Ajouter des exercices

1. Créer un nouveau dossier dans `exercices/`
2. Suivre la structure des exercices existants
3. Ajouter un README avec les instructions
4. Mettre à jour le README principal

### Ajouter des ressources

1. Ajouter dans le dossier `ressources/`
2. Mettre à jour `ressources/README.md`
3. Référencer dans les slides si pertinent

## 📊 Évaluation

### Critères d'évaluation suggérés

**Exercices** (40%) :
- Code fonctionnel
- Qualité du code
- Documentation
- Résultats et analyses

**Ateliers** (50%) :
- Projet complet et fonctionnel
- Architecture et design
- Documentation
- Présentation

**Participation** (10%) :
- Contributions au dépôt
- Questions et réponses
- Aide aux autres étudiants

## 🆘 Support technique

### Problèmes courants

**Slides ne s'affichent pas** :
- Vérifier la connexion internet (pour CDN Reveal.js)
- Télécharger Reveal.js localement si besoin

**Exercices ne fonctionnent pas** :
- Vérifier les dépendances Python
- Vérifier les versions des bibliothèques
- Consulter les issues GitHub

**Git/Push ne fonctionne pas** :
- Vérifier la configuration Git
- Vérifier les permissions GitHub
- Consulter CONTRIBUTING.md

## 📝 Notes importantes

- Le dépôt est public et open source
- Les étudiants peuvent contribuer
- Les corrections peuvent être ajoutées au dépôt
- Le contenu peut être amélioré en continu

## 🔄 Mise à jour du dépôt

Pour mettre à jour le dépôt après modifications :

```bash
git add .
git commit -m "Description des modifications"
git push origin main
```

## 📧 Contact

Pour toute question ou suggestion, ouvrir une issue sur GitHub.

---

**Bon cours !**

*Abid Hamza*

