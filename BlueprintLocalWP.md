# 📝 FICHE RECAPITULATIVE - LES BLUEPRINTS DANS LOCAL (WORDPRESS)

Un **Blueprint** (modèle) est une sauvegarde complète d'un site WordPress configuré (fichiers, base de données, thèmes, extensions et réglages) permettant de cloner instantanément cette base de travail pour de futurs projets.

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
- Sélectionner le Blueprint souhaité dans la liste.
- Nommer le nouveau site et lancer l'installation.
