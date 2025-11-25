# Instructions pour convertir les slides en Word/PDF

## Fichiers disponibles

1. **cours-outils-data-format-word.md** : Version optimisée pour conversion Word/PDF
2. **cours-outils-data.md** : Version Markdown originale
3. **index.html** : Version HTML pour projection (Reveal.js)

## Conversion en Word (.docx)

### Méthode 1 : Avec Pandoc (Recommandé)

```bash
# Installer Pandoc
# Windows : Télécharger depuis https://pandoc.org/installing.html
# Mac : brew install pandoc
# Linux : sudo apt-get install pandoc

# Conversion en Word
pandoc slides/cours-outils-data-format-word.md -o slides/cours-outils-data.docx

# Avec styles personnalisés
pandoc slides/cours-outils-data-format-word.md -o slides/cours-outils-data.docx --reference-doc=template.docx
```

### Méthode 2 : Avec LibreOffice

1. Ouvrir LibreOffice Writer
2. Fichier > Ouvrir > Sélectionner `cours-outils-data-format-word.md`
3. LibreOffice détectera automatiquement le format Markdown
4. Fichier > Exporter au format PDF ou Enregistrer sous > Format Word

### Méthode 3 : Avec Word directement

1. Ouvrir Microsoft Word
2. Fichier > Ouvrir > Sélectionner `cours-outils-data-format-word.md`
3. Word proposera de convertir le Markdown
4. Ajuster le formatage si nécessaire
5. Enregistrer en .docx

## Conversion en PDF

### Méthode 1 : Avec Pandoc

```bash
# Conversion directe en PDF (nécessite LaTeX)
pandoc slides/cours-outils-data-format-word.md -o slides/cours-outils-data.pdf

# Avec options de mise en page
pandoc slides/cours-outils-data-format-word.md -o slides/cours-outils-data.pdf \
  --pdf-engine=xelatex \
  -V geometry:margin=2cm \
  -V fontsize=12pt
```

### Méthode 2 : Depuis Word

1. Ouvrir le fichier .docx dans Word
2. Fichier > Exporter > Créer un document PDF/XPS
3. Choisir les options (qualité, sécurité)
4. Enregistrer

### Méthode 3 : Depuis LibreOffice

1. Ouvrir le fichier dans LibreOffice Writer
2. Fichier > Exporter au format PDF
3. Configurer les options (qualité, sécurité)
4. Exporter

### Méthode 4 : Depuis le navigateur (HTML)

1. Ouvrir `slides/index.html` dans un navigateur
2. Appuyer sur `Ctrl+P` (ou Cmd+P sur Mac)
3. Choisir "Enregistrer en PDF" comme destination
4. Configurer les options d'impression
5. Enregistrer

## Personnalisation du formatage

### Pour Word

Après conversion, vous pouvez :
- Ajuster les styles de titre
- Modifier les polices
- Ajouter un en-tête/pied de page
- Insérer une page de garde
- Ajuster les marges

### Pour PDF

Options recommandées :
- Format : A4
- Marges : 2 cm
- Police : Arial ou Calibri, taille 12pt pour le texte
- Titres : Police plus grande, gras
- Couleurs : Utiliser des couleurs cohérentes pour les titres

## Conseils

1. **Vérifier le formatage** après conversion
2. **Ajuster les schémas** si nécessaire (les diagrammes ASCII peuvent nécessiter des ajustements)
3. **Ajouter une page de garde** avec le titre du cours et votre nom
4. **Numéroter les pages** pour faciliter la navigation
5. **Créer un sommaire** automatique dans Word

## Outils en ligne (alternative)

Si vous n'avez pas Pandoc installé :
- **Dillinger** : https://dillinger.io/ (Markdown vers HTML, puis imprimer en PDF)
- **Markdown to PDF** : Extensions de navigateur disponibles
- **CloudConvert** : https://cloudconvert.com/ (conversion en ligne)

## Template Word personnalisé (optionnel)

Pour créer un template Word avec vos styles :

1. Créer un document Word avec les styles souhaités
2. Enregistrer comme template (.dotx)
3. Utiliser avec Pandoc : `--reference-doc=template.dotx`

---

**Note** : Le fichier `cours-outils-data-format-word.md` est optimisé pour la conversion avec des titres clairs et une structure adaptée à Word/PDF.

