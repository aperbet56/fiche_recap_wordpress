## 📝 FICHE RECAPITULATIVE CUSTOM JS & CSS SUR WORDPRESS

Guide récapitulatif des bonnes pratiques pour ajouter, gérer et optimiser du code CSS et JavaScript personnalisé sur un site WordPress.

## 1. 💡 Méthode 1 : Sans code (Via l'interface WordPress)

Idéal pour des ajustements CSS rapides et légers (ne fonctionne pas pour le JavaScript).

- **Thèmes classiques :** Aller dans `Apparence > Personnaliser > CSS additionnel`.
- **Thèmes FSE (Full Site Editing) :** Aller dans `Apparence > Éditeur > Styles (icône lune/soleil) > Trois petits points (⋮) > CSS additionnel`.

## 2. 💡 Méthode 2 : Via un Thème Enfant (Recommandé)

La méthode la plus propre et performante pour éviter d'alourdir la base de données et conserver vos modifications lors des mises à jour du thème parent.

### 📁 Structure des fichiers

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

### ⚙️ Chargement dans `functions.php`

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
        get_stylesheet_directory_uri() . '/assets/js/custom.js', // Chemin
        array('jquery'), // Dépendances (ex: 'jquery' ou array() pour du Vanilla JS)
        '1.0.0', // Version
        true // Charger dans le footer (true = recommandé pour les performances)
    );
}
add_action('wp_enqueue_scripts', 'mon_theme_enfant_scripts');
```
