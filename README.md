## 📝 FICHE RECAPITULATIVE WORDPRESS

## 1. 🌐 Qu'est-ce que WordPress ?

WordPress est un CMS (Content Management System) open-source écrit en PHP et adossé à une base de données MySQL ou MariaDB.

**WordPress est le système de gestion de contenu (CMS) le plus populaire au monde**, propulsant plus de 40 % des sites web sur Internet. Il permet de créer des sites vitrines, des blogs, des portfolios ou des boutiques en ligne sans nécessiter de compétences avancées en programmation.

Ce guide regroupe les concepts essentiels, l'architecture et les commandes indispensables pour maîtriser l'outil.

## 2. ⚠️ Les distinctions capitales

- **WordPress.org vs WordPress.com** :
  - _wordPress.org_ (le CMS) : Gratuit, open-source et auto-hébergé. Vous achetez votre hébergement, possédez 100 % de vos données et installez ce que vous voulez. C'est la solution standard pour les professionnels.
  - _wordPress.com_ (la plateforme) : Service clé en main commercial. Plus simple mais bridé, payant dès que l'on veut personnaliser le site en profondeur.
- **Articles (Posts) vs Pages (Pages)** :
  - _Articles_ : Contenu chronologique, temporel, organisé par catégories et étiquettes (ex: blog, actualités).
  - _Pages_ : Contenu statique, intemporel, hiérarchique, indépendant du temps (ex: À propos, Contact).
- **La Boucle (The Loop)** : Le mécanisme PHP interne utilisé par WordPress pour afficher les articles ou le contenu d'une page.

## 3. 🏗️ L'Architecture : Les 3 Piliers de WordPress

Le fonctionnement de WordPress repose sur la séparation stricte du fond, de la forme et des fonctionnalités.

| Conposant                                     | Rôle Principal                                                                                                  | Exemples connus                               |
| :-------------------------------------------- | :-------------------------------------------------------------------------------------------------------------- | :-------------------------------------------- |
| **Le Contenu / Le Cœur & La Base de données** | Stocke le texte, les options et l'arborescence dans une base de données MySQL.                                  | Articles, pages, commentaires.                |
| **Le Thème (Design)**                         | Gère l'apparence visuelle, la structure des pages et l'ergonomie (FSE). Un seul thème peut être actif à la fois | Astra, Hello Elementor, Divi, GeneratePress.  |
| **Les Extensions (Plugins)**                  | Ajoutent des fonctionnalités techniques spécifiques au site. Elles restent actives même si l'on change de thème | WooCommerce (Boutique), Yoast/RankMath (SEO). |

## 4. 🗂️ Gestion du Contenu : Articles vs Pages

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

## 5. ⚙️ Le Tableau de Bord (Back-Office) : Les Menus Clés

- **Tableau de bord** : Vue d'ensemble de l'activité du site et alertes de mises à jour. Votre espace de travail privé pour configurer le site et rédiger.
- **Médias** : Bibliothèque centrale stockant vos images, vidéos, PDF et documents.
- **Apparence** : Gestion des thèmes, des menus de navigation et de l'Éditeur de site.
- **Extensions** : Interface pour rechercher, installer, activer ou supprimer des fonctionnalités.
- **Réglages** : Configuration technique critique.

## 6. 🛠️ L'Édition Moderne : Gutenberg & FSE

- **L'Éditeur de Blocs (Gutenberg)** : Le système d'édition natif de WordPress. Chaque élément de contenu (paragraphe, titre, image, bouton) est un "bloc" autonome que l'on peut déplacer, styliser et réutiliser. Il génère du code HTML propre sans shortcodes lourds.

- **Le FSE (Full Site Editing / Édition Totale du Site)** : Permet de modifier visuellement l'intégralité du site (y compris l'en-tête, le pied de page et les modèles de page) directement avec des blocs, sans toucher au code PHP ou CSS.

- **Constructeurs tiers (Page Builders)** : Pour des besoins ultra-spécifiques ou complexes, des extensions comme Elementor, Divi Builder ou Bricks remplacent ou complètent l'éditeur natif.

## 7. 🔧 Configuration Initiale & SEO

Lors du déploiement d'un site, 4 actions de configuration sont obligatoires :

- **Visibilité pour les moteurs de recherche** : Durant la phase de développement, l'option "Demander aux moteurs de recherche de ne pas indexer ce site" (`Réglages > Lecture`) doit être cochée. **Elle doit absolument être décochée au moment de la mise en production**.

- **Structure des URL (Permaliens)** : Dans `Réglages > Permaliens`, basculer absolument sur "Titre de l'article" (`/%postname%/`) pour l'optimisation SEO (évite les URL du type `?p=123`). Cela génère des URL propres bénéfiques pour le SEO.

- **Définition de la page d'accueil statique** : Par défaut, WordPress affiche le flux des derniers articles. Pour un site vitrine professionnel, il faut aller dans `Réglages > Lecture` et sélectionner une Page statique dédiée pour l'accueil.

- **Changer le slogan** : Dans `Réglages > Général`, modifier ou supprimer le slogan par défaut "Un site utilisant WordPress" afin de soigner le référencement de la page d'accueil.

## 8. 🔒 Sécurité Maintenance et Performances

### Sécurité :

- **Mises à jour** : Effectuez régulièrement les mises à jour du Cœur WordPress, des thèmes et des extensions pour combler les failles de sécurité.

- **Sauvegardes (Backups)** : Automatisez des sauvegardes régulières (fichiers + base de données) sur un cloud externe via des extensions dédiées (ex: UpdraftPlus).

- **Protection des accès** : Utilisez des identifiants complexes (Ne jamais utiliser l'identifiant par défaut admin) et modifiez si possible l'URL de connexion par défaut (`/wp-admin` ou /`wp-login.php` par une URL secrète via une extension de sécurité) pour éviter les attaques par force brute.

- **Limiter les tentatives de connexion** : pour bloquer les attaques par force brute.

- **Sécuriser le fichier `wp-config.php`** : en déplaçant ses droits d'accès ou en restreignant la lecture.

- **Gestion des accès (Principe du moindre privilège)** : Ne jamais créer ou laisser d'utilisateur avec l'identifiant par défaut admin. Assigner précisément les rôles adéquats selon le besoin : Administrateur (droits totaux), Éditeur (gère tout le contenu), Auteur (publie ses propres articles), Contributeur (écrit mais ne peut pas publier seul), Abonné (profil simple).

### Maintenance :

- **Maintenance** : Toujours réaliser une sauvegarde ( les fichiers + la base de données via un outil comme UpdraftPlus) avant de lancer les mises à jour majeures du cœur ou des plugins.

### Performances :

- **Utiliser un système de mise en cache** : (ex: WP Rocket, LiteSpeed Cache).
- **Optimiser les images** (compression et formats modernes comme le WebP).
- **Utiliser un réseau de diffusion de contenu** : (ex : CDN).
- **Choisir un hébergement de qualité adapté au trafic.**
