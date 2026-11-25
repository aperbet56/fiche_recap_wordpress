## 📝 FICHE RECAPITULATIVE CUSTOM JS & CSS SUR WORDPRESS

Guide récapitulatif des bonnes pratiques pour ajouter, gérer et optimiser du code CSS et JavaScript personnalisé sur un site WordPress.

## 📁 1. Où placer son code ? (Par ordre de recommandation)

| Méthode                                            | CSS | JS  | Avantages                                | Inconvénients                        |
| :------------------------------------------------- | :-: | :-: | :--------------------------------------- | :----------------------------------- |
| **Thème Enfant (`functions.php`)**                 | ✅  | ✅  | Sécurisé, performant, versionnable (Git) | Nécessite un accès FTP/fichiers      |
| **Extension dédiée (ex: WPCode)**                  | ✅  | ✅  | Interface simple, gestion conditionnelle | Ajoute un plugin supplémentaire      |
| **Personnalisateur (`Apparence > Personnaliser`)** | ✅  | ❌  | Natif, aperçu en direct, rapide          | Uniquement pour du CSS léger         |
| **Constructeur de pages (Elementor, Divi...)**     | ✅  | ✅  | Ciblé par page ou élément                | Code dispersé, difficile à maintenir |

> ⚠️ **Règle d'or :** Ne jamais modifier directement les fichiers d'un thème parent ou d'une extension (écrasement garanti à la prochaine mise à jour).

### Ajouter du CSS Sans code (Via l'interface WordPress)

Idéal pour des ajustements CSS rapides et légers (ne fonctionne pas pour le JavaScript).

- **Thèmes classiques :** Aller dans `Apparence > Personnaliser > CSS additionnel`.
- **Thèmes FSE (Full Site Editing) :** Aller dans `Apparence > Éditeur > Styles (icône lune/soleil) > Trois petits points (⋮) > CSS additionnel`.

### Via un Thème Enfant (Recommandé)

La méthode la plus propre et performante pour éviter d'alourdir la base de données et conserver vos modifications lors des mises à jour du thème parent.

# 🎯 2. Ajouter du Custom CSS

### Méthode A : Via l'interface native (Rapide)

1. Aller dans **Apparence > Personnaliser > CSS additionnel**.
2. Écrire le code CSS et cliquer sur **Publier**.
   _(Note : Si vous utilisez un thème FSE / Full Site Editing récent, allez dans **Apparence > Éditeur > Styles > ⋮ > CSS additionnel**)._

### Méthode B : Via un Thème Enfant (Recommandé pour les projets complexes)

1. 📁 Structure des fichiers

```text
wp-content/themes/mon-theme-enfant/
├── style.css
├── functions.php
└── assets/
    ├── css/
    │   └── custom.css
    └── js/
        └── custom.js
```

2. ⚙️ Chargement dans `functions.php`

Utilisez toujours les hooks `wp_enqueue_scripts` pour charger vos fichiers proprement.

```php
<?php
function mon_theme_enfant_scripts() {
    // 1. Charger le CSS personnalisé
    wp_enqueue_style(
        'mon-custom-css', // Identifiant unique (handle)
        get_stylesheet_directory_uri() . '/assets/css/custom.css', // Chemin
        array(), // Dépendances éventuelles
        '1.0.0' // Version (utile pour vider le cache)
    );

    // 2. Charger le JS personnalisé
    wp_enqueue_script(
        'mon-custom-js', // Identifiant unique (handle)
        get_stylesheet_directory_uri() . '/assets/js/custom.js', // Chemin du fichier
        array('jquery'), // Dépendances (ex: 'jquery' ou array() pour du Vanilla JS)
        '1.0.0', // Version
        true // Charger dans le footer (true = recommandé pour les performances)
    );
}
add_action('wp_enqueue_scripts', 'mon_theme_enfant_scripts');
```

## ⚡ 3. Ajouter du Custom JS

WordPress **interdit** l'insertion directe de balises `<script>` dans l'éditeur classique ou le personnalisateur pour des raisons de sécurité.

### Méthode recommandée : `wp_enqueue_script()` dans `functions.php`

Créer un fichier `custom.js` dans le thème enfant et le déclarer ainsi :

```php
<?php
function mon_theme_enqueue_scripts() {
    wp_enqueue_script(
        'custom-script', // Identifiant unique
        get_stylesheet_directory_uri() . '/js/custom.js', // Chemin du fichier
        array( 'jquery' ), // Dépendances (laisser array() si Vanilla JS)
        '1.0.0', // Version
        true // true = charger dans le footer (recommandé pour les performances)
    );
}
add_action( 'wp_enqueue_scripts', 'mon_theme_enqueue_scripts' );
```

### ⚠️ Particularité jQuery dans WordPress

WordPress charge jQuery en mode **`noConflict`**. Le symbole `$` n'est pas reconnu globalement par défaut.
