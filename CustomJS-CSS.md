## 📝 FICHE RECAPITULATIVE CUSTOM JS & CSS SUR WORDPRESS

Guide récapitulatif des bonnes pratiques pour ajouter, gérer et optimiser du code CSS et JavaScript personnalisé sur un site WordPress.

## 📁 1. Où placer son code ? (Par ordre de recommandation)

| Méthode                                            | CSS | JS  | Avantages                                | Inconvénients                        |
| :------------------------------------------------- | :-: | :-: | :--------------------------------------- | :----------------------------------- |
| **Thème Enfant (`functions.php`)**                 | ✅  | ✅  | Sécurisé, performant, versionnable (Git) | Nécessite un accès FTP/fichiers      |
| **Extension dédiée (ex: WPCode)**                  | ✅  | ✅  | Interface simple, gestion conditionnelle | Ajoute un plugin supplémentaire      |
| **Personnalisateur (`Apparence > Personnaliser`)** | ✅  | ❌  | Natif, aperçu en direct, rapide          | Uniquement pour du CSS léger         |
| **Constructeur de pages (Elementor, Divi...)**     | ✅  | ✅  | Ciblé par page ou élément                | Code dispersé, difficile à maintenir |

> ⚠️ **Règle d'or :** Ne jamais modifier directement les fichiers d'un thème parent ou d'une extension (écrasement garanti à la prochaine mise à jour).

### Ajouter du CSS Sans code (Via l'interface WordPress)

Idéal pour des ajustements CSS rapides et légers (ne fonctionne pas pour le JavaScript).

- **Thèmes classiques :** Aller dans `Apparence > Personnaliser > CSS additionnel`.
- **Thèmes FSE (Full Site Editing) :** Aller dans `Apparence > Éditeur > Styles (icône lune/soleil) > Trois petits points (⋮) > CSS additionnel`.

### Via un Thème Enfant (Recommandé)

La méthode la plus propre et performante pour éviter d'alourdir la base de données et conserver vos modifications lors des mises à jour du thème parent.

# 🎯 2. Ajouter du Custom CSS

### Méthode A : Via l'interface native (Rapide)

1. Aller dans **Apparence > Personnaliser > CSS additionnel**.
2. Écrire le code CSS et cliquer sur **Publier**.
   _(Note : Si vous utilisez un thème FSE / Full Site Editing récent, allez dans **Apparence > Éditeur > Styles > ⋮ > CSS additionnel**)._

### Méthode B : Via un Thème Enfant (Recommandé pour les projets complexes)

1. 📁 Structure des fichiers

```text
wp-content/themes/mon-theme-enfant/
├── style.css
├── functions.php
└── assets/
    ├── css/
    │   └── custom.css
    └── js/
        └── custom.js
```

2. ⚙️ Chargement dans `functions.php`

Utilisez toujours les hooks `wp_enqueue_scripts` pour charger vos fichiers proprement.
