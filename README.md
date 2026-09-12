# AURAN MOTORS

Site vitrine monopage du **showroom de voitures premium et exclusives à Antananarivo**.
Une seule page : `index.html` (HTML + CSS + JavaScript vanilla, aucun build, aucune dépendance).

## Lancer le site

Ouvrir le fichier directement dans le navigateur :

```
start index.html
```

Ou via un serveur statique (recommandé pour l'exposition à un vrai domaine) :

```
python -m http.server 8080
# ou
npx serve .
```

Aucune API, aucun backend local : le site fonctionne en statique pur.

## Structure

```
index.html              → tout le site (styles, structure, scripts)
assets/
  img/
    hero.jpg            → hero plein écran
    fleet/              → photos des véhicules de la collection
    lifestyle/          → photos atelier (atelier.jpg, detail.jpg)
  fonts/                → webfonts locales (Manrope, Cormorant Garamond)
```

## Fonctionnalités

- **Hero plein écran** (image + titre, animation lente).
- **Pièce maîtresse** : Porsche 911 affichée en pleine hauteur d'écran, image entière (`object-fit: contain`).
- **Collection** : 5 véhicules réels, filtres « Sportives / Électriques ».
- **Favoris** : mémorisés en `localStorage` (clé `am_favs`), compteur dans la navigation, section dédiée.
- **Comparateur** : jusqu'à 3 véhicules (clé `am_cmp`), barre flottante + fenêtre modale avec fiches techniques.
- **Bouton WhatsApp flottant** et liens réseaux sociaux.
- **Formulaire de contact** : validation côté client, puis envoi via `mailto:` (l'app mail de l'utilisateur s'ouvre avec le brouillon pré‑rempli).
- **SEO** : meta description, Open Graph, donnnées structurées JSON‑LD (`AutoDealer` + `ItemList`), texte alternatif, titres sémantiques. Favicon SVG inline.
- Zones : signature, bandeau défilant, la maison, parcours en 4 étapes, import mondial, rachat, témoignages, contact.

## Photos des véhicules

| Carte | Fichier | Cadre CSS |
| --- | --- | --- |
| Alpine A110 | `fleet/alpine-a110.jpg` | paysage `16/10` |
| Audi e-tron GT | `fleet/audi-etron-gt.jpg` | paysage `16/10` |
| Mercedes-Benz EQS | `fleet/mecedes-benz.jpg` | carré `1/1` |
| Porsche 911 | `fleet/porsche-911.jpg` | portrait `2/3` |
| Tesla Model 3 | `fleet/tesla-model-3.jpg` | portrait `2/3` |

Pour changer de visuel : remplacer le fichier (même nom) ou pointer la balise `<img>`
vers un nouveau fichier, puis aligner la classe de la carte :
`.media` par défaut = `16/10`, `.portrait` = `2/3`, `.square` = `1/1`.

> Note : le fichier EQS s'appelle volontairement `mecedes-benz.jpg` (état actuel du dossier).
> Si vous le renommez, mettre à jour la balise `<img>` de la carte correspondante.

## Coordonnées — à confirmer côté client

- Téléphone affiché : `+261 33 42 028 82`
- Email affiché **et destination du formulaire** : `jobanitah@gmail.com`
- Horaires : sur rendez-vous, 08h30–18h30 du lundi au samedi (dimanche sur rendez-vous)

Le formulaire envoie vers l'email `jobanitah@gmail.com` via `mailto:`. Pour un envoi
**réel** sans dépendre de l'app mail du visiteur (recommandé avant mise en ligne), remplacer
cette ligne dans `index.html` par un service type Formspree / Web3Forms / FormSubmit.co
ou un envoi WhatsApp (`wa.me/+261334202882`).

## Conventions

- Police display : **Cormorant Garamond** ; texte : **Manrope** (fichiers locaux en `woff2`, `font-display: swap`).
- Palette : fonds sombres (obsidienne/plomb), accents dorés (`--or: #c9a961`).
- Prix volontairement affichés « Sur demande » (aucun tarif inventé).
- Réduit les animations si `prefers-reduced-motion`.