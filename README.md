# Feuilles de plateau

Petite appli web (un seul fichier HTML, aucun serveur) pour composer les équipes
d'un plateau et générer les tableaux à découper/coller sur la feuille de match
officielle, à la bonne taille.

**Utilisation en ligne** : ouvrir la page publiée (GitHub Pages), charger son
`players.csv` et son `staff.csv` avec les boutons dédiés, composer les équipes,
puis « Générer les tableaux » et imprimer en taille réelle (100 %, pas
« ajuster à la page »).

**Utilisation locale** : ouvrir `index.html` directement dans le navigateur.
Si `players.csv` / `staff.csv` sont dans le même dossier, ils se chargent
automatiquement ; sinon, utiliser les boutons « Charger ».

## Format des fichiers CSV

- `players.csv` et `staff.csv` : `nom;prenom;licence`. La licence est facultative
  (case vide) ou peut être une date de naissance `JJ/MM/AAAA` à la place.
- `staff.csv` est utilisé pour choisir le Délégué de chaque équipe.

## Vie privée

**Ces deux fichiers contiennent les vrais noms et numéros de licence des
joueurs et de l'encadrement : ils ne sont jamais commités dans ce dépôt**
(voir `.gitignore`). Chaque coach charge sa propre liste depuis son
ordinateur ; le fichier n'est lu que dans le navigateur, il n'est jamais
envoyé nulle part. Les compositions d'équipe sont mémorisées uniquement
dans le navigateur de chaque coach (`localStorage`), sans synchronisation
entre appareils.

## Fonctionnement

Calé sur le modèle « Feuille de PLATEAU U9 » (Nom Prénom / N° Licence, 8 joueurs,
un Délégué par équipe) :

- Jusqu'à 5 équipes (A–E), 8 joueurs max chacune. Cliquer un joueur dans la liste
  de gauche l'ajoute à l'équipe affichée ; il faut le retirer avant de le mettre
  dans une autre équipe.
- Un nom d'équipe et un Délégué (choisi dans staff.csv) par équipe.
- « Vider cette équipe » / « Vider toutes les équipes » remettent à zéro.
- « Générer les tableaux » affiche un tableau par équipe ayant au moins un
  joueur, un nom ou un délégué, prêt à découper (deux par ligne, 3 mm d'écart).
  Chaque tableau fait 97 × 75,7 mm, comme sur le modèle.
