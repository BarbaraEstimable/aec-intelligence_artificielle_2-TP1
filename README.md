# Plus Court Chemin entre Villes

## Tables des matières

- [Contexte](#-contexte)
- [Fonctionnalités](#-fonctionnalités)
- [Technologies utilisées](#-technologies-utilisées)
- [Installation](#-installation)
- [Le fonctionnement](#-Le-fonctionnement)

---
## Contexte

On souhaite modéliser un réseau routier entre 8 villes nord-américaines sous la forme d’un graphe orienté pondéré. Chaque ville est un noeud, chaque route entre deux villes est un arc orienté dont le poids représente la distance en kilomètres. Comme le graphe est orienté, la route Montréal → Toronto et la route Toronto → Montréal peuvent avoir des distances différentes, ou ne pas exister toutes les deux.
L’objectif est de trouver le plus court chemin entre une ville de départ et une ville d’arrivée, en utilisant les algorithmes de plus court chemin, puis de comparer leurs performances sur le trajet **Québec → Buffalo**.  
Les algorithmes que j'ai choisi sont Dijkstra et A*.

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
- Nous travaillerons avec un graphe orienté pondéré (le poids d’un arc représente une distance en km entre deux villes)

- Une Ville est un objet possédant un nom et des coordonnées géographiques (x, y) utilisées pour le calcul de l’heuristique de A*

- Un Arc est orienté : si une route Montréal → Toronto existe avec un poids donné, cela ne signifie pas que Toronto → Montréal existe avec le même poids

- Le jeu de données est entièrement fourni : vous n’avez pas à inventer les villes, coordonnées ou distances

- Une implémentation graphique devra être réalisée : visualisation du graphe avec les arcs fléchés, les poids, et le chemin solution mis en évidence. (Utilisation de la   librairie de votre choix, Graphviz ou Matplotlib ou autre)

- Implémenter au moins 2 algorithmes parmi : Dijkstra, A*, Bellman- Ford

- Heuristique de A* : Distance Euclidienne entre les coordonnées (x, y) des villes

- Choisir au moins 3 métriques pertinentes : nombre de noeuds explorés, coût total du chemin (km), temps d’exécution, …

- Une analyse des résultats est attendue : discuter des différences de performance entre les algorithmes, et expliquer dans quels cas chacun est préférable

---
## Fonctionnalités

- **Modélisation du graphe** avec des classes `Ville` (nom et coordonnées x, y) et `Arc` (origine, destination, distance).
- **Algorithmes de plus court chemin** : Dijkstra, A* 
- **Heuristique de A\*** : distance euclidienne entre les coordonnées des villes.
- **Mesure des performances** de chaque algorithme, affichées dans la console : nombre de nœuds explorés, coût total du chemin (km) et temps d'exécution.
- **Visualisation du graphe** avec arcs fléchés, poids affichés et chemin solution mis en évidence.
- **Analyse comparative** des algorithmes sur le trajet Québec → Buffalo.

---
## Technologies utilisées

| Technologie | Utilisation |
|-------------|-------------|
| **Python 3** | Langage principal |
| **Jupyter Notebook** | Format de remise du code |
| **heapq** | File de priorité pour Dijkstra et A* |
| **math** | Calcul de la distance euclidienne (heuristique) |
| **time** | Mesure du temps d'exécution |
| **Matplotlib** | Visualisation du graphe |
| **Git / GitHub** | Versionnement du code |

---
## Installations

```bash
git clone https://github.com/BarbaraEstimable/IA2_projet1.git
cd IA2_projet1
pip install jupyter matplotlib
jupyter notebook Projet1.ipynb
```

---
## Le fonctionnement

---
