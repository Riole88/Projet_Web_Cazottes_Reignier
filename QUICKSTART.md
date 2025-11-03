# Quickstart - Flexbox, Grid et SCSS

## FLEXBOX

Flexbox permet de créer des mises en page flexibles en une dimension (ligne ou colonne).

### Conteneur flexible

```css
.container {
  display: flex;  /* ou inline-flex */
}
```

Les éléments enfants deviennent des **éléments flexibles** et sont organisés selon un **axe principal**.

### Direction et alignement

```css
.container {
  display: flex;
  flex-direction: row;        /* Horizontal (défaut) */
  flex-direction: column;     /* Vertical */
  justify-content: center;    /* Alignement sur l'axe principal */
  align-items: center;        /* Alignement sur l'axe secondaire */
  flex-wrap: wrap;            /* Retour à la ligne */
}
```

### Propriétés du conteneur

- `flex-direction` : `row` | `row-reverse` | `column` | `column-reverse`
- `justify-content` : `flex-start` | `flex-end` | `center` | `space-between` | `space-around` | `space-evenly`
- `align-items` : `stretch` | `flex-start` | `flex-end` | `center` | `baseline`
- `flex-wrap` : `nowrap` | `wrap` | `wrap-reverse`
- `gap` : espacement entre les éléments

### Propriétés des éléments

```css
.item {
  order: 2;              /* Ordre d'affichage */
  flex: 1;               /* Prend tout l'espace disponible */
  flex-grow: 2;          /* Coefficient de croissance */
  flex-shrink: 1;        /* Coefficient de rétrécissement */
  flex-basis: 200px;     /* Taille initiale */
  align-self: center;    /* Alignement individuel */
}
```

### Exemples pratiques

```css
/* Centrer un élément */
.center {
  display: flex;
  justify-content: center;
  align-items: center;
}

/* Navigation avec espacement */
.nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

/* Colonnes égales */
.columns {
  display: flex;
}
.column {
  flex: 1;
}

/* Grille flexible */
.grid {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}
.grid-item {
  flex: 1 1 300px;  /* min 300px, peut grandir et rétrécir */
}
```

## CSS GRID

Grid permet de créer des mises en page en deux dimensions (lignes ET colonnes).

### Grille de base

```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);  /* 3 colonnes égales */
  grid-template-rows: repeat(2, 200px);   /* 2 lignes de 200px */
  gap: 20px;                              /* Espacement */
}
```

### Définition des colonnes/lignes

```css
.container {
  display: grid;
  grid-template-columns: 200px 1fr 200px;      /* Colonnes fixes et flexibles */
  grid-template-columns: repeat(12, 1fr);      /* 12 colonnes égales */
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));  /* Adaptatif */
  gap: 20px;
}
```

### Positionnement des éléments

```css
.item {
  grid-column: 1 / 3;      /* De la colonne 1 à 3 */
  grid-row: 1 / 2;          /* Ligne 1 */
  grid-column: span 2;      /* Occupe 2 colonnes */
}
```

### Zones nommées

```css
.container {
  display: grid;
  grid-template-columns: 200px 1fr;
  grid-template-areas:
    "header header"
    "sidebar main"
    "footer footer";
}

.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main { grid-area: main; }
.footer { grid-area: footer; }
```

### Alignement

```css
.container {
  justify-items: center;    /* Alignement horizontal */
  align-items: center;     /* Alignement vertical */
}

.item {
  justify-self: end;       /* Alignement individuel horizontal */
  align-self: center;      /* Alignement individuel vertical */
}
```

### Exemples pratiques

```css
/* Layout classique */
.layout {
  display: grid;
  grid-template-columns: 200px 1fr;
  grid-template-rows: auto 1fr auto;
  grid-template-areas:
    "header header"
    "sidebar main"
    "footer footer";
  min-height: 100vh;
}

/* Grille de cartes responsive */
.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}
```

## SCSS

SCSS est un préprocesseur CSS qui ajoute des fonctionnalités avancées.

### Variables

```scss
$primary-color: #3498db;
$spacing: 1rem;
$font-main: 'Helvetica', sans-serif;

.button {
  background-color: $primary-color;
  padding: $spacing;
  font-family: $font-main;
}
```

### Nesting (Imbrication)

```scss
.nav {
  background-color: #333;
  
  ul {
    list-style: none;
  }
  
  li {
    a {
      color: white;
      
      &:hover {
        color: yellow;
      }
    }
  }
}
```

Le `&` représente le sélecteur parent.

### Partials et @import

```scss
// _variables.scss
$primary-color: #3498db;

// main.scss
@import 'variables';

.button {
  background-color: $primary-color;
}
```

Les fichiers préfixés par `_` sont des partials (non compilés seuls).

### Mixins

```scss
@mixin flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}

@mixin button($bg-color, $text-color) {
  background-color: $bg-color;
  color: $text-color;
  padding: 1rem 2rem;
  border-radius: 4px;
}

.button {
  @include flex-center;
  @include button(#3498db, white);
}
```

### Héritage (@extend)

```scss
.message {
  padding: 1rem;
  border: 1px solid #ccc;
}

.success {
  @extend .message;
  background-color: green;
}
```

### Opérateurs

```scss
$base-size: 16px;

.container {
  width: $base-size * 10;      // 160px
  padding: $base-size / 2;     // 8px
  font-size: $base-size * 1.5; // 24px
}
```

### Fonctions

```scss
$primary: #3498db;

.button {
  background-color: $primary;
  
  &:hover {
    background-color: darken($primary, 10%);
  }
}
```

Autres fonctions : `lighten()`, `rgba()`, `mix()`, `percentage()`, `round()`, etc.

### Conditions et boucles

```scss
// @if / @else
@mixin theme($theme) {
  @if $theme == dark {
    background-color: #333;
  } @else {
    background-color: white;
  }
}

// @for
@for $i from 1 through 12 {
  .col-#{$i} {
    width: percentage($i / 12);
  }
}

// @each
$colors: red, blue, green;
@each $color in $colors {
  .btn-#{$color} {
    background-color: $color;
  }
}
```

### Interpolation

```scss
$name: "button";
$property: "margin";

.#{$name} {
  #{$property}: 1rem;
}
```

### Compilation

```bash
# Installation
npm install -g sass

# Compilation simple
sass scss/main.scss css/main.css

# Watch mode (recompilation automatique)
sass --watch scss:css

# Via npx (sans installation)
npx sass scss/main.scss css/main.css

# Options
sass scss/main.scss css/main.css --style compressed  # Minifier
sass scss/main.scss css/main.css --source-map        # Source maps
```

## Récapitulatif

### Flexbox vs Grid

- **Flexbox** : 1 dimension (ligne OU colonne), pour aligner des éléments dans un conteneur
- **Grid** : 2 dimensions (lignes ET colonnes), pour créer des layouts complets
- Utilisez les deux : Grid pour la structure, Flexbox pour les composants

### Structure SCSS recommandée

```
scss/
├── _variables.scss    # Variables globales
├── _mixins.scss       # Mixins réutilisables
├── _layout.scss       # Styles de layout
├── _components.scss   # Composants
└── main.scss          # Point d'entrée
```