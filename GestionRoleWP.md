## 📝 GESTION AVANCEE DES ROLES SOUS WORDPRESS AVEC LE PLUDGGIN MEMBERS

Ce document récapitule les fonctionnalités clés et les bonnes pratiques pour configurer une gestion fine des rôles, des capacités (permissions) et des accès aux contenus avec l'extension **Members**.

## 1. 📋 Introduction

Le plugin **Members** permet d'étendre le système natif des rôles et capacités (_Capabilities_) de WordPress. Il offre une interface graphique pour :

- Créer, modifier, cloner et supprimer des rôles utilisateurs.
- Accorder ou refuser explicitement des permissions granulaires.
- Attribuer plusieurs rôles à un seul utilisateur.
- Restreindre l'accès au contenu (pages, articles, CPT) et au site entier.

## 2. 🔑 Concepts de base

Sous WordPress, les permissions reposent sur deux notions fondamentales que le plugin **Members** permet de manipuler graphiquement :

- **Rôle (Role) :** Un profil attribué à un utilisateur (ex. : _Éditeur_, _Auteur_, _Gestionnaire de boutique_).
- **Capacité (Capability) :** Une action spécifique qu'un rôle est autorisé ou non à effectuer (ex. : `edit_posts`, `publish_pages`, `manage_options`).

## 3. ⚙️ Installation et activation

1. Aller dans **Extensions > Ajouter** depuis le tableau de bord WordPress.
2. Rechercher **Members** (développé par _MemberPress_).
3. Installer et activer l'extension.
4. Un nouveau menu **Membres** apparaît dans la barre latérale gauche de l'administration.

**Options recommandées** (dans _Membres > Réglages_) :

- ✅ Activer l'éditeur de rôles et de capacités.
- ✅ Autoriser les utilisateurs à avoir **plusieurs rôles** (très utile pour combiner des droits sans créer une multitude de rôles hybrides).
- ✅ Activer les permissions de contenu (si besoin de restreindre certaines pages).

## 4. 🛠️ Fonctionnalités principales

### A. Créer, cloner ou modifier un rôle

- **Modifier un rôle existant :** Aller dans **Membres > Rôles**, survoler un rôle et cliquer sur _Modifier_.
- **Cloner un rôle (Recommandé) :** Permet de créer un rôle sur mesure à partir d'une base saine (ex. : cloner le rôle _Éditeur_ pour créer un _Éditeur Junior_ sans accès aux pages).
- **Créer un rôle vierge :** Cliquer sur **Membres > Ajouter un rôle** pour partir de zéro.

### B. Gérer les capacités (Accorder / Refuser)

Dans l'interface d'édition d'un rôle, chaque capacité possède deux cases à cocher :

- **Accorder (Grant) :** Autorise explicitement l'action.
- **Refuser (Deny) :** Interdit formellement l'action.

> 💡 **Bon à savoir :** La règle **Refuser** prend toujours le dessus sur **Accorder**, même si un utilisateur possède plusieurs rôles cumulatifs.

### C. Attribution de rôles multiples

- Aller dans **Membres > Réglages** et cocher l'option **Activer la fonctionnalité de rôles multiples**.
- Dans la fiche d'un utilisateur (**Utilisateurs > Tous les utilisateurs**), il devient possible de cocher plusieurs rôles simultanément (ex. : _Auteur_ + _Modérateur de commentaires_).

### D. Exemple : Créer un rôle "Client" sécurisé

Pour un client qui doit gérer le contenu sans casser le site :

- **Cloner** le rôle `Éditeur`.
- **Refuser** dans la catégorie _Apparence_ : `switch_themes`, `edit_themes`, `edit_theme_options`.
- **Refuser** dans la catégorie _Extensions_ : `activate_plugins`, `install_plugins`, `update_plugins`.
- **Refuser** dans la catégorie _Général_ : `manage_options`, `export`, `import`.

## 5. 👥 Architecture des Rôles du Projet

_(Adapter cette section selon les rôles créés sur votre site)_

### A. Rôles Natifs Modifiés

