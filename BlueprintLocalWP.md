# 📝 FICHE RECAPITULATIVE - LES BLUEPRINTS DANS LOCAL (WORDPRESS)

Un **Blueprint** (modèle) est une sauvegarde complète d'un site WordPress configuré (fichiers, base de données, thèmes, extensions et réglages) permettant de cloner instantanément cette base de travail pour de futurs projets.

Ce document récapitule le fonctionnement, la création et l'utilisation des **Blueprints** dans [LocalWP](https://localwp.com) afin d'accélérer le déploiement de nouveaux projets WordPress.

## 1. 🎯 Pourquoi utiliser un Blueprint ?

- **Gain de temps considérable :** Évite de réinstaller et configurer les mêmes extensions à chaque nouveau projet.
- **Standardisation :** Garantit une base saine, sécurisée et uniforme (idéal en agence ou en freelance).
- **Productivité :** Permet de partir d'un WordPress débarrassé des éléments inutiles par défaut (articles d'exemple, extensions préinstallées).

## 2. 🛠️ Créer un Blueprint (Étape par étape)

- **Créer un site vierge** dans Local (ex. nommé `Modele-Base-WP`).

- **Nettoyer WordPress :**

  - Supprimer les articles, pages et commentaires d'exemple (_Bonjour tout le monde_, _Page d'exemple_).
  - Supprimer les thèmes inutiles (ne garder que le thème actif et un thème par défaut de secours).
  - Supprimer les extensions inutiles (_Hello Dolly_, _Akismet_).

- **Configurer les réglages de base :**

  - _Réglages > Général_ : Fuseau horaire (Paris), format de date/heure, langue.
  - _Réglages > Permaliens_ : Sélectionner **Titre de la publication**.
  - _Réglages > Lecture_ : Cocher _Demander aux moteurs de recherche de ne pas indexer ce site_ (bonne pratique en développement).

- **Installer vos essentiels :**

  - Thème favori ou thème enfant (_Hello Elementor_, _Astra_, _GeneratePress_, thème sur mesure...).
  - Extensions indispensables (SEO, sauvegarde, sécurité, constructeur de page, etc.).

- **Enregistrer le Blueprint :**

  - Dans Local, faire un **clic droit** sur le nom du site dans la barre latérale.
  - Cliquer sur **`Save as Blueprint`**.
  - Donner un nom explicite (ex. `WP-Vitrine-2026` ou `WP-WooCommerce`) et valider.

## 3. 🚀 Utiliser un Blueprint pour un nouveau projet

- Cliquer sur le bouton **`+`** (en bas à gauche) pour créer un site.
- Cliquer sur **`Create from a Blueprint`** (Créer à partir d'un Blueprint) en bas de la fenêtre de création au lieu de _Create a new site_.
- Sélectionner le Blueprint souhaité dans la liste et cliquez sur **"Continue"**.
- Nommer le nouveau site et lancer l'installation.
- LocalWP clone l'intégralité du modèle et met automatiquement à jour les URLs dans la base de données.

## 4. ⚙️ Gérer et mettre à jour ses Blueprints

- **Accéder aux Blueprints :** Menu principal de Local > onglet **Blueprints** (icône de plan/schéma dans la barre latérale gauche).

- **Mettre à jour un Blueprint :** Il n'existe pas de bouton « Modifier » direct. La méthode recommandée est de :
  - Créer un site temporaire à partir de l'ancien Blueprint.
  - Mettre à jour WordPress, le thème et les extensions.
  - Enregistrer ce site mis à jour comme nouveau Blueprint (`Save as Blueprint`).
  - Supprimer l'ancien Blueprint et le site temporaire.

* **Emplacement sur le disque :** Les fichiers `.zip` des Blueprints sont stockés dans le dossier de configuration de Local (utile pour les partager avec une équipe).

Pour voir, renommer ou supprimer vos modèles existants :

- Ouvrez les paramètres de LocalWP (icône **engrenage** ou menu _Local > Preferences_).
- Allez dans l'onglet **"Blueprints"**.
- Depuis cet écran, vous pouvez :
  - **Renommer** un Blueprint existant.
  - **Supprimer** un Blueprint obsolète.
  - **Localiser les fichiers** (`.zip`) sur votre ordinateur pour sauvegarder ou les partager avec une équipe.

## 5. ⚠️ Points de vigilance

- **Licences Pro :** Ne pas activer de clés de licence payantes dans le Blueprint si le nombre d'activations est limité (les activer uniquement sur le projet final).
- **Identifiants :** Le nouveau site créé héritera exactement des mêmes identifiants administrateur (`user` / `password`) que ceux du site ayant servi à créer le Blueprint.

## 6. 💡 Bonnes pratiques et astuces

- **Mises à jour régulières :** Pensez à recréer ou mettre à jour vos Blueprints tous les 2 à 3 mois pour éviter d'avoir des dizaines de mises à jour d'extensions à faire dès la création d'un site.
- **Catégorisez vos modèles :** Créez plusieurs Blueprints selon vos types de projets (ex: _Site Vitrine_, _E-commerce_, _Blog_, _Landing Page_).
- **Pas de clés de licence sensibles :** Évitez d'enregistrer vos clés API ou licences Pro personnelles dans un Blueprint si vous prévoyez de partager le fichier `.zip` avec d'autres développeurs.
- **Nettoyage :** Videz le cache et supprimez les données temporaires (transients) avant de sauvegarder le Blueprint pour qu'il soit le plus léger possible.
- **Gardez le blueprint léger :** N'installez que les outils indispensables à 90 % de vos projets pour éviter d'alourdir inutilement vos futurs sites.
- **Utilisez un mot de passe générique local :** Utilisez un identifiant simple en local (ex. `admin` / `admin`) que vous modifierez impérativement lors de la mise en production.
