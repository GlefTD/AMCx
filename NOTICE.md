# Avis et conditions d’usage — AMCx

Ce fichier n’est pas une licence. Il complète `LICENSE` (code) et décrit
ce que tu peux et ne peux pas dire du projet.

## Ce qu’est AMCx

AMCx est un explorateur **indépendant** des publications IITA / IATI
d’Affaires mondiales Canada. Ce n’est **pas** un produit, un service
ni un site officiel du gouvernement du Canada.

Aucune affiliation, aucun partenariat, aucune approbation
d’Affaires mondiales Canada, d’IATI ou du gouvernement du Canada
n’est implicitement ou explicitement accordée.

## Deux objets distincts

| Objet | Licence | Qui en est responsable |
| --- | --- | --- |
| Code AMCx (`index.html`, scripts, styles, docs du dépôt hors données) | MIT — voir `LICENSE` | Auteur·ices du dépôt |
| Données de projets (XML IITA, jeux consolidés dans `datasets/` et `data/`, exports CSV/XML générés par l’app) | [Licence du gouvernement ouvert — Canada](https://open.canada.ca/en/open-government-licence-canada) | Affaires mondiales Canada |

Les données IITA d’AMC sont aussi listées sur le
[Portail du gouvernement ouvert](https://open.canada.ca/data/en/dataset/2f7e22f0-88f6-430c-9723-547043f898ad)
et sur le [Registre IATI (gac-amc)](https://www.iatiregistry.org/publisher/gac-amc).

## Disclaimer (à coller aussi dans le README)

AMCx est fourni « tel quel », sans garantie d’aucune sorte,
y compris d’exactitude, d’actualité, d’exhaustivité ou d’aptitude
à un usage particulier.

Les montants, statuts, titres, partenaires et résultats affichés
proviennent des fichiers IITA publiés par Affaires mondiales Canada.
En cas d’écart, **la fiche AMC et le XML source font foi**.
N’utilise pas AMCx comme source officielle pour une décision
financière, juridique, journalistique ou administrative
sans vérifier le fichier IITA et le portail AMC.

Les auteur·ices d’AMCx ne sont pas responsables des dommages
découlant de l’usage du logiciel ou des données affichées.

Rien n’est envoyé à un serveur AMCx après le chargement :
la session vit dans le navigateur (mémoire + IndexedDB).

## Si tu republies des extraits de projets

La Licence du gouvernement ouvert — Canada demande en substance :

1. Citer la source : Affaires mondiales Canada, fichiers IITA / IATI.
2. Fournir un lien vers la licence :
   https://ouvert.canada.ca/fr/licence-du-gouvernement-ouvert-canada
3. Indiquer si tu as modifié l’information (filtre, fusion, traduction, gzip, etc.).
4. Ne pas laisser croire que le gouvernement approuve ton usage.

Exemple d’attribution :

> Données des projets d’aide internationale : Affaires mondiales Canada,
> fichiers IITA, Licence du gouvernement ouvert — Canada.
> Jeu consolidé / filtré par AMCx. En cas d’écart, le XML officiel fait foi.

## Marques

« Affaires mondiales Canada », « Global Affairs Canada », « IITA »,
« IATI » et les identifiants de projets `CA-3-*` appartiennent à
leurs titulaires. AMCx n’accorde aucun droit sur ces marques.

## Sécurité

AMCx n’est pas un service d’hébergement de données personnelles.
N’y dépose pas de documents classifiés ou non publics.
Pour un problème de sécurité dans le *code*, ouvre une issue privée
ou un avis dans le dépôt — ne publie pas d’exploit.
