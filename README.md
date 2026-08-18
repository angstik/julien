# Bon anniversaire Julien

Page HTML autonome : une explosion de lettres, puis un poème autour du chiffre 26.

## Mise en ligne (GitHub Pages)

1. Placer `index.html` à la racine du dépôt.
2. `Settings` → `Pages` → **Source** : *Deploy from a branch*.
3. Branche `main`, dossier `/ (root)`, puis **Save**.
4. La page est publiée sous `https://<utilisateur>.github.io/<depot>/` (compter une à deux minutes).

## Caractéristiques

- **Fichier unique.** Aucune dépendance, aucun script externe, aucune requête réseau : polices système uniquement, favicon en data-URI. La page fonctionne aussi hors ligne, ouverte directement depuis le disque.
- **Explosion en lettres.** Les confettis sont les 26 lettres de l'alphabet, dessinées sur un `<canvas>` (gravité, frottement, rotation, usure). Quatre salves à l'ouverture, une mini-explosion à chaque clic, une grosse au bouton « Relancer l'explosion ».
- **Alphabet.** Les 26 lettres s'affichent sous le titre ; J, U, L, I, E et N s'allument une à une avec une gerbe d'étincelles.
- **Poème.** Six strophes, chacune accrochée à un fait vérifiable sur 26, révélées au défilement via `IntersectionObserver` :

  | Marqueur | Fait |
  |---|---|
  | A → Z | lettres de l'alphabet latin |
  | Fe · 26 | numéro atomique du fer |
  | 26 os | os d'un pied humain |
  | 26,2 mi | longueur d'un marathon |
  | 26 × 2 | semaines d'une année |
  | 25 · 27 | seul entier situé entre un carré parfait et un cube parfait |

- **Accessibilité.** `prefers-reduced-motion` respecté (ni canvas ni transitions), focus clavier visible, responsive jusqu'au mobile.

## Personnalisation

Tout est en haut du fichier.

- Couleurs : variables CSS `--nuit`, `--rose`, `--jaune`, `--menthe`, `--ciel`, `--violet` dans `:root`.
- Palette des confettis : constante `PALETTE` dans le script.
- Lettres qui s'allument : constante `MOT` (`"JULIEN"`).
- Densité des explosions : les nombres passés à `eclate(x, y, nombre, force)` dans `feu()`.
- Couleur d'une strophe : attribut `style="--c:var(--rose)"` sur le `div.strophe`.

## Licence

Usage libre.
