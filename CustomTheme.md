## 🎨 DEVELOPPEMENT DE THEMES PERSONNALISES (CUSTOM THEMES)

Créer un thème personnalisé permet de concevoir un site unique, performant et parfaitement adapté aux besoins du projet, sans le surplus de code des thèmes génériques.

Ce guide rassemble l'essentiel pour créer, structurer et développer un thème WordPress sur mesure à partir de zéro (_from scratch_).

## 1. 🏠 Structure Minimale d'un Thème

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

## 2. 📂 La Hiérarchie des Fichiers

WordPress utilise un système de cascade pour choisir quel fichier PHP va afficher une page. Si un fichier spécifique n'existe pas, il passe au suivant jusqu'à arriver à `index.php`.

#### Fichiers de structure réutilisables :

- `header.php` : Contient la balise `<head>`, le menu de navigation et le haut de page. Appelé avec `get_header();`.
- `footer.php` : Contient le pied de page, les scripts et la fermeture des balises HTML. Appelé avec `get_footer();`.
- `sidebar.php` : Gère les barres latérales (zones de widgets). Appelé avec `get_sidebar();`.

#### Fichiers de gabarits spécifiques :

- `front-page.php` : Utilisé exclusivement pour la page d'accueil statique du site.
- `home.php` : La page qui liste les derniers articles de blog.
- `single.php` : Affiche le détail d'un article de blog unique (_Post_).
- `page.php` : Affiche une page statique unique (_Page_).
- `archive.php` : Affiche les listes d'articles (par catégorie, tag ou date).
- `404.php` : Page d'erreur en cas d'URL introuvable (lien mort).

### Architecture recommandée pour un thème classique :

```text
mon-theme-personnel/
├── assets/             # CSS, JS, Images, Polices
│   ├── css/
│   └── js/
├── parts/              # Morceaux de templates (ex: site-header.php)
├── inc/                # Fichiers PHP de configuration (fonctions, hooks)
├── 404.php             # Page d'erreur 404
├── archive.php         # Affichage des listes (catégories, tags, auteurs)
├── footer.php          # Pied de page global
├── functions.php       # Configuration, hooks et scripts du thème
├── header.php          # En-tête global
├── index.php           # Template par défaut
├── page.php            # Modèle pour les pages statiques
├── single.php          # Modèle pour les articles de blog (Posts)
├── style.css           # En-tête du thème (Obligatoire)
└── screenshot.jpg      # Image d'aperçu dans le tableau de bord (1200x900px)
```

## 3. ⚙️ Le fichier de configuration : `functions.php`

Ce fichier agit comme une extension intégrée à votre thème. C'est ici que vous activez les fonctionnalités de WordPress et liez vos scripts.

### Bonnes pratiques d'intégration des styles et scripts :

_Ne jamais ajouter de balises `<link>` ou `<script>` en dur dans `header.php`_. Utilisez toujours le hook `wp_enqueue_scripts`.

```php
<?php
// Dans wp-content/themes/mon-theme-personnel/functions.php

function mon_theme_scripts() {
    // Intégrer la feuille de style principale style.css
    wp_enqueue_style( 'mon-theme-main-style', get_stylesheet_uri(), array(), '1.0.0' );

    // Intégrer un script JavaScript (ici chargé en pied de page avec 'true')
    wp_enqueue_script( 'mon-theme-main-js', get_template_directory_uri() . '/js/main.js', array('jquery'), '1.0.0', true );
}
add_action( 'wp_enqueue_scripts', 'mon_theme_scripts' );

function mon_theme_supports() {
    // Ajouter le support des balises de titre dynamiques (<title>)
    add_theme_support( 'title-tag' );

    // Activer les images à la une pour les articles
    add_theme_support( 'post-thumbnails' );

    // Enregistrer les emplacements de menus de navigation
    register_nav_menus( array(
        'main-menu' => __( 'Menu Principal', 'mon-theme-personnel' ),
        'footer-menu' => __( 'Menu Pied de Page', 'mon-theme-personnel' ),
    ) );
}
add_action( 'after_setup_theme', 'mon_theme_supports' );
```

## 4. 🔄 La Boucle WordPress (The Loop)

C'est le mécanisme central de WordPress. La boucle WordPress parcourt la base de données pour récupérer et afficher le contenu demandé par l'utilisateur.

```php
<?php
get_header(); // Inclut header.php

if ( have_posts() ) :
    while ( have_posts() ) : the_post(); ?>

        <article id="post-<?php the_ID(); ?>" <?php post_class(); ?>>
            <h2><a href="<?php the_permalink(); ?>"><?php the_title(); ?></a></h2>
            <div class="post-meta">Publié le <?php the_date(); ?> par <?php the_author(); ?></div>
            <div class="post-content">
                <?php the_excerpt(); // Affiche un résumé de l'article ?>
            </div>
        </article>

    <?php endwhile;
else : ?>
    <p>Aucun contenu trouvé pour le moment.</p>
<?php endif;

get_footer(); // Inclut footer.php
?>
```

## 5. 🪝 Les fonctions natives indispensables

Ces fonctions PHP s'utilisent à l'intérieur de vos fichiers de thèmes pour injecter le contenu dynamiquement :

- `wp_head()` : **Obligatoire juste avant `</head>` dans `header.php`**. Permet aux plugins d'injecter des styles/scripts.
- `wp_footer()` : **Obligatoire juste avant `</body>` ans `footer.php`**. Permet d'injecter les scripts de pied de page.
- `the_title()` / `get_the_title()` : Affiche ou retourne le titre du contenu actuel.
- `the_content()` : Affiche le corps principal créé dans l'éditeur (Gutenberg).
- `the_post_thumbnail( 'large' )` : Affiche l'image à la une au format configuré.
- `the_permalink()` : Génère l'URL du post actuel.
- `the_category()` : Affiche les catégories associées.
