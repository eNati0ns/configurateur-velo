# Mettre le site en ligne — guide pas-à-pas

Coût : **0.- CHF**, aucune carte bancaire demandée. Pas de nom de domaine requis :
ton site sera accessible via une adresse du type `mon-velo-configurateur.netlify.app`.

Il y a deux comptes gratuits à créer : **GitHub** (garde tes fichiers) et
**Netlify** (publie le site en ligne et le republie automatiquement à chaque
modification).

---

## Étape 1 — Créer un compte GitHub

1. Va sur **github.com**
2. Clique sur **Sign up**
3. Renseigne un email, un mot de passe, un nom d'utilisateur → suis les étapes
4. Confirme ton email (un mail te sera envoyé)

## Étape 2 — Créer un dépôt ("repository")

Un dépôt, c'est juste un dossier de projet sur GitHub.

1. Une fois connecté, clique sur le bouton vert **New** (ou le **+** en haut à droite → **New repository**)
2. **Repository name** : `configurateur-velo`
3. Laisse-le en **Public**
4. Ne coche aucune case (pas de README, pas de .gitignore)
5. Clique **Create repository**

## Étape 3 — Envoyer les fichiers sur GitHub

Tu arrives sur une page presque vide avec un lien **"uploading an existing file"**.

1. Clique sur ce lien (**uploading an existing file**)
2. Glisse-dépose **tout le contenu** du dossier que je t'ai donné :
   - `index.html`
   - le dossier `data` (avec `parts.json` dedans)
   - `README.md`
3. En bas de page, clique **Commit changes**

Tes fichiers sont maintenant en ligne sur GitHub (mais pas encore visibles comme un vrai site web — ça, c'est Netlify qui va s'en charger).

## Étape 4 — Créer un compte Netlify

1. Va sur **netlify.com**
2. Clique **Sign up**
3. Choisis **"Sign up with GitHub"** (le plus simple : ça relie directement les deux comptes)
4. Autorise Netlify à accéder à ton compte GitHub

## Étape 5 — Connecter le site

1. Sur Netlify, clique **Add new site** → **Import an existing project**
2. Choisis **GitHub**
3. Sélectionne le dépôt **configurateur-velo**
4. Netlify te propose des réglages de build : **ne change rien**, laisse tout vide/par défaut
5. Clique **Deploy site**

Après 30 à 60 secondes, ton site est en ligne ! Netlify te donne une adresse du type :
`https://random-name-123abc.netlify.app`

Tu peux la renommer : **Site settings → Change site name** → choisis un nom du type `mon-velo-configurateur` → ton adresse devient `mon-velo-configurateur.netlify.app`.

---

## Comment mettre à jour le site plus tard

C'est là que ce montage devient pratique :

1. Va sur ton dépôt GitHub → ouvre `data/parts.json`
2. Clique sur l'icône **crayon** (Edit this file) en haut à droite du fichier
3. Modifie le contenu (voir `README.md` pour les règles à respecter)
4. En bas de page, clique **Commit changes**
5. Netlify détecte le changement automatiquement et republie le site tout seul en ~1 minute — tu n'as rien d'autre à faire.

Tu peux suivre la republication dans l'onglet **Deploys** sur Netlify (un point orange = en cours, vert = publié).

---

## Si quelque chose ne marche pas

- **Le site est blanc / le panneau de gauche est vide** → il y a probablement une erreur de syntaxe dans `parts.json` (virgule oubliée, guillemet manquant). Colle le contenu du fichier sur **jsonlint.com** pour trouver l'erreur exacte.
- **"Page not found" sur Netlify** → vérifie que `index.html` est bien à la racine du dépôt GitHub (pas dans un sous-dossier).
- Pour tout casser sans risque et recommencer : tu peux toujours re-uploader les fichiers d'origine sur GitHub, rien n'est perdu.

## Accès bloqué depuis un réseau d'entreprise (proxy / pare-feu)

Beaucoup d'entreprises bloquent par défaut les hébergements gratuits comme
`*.netlify.app`, `*.vercel.app` ou `*.github.io` — leurs systèmes de sécurité
les classent "suspects" car ils sont parfois utilisés pour du phishing,
même quand le contenu est légitime.

- Utilise toujours l'**URL principale du site** (celle que tu as choisie dans
  Site settings → Change site name), pas une URL de "Deploy preview" avec un
  hash aléatoire (`xxxxxxxx--nom-du-site.netlify.app`) — celles-ci sont
  encore plus souvent bloquées.
- Si le blocage persiste, c'est une décision de la politique de sécurité de
  l'entreprise, pas un problème du site : il faut demander à l'IT
  d'autoriser le domaine, ou tester en dehors du réseau professionnel
  (téléphone, réseau personnel).
- Un nom de domaine personnel (quelques CHF/an) passe presque toujours mieux
  qu'un sous-domaine `*.netlify.app`, car il n'est pas associé à
  l'hébergement gratuit générique.
