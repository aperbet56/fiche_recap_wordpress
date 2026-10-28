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
  - _Pages_ : Contenu statique, hiérarchique, indépendant du temps (ex: À propos, Contact).
- **La Boucle (The Loop)** : Le mécanisme PHP interne utilisé par WordPress pour afficher les articles ou le contenu d'une page.

## 2. 🏗️ L'Architecture : Les 3 Piliers de WordPress

Le fonctionnement de WordPress repose sur la séparation stricte du fond, de la forme et des fonctionnalités.

| Conposant                    | Rôle Principal                                                                 | Exemples connus                               |
| :--------------------------- | :----------------------------------------------------------------------------- | :-------------------------------------------- |
| **Le Contenu / Le Cœur**     | Stocke le texte, les options et l'arborescence dans une base de données MySQL. | Articles, pages, commentaires.                |
| **Le Thème (Design)**        | Gère l'apparence visuelle, la structure des pages et l'ergonomie (FSE).        | Astra, Hello Elementor, Divi, GeneratePress.  |
| **Les Extensions (Plugins)** | Ajoutent des fonctionnalités techniques spécifiques au site.                   | WooCommerce (Boutique), Yoast/RankMath (SEO). |

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
