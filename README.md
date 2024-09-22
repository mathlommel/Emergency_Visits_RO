# Emergency_Visits_RO
Implémentation d'algorithmes de Branch and Bound et modélisation en PLNE pour le problème de planification de visites aux urgences

Au sein d'une unité d'urgence médicale, un ensemble de patients est affecté à chaque médecin urgentiste. On souhaite alors ordonner les visites d'un médecin de sorte à faire attendre aussi peu que possible les patients le plus dans le besoin.

On note $I$ l'ensemble des patients affectés au médecin considéré. Pour chaque patient $i \in I$, une heure de visite au plus tard $H_i$, une pénalité de retard $P_i$ et une durée de visite $D_i$ sont déterminés en fonction des symptômes dont le patient souffre. Ainsi, si la visite du patient *i* démarre à un instant $t_i > H_i$, la pénalité de retard sera $P_i.(t_i-H_i)$, mais il n'y a pas de récompense si la visite commence avant $H_i$.

On suppose que le premier patient passe à l'instant t=0 et que le médecin ne prend pas de pause entre les patients. Le problème consiste à déterminer l'ordre de passage des patients afin de minimiser la somme des pénalités de retard. 

Dans le cadre de ce projet, on se propose de résoudre ce problème en implémentant 3 algorithmes de Branch and Bound, et une résolution par programmation linéaire.

- 1er Branch and Bound : Pour chaque noeud *i* de l'arbre, on crée un noeud fils pour chaque patient *j* non traité, que l'on traitera en positon *i*.
- 2nd Branch and Bound : On remarque que les pénalités interviennent majoritairement à la fin de l'arbre. On propose donc de réaliser la même règle de branchement, en partant de la fin (à chaque noeud *i* de l'arbre, on crée un noeud fils pour chaque patient *j* non traité, que l'on traitera en position *n-i*.
- 3e Branch and Bound : Ce dernier algorithme est plus général, et sera basé sur la relaxation de la modélisation en programme linéaire du problème.
- Et enfin, un programme linéaire sera créé, et résolu via un solver (ici la librairie JuMP de Julia sera utilisée).

Dans ce repository, on retrouve les 3 parties du notebook global du projet : l'écriture des algorithmes, les tests, et une dernière partie remettant en cause la modélisation mathématique du problème, soulevant certaines questions éthiques. 

Une version pdf du projet est aussi disponible (*notebook.pdf*).


## Contributors
Lucas OFFROY & Mathias LOMMEL

---------------------------------------
Recherche Opérationnelle

Département __Mathématiques Appliquées__

INSA Rennes, 2023-2024

