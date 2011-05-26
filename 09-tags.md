Tags
====
Git intègre un système de tags, permettant de marquer certains commits.
Il existe deux types de tags : les tags légers et les tags annotés. 

Voir les tags
-------------
Avant de créer des tags, voici comment les lister :

    git tag
    v0.2
    v1.1.0
    v1.1.3
    v1.4

    git tag -l 'v1.1.*' # recherche par pattern
    v1.1.0
    v1.1.3


Créer un tag annoté
-------------------
Les tags annotés sont des objets à part entière dans git. Ils contiennent le tageur, son email, la date, un message et peuvent être signés (PGP).

    git tag -a v2.0 # un éditeur s'ouvre pour le message
    git tag -a v2.0 -m "message"

Pour signer, si vous avez une clé : 

    git tag -s v2.0 # -m "message" éventuellement

Pour visualiser toutes les infos d'un tag :

    git show v2.0
    tag v2.0
    Tagger: Florian Cargoët <florian.cargoet+github@centrale-marseille.fr>
    Date:   Wed May 25 15:27:44 2011 +0200
    
    Here is version 2.0!
    
    RELEASE NOTES:
     - stuff added
     - bugs fixed
    
    commit 8b869b1dd7fac6a2c590a85e9e2a37918a35aacd
    Author: Florian Cargoët <florian.cargoet+github@centrale-marseille.fr>
    Date:   Thu May 12 15:55:50 2011 +0200
    
        added yet another feature
    [...]


Créer un tag léger
------------------
Un tag léger est un simple _pointeur_ vers un commit. Il ne contient pas d'autres informations. Pas de tageur, pas de date, pas de message, rien.

    git tag v2.1

Quand on fait `git show`, il n'y a pas d'info de tag donc `git` montre juste le commit.

Taguer a posteriori
-------------------

Pour taguer un autre commit que le dernier, il suffit de le préciser :

    git tag -a v2.2 <SHA1>

Publier les tags
----------------
Par défaut, les tags ne sont pas publiés lors d'un `push`. Il faut les publier exactement comme des branches :

    git push <remote> <tagname>
    git push origin v2.0

Pour pousser tous les tags d'un coup :

    git push <remote> --tags
