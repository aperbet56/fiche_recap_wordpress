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

### Via une Extension dédiée

Pratique si vous n'avez pas de thème enfant ou si vous changez souvent de thème.

- **WPCode (Insert Headers and Footers) :** Idéal pour gérer des extraits (snippets) JS, CSS et PHP avec des conditions d'affichage avancées.
- **Simple Custom CSS and JS :** Léger, permet de créer des fichiers CSS/JS externes directement depuis l'administration.

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

```javascript
// Avec jQuery
jQuery(document).ready(function(\$) {
    // Votre code avec le symbole \(fonctionne ici\)('.mon-bouton').on('click', function() {
        console.log('Clic détecté !');
    });
});
```

**✅ Alternative moderne (Vanilla JS - Sans jQuery) :**

```javascript
document.addEventListener("DOMContentLoaded", function () {
  const bouton = document.querySelector(".mon-bouton");
  if (bouton) {
    bouton.addEventListener("click", () => {
      console.log("Clic détecté !");
    });
  }
});
```

## 🚀 4. Bonnes pratiques - Astuces - Sécurité

- **Chargement conditionnel :** Évitez de charger un script lourd sur tout le site s'il ne sert que sur une page.

  ```php
  if ( is_page( 'contact' ) ) {
      wp_enqueue_script( 'script-contact', ... );
  }
  ```

* **Cache navigateur (Cache Busting) :** Utilisez `filemtime()` à la place du numéro de version (`'1.0.0'`) pendant le développement pour forcer le rechargement du fichier à chaque modification :

  ```php
  filemtime( get_stylesheet_directory() . '/css/custom.css' )
  ```

* **Ciblage CSS spécifique :** WordPress ajoute automatiquement des classes utiles sur la balise `<body>` (ex: `.home`, `.page-id-42`, `.logged-in`, `.single-post`). Utilisez-les pour isoler vos styles.

* **Ne jamais modifier le thème parent :** Toute modification directe sera écrasée à la prochaine mise à jour.
* **Utiliser les DevTools :** Testez vos règles CSS directement dans l'inspecteur de votre navigateur (`F12`) avant de les copier.
* **Ciblage précis :** Utilisez les classes générées automatiquement dans la balise `<body>` par WordPress (ex: `.page-id-42`, `.logged-in`, `.single-post`) pour cibler un élément sans affecter le reste du site.
* **Éviter `!important` :** Privilégiez une meilleure spécificité CSS (ex: `body .ma-classe` au lieu de `.ma-classe { color: red !important; }`).
* **Gestion du cache :** Pensez à incrémenter le numéro de version (`'1.0.1'`) dans `wp_enqueue_style` / `wp_enqueue_script` et à vider votre plugin de cache après chaque modification. Après toute modification CSS/JS, pensez à vider le cache de votre extension (WP Rocket, LiteSpeed, etc.) et celui de votre navigateur (`Ctrl + F5` ou `Cmd + Shift + R`).
* **Chargement dans le footer :** Privilégiez le chargement des scripts en pied de page (`true` en 5e paramètre de `wp_enqueue_script`) pour ne pas bloquer l'affichage de la page (Render-blocking).

## 5. 🛠️ Débogage rapide

| Problème rencontré                                      | Solution / Vérification                                                                                                       |
| :------------------------------------------------------ | :---------------------------------------------------------------------------------------------------------------------------- |
| **Le CSS ne s'applique pas**                            | Vider le cache (navigateur + plugin de cache WordPress + CDN). Vérifier la priorité des sélecteurs dans l'inspecteur (`F12`). |
| **Erreur JS `Uncaught TypeError: $ is not a function`** | Encapsuler le code jQuery dans `jQuery(function($) { ... });`.                                                                |
| **Le script ne trouve pas l'élément HTML**              | Vérifier que le script est bien chargé dans le footer (`true` en 5e paramètre) ou entouré de `DOMContentLoaded`.              |
| **Écran blanc après modification de `functions.php`**   | Erreur de syntaxe PHP. Se connecter en FTP/SFTP et corriger ou annuler la dernière modification.                              |
