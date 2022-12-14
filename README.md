# Jeu de Grundy 

***
Version Joueur contre Joueur ou Joueur contre IA.
***
### But du jeu : 
Si l'adversaire ne peut plus jouer, vous avez gagné.

### Règle du jeu : 
Le jeu se joue seul ou à 2.  
Il commence sur un plateau de n (vous décidez) allumettes alignées sur la même rangée.  
Le premier joueur peut alors décider de séparer un certain nombre d'allumettes de cette première rangée.  
/!\ Il faut au minimum déplacer 1 allumettes et il doit au minimum en rester 1 sur la rangée initiale.  
/!\ De plus, le joueur ne peut pas séparer un tas en 2 tas de tailles exactement similaires.  
Les allumettes séparées forment une nouvelle rangée qui pourra être séparée par la suite.  
Vous l'aurez donc compris, un t'as de 2 allumettes ne pourra plus être séparé car il enfreindrait la règle N°2.  
Lorsqu'il ne reste que des rangées de 1 ou 2 allumettes, le jeu est terminé.  

***
### Méthode suivie par l'IA: 

La stratégie gagnante se base sur l’état de la disposition mère. Il existe deux états différents : l’état gagnant et l’état perdant.  
Une disposition mère est dite perdante si pour le joueur qui joue il n’est possible que de perdre si le joueur en face ne fait pas d’erreur.  
On peut aussi déduire qu’une disposition mère est perdante si toutes les dispositions filles sont gagnantes.  
Une situation est gagnante si elle possède au moins une disposition fille perdante.  
Le but est donc de mettre l’adversaire dans une disposition perdante.  
Si la situation dans lequel est l’ordinateur est perdante, il joue de manière aléatoire en espérant que l’humain fera une erreur.  

**Exemple :**  
[2,2,2] est une situation perdante que le joueur à qui c’est le tour ne peut pas jouer.  
[3] est une situation gagnante car toutes ses décomposition au moins une de ses dispositions est perdante à savoir.  
[4] est une situation perdante car toutes ses décompositions sont gagnantes [3,1] et [1,3].  
On le sait car 3 est une situation gagnante (c.f. au-dessus) et 1 n’est pas jouable.  
L’algorithme de résolution est principalement basé sur une méthode estPerdant() qui prend en paramètre une disposition mère.   
Cette algorithme parcourt de manière récursive toutes les dispositions filles (parcours d’arbre en profondeur).  
Il remonte lorsqu'une disposition fille est perdante ou que toutes les dispositions filles sont gagnantes.

***
Projet réalisé dans le cadre d'une SAE (Semestre 1 IUT Vannes)

Note finale de 18,50.
