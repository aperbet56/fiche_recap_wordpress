## 📝 FICHE RECAPITULATIVE LOCALWP – ENVIRONNEMENT DE DEVELOPPEMENT WORDPRESS

**Local** est un logiciel gratuit (outil de référence) permettant de créer, gérer et tester des sites WordPress en local (directement sur votre ordinateur) sans avoir besoin d'une connexion internet ni de configurer manuellement un serveur (Apache/Nginx, PHP, MySQL).

Ce fichier récapitule la configuration, l'utilisation et les bonnes pratiques liées à **Local** (anciennement _Local by Flywheel_) pour le développement d'un projet WordPress.

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
- **Démarrer / Arrêter :** Utilisez le bouton **Start site** / **Stop site** en haut à droite pour économiser les ressources de votre ordinateur.

**Accès :**

- **WP Admin :** Bouton pour ouvrir directement le tableau de bord (`/wp-admin`).
- **Open Site :** Bouton pour afficher le site public.

**Base de données:**

- **Gérer la base de données :** Onglet **Database** -> **Open AdminerEvo** (ou TablePlus/Sequel Ace) pour explorer vos tables SQL.

**Utiliser WP-CLI :**

- **Cliquez sur **Site shell** sous le nom du site pour ouvrir un terminal préconfiguré avec WP-CLI.**

Local crée automatiquement :

- Une base de données
- Un WordPress fonctionnel
- Une URL locale (ex: `http://mon-site-test.local`)

## 4. 📁 Structure des Fichiers & Outils Intégrés

### Emplacement par défaut des projets :

Par défaut, Local stocke tous vos projets dans le dossier `Local Sites` de votre répertoire utilisateur :

- **Windows :** `C:\Users\[NomUtilisateur]\Local Sites\[nom-du-site]\`
- **macOS :** `~/Local Sites/[nom-du-site]/`

### Arborescence d'un site :

```text
~/Local Sites/
└── mon-projet/
    ├── app/
    │   ├── public/          <-- Racine de WordPress (wp-content, wp-config.php...)
    │   └── sql/             <-- Sauvegardes SQL générées à l'arrêt du site
    ├── conf/                <-- Fichiers de configuration (PHP, Nginx/Apache, MySQL)
    └── logs/                <-- Journaux d'erreurs (PHP, serveur web, base de données)
```

### Onglets du tableau de bord Local :

- **Overview :** Gestion du domaine, activation du SSL, version PHP, activation du _One-click Admin_ (connexion sans mot de passe).
- **Database :** Accès rapide à la base de données via **Adminer** (ou TablePlus/Sequel Ace) et identifiants de connexion (`root` / `root`).
- **Tools :** Accès à **Mailpit** (e-mails locaux) et configuration des **Live Links**.

## 5. 💡 Commandes Utiles (via "Site Shell")

En cliquant sur **`Site Shell`** sous le nom de votre site dans Local, vous ouvrez un terminal directement connecté à l'environnement du site :

```bash
# Lister les extensions installées
wp plugin list

# Mettre à jour toutes les extensions
wp plugin update --all

# Créer un nouvel utilisateur administrateur
wp user create jean jean@exemple.fr --role=administrator --user_pass=MotDePasse123

# Exporter la base de données dans un fichier SQL
wp db export sauvegarde.sql

# Remplacer une URL dans la base (utile après une migration)
wp search-replace 'https://ancien-domaine.fr' 'http://mon-site.local' --all-tables
```

## 6. 💡 Commandes et astuces utiles

- **Activer le HTTPS :** Dans l'onglet _Overview_ de votre site, cliquer sur **`Trust`** à côté de la mention _SSL_.
- **Ouvrir le terminal WP-CLI :** Clic droit sur le nom du site dans la barre latérale > **`Open Site Shell`**.
- **Cloner ou exporter un site :** Clic droit sur le nom du site > **`Clone`** ou **`Export`** (génère une archive `.zip` complète incluant les fichiers et la base de données).
- **Vérifier les e-mails sortants :** Aller dans l'onglet **`Tools`** > **`Mailpit`** (ou _Open Mailpit_)
- **Déploiement rapide:** Connectez directement votre compte **WP Engine** ou **Flywheel** (onglet _Connect_) pour pousser votre site en ligne en un clic.

## 7. 🔧 Dépannage rapide

- **Conflit de ports (Port 80/443 déjà utilisé) :** Allez dans _Preferences > Advanced > Router Mode_ et passez de `Site Domains` à `localhost` (l'URL deviendra `localhost:1000X` au lieu de `monsite.local`).
- **Site lent sous Windows :** Ajoutez le dossier `Local Sites` aux exclusions de votre antivirus (Windows Defender).
- **Erreurs PHP :** Consultez le fichier `logs/php/error.log` ou activez `WP_DEBUG` directement dans `app/public/wp-config.php`.
