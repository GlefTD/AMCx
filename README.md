# AMCx

Explorateur local des projets d’aide internationale d’**Affaires mondiales Canada** (AMC), à partir des fichiers IITA / IATI officiels.

Le portail AMC est utile, mais trop lent dès qu’on veut fouiller, comparer ou travailler hors ligne. AMCx charge les XML officiels (ou un jeu consolidé) **dans le navigateur**, les parse une fois, puis tout reste local : recherche, filtres, fiches, favoris, export.

Rien n’est envoyé à un serveur AMCx. Après le premier chargement, les données vivent dans IndexedDB.

- Dépôt : [github.com/GlefTD/AMCx](https://github.com/GlefTD/AMCx)
- Données consolidées : [`datasets/`](https://github.com/GlefTD/AMCx/tree/main/datasets)
- Source officielle IITA : [Initiative IITA — Affaires mondiales Canada](https://www.international.gc.ca/world-monde/issues_development-enjeux_developpement/priorities-priorites/initiative.aspx?lang=fra)

## Ce que ça fait

- Lire les XML IITA `dfatd-maecd_activit_status_*.xml` (ou un all-in-one)
- Afficher ~des milliers de projets avec défilement virtuel
- Chercher par texte, identifiant, pays, secteur, partenaire, statut, humanitaire  
  Exemples : `id:P009528` · `pays:PS` · `secteur:72010` · `partenaire:WFP` · `statut:3` · `hum:1`
- Étendre la recherche aux descriptions, résultats et marqueurs
- Filtrer par statut, dates, montants, pays, secteur, partenaire
- Ouvrir une fiche complète (titre, partenaire, budgets, pays, secteurs, marqueurs, transactions, résultats, lien AMC)
- Marquer des favoris, exporter CSV / XML filtré
- Geler une version et voir un **diff** (ajouts, retraits, modifications) au prochain chargement
- Mode simple téléphone : grille compacte, tiroir filtres / fichiers, fiche en feuille, gestes

## Utilisation

Ouvrir `index.html` dans un navigateur moderne (Chrome, Safari, Firefox, Edge). Aucune installation.

### Charger des données

Trois chemins :

1. **Données consolidées (recommandé)**  
   Bouton *Charger Données Consolidées* → choisir un XML.  
   En mode simple, si aucune donnée n’est en cache, le dernier jeu est chargé tout seul.  
   Ordre des sources : `/data/*.xml.gz` sur Cloudflare (≈12 Mo) → GitHub gzip → GitHub XML 60 Mo.

2. **Fichiers officiels**  
   Télécharger les XML IITA sur le site AMC, puis les glisser dans la zone d’import ou *Choisir des fichiers*.

3. **Cache local**  
   Au rechargement de la page, la dernière session revient depuis IndexedDB.

Le jeu actuel dans le dépôt :

```
datasets/iati-amc-ALLINONEDATASET_20260911.xml      (~60 Mo, ignoré par Cloudflare)
data/iati-amc-ALLINONEDATASET_20260911.xml.gz       (~12 Mo, à servir depuis le worker)
```

Convention de nom : `iati-amc-<NOM>_<AAAAMMJJ>.xml`.

### Mode bureau

Colonnes redimensionnables, graphiques pays / secteurs / partenaires, fiche latérale, raccourcis :

| Touche | Action |
| --- | --- |
| `/` | Recherche |
| `j` / `k` ou flèches | Ligne suivante / précédente |
| `F` | Favori |
| `C` | Copier la fiche |
| `Esc` | Fermer |

### Mode simple (téléphone)

Détection auto sur écran étroit / tactile, ou bouton **S**.

- Grille 3 lignes : identifiant + statut, dates / montants, titre, pays
- ⌕ filtres et favoris · ☰ fichiers, import, export, diff
- Fiche à 50 % de l’écran
- Glisser **Fiche** vers le haut : plein écran · vers le bas : fermer
- Glisser la fiche vers la gauche : retour à la grille
- Glisser un projet vers la droite : fiche plein écran

## Données

Les montants, statuts et textes viennent des publications IITA d’AMC (norme IATI 2.03, devise CAD). AMCx n’est **pas** un produit officiel d’Affaires mondiales Canada. En cas d’écart, la fiche AMC et le XML source font foi.

Liens utiles :

- [Banque de projets AMC](https://w05.international.gc.ca/projectbrowser-banqueprojets/)
- Fichiers IITA typiques :  
  `dfatd-maecd_activit_status_2.xml` (actif), `_3.xml` (finalisation), `_4*.xml` (fermé)

## Technique

Un seul fichier HTML/CSS/JS.

- Web Worker : parse streaming des blocs `<iati-activity>`
- IndexedDB : cache projets + instantané de diff
- Virtual scroll : seules les lignes visibles sont dessinées
- Chargement distant : `/data/*.xml.gz` (Cloudflare Assets, limite 25 Mio) puis GitHub raw

Pas de cadre, pas de bundler. `wrangler.jsonc` publie le statique. `.assetsignore` exclut `datasets/*.xml` (60 Mo > limite Assets).

## Limites

- Le XML all-in-one fait **60 Mo**. Cloudflare Workers Assets refuse les fichiers > 25 Mio. jsDelivr refuse > 20 Mo. D’où le gzip ~12 Mo dans `data/`.
- `cache: no-store` (v0.1.5) forçait un re-téléchargement GitHub à chaque visite sans cache HTTP
- IndexedDB peut refuser le pack sur iPhone (quota) : le prochain chargement retélécharge
- Le parse regex IITA couvre le jeu AMC ; ce n’est pas un validateur IATI générique

## Licence et usage

Projet personnel / communautaire. Les données restent la propriété et la responsabilité d’Affaires mondiales Canada. Réutiliser le code librement ; citer la source officielle si vous republiez des extraits de projets.
