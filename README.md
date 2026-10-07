# Plus Court Chemin entre Villes

## Tables des matières

- [Contexte](#-contexte)
- [Fonctionnalités](#-fonctionnalités)
- [Technologies utilisées](#-technologies-utilisées)
- [Installation](#-installation)
- [Le fonctionnement](#-Le-fonctionnement)

---
## Contexte

On souhaite modéliser un réseau routier entre 8 villes nord-américaines sous la forme d'un graphe orienté pondéré. Chaque ville est un nœud, chaque route entre deux villes est un arc orienté dont le poids représente la distance en kilomètres. Comme le graphe est orienté, la route Montréal → Toronto et la route Toronto → Montréal peuvent avoir des distances différentes, ou ne pas exister toutes les deux.
 
L'objectif est de trouver le plus court chemin entre une ville de départ et une ville d'arrivée, en utilisant des algorithmes de plus court chemin, puis de comparer leurs performances sur le trajet **Québec → Buffalo**.
 
Les algorithmes que j'ai choisis sont **Dijkstra** et **A\***.

### Les données:

#### Villes

| Ville | x | y |
|-------|------:|-------:|
| Montréal | 45.30 | -73.35 |
| Québec | 46.81 | -71.21 |
| Ottawa | 45.42 | -75.70 |
| Toronto | 43.65 | -79.38 |
| Buffalo | 42.89 | -78.87 |
| Boston | 42.36 | -71.06 |
| New York | 40.71 | -74.01 |
| Chicago | 41.88 | -87.63 |

#### Routes (arcs orientés)

| Origine | Destination | Distance (km) |
|---------|-------------|--------------:|
| Montréal | Québec | 250 |
| Montréal | Ottawa | 200 |
| Montréal | Boston | 435 |
| Montréal | New York | 595 |
| Québec | Montréal | 255 |
| Québec | Boston | 650 |
| Ottawa | Montréal | 195 |
| Ottawa | Toronto | 450 |
| Toronto | Ottawa | 445 |
| Toronto | Buffalo | 155 |
| Toronto | Chicago | 840 |
| Buffalo | Toronto | 160 |
| Buffalo | New York | 590 |
| Buffalo | Boston | 700 |
| Buffalo | Chicago | 860 |
| Boston | New York | 345 |
| Boston | Montréal | 440 |
| Boston | Buffalo | 695 |
| New York | Boston | 350 |
| New York | Buffalo | 585 |
| New York | Chicago | 1 270 |
| Chicago | Toronto | 835 |
| Chicago | Buffalo | 855 |
| Chicago | New York | 1 275 |

### Directives

- Nous travaillerons avec un graphe orienté pondéré (le poids d'un arc représente une distance en km entre deux villes).
- Une Ville est un objet possédant un nom et des coordonnées géographiques (x, y) utilisées pour le calcul de l'heuristique de A*.
- Un Arc est orienté : si une route Montréal → Toronto existe avec un poids donné, cela ne signifie pas que Toronto → Montréal existe avec le même poids.
- Le jeu de données est entièrement fourni : vous n'avez pas à inventer les villes, coordonnées ou distances.
- Une implémentation graphique devra être réalisée : visualisation du graphe avec les arcs fléchés, les poids, et le chemin solution mis en évidence (Graphviz, Matplotlib ou autre).
- Implémenter au moins 2 algorithmes parmi : Dijkstra, A*, Bellman-Ford.
- Heuristique de A* : distance euclidienne entre les coordonnées (x, y) des villes.
- Choisir au moins 3 métriques pertinentes : nombre de nœuds explorés, coût total du chemin (km), temps d'exécution, …
- Une analyse des résultats est attendue : discuter des différences de performance entre les algorithmes, et expliquer dans quels cas chacun est préférable.

---

## Fonctionnalités

- **Modélisation du graphe** avec une classe `Ville` (nom et coordonnées x, y) et une classe `Graphe` qui stocke les arcs orientés dans une liste d'adjacence.
- **Algorithmes de plus court chemin** : Dijkstra et A*, tous deux avec une file de priorité (`heapq`).
- **Heuristique de A\*** : distance euclidienne entre les coordonnées des villes.
- **Reconstruction du chemin** à partir des prédécesseurs de chaque ville.
- **Mesure des performances** de chaque algorithme, affichées dans la console sous forme de tableau : distance totale (km), nombre de nœuds explorés et temps d'exécution (ms).
- **Visualisation du graphe** avec Graphviz : arcs fléchés, poids affichés et chemin solution mis en évidence en vert.
- **Analyse comparative** des deux algorithmes sur le trajet Québec → Buffalo.

---

## Technologies utilisées

| Technologie | Utilisation |
|-------------|-------------|
| **Python ** | Langage principal |
| **Jupyter Notebook / Google Colab** | Développement et exécution du code |
| **heapq** | File de priorité pour Dijkstra et A* |
| **math** | Calcul de la distance euclidienne (heuristique) |
| **time** | Mesure du temps d'exécution  (`time.perf_counter()`) |
| **Graphviz** | Visualisation du graphe orienté |
| **IPython.display** | Affichage de l'image du graphe dans le notebook |
| **Git / GitHub** | Versionnement du code |

---

## Installations

Ouvrir le notebook avec le bouton **Open in Colab**, puis exécuter toutes les cellules dans l'ordre (*Exécution → Tout exécuter*). La cellule d'importation installe Graphviz automatiquement.

---

## Le fonctionnement

Le notebook est organisé en étapes :
 
1. **Données fournies** : les dictionnaires `VILLES` et `ROUTES` de l'énoncé.
2. **Importations** : `heapq`, `time`, `math` et `graphviz`.
3. **Les classes** :
   - `Ville` stocke le nom et les coordonnées (x, y) d'une ville.
   - `Graphe` contient la liste d'adjacence et les villes, avec les méthodes `ajoute_ville`, `ajoute_arc`, `voisins` et `sont_voisins`.
   - `construction_graphe()` crée le graphe à partir des données.
4. **Reconstruction du chemin** : `remonte_chemin()` part de la ville d'arrivée et remonte les prédécesseurs jusqu'au départ.
5. **Dijkstra** : explore toujours la ville la plus proche du départ jusqu'à atteindre l'arrivée.
6. **A\*** : utilise le coût réel depuis le départ (g) plus l'heuristique euclidienne vers l'arrivée (h) pour choisir la prochaine ville à explorer (f = g + h).
7. **Visualisation** : `visualiser_graphe()` génère le graphe avec Graphviz et met en vert les arcs du chemin optimal.
8. **Comparaison** : `comparer()` exécute les deux algorithmes sur Québec → Buffalo et affiche le tableau des métriques.

---
## Le Résultat
### Trajet Québec → Buffalo
 
**Chemin optimal :** Québec → Montréal → Ottawa → Toronto → Buffalo
**Distance totale :** 1 060 km
 
| Métrique | A* | Dijkstra |
|----------|---:|---------:|
| Distance (km) | 1 060 | 1 060 |
| Nœuds explorés | 7 | 7 |
| Temps (ms) | 0,0686 | 0,0186 |
 
> Les temps d'exécution varient légèrement à chaque exécution.
 
### Visualisation
 
<img width="800" height="194" alt="image" src="https://github.com/user-attachments/assets/333efbd1-0016-47aa-a91a-946741358f75" />

 
Les arcs en **vert** forment le chemin optimal ; les arcs en **rouge** sont les autres routes du réseau.
 
### Analyse

**Les différences de performance entre les algorithmes**

Tous les deux algorithmes ont la même distance de 1060 km et le même nombre de nœuds explorés de 7. La différence que je remarque est dans le temps en ms : Dijkstra a un temps de 0.0186 ms, ce qui est plus rapide comparativement à A* qui lui a un temps de 0.0686 ms.

Je m'attendais à ce que A* soit plus rapide parce qu'il utilise l'heuristique euclidienne pour orienter sa recherche. Mais ici, les deux explorent le même nombre de nœuds, donc l'heuristique ne fait pas gagner de nœuds à A*. En plus, A* doit calculer l'heuristique pour chaque voisin, ce qui ajoute du travail et ça se voit dans le temps en ms.

Une raison pour ça, c'est que les coordonnées sont en degrés alors que les distances sont en km. Par exemple, l'heuristique entre Québec et Buffalo donne environ 8.6, alors que le vrai chemin est de 1060 km. L'heuristique est tellement petite comparativement aux distances qu'elle n'oriente presque pas la recherche, et A* se comporte comme Dijkstra.

Le graphe est aussi petit avec seulement 8 villes, donc les temps sont très proches et peuvent changer un peu à chaque exécution.

**Dans quels cas chacun est préférable**

A* est préférable lorsqu'il y a beaucoup de nœuds et une bonne heuristique, parce qu'il oriente sa recherche vers la destination comparativement à Dijkstra. Avec une heuristique dans la même unité que les distances, il pourrait explorer moins de nœuds.

Dans le cas de Dijkstra, les poids doivent être toujours positifs et il va explorer plusieurs nœuds sans connaître sa destination, il opère à l'aveuglette. Par contre, il n'a pas besoin d'heuristique, donc il est préférable pour un petit graphe comme celui-ci, ou quand on n'a pas de coordonnées pour les villes.

---
