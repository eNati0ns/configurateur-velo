# Comment ajouter des pièces (sans coder)

Tout le contenu du configurateur vient d'un seul fichier :
**`data/parts.json`**

C'est un fichier texte tout simple. Tu ne touches jamais à `index.html`.

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
- **`geometrie`** (cadres uniquement) : doit être une valeur parmi `"aero"`, `"climb"`, `"endurance"`, `"classic"` — ce sont les 4 formes de cadre que le programme sait dessiner. Tu peux créer autant de cadres que tu veux en réutilisant ces 4 formes avec ta propre couleur/poids/nom. Pour une 5e forme totalement différente, il faudra qu'on la code ensemble.
- **`profil_mm`** (roues uniquement) : hauteur de jante en mm (ex: 24 = roue légère, 50 = roue aéro profilée). Change l'apparence de la roue.

## Ne pas casser le fichier

Un fichier JSON est très strict sur la forme :
- Chaque `{ ... }` doit avoir toutes ses virgules, mais **pas de virgule après le tout dernier élément** d'une liste.
- Toujours des guillemets doubles `" "` (jamais de guillemets simples).
- Avant d'enregistrer, tu peux coller tout le contenu du fichier sur **jsonlint.com** pour vérifier qu'il n'y a pas d'erreur de syntaxe (une virgule oubliée, une accolade en trop...).

## Et après ?

Une fois le fichier modifié et enregistré :
- Si tu es sur **GitHub + Netlify** (voir GUIDE-DEPLOIEMENT.md) : le site se met à jour tout seul en ~1 minute après avoir sauvegardé sur GitHub.
- Si tu es sur **Netlify Drop** : il faut re-glisser tout le dossier sur netlify.com/drop pour publier la mise à jour.
