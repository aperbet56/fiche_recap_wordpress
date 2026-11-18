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

### Exemple : Créer un rôle "Client" sécurisé

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

## 7. Capacités courantes utiles

- `read` : Accès au tableau de bord WordPress (indispensable pour tout rôle back-office).
- `edit_posts` / `publish_posts` / `delete_posts` : Gestion de ses propres articles.
- `edit_others_posts` / `delete_others_posts` : Gestion des articles des autres utilisateurs.
- `manage_categories` : Création et édition des catégories et étiquettes.
- `upload_files` : Accès à la médiathèque et ajout de fichiers.
- `edit_theme_options` : Accès aux menus, widgets et personnalisation du thème.
- `list_users` / `edit_users` / `create_users` : Gestion des comptes utilisateurs.

## 8. 🔒 Restriction de contenu

Si le module **Permissions de contenu** est actif, une nouvelle boîte apparaît sous l'éditeur de chaque article, page ou Custom Post Type (CPT).

- **Qui peut voir ce contenu ?** Cochez les rôles autorisés à lire la page. Si rien n'est coché, le contenu reste public.
- **Message d'erreur** : Personnalisez le texte affiché aux utilisateurs non connectés ou n'ayant pas le bon rôle.

## 9. 🛡️ Bonnes pratiques de sécurité

- 🔒 **Principe du moindre privilège** : N'accordez que les permissions strictement nécessaires à la mission de l'utilisateur.
- 🚫 **Ne jamais modifier le rôle Administrateur** : Gardez toujours un rôle `Administrateur` intact avec 100 % des droits pour éviter de vous bloquer hors de votre propre site.
- 🔄 **Nettoyage** : Si vous désinstallez le plugin _Members_, sachez que les rôles et permissions créés restent enregistrés dans la base de données WordPress (`wp_options`). Supprimez les rôles inutiles _avant_ de désactiver le plugin.
- 🧩 **Compatibilité plugins tiers** : De nombreux plugins (WooCommerce, Yoast SEO, Elementor) ajoutent leurs propres onglets de permissions dans l'interface de _Members_. Vérifiez ces onglets lors de la création d'un rôle.