- **Administrateur (`administrator`)** : Accès total. _Ne jamais retirer ses capacités critiques._
- **Éditeur (`editor`)** : Gestion de tous les contenus. _(Ex: ajout de l'accès aux formulaires ou aux menus)._
- **Auteur (`author`) / Contributeur (`contributor`)** : Gestion limitée à leurs propres articles.

### B. Rôles Personnalisés (Custom Roles)

- **`gestionnaire_boutique`** _(Cloné depuis Éditeur)_ :
  - **Accès** : Produits WooCommerce, Commandes, Coupons.
  - **Restrictions** : Pas d'accès aux réglages système, extensions ni thèmes.
- **`moderateur_contenu`** _(Créé de zéro)_ :
  - **Accès** : Modération des commentaires, relecture des articles en attente.

## 6. 🚀 Attribution de rôles multiples

Une fois l'option activée dans les réglages :

1. Allez dans **Comptes > Tous les comptes**.
2. Modifiez le profil de l'utilisateur souhaité.
3. Dans la section **Rôles**, cochez simplement toutes les cases correspondant aux rôles à cumuler (ex: _Auteur_ + _Gestionnaire de boutique_).

## 7. 💡 Capacités courantes utiles

- `read` : Accès au tableau de bord WordPress (indispensable pour tout rôle back-office).
- `edit_posts` / `publish_posts` / `delete_posts` : Gestion de ses propres articles.
- `edit_others_posts` / `delete_others_posts` : Gestion des articles des autres utilisateurs.
- `edit_pages` : Créer et modifier des pages.
- `manage_categories` : Création et édition des catégories et étiquettes.
- `moderate_comments` : Gérer les commentaires.
- `upload_files` : Accès à la médiathèque et ajout de fichiers.
- `edit_theme_options` : Accès aux menus, widgets et personnalisation du thème.
- `manage_options` : Accéder aux réglages généraux du site (Admin).
- `list_users` / `edit_users` / `create_users` : Gestion des comptes utilisateurs.

- **Créer une capacité personnalisée :**

  - Dans l'éditeur de rôle, utiliser le bouton **Ajouter une capacité** (_Add New Capability_) en haut de la page pour créer des permissions sur-mesure utilisables dans votre code PHP (`current_user_can('ma_capacite')`).

## 8. 🔒 Restriction de contenu

Si le module **Permissions de contenu** est actif, une nouvelle boîte apparaît sous l'éditeur de chaque article, page ou Custom Post Type (CPT).

- **Qui peut voir ce contenu ?** Cochez les rôles autorisés à lire la page. Si rien n'est coché, le contenu reste public.
- **Message d'erreur** : Personnalisez le texte affiché aux utilisateurs non connectés ou n'ayant pas le bon rôle.

## 9. 🛡️ Bonnes pratiques de sécurité

- 🔒 **Principe du moindre privilège** : N'accordez que les permissions strictement nécessaires à la mission de l'utilisateur.
- 🚫 **Ne jamais modifier le rôle Administrateur** : Gardez toujours un rôle `Administrateur` intact avec 100 % des droits pour éviter de vous bloquer hors de votre propre site.
- 🔄 **Nettoyage** : Si vous désinstallez le plugin _Members_, sachez que les rôles et permissions créés restent enregistrés dans la base de données WordPress (`wp_options`). Supprimez les rôles inutiles _avant_ de désactiver le plugin.
- 🧩 **Compatibilité plugins tiers** : De nombreux plugins (WooCommerce, Yoast SEO, Elementor) ajoutent leurs propres onglets de permissions dans l'interface de _Members_. Vérifiez ces onglets lors de la création d'un rôle.

## 10. Créer un rôle (`add_role`)

Pour éviter que le code ne s'exécute à chaque chargement de page (ce qui nuit aux performances), l'ajout d'un rôle doit idéalement être lié à **l'activation d'un plugin** ou au **changement de thème**.

La fonction `add_role()` prend 3 paramètres : l'identifiant (slug), le nom affiché, et un tableau de capacités (_capabilities_).

### Dans un plugin (Recommandé)

Utilisez `register_activation_hook()` dans le fichier principal de votre extension :

```php
<?php
function mon_plugin_ajouter_role() {
    add_role(
        'gestionnaire_contenu', // Identifiant unique (slug)
        'Gestionnaire de Contenu', // Nom affiché dans l'admin
        [
            'read'         => true,  // Accès au tableau de bord
            'edit_posts'   => true,  // Peut modifier ses propres articles
            'delete_posts' => false, // Ne peut pas supprimer ses articles
            'upload_files' => true,  // Peut téléverser des médias
        ]
    );
}
register_activation_hook( __FILE__, 'mon_plugin_ajouter_role' );
```

### Dans un thème (`functions.php`)

Utilisez le hook `after_switch_theme` :

```php
<?php
function mon_theme_ajouter_role() {
    add_role(
        'gestionnaire_contenu',
        'Gestionnaire de Contenu',
        [
            'read'       => true,
            'edit_posts' => true,
        ]
    );
}
add_action( 'after_switch_theme', 'mon_theme_ajouter_role' );
```

## 11. Modifier les capacités d'un rôle existant

Pour ajouter ou retirer une permission à un rôle déjà créé, utilisez `get_role()` combiné à `add_cap()` ou `remove_cap()`.

```php
<?php
function modifier_capacites_role() {
    \$role = get_role( 'gestionnaire_contenu' );

    if ( \$role ) {
        // Ajouter une capacité, permission
        \$role->add_cap( 'publish_posts' );

        // Retirer une capacité, permission
        \$role->remove_cap( 'upload_files' );
    }
}
add_action( 'admin_init', 'modifier_capacites_role' );
```

> **Note :** `add_role()` ne met pas à jour un rôle s'il existe déjà en base de données. Il faut soit le supprimer avant de le recréer, soit utiliser `add_cap()` / `remove_cap()`.

## 12. Supprimer un rôle (`remove_role`)

Il est recommandé de supprimer le rôle personnalisé lors de la désactivation du plugin ou du changement de thème pour garder une base de données propre :

```php
<?php
function mon_plugin_supprimer_role() {
    remove_role( 'gestionnaire_contenu' );
}
register_deactivation_hook( __FILE__, 'mon_plugin_supprimer_role' );
```

## 13. 📚 Ressources utiles

🔗 **Documentation officielle :** [WordPress Roles and Capabilities](https://wordpress.org)
🔗 [Plugin Members – WordPress](https://developer.wordpress.org/plugins/intro/)
