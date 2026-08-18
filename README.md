# Bon anniversaire Julien

Page HTML autonome : une explosion de lettres, puis un poème autour du chiffre 26.

## Mise en ligne (GitHub Pages)

1. Placer `index.html` et `og.png` à la racine du dépôt (dépôt **public**).
2. `Settings` → `Pages` → **Source** : *Deploy from a branch*.
3. Branche `main`, dossier `/ (root)`, puis **Save**.
4. La page est publiée sous `https://<utilisateur>.github.io/<depot>/` (compter une à deux minutes).

## Aperçu de partage (Open Graph)

`og.png` (1200 × 630) s'affiche quand le lien est envoyé sur WhatsApp, iMessage, Slack, LinkedIn, X…

Les balises `og:url` et `og:image` sont déjà renseignées sur <https://angstik.github.io/julien/>
(URL absolue obligatoire : un chemin relatif ne produit aucun aperçu). Vérification du rendu sur
<https://www.opengraph.xyz/>. Les plateformes gardent l'aperçu en cache : en cas de correction
après un premier partage, ajouter `?v=2` à la fin du lien pour forcer le rafraîchissement.

## Caractéristiques

- **Fichier unique.** Aucune dépendance, aucun script externe, aucune requête réseau : polices système uniquement, favicon en data-URI. La page fonctionne aussi hors ligne, ouverte directement depuis le disque.
- **Arc JULIEN.** Au premier temps de l'explosion, les six lettres du prénom apparaissent de gauche à droite sur un arc de 112° dont le rayon grandit progressivement — la coque d'une bombe de feu d'artifice qui s'ouvre. Aucune gravité, aucune rotation d'ensemble : chaque lettre garde son rayon et son angle, orientée selon la tangente de l'arc. Crème pleine, graisse 900, contour sombre et halo qui pulse, avec trois éclats dorés scintillants qui tournent autour de chaque lettre. Taille et rayon sont calculés ensemble pour que les six lettres tiennent sans se chevaucher, du mobile au grand écran. L'arc tient environ 3,5 s à pleine opacité, bien après la retombée des confettis, puis s'efface en fondu.
- **Explosion en lettres.** Les confettis sont les 26 lettres de l'alphabet, dessinées sur un `<canvas>` (gravité, frottement, rotation, usure). Quatre salves à l'ouverture, une mini-explosion à chaque clic. Le bouton « Relancer l'explosion » ramène en haut de page et rejoue toute la séquence d'ouverture.
- **Pluie de cœurs et d'étoiles.** Chaque gerbe envoie 26 cœurs de couleurs différentes et 26 étoiles dorées. Trois déclencheurs :
  - *la première*, 6 secondes après la fin de l'explosion de lettres, part du bas de l'écran avec un élan vers le haut : on n'en voit que la cime, ce qui invite à faire défiler la page ;
  - *au défilement*, chaque strophe qui franchit le milieu de l'écran envoie sa gerbe à hauteur du milieu (bande de détection `rootMargin:"-50% 0px -50% 0px"`, une gerbe maximum toutes les 1,5 s) ;
  - *à l'arrêt*, si rien ne s'est passé pendant 10 à 15 secondes, une gerbe part toute seule. Toute explosion, y compris un clic, repousse ce minuteur.

  Cœurs et étoiles sont plus lents que les lettres : gravité réduite, oscillation latérale, durée de vie allongée. Rien ne se déclenche quand l'onglet est en arrière-plan ; le minuteur redémarre au retour.
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
- Densité des explosions : les nombres passés à `eclate(x, y, nombre, force, coeur)` dans `feu()`.
- Délai d'inactivité avant une gerbe : `setTimeout(pluieDeCoeurs, 10000 + Math.random() * 5000)` dans `programme()`.
- Couleurs des cœurs : constante `COEURS`.
- Couleur d'une strophe : attribut `style="--c:var(--rose)"` sur le `div.strophe`.

## Licence

Usage libre.
