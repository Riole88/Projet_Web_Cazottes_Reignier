# Projet Web

Ce projet contient deux systèmes de styles SCSS différents, permettant de basculer entre deux approches de développement.

## Architecture des styles

### Système scss-cours (moderne)

Le dossier `scss-cours/` contient une architecture de styles moderne basée sur :

- **Flexbox** : Utilisation de mixins Flexbox pour la gestion des layouts flexibles
- **CSS Grid** : Utilisation native de CSS Grid pour les structures en grille
- **Mixins de grille** : Mixins réutilisables pour créer des grilles responsives (`_mixins-grid.scss`)
- **Mixins Flexbox** : Mixins réutilisables pour les layouts flexbox (`_mixins-flex.scss`)
- **Architecture modulaire** : Organisation en fichiers partiels (`_variables.scss`, `_layout.scss`, `_header.scss`, `_sections.scss`, `_article.scss`, `_index.scss`)

#### Structure scss-cours

```
scss-cours/
├── _variables.scss          # Variables globales (couleurs, espacements, breakpoints)
├── _mixins-flex.scss        # Mixins pour Flexbox
├── _mixins-grid.scss        # Mixins pour CSS Grid
├── _mixins-responsive.scss  # Mixins pour les media queries
├── _layout.scss            # Styles de layout général (page, conteneur, footer)
├── _header.scss            # Styles du header (logo, navigation, ariane)
├── _sections.scss          # Styles des sections spéciales (Soutenez-nous, Nous suivre, etc.)
├── _article.scss           # Styles spécifiques à la page article
├── _index.scss             # Styles spécifiques à la page d'accueil
├── main.scss              # Point d'entrée pour la page d'accueil
└── article-cours.scss      # Point d'entrée pour la page article
```

#### Compilation

Les fichiers SCSS sont compilés vers CSS dans le dossier `css/` :
- `main.scss` : `css/styles-cours.css` (pour la page d'accueil):
- `article-cours.scss` : `css/article-cours.css` (pour la page article)

Pour compiler :
```bash
npx sass scss-cours/main.scss css/styles-cours.css
npx sass scss-cours/article-cours.scss css/article-cours.css
```

### Système scss (traditionnel)

Le dossier `scss/` contient l'architecture de styles originale, sans l'utilisation de Flexbox, CSS Grid ou de mixins de grille modernes.

#### Structure scss

```
scss/
├── _variables.scss    # Variables globales
├── _base.scss         # Styles de base
├── _mixins.scss       # Mixins généraux (sans grille moderne)
├── _responsive.scss   # Styles responsive
├── _article.scss      # Styles spécifiques à la page article
├── main.scss         # Point d'entrée pour la page d'accueil
└── article.scss      # Point d'entrée pour la page article
```

#### Compilation

Les fichiers SCSS sont compilés vers CSS dans le dossier `css/` :
- `main.scss` : `css/styles.css` (pour la page d'accueil)
- `article.scss` : `css/article.css` (pour la page article)

## Basculer entre les deux systèmes

Pour utiliser le système **scss-cours** (moderne avec Flexbox/CSS Grid), les fichiers HTML doivent référencer :

**Dans `index.html`** :
```html
<link rel="stylesheet" href="css/styles-cours.css" type="text/css">
```

**Dans `article.html`** :
```html
<link rel="stylesheet" href="css/article-cours.css" type="text/css">
```

Pour utiliser le système **scss** (traditionnel), les fichiers HTML doivent référencer :

**Dans `index.html`** :
```html
<link rel="stylesheet" href="css/styles.css" type="text/css">
```

**Dans `article.html`** :
```html
<link rel="stylesheet" href="css/article.css" type="text/css">
```

### Exemple de modification

Pour passer du système scss-cours au système scss dans `article.html`, modifiez :

**Avant** :
```html
<link rel="stylesheet" href="css/article-cours.css" type="text/css">
```

**Après** :
```html
<link rel="stylesheet" href="css/article.css" type="text/css">
```

Et dans `index.html`, modifiez :

**Avant** :
```html
<link rel="stylesheet" href="css/styles-cours.css" type="text/css">
```

**Après** :
```html
<link rel="stylesheet" href="css/styles.css" type="text/css">
```

## Différences principales

| Fonctionnalité | scss-cours | scss |
|---------------|------------|------|
| Flexbox (mixins) | Oui | Non |
| CSS Grid | Oui | Non |
| Mixins de grille | Oui | Non |
| Architecture modulaire | Basique | Basique |
| Responsive (mixins) | Oui | Oui |