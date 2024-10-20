# Union-find
L'algorithme Union-Find, également connu sous le nom de Disjoint Set Union
(DSU) ou Union-Find Structure, est une structure de données qui permet
de gérer un ensemble d'éléments partitionnés en sous-ensembles disjoints.
En effet, un ensemble disjoint est un ensemble d'éléments qui ne se chevauchent
pas.
Par exemple, soit $A$ et $B$ les ensembles constitués d'entiers comme suit :

- $A = \{1, 2, 3\}$
- $B = \{4, 5\}$

Ces ensembles sont disjoints car ils n'ont aucun élément en commun.

Union-find implémente deux opérations principales :

- **Union** : pour fusionner deux ensembles en un;
- **Find** : pour trouver le représentant (ou racine) de l'ensemble auquel
un élément appartient.

### Représentation
Imaginons que nous ayons un ensemble d'éléments numérotés de 0 à n-1.
Chaque sous-ensemble est représenté par l'un de ses éléments,
appelé "représentant" ou "parent".
