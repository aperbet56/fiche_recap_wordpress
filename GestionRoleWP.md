## 📝 GESTION AVANCEE DES ROLES SOUS WORDPRESS AVEC LE PLUDGGIN MEMBERS

Ce document récapitule les fonctionnalités clés et les bonnes pratiques pour configurer une gestion fine des rôles, des capacités (permissions) et des accès aux contenus avec l'extension **Members**.

## 1. 📋 Concepts de base

Sous WordPress, les permissions reposent sur deux notions fondamentales que le plugin **Members** permet de manipuler graphiquement :

- **Rôle (Role) :** Un profil attribué à un utilisateur (ex. : _Éditeur_, _Auteur_, _Gestionnaire de boutique_).
- **Capacité (Capability) :** Une action spécifique qu'un rôle est autorisé ou non à effectuer (ex. : `edit_posts`, `publish_pages`, `manage_options`).

## 2. ⚙️ Installation et activation

1. Aller dans **Extensions > Ajouter** depuis le tableau de bord WordPress.
2. Rechercher **Members** (développé par _MemberPress_).
3. Installer et activer l'extension.
4. Un nouveau menu **Membres** apparaît dans la barre latérale gauche de l'administration.

## 3. 🛠️ Fonctionnalités principales

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
