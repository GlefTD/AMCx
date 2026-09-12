# Contribuer à AMCx

Merci. Le projet tient dans un HTML autonome ; garde-le simple.

## Avant d’ouvrir une PR

- Décrire le problème et le résultat attendu.
- Tester bureau + mode simple (téléphone).
- Ne pas committer de secrets, de dumps personnels, ni de XML hors
  des publications IITA officielles.

## Données

Les XML dans `datasets/` et `data/` sont des republications des
fichiers IITA d’AMC. Si tu mets à jour le jeu :

- garde le nom `iati-amc-<NOM>_<AAAAMMJJ>.xml`
- fournis aussi le `.xml.gz` dans `data/` (limite Cloudflare Assets : 25 Mio)
- ne commite pas de fichier modifié au contenu (sauf concat / gzip)

## Code

Licence MIT (`LICENSE`). En envoyant une PR, tu acceptes que ta
contribution soit publiée sous cette licence.
