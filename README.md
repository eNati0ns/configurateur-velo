# Comment ajouter des pièces (sans coder)

Tout le contenu du configurateur vient d'un seul fichier :
**`data/parts.json`**

C'est un fichier texte tout simple. Tu ne touches jamais à `index.html`.

## Mode "Frameset only"

Une case à cocher en haut du panneau permet de n'afficher que le cadre et
la fourche, sans roues ni groupe — pratique pour travailler la géométrie
d'un cadre sans distraction.

## Règle d'or

Pour ajouter une pièce : **copie un bloc existant qui ressemble à ce que tu veux, colle-le juste après (avec une virgule entre les deux), et change les valeurs.**

Exemple — ajouter une 3e cassette :

```json
"cassettes": [
  { "id": "shim-105-cs", "marque": "Shimano", "modele": "105 11-30T", "vitesses": 11, "poids_g": 284 },
  { "id": "sram-xg1290", "marque": "SRAM", "modele": "XG-1290 10-33T", "vitesses": 12, "poids_g": 195 },
  { "id": "campy-chorus-cs", "marque": "Campagnolo", "modele": "Chorus 11-29T", "vitesses": 12, "poids_g": 262 }
]
```

(on a dupliqué la 2e ligne, changé les valeurs, et ajouté une virgule après la 2e ligne pour séparer les deux)

## Règles importantes à respecter

- **`id`** : un code unique, sans espace ni accent, propre à chaque pièce (ex: `shim-ultegra-cs`). Il ne doit jamais être utilisé deux fois dans la même catégorie.
- **Ne jamais changer ni supprimer** l'entrée avec `"id": "fd-none"` dans `derailleurs_avant` — le programme s'en sert pour savoir qu'aucun dérailleur avant n'est monté (vélo mono-plateau).
- **`poids_g`** : poids en grammes, un nombre simple (pas de guillemets, pas d'unité).
- **`vitesses`** : nombre de vitesses (10, 11, 12...). Doit être identique entre la cassette et le dérailleur arrière pour que ce soit compatible.
- **`plateaux`** (manivelles uniquement) : 1 ou 2 (nombre de plateaux à l'avant).
- **`couleur`** (cadres et roues uniquement) : un code couleur du type `"#c1443a"`. Tu peux en trouver facilement en cherchant "color picker" sur Google.
- **`profil_mm`** (roues uniquement) : hauteur de jante en mm (ex: 24 = roue légère, 50 = roue aéro profilée). Change l'apparence de la roue.

### Cadres — toutes les mesures viennent de la fiche géométrique du fabricant, **en millimètres** (le programme convertit tout seul en mètres)

| Champ JSON | Mesure (voir schéma du fabricant) |
|---|---|
| `reach_mm` | Reach |
| `stack_mm` | Stack |
| `top_tube_effectif_mm` | Top Tube (effective) — gardé pour référence, pas utilisé dans le dessin |
| `seat_tube_ct_mm` | Seat Tube C-T |
| `head_angle_deg` | Head Angle (en degrés, pas en mm) |
| `seat_angle_deg` | Seat Angle (en degrés) |
| `head_tube_mm` | Head Tube |
| `chainstay_mm` | Chainstay |
| `wheelbase_mm` | Wheelbase — gardé pour référence/contrôle |
| `front_centre_mm` | Front Centre |
| `standover_mm` | Standover — gardé pour référence, pas utilisé dans le dessin |
| `bb_drop_mm` | BB Drop |
| `bb_height_mm` | BB Height — gardé pour référence |
| `fork_rake_mm` | Fork Rake / Offset — gardé pour référence |
| `trail_mm` | Trail — gardé pour référence |
| `fork_length_a2c_mm` | Fork Length (A2C) — gardé pour référence |
| `seatpost_length_mm` | Seatpost Length — gardé pour référence, la tige de selle n'est pas dessinée (ce n'est pas le cadre) |

Toutes ces mesures sont **obligatoires** pour qu'un cadre se dessine correctement — copie le bloc `f-sl9-52` en entier et remplace chaque valeur par celles de la fiche technique de ton nouveau cadre. Le rendu 3D ne dessine que le cadre et la fourche (pas de potence, cintre, selle ou tige de selle : ce sont des composants séparés qu'on ajoutera plus tard).

Pas de champ `geometrie` à choisir : la forme du cadre est maintenant calculée directement à partir de ces mesures, ce n'est plus une des 4 formes toutes faites d'avant.

## Ne pas casser le fichier

Un fichier JSON est très strict sur la forme :
- Chaque `{ ... }` doit avoir toutes ses virgules, mais **pas de virgule après le tout dernier élément** d'une liste.
- Toujours des guillemets doubles `" "` (jamais de guillemets simples).
- Avant d'enregistrer, tu peux coller tout le contenu du fichier sur **jsonlint.com** pour vérifier qu'il n'y a pas d'erreur de syntaxe (une virgule oubliée, une accolade en trop...).

## Et après ?

Une fois le fichier modifié et enregistré :
- Si tu es sur **GitHub + Netlify** (voir GUIDE-DEPLOIEMENT.md) : le site se met à jour tout seul en ~1 minute après avoir sauvegardé sur GitHub.
- Si tu es sur **Netlify Drop** : il faut re-glisser tout le dossier sur netlify.com/drop pour publier la mise à jour.
