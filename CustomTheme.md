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

## 📂 2. La Hiérarchie des Fichiers

WordPress utilise un système de cascade pour choisir quel fichier PHP va afficher une page. Si un fichier spécifique n'existe pas, il passe au suivant jusqu'à arriver à `index.php`.

#### Fichiers de structure réutilisables :

- `header.php` : Contient la balise `<head>`, le menu de navigation et le haut de page.
- `footer.php` : Contient le pied de page, les scripts et la fermeture des balises HTML.
- `sidebar.php` : Gère les barres latérales (zones de widgets).

#### Fichiers de gabarits spécifiques :

- `front-page.php` : Utilisé exclusivement pour la page d'accueil statique du site.
- `home.php` : La page qui liste les derniers articles de blog.
- `single.php` : Affiche le détail d'un article de blog unique (_Post_).
- `page.php` : Affiche une page statique unique (_Page_).
- `archive.php` : Affiche les listes d'articles (par catégorie, tag ou date).
- `404.php` : Page d'erreur en cas d'URL introuvable (lien mort).
