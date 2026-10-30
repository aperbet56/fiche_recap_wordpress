## 📝 FICHE RECAPITULATIVE : TOUT COMPRENDRE SUR WORDPRESS

Bienvenue dans cette fiche mémo sur **WordPress**, le système de gestion de contenu (CMS) le plus populaire au monde, propulsant plus de 40 % des sites web sur Internet.

## 1. 🌐 Qu'est-ce que WordPress ?

WordPress est un CMS (Content Management System : un CMS est un outil qui va offrir une interface pour créér et gérer les contenus de votre site web internet plutôt que de le coder à la main) open-source écrit en PHP et adossé à une base de données MySQL ou MariaDB.

Il permet de créer des sites vitrines, des blogs, des portfolios ou des boutiques en ligne sans nécessiter de compétences avancées en programmation.

Ce guide regroupe les concepts essentiels, l'architecture et les commandes indispensables pour maîtriser l'outil.

## 2. ⚠️ Les distinctions capitales

- **WordPress.org vs WordPress.com** :
  - _wordPress.org_ (le CMS) : Gratuit, open-source et auto-hébergé. Vous achetez votre hébergement, possédez 100 % de vos données et installez ce que vous voulez. C'est la solution standard pour les professionnels.
  - _wordPress.com_ (la plateforme) : Service clé en main commercial. Plus simple mais bridé, payant dès que l'on veut personnaliser le site en profondeur.
- **Articles (Posts) vs Pages (Pages)** :
  - _Articles_ : Contenu chronologique, temporel, organisé par catégories et étiquettes (ex: blog, actualités).
  - _Pages_ : Contenu statique, intemporel, hiérarchique, indépendant du temps (ex: À propos, Contact).
- **La Boucle (The Loop)** : Le mécanisme PHP interne utilisé par WordPress pour afficher les articles ou le contenu d'une page.

## 3. 📂 Structure des Fichiers (Arborescence standard)

```text
wordpress/
├── wp-admin/               # Fichiers de l'administration
├── wp-includes/            # Librairies et fonctions de base de WordPress
├── wp-content/             # DOSSIER PRINCIPAL POUR LES DÉVELOPPEURS
│   ├── themes/             # Vos thèmes installés
│   ├── plugins/            # Vos extensions installées
│   └── uploads/            # Médias téléversés (images, PDF...)
├── wp-config.php           # Fichier de configuration (Base de données, clés de sécurité)
├── .htaccess               # Fichier de configuration du serveur Apache (Permaliens, redirections)
└── index.php               # Point d'entrée du site
```

## 4. 📁 Fichiers de Configuration Critiques

### `wp-config.php`

Ce fichier situé à la racine contient les accès à la base de données et les options de débogage.

```php
// ** Réglages MySQL ** //
define( 'DB_NAME', 'nom_de_la_base' );
define( 'DB_USER', 'utilisateur' );
define( 'DB_PASSWORD', 'mot_de_passe' );
define( 'DB_HOST', 'localhost' );

// ** Mode Débogage (À activer en développement, désactiver en production) ** //
define( 'WP_DEBUG', true );
define( 'WP_DEBUG_LOG', true ); // Écrit les erreurs dans wp-content/debug.log
define( 'WP_DEBUG_DISPLAY', false ); // Masque les erreurs à l'écran
```

### `.htaccess` (Serveurs Apache)

Gère les redirections, la sécurité et la structure des permaliens (URLs propres).

## 5. 🏗️ L'Architecture de WordPress

WordPress repose sur les technologies suivantes :

- **PHP :** Le langage de programmation côté serveur qui gère la logique du site.
- **MySQL / MariaDB :** La base de données qui stocke le contenu (articles, pages, utilisateurs, réglages).
- **HTML / CSS / JavaScript :** Les langages du côté client pour l'affichage et l'interactivité.
- **Serveur Web** : Fonctionne généralement sous Apache ou Nginx.

### Les 3 Piliers du fonctionnement :

Le fonctionnement de WordPress repose sur la séparation stricte du fond, de la forme et des fonctionnalités.

| Conposant                                     | Rôle Principal                                                                                                  | Exemples connus                               |
| :-------------------------------------------- | :-------------------------------------------------------------------------------------------------------------- | :-------------------------------------------- |
| **Le Contenu / Le Cœur & La Base de données** | Stocke le texte, les options et l'arborescence dans une base de données MySQL.                                  | Articles, pages, commentaires.                |
| **Le Thème (Design)**                         | Gère l'apparence visuelle, la structure des pages et l'ergonomie (FSE). Un seul thème peut être actif à la fois | Astra, Hello Elementor, Divi, GeneratePress.  |
| **Les Extensions (Plugins)**                  | Ajoutent des fonctionnalités techniques spécifiques au site. Elles restent actives même si l'on change de thème | WooCommerce (Boutique), Yoast/RankMath (SEO). |

