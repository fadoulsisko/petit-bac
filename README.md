# Petit Bac

Jeu de Baccalauréat en français, pour **2 à 10 joueurs sur un même appareil**, sans inscription.

**[Jouer en ligne](https://petit-bac-sisko.fadoulsisko.chatgpt.site)**

## Fonctionnalités

- Six catégories : Prénom, Pays, Ville, Fruit, Légume et Animal.
- Chronomètre de 60 secondes par joueur par défaut, réglable à 15 ou 30 secondes.
- Nombre de manches saisi librement (entier positif).
- Écran de confirmation et retour aux paramètres avant le premier chrono.
- Lettre aléatoire différente pour chaque joueur d'une même manche ; la lettre précédente d'un joueur n'est pas réutilisée immédiatement à la manche suivante.
- Rotation du premier joueur à chaque manche et à chaque nouvelle partie dans la session.
- Enregistrement automatique des réponses à la fin du chronomètre.
- Correction collective après le passage de tous les joueurs.
- 10 points par mot reconnu, 0 point pour une réponse vide ou incorrecte.
- Contestation de la correction et validation par le groupe.
- Exemples de l'animateur pour la lettre de chaque joueur, scores cumulés et classement final.
- Interface adaptée aux ordinateurs, tablettes et téléphones.

## Lancer le jeu sur son ordinateur

Le jeu est une application statique en HTML, CSS et JavaScript. Aucun serveur métier, compte, clé API ou installation npm n'est nécessaire.

Avec Python 3 installé :

```bash
git clone https://github.com/fadoulsisko/petit-bac.git
cd petit-bac
python -m http.server 8000 --directory dist
```

Ouvrir ensuite **http://localhost:8000** dans un navigateur récent. Selon le système, remplacer `python` par `python3` ou `py`.

## Organisation des fichiers

| Fichier | Rôle |
| --- | --- |
| `dist/index.html` | Page, métadonnées et règles |
| `dist/style.css` | Présentation et adaptation aux tailles d'écran |
| `dist/app.js` | Paramètres, tours, chrono, corrections et scores |
| `dist/data.js` | Répertoire de mots et fonction de validation |
| `dist/favicon.svg` | Icône du jeu |

Le dossier `dist` contient directement les sources utilisées par le navigateur ; aucune compilation n'est nécessaire.

## Correction des réponses

La correction utilise un **répertoire local**, sans appel à une IA ni à une API. Il n'est pas exhaustif, notamment pour les prénoms et villes. Un mot absent reçoit initialement 0 point mais peut être validé par le groupe s'il commence par la bonne lettre et correspond à la catégorie. Les accents, majuscules et séparateurs sont normalisés.

Les catégories de légumes suivent l'usage culinaire. Certaines lettres n'ont pas d'exemple disponible dans certaines catégories. Les lettres peuvent revenir d'une manche à l'autre, ce qui permet de jouer plus de 26 manches.

Pour enrichir les réponses reconnues, modifier les listes de `dist/data.js` en conservant l'ordre des six catégories.

## Hébergement et données

La version publique est hébergée à l'adresse indiquée en haut de ce document. Ce dépôt contient une copie de la version publiée le 7 octobre 2026, incluant les dernières améliorations.

Tout hébergement statique peut servir le contenu du dossier `dist`. Ce dépôt n'active pas à lui seul GitHub Pages et aucun déploiement automatique depuis GitHub n'est configuré.

La partie reste uniquement en mémoire dans le navigateur : recharger ou fermer la page efface les scores et réglages de la session. Le jeu ne synchronise pas plusieurs appareils. Les polices sont chargées depuis Google Fonts, avec des polices de remplacement si elles sont indisponibles.

## Vérification rapide

Avec Node.js installé :

```bash
node --check dist/app.js
node --check dist/data.js
```

Avant publication, vérifier une partie complète, le retour aux paramètres, l'expiration du chrono, la rotation des joueurs, les corrections et le classement sur ordinateur et téléphone.

