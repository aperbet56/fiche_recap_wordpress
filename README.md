## FICHE RECAPITULATIVE WORDPRESS

WordPress est un CMS (Content Management System) open-source écrit en PHP et adossé à une base de données MySQL ou MariaDB.

**WordPress est le système de gestion de contenu (CMS) le plus populaire au monde**, propulsant plus de 40 % des sites web sur Internet.

Ce guide regroupe les concepts essentiels, l'architecture et les commandes indispensables pour maîtriser l'outil.

## 1. ⚠️ Les distinctions capitales

- **WordPress.org vs WordPress.com** :
  - _wordPress.org_ (le CMS) : Gratuit, open-source et auto-hébergé. Vous achetez votre hébergement, possédez 100 % de vos données et installez ce que vous voulez. C'est la solution standard pour les professionnels.
  - _wordPress.com_ (la plateforme) : Service clé en main commercial. Plus simple mais bridé, payant dès que l'on veut personnaliser le site en profondeur.
- **Articles (Posts) vs Pages** :
  - _Articles_ : Contenu chronologique, temporel, organisé par catégories et étiquettes (ex: blog, actualités).
  - _Pages_ : Contenu statique, intemporel, hiérarchique, indépendant du temps (ex: À propos, Contact).
- **La Boucle (The Loop)** : Le mécanisme PHP interne utilisé par WordPress pour afficher les articles ou le contenu d'une page.

## 2. 🏗️ L'Architecture : Les 3 Piliers de WordPress

Le fonctionnement de WordPress repose sur la séparation stricte du fond, de la forme et des fonctionnalités.

| Conposant                                     | Rôle Principal                                                                                                  | Exemples connus                               |
| :-------------------------------------------- | :-------------------------------------------------------------------------------------------------------------- | :-------------------------------------------- |
| **Le Contenu / Le Cœur & La Base de données** | Stocke le texte, les options et l'arborescence dans une base de données MySQL.                                  | Articles, pages, commentaires.                |
| **Le Thème (Design)**                         | Gère l'apparence visuelle, la structure des pages et l'ergonomie (FSE). Un seul thème peut être actif à la fois | Astra, Hello Elementor, Divi, GeneratePress.  |
| **Les Extensions (Plugins)**                  | Ajoutent des fonctionnalités techniques spécifiques au site. Elles restent actives même si l'on change de thème | WooCommerce (Boutique), Yoast/RankMath (SEO). |

## 3. 📝 Gestion du Contenu : Articles vs Pages

WordPress segmente nativement les publications en deux types :

- **Les Articles (Flux dynamique)** :

  - _Classés par ordre chronologique inverse._
  - _Organisés par Catégories (obligatoires) et Étiquettes / Tags (optionnels)._
  - _Idéaux pour les blogs, l'actualité, les portfolios ou les actualités._
  - _Intègrent un espace de commentaires pour l'interaction._

- **Les Pages (Structure statique)** :
  - _Organisées de manière hiérarchique (ex: Page enfant Nos Valeurs sous la page parente À Propos)_
  - _Pas de notion de date de publication mise en avant, pas de catégories._
  - _Destinées aux contenus permanents (ex: Accueil, Contact, Mentions Légales)._

## 4. ⚙️ Le Tableau de Bord (Back-Office) : Les Menus Clés

- **Tableau de bord** : Vue d'ensemble de l'activité du site et alertes de mises à jour.
- **Médias** : Bibliothèque centrale stockant vos images, vidéos, PDF et documents.
- **Apparence** : Gestion des thèmes, des menus de navigation et de l'Éditeur de site.
- **Extensions** : Interface pour rechercher, installer, activer ou supprimer des fonctionnalités.
- **Réglages** : Configuration technique critique.

## 5. 🛠️ L'Édition Moderne : Gutenberg & FSE

- **L'Éditeur de Blocs (Gutenberg)** : Le système d'édition natif de WordPress. Chaque élément de contenu (paragraphe, titre, image, bouton) est un "bloc" autonome que l'on peut déplacer, styliser et réutiliser. Il génère du code HTML propre sans shortcodes lourds.

- **Le FSE (Full Site Editing / Édition Totale du Site)** : Permet de modifier visuellement l'intégralité du site (y compris l'en-tête, le pied de page et les modèles de page) directement avec des blocs, sans toucher au code PHP ou CSS.

- **Constructeurs tiers (Page Builders)** : Pour des besoins ultra-spécifiques ou complexes, des extensions comme Elementor, Divi Builder ou Bricks remplacent ou complètent l'éditeur natif.

## 6. 🔧 Configuration Initiale & SEO

Lors du déploiement d'un site, 4 actions de configuration sont obligatoires :

- **Visibilité pour les moteurs de recherche** : Dans Réglages > Lecture, vérifier que la case "Demander aux moteurs de recherche de ne pas indexer ce site" est décochée en production.

- **Structure des URL (Permaliens)** : Dans Réglages > Permaliens, basculer absolument sur "Titre de l'article" (/%postname%/) pour l'optimisation SEO (évite les URL du type ?p=123).

- **Page d'accueil statique** : Dans Réglages > Lecture, définir une Page précise comme page d'accueil au lieu du flux des derniers articles.

- **Changer le slogan** : Dans Réglages > Général, modifier ou supprimer le slogan par défaut "Un site utilisant WordPress".

## 7. 🔒 Sécurité & Maintenance

- **Mises à jour** : Effectuez régulièrement les mises à jour du Cœur WordPress, des thèmes et des extensions pour combler les failles de sécurité.

- **Sauvegardes (Backups)** : Automatisez des sauvegardes régulières (fichiers + base de données) sur un cloud externe via des extensions dédiées (ex: UpdraftPlus).

- **Protection des accès** : Utilisez des identifiants complexes (évitez absolument l'utilisateur "admin") et modifiez si possible l'URL de connexion par défaut (/wp-admin).
