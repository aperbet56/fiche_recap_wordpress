## 📝 FICHE RECAPITULATIVE ELEMENTOR

**Elementor** est un constructeur de pages (_Page Builder_) visuel en glisser-déposer (_Drag & Drop_) pour **WordPress**. Il permet de créer des sites web professionnels sans écrire une seule ligne de code, tout en offrant des options avancées pour les développeurs.

## 1. 🚀 Fonctionnalités Principales

- **Éditeur visuel en temps réel (WYSIWYG) :** Voyez vos modifications instantanément pendant que vous concevez la page.

- **Système de mise en page flexible :** Basé sur des **Conteneurs Flexbox** et des **Grilles CSS** (_CSS Grid_) pour un alignement précis.

* **Design Responsive :** Contrôle total sur l'affichage selon la taille de l'écran (Ordinateur, Tablette, Mobile).

* **Bibliothèque de modèles :** Accès à des centaines de blocs et de pages préconçus prêts à l'emploi.

* **Styles globaux (Design System) :** Gestion centralisée des couleurs, typographies et styles de boutons sur l'ensemble du site.

## 2. 🆓 Elementor Free vs 💎 Elementor Pro

| Fonctionnalité                                                    | Version Gratuite (Free) | Version Payante (Pro) |
| :---------------------------------------------------------------- | :---------------------: | :-------------------: |
| **Éditeur glisser-déposer**                                       |           ✅            |          ✅           |
| **Widgets de base** (Texte, Image, Vidéo, Bouton...)              |    ✅ (30+ widgets)     |   ✅ (100+ widgets)   |
| **Theme Builder** (En-tête, Pied de page, Pages 404, Archives)    |           ❌            |          ✅           |
| **Popup Builder** (Fenêtres modales et bannières)                 |           ❌            |          ✅           |
| **Form Builder** (Formulaires de contact avancés)                 |           ❌            |          ✅           |
| **WooCommerce Builder** (Fiches produits et boutiques sur-mesure) |           ❌            |          ✅           |
| **Contenu dynamique** (ACF, Pods, Toolset)                        |           ❌            |          ✅           |
| **CSS personnalisé** par élément                                  |           ❌            |          ✅           |

## 3. 🧱 Structure de l'Interface

### 🧱 Architecture d'une Page

1. **Conteneur (Container)** : La brique de base qui structure la mise en page (en ligne ou en colonne) et gère l'alignement des éléments internes.

2. **Widgets** : Les blocs de contenu placés à l'intérieur des conteneurs (Texte, Image, Formulaire, Carrousel, etc.).

### 🧩 Widgets Essentiels

### ⚙️ Configuration

1. **Panneau de gauche (L'Inspecteur) :**

   - **Contenu :** Textes, images, liens, requêtes.
   - **Style :** Couleurs, typographie, marges intérieures (_Padding_), bordures, ombres.
   - **Avancé :** Marges extérieures (_Margin_), animations, positionnement, attributs personnalisés et responsive.

2. **Zone centrale (Le Canevas) :** L'aperçu en direct de votre page.

3. **Barre supérieure / inférieure :**
   - **Navigateur (Structure) :** Vue en arborescence pour sélectionner et réorganiser facilement les éléments imbriqués.
   - **Historique :** Annuler/Rétablir des actions ou revenir à une révision précédente.
   - **Mode Responsive :** Basculer entre les vues Desktop, Tablette et Mobile.

## 4. ⌨️ Raccourcis Clavier Utiles (Windows / Mac)

_(Remplacer `Ctrl` par `Cmd` sur macOS)_

- `Ctrl + Z` : Annuler la dernière action
- `Ctrl + Shift + Z` : Rétablir l'action
- `Ctrl + C` / `Ctrl + V` : Copier / Coller un élément
- `Ctrl + Shift + V` : **Coller le style uniquement** d'un élément sur un autre
- `Ctrl + D` : Dupliquer l'élément sélectionné
- `Ctrl + E` : Ouvrir le **Finder** (navigation rapide entre les pages et réglages)
- `Ctrl + I` : Ouvrir/Fermer le **Navigateur** (arborescence)
- `Ctrl + P` : Basculer entre le mode édition et l'aperçu complet
- `Ctrl + S` : Enregistrer / Mettre à jour

## 5. 💡 Bonnes Pratiques - Sécurité - Performances

- **Privilégier les Conteneurs (Flexbox / Grid) :** Évitez l'ancien système de "Sections et Colonnes" pour alléger le code DOM et améliorer la vitesse de chargement.

- **Utiliser les Styles Globaux :** Définissez vos polices et palettes de couleurs dans les _Réglages du site_ plutôt que de styliser chaque widget individuellement.

- **Limiter les imbrications :** Moins il y a de conteneurs imbriqués les uns dans les autres, plus le site sera rapide (meilleur score Google PageSpeed).

- **Utiliser le thème Hello Elementor :** C'est un thème ultra-léger conçu spécialement pour servir de toile vierge au _Theme Builder_ d'Elementor Pro.

- **Optimiser les médias :** Compressez toujours vos images (format WebP recommandé) avant de les importer dans WordPress.

* **Activer les fonctionnalités d'optimisation** : Dans _Elementor > Réglages > Fonctionnalités_, activer le chargement optimisé du DOM et des ressources CSS/JS.

* **Désactiver les fonctionnalités inutiles :** Aller dans _Elementor > Réglages > Fonctionnalités_ pour activer les améliorations de performance (ex: _Chargement CSS amélioré_, _Chargement des polices Google en local_).

* **Limiter les add-ons :** Ne pas multiplier les extensions tierces (Essential Addons, Crocoblock, etc.) si Elementor natif suffit.

## 6. 🔗 Ressources Officielles

- [Site officiel d'Elementor](https://elementor.com)
- [Documentation et Centre d'aide](https://elementor.comhelp/)
- [Répertoire WordPress (Version Gratuite)](https://wordpress.org)
