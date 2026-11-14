## 📝 FICHE RECAPITULATIVE LOCALWP – ENVIRONNEMENT DE DEVELOPPEMENT WORDPRESS

**Local** est un logiciel gratuit (outil de référence) permettant de créer, gérer et tester des sites WordPress en local (directement sur votre ordinateur) sans avoir besoin d'une connexion internet ni de configurer manuellement un serveur (Apache/Nginx, PHP, MySQL).

## 1. 🚀 Fonctionnalités principales

- **Création rapide de sites :** Installation de WordPress en un clic (choix du nom du site, de l'environnement et des identifiants admin).
- **Environnements personnalisables :** Choix à la volée de la version de **PHP**, du serveur web (**Nginx** ou **Apache**) et de la base de données (**MySQL** ou **MariaDB**).
- **SSL en un clic :** Activation immédiate du protocole `HTTPS` en local pour éviter les alertes de sécurité des navigateurs.
- **Outils intégrés :**
  - **WP-CLI :** Préinstallé et accessible directement via le bouton _"Open Site Shell"_.
  - **Mailpit / MailHog :** Interception de tous les e-mails envoyés par WordPress en local pour les tester sans spammer de vraies boîtes mail.
  - **Adminer / TablePlus :** Accès direct à la base de données en un clic.
- **Live Links :** Génération d'une URL publique temporaire (via un tunnel sécurisé) pour partager votre site local avec un client ou tester sur mobile.
- **Blueprints (Modèles) :** Sauvegarde d'un site configuré (avec vos extensions et thèmes favoris) pour le réutiliser comme base lors de vos prochains projets.
- **Déploiement simplifié :** Connexion directe avec les hébergeurs **WP Engine** et **Flywheel** (import/export en un clic), ainsi que l'exportation standard au format `.zip`.

## 2. 🧰 Installer LocalWP

### 🔗 Lien de téléchargement :

👉 [https://localwp.com](https://localwp.com)

- **Téléchargez **Local** selon votre système d'exploitation (Windows / macOS / Linux).**
- **Suivez l’installation classique (suivant / suivant / installer).**
- **Lancez l’application.**

## 3. ⚙️ Démarrage Rapide

**Création d'un site :**

- Cliquer sur le bouton **`+`** (en bas à gauche) > _Create a new site_.
- **Nom du site :** Définir le nom du projet (ex: _Mon Projet_). Cela générera automatiquement le domaine local (ex: `mon-projet.local`).
- **Environnement :** Choisir _Preferred_ (recommandé) ou _Custom_ (pour fixer une version précise de PHP/MySQL).
- **WordPress :** Renseigner l'identifiant administrateur, le mot de passe et l'e-mail.

**Accès :**

- **WP Admin :** Bouton pour ouvrir directement le tableau de bord (`/wp-admin`).
- **Open Site :** Bouton pour afficher le site public.

💡 Local crée automatiquement :

- Une base de données
- Un WordPress fonctionnel
- Une URL locale (ex: `http://mon-site-test.local`)

## 4. 📁 Structure des Fichiers & Outils Intégrés

### Emplacement par défaut des projets

Par défaut, Local stocke tous vos projets dans le dossier `Local Sites` de votre répertoire utilisateur :

- **Windows :** `C:\Users\[NomUtilisateur]\Local Sites\[nom-du-site]\`
- **macOS :** `~/Local Sites/[nom-du-site]/`

### Arborescence d'un site
