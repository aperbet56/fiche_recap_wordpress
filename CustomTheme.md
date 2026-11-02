## 🎨 DEVELOPPEMENT DE THEMES PERSONNALISES (CUSTOM THEMES)

Créer un thème personnalisé permet de concevoir un site unique, performant et parfaitement adapté aux besoins du projet, sans le surplus de code des thèmes génériques.

## 🏠 1. Structure Minimale d'un Thème

Pour que WordPress reconnaisse un thème, un dossier portant le nom de votre thème doit être créé dans `wp-content/themes/` avec au minimum ces **deux fichiers indispensables** :

```text
wp-content/themes/mon-theme-personnel/
├── style.css       # Contient les métadonnées du thème et les styles CSS
└── index.php       # Fichier de secours principal pour afficher le contenu
```

#### Exemple d'en-tête obligatoire dans `style.css` :

```css
/*
Theme Name: Mon Thème Personnalisé
Theme URI: https://mon-site.com
Author: Votre Nom
Author URI: https://votre-site.com
Description: Une description plus moins longue de votre thème.
Version: 1.0.0
License: GNU General Public License v2 or later
Text Domain: mon-theme-personnel
*/
```
