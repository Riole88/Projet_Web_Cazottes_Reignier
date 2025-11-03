# Projet Web

Ce projet contient deux systèmes de styles SCSS différents, permettant de basculer entre deux approches de développement.

## Installation

Pour cloner le projet depuis GitHub :

```bash
git clone https://github.com/Riole88/Projet_Web_Cazottes_Reignier
cd Projet_Web_Cazottes_Reignier
```

Le projet est maintenant prêt à être utilisé. Les fichiers HTML peuvent être ouverts directement dans un navigateur.

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

## Utilisation des fichiers HTML

Le projet contient des fichiers HTML séparés pour chaque système de styles, il n'est donc pas nécessaire de modifier les liens CSS :

### Système scss-cours (moderne)

Pour utiliser le système **scss-cours** avec Flexbox et CSS Grid :
- Ouvrir `index.html` (utilise `css/styles-cours.css`)
- Ouvrir `article.html` (utilise `css/article-cours.css`)

### Système scss (traditionnel)

Pour utiliser le système **scss** traditionnel :
- Ouvrir `index 2.html` (utilise `css/styles.css`)
- Ouvrir `article 2.html` (utilise `css/article.css`)

Chaque fichier HTML est déjà configuré avec le bon fichier CSS, il suffit d'ouvrir le fichier correspondant au système souhaité.

## Différences principales

| Fonctionnalité | scss-cours | scss |
|---------------|------------|------|
| Flexbox (mixins) | Oui | Non |
| CSS Grid | Oui | Non |
| Mixins de grille | Oui | Non |
| Architecture modulaire | Basique | Basique |
| Responsive (mixins) | Oui | Oui |