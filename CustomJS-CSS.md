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