## 6. 🗂️ Gestion du Contenu : Articles vs Pages

WordPress segmente nativement les publications en deux types :

- **Les Articles (Flux dynamique)** :

  - _Classés par ordre chronologique inverse (du plus récent au plus ancien)._
  - _Organisés par Catégories (obligatoires) et Étiquettes / Tags (optionnels)._
  - _Idéaux pour les blogs, l'actualité, les portfolios ou les actualités._
  - _Intègrent un espace de commentaires pour l'interaction._

- **Les Pages (Structure statique)** :
  - _Organisées de manière hiérarchique (ex: Page enfant Nos Valeurs sous la page parente À Propos) Classées par structure hiérarchique (Parents / Enfants)_
  - _Pas de notion de date de publication mise en avant, pas de catégories._
  - _Destinées aux contenus permanents (ex: Accueil, Contact, Mentions Légales)._

## 7. ⚙️ Le Tableau de Bord (Back-Office) : Les Menus Clés

- **Tableau de bord** : Vue d'ensemble de l'activité du site et alertes de mises à jour. Votre espace de travail privé pour configurer le site et rédiger.
- **Médias** : Bibliothèque centrale stockant vos images, vidéos, PDF et documents.
- **Apparence** : Gestion des thèmes, des menus de navigation et de l'Éditeur de site.
- **Extensions** : Interface pour rechercher, installer, activer ou supprimer des fonctionnalités.
- **Réglages** : Configuration technique critique.

## 8. 🛠️ L'Édition Moderne : Gutenberg & FSE

- **L'Éditeur de Blocs (Gutenberg)** : Le système d'édition natif de WordPress. Chaque élément de contenu (paragraphe, titre, image, bouton) est un "bloc" autonome que l'on peut déplacer, styliser et réutiliser. Il génère du code HTML propre sans shortcodes lourds.

- **Le FSE (Full Site Editing / Édition Totale du Site)** : Permet de modifier visuellement l'intégralité du site (y compris l'en-tête, le pied de page et les modèles de page) directement avec des blocs, sans toucher au code PHP ou CSS.

- **Constructeurs tiers (Page Builders)** : Pour des besoins ultra-spécifiques ou complexes, des extensions comme Elementor, Divi Builder ou Bricks remplacent ou complètent l'éditeur natif.

## 9. 🔧 Configuration Initiale & SEO

Lors du déploiement d'un site, 4 actions de configuration sont obligatoires :

- **Visibilité pour les moteurs de recherche** : Durant la phase de développement, l'option "Demander aux moteurs de recherche de ne pas indexer ce site" (`Réglages > Lecture`) doit être cochée. **Elle doit absolument être décochée au moment de la mise en production**.

- **Structure des URL (Permaliens)** : Dans `Réglages > Permaliens`, basculer absolument sur "Titre de l'article" (`/%postname%/`) pour l'optimisation SEO (évite les URL du type `?p=123`). Cela génère des URL propres bénéfiques pour le SEO.

- **Définition de la page d'accueil statique** : Par défaut, WordPress affiche le flux des derniers articles. Pour un site vitrine professionnel, il faut aller dans `Réglages > Lecture` et sélectionner une Page statique dédiée pour l'accueil.

- **Changer le slogan** : Dans `Réglages > Général`, modifier ou supprimer le slogan par défaut "Un site utilisant WordPress" afin de soigner le référencement de la page d'accueil.

## 10. 💻 Commandes de Base avec WP-CLI

**WP-CLI** est l'outil indispensable ( Interface en ligne de commande) pour administrer WordPress rapidement sans passer par l'interface graphique.

- **Mises à jour :**

  - `wp core update` : Mettre à jour WordPress.
  - `wp plugin update --all` : Mettre à jour toutes les extensions.

- **Télécharger les fichiers WordPress :**

  - `wp core download` : Télécharge les fichiers WordPress.

- **Installer et activer une extension :**

  - `wp plugin list` : Liste les extensions installées.
  - `wp plugin install <nom>` : Installe une extension.
  - `wp plugin activate <nom>` : Active une extension.
  - `wp plugin install <nom> --activate` : Installe et active une extension.

- **Base de données :**

  - `wp db export` : Exporter la base de données en `.sql`.
  - `wp db import fichier.sql` : Importer une base de données.

- **Administration :**

  - `wp user create login email@test.com --role=administrator` : Créer un administrateur.
  - `wp search-replace 'http://ancien-site.com' 'https://nouveau-site.com'` : Remplacer les URLs proprement dans la base. Commandes de Base avec WP-CLI

## 11. 🔒 Sécurité Maintenance & Performances

### 🛡️ Sécurité :

- **Mises à jour régulières** : Effectuez régulièrement les mises à jour du Cœur WordPress, des thèmes et des extensions pour combler les failles de sécurité.

- **Sauvegardes (Backups)** : Automatisez des sauvegardes régulières (fichiers + base de données) sur un cloud externe via des extensions dédiées (ex: UpdraftPlus).

- **Protection des accès** : Utilisez des identifiants complexes (Ne jamais utiliser l'identifiant par défaut admin) et modifiez si possible l'URL de connexion par défaut (`/wp-admin` ou /`wp-login.php` par une URL secrète via une extension de sécurité) pour éviter les attaques par force brute.

- **Limiter les tentatives de connexion** : pour bloquer les attaques par force brute.

- **Sécuriser le fichier `wp-config.php`** : en déplaçant ses droits d'accès ou en restreignant la lecture.

- **Gestion des accès (Principe du moindre privilège)** : Ne jamais créer ou laisser d'utilisateur avec l'identifiant par défaut admin. Assigner précisément les rôles adéquats selon le besoin : Administrateur (droits totaux), Éditeur (gère tout le contenu), Auteur (publie ses propres articles), Contributeur (écrit mais ne peut pas publier seul), Abonné (profil simple).

- **Préfixe de Base de données** : Modifier le préfixe par défaut `wp_` lors de l'installation (ex: `site43_`).

- **Extensions de confiance** : Télécharger uniquement depuis le répertoire officiel ou des extensions réputées.

- **Masquer la version** : Retirer le numéro de version de WordPress du code source.

- **Thèmes Enfants (Child Themes) :** Toujours créer un thème enfant pour personnaliser le code d'un thème existant sans perdre les modifications lors des mises à jour.

### 🧰 Maintenance :

- **Toujours réaliser une sauvegarde** ( les fichiers + la base de données via un outil comme UpdraftPlus) avant de lancer les mises à jour majeures du cœur ou des plugins.

### 🚀 Performances :

- **Utiliser un système de mise en cache** : (ex: WP Rocket, LiteSpeed Cache).
- **Optimiser les images** (compression et formats modernes comme le WebP).
- **Nettoyage de la Base de données** : Supprimer régulièrement les révisions d'articles et les commentaires indésirables.
- **Choisir un hébergement de qualité adapté au trafic.** : Privilégier un hébergement de qualité avec la dernière version stable de PHP.

## 12. ⚡ Extensions Incontournables (Essentiels)

### 📈 SEO & Performances / Cache :

- **Yoast SEO** ou **Rank Math** : Optimisation du référencement naturel.
- **WP Rocket** ou **LiteSpeed Cache** : Amélioration de la vitesse de chargement.

### 🛡️ Sécurité & Sauvegarde :

- **Wordfence Security** : Pare-feu et scanneur de malware.
- **UpdraftPlus** : Sauvegardes automatisées vers le cloud (Drive, Dropbox).

### 🎨 Construction de page (Page Builders) :

- **Elementor** ou **Divi** : Création visuelle en glisser-déposer (en complément de l'éditeur natif **Gutenberg**).

### 🛒 E-commerce :

- **WooCommerce** : l'extension standard pour transformer le site en boutique.

### ✍️ Formulaires

- **Contact Form 7** ou **WPForms**

## 13. 🎯 Avantages et Inconvénients

### 👍 Les Points Forts

- **Gratuit et Open-Source** : Communauté gigantesque et évolution constante.
- **Flexibilité absolue** : Permet de créer absolument tout type de site.
- **Excellent pour le SEO** : Structure nativement appréciée par les moteurs de recherche.
- **Propriété des données** : Avec la version .org, le site vous appartient à 100 %.

### 👎 Les Points Faibles

- **Maintenance requise** : Les mises à jour régulières sont indispensables pour éviter les bugs.
- **Vulnérabilité** : Étant le plus utilisé, c'est la cible principale des pirates (nécessite une bonne sécurisation).
- **Performances** : Un abus de plugins ou un thème mal codé peut gravement ralentir le site.
