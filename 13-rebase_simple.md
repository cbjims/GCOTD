Rebase simple
=============

`git rebase` est une commande puissante (et donc dangereuse). Ici, je ne présente qu'une des possibilités du `rebase`.

Avertissement
-------------
Le principe du `rebase` est de modifier l'historique. C'est tout à fait légitime de retravailler son historique local (pour réparer une erreur, pour linéariser l'historique…). Par contre, il ne faut **jamais** toucher à quelque chose qui a été publié (_push_). J'en ai déjà parlé pour `git commit --amend`, c'est également valable pour `git rebase`.

git rebase &lt;branch&gt;
-------------------------
Il y a deux façons dans git d'intégrer le travail effectué sur une branche dans une autre : 

 - `git merge <branch>`
 - `git rebase <branch>`

La version simple du `rebase` permet de prendre les commits de la branche courant et de les "rejouer" sur la branche cible. Au final, le HEAD de la branche est dans le même état que si on avait fait un `merge`. Ce sont les états intermédiaires qui sont différents.

Graphiquement, ça donne ça :


                              +------+
                              |master|
                              +--+---+
                                 |
                                 v
    +----+   +----+   +----+   +----+
    | C1 +-->| C2 +-->| C5 +-->| C6 |
    +----+   +--+-+   +----+   +----+
                |
                |     +----+   +----+
                +---->| C3 +-->| C4 |
                      +----+   +----+                  
                                 ^                     
                                 |                     
                            +----+----+  
                            |feature-a|                
                            +---------+                
                                                       
    git checkout feature-a
    git rebase master                   
                                                                    
                              +------+         +---------+          
                              |master|         |feature-a|          
                              +--+---+         +---+-----+          
                                 |                 |                
                                 v                 v                
    +----+   +----+   +----+   +----+   +----+   +----+ 
    | C1 +-->| C2 +-->| C5 +-->| C6 +-->| C3’+-->| C4’| 
    +----+   +--+-+   +----+   +----+   +----+   +----+ 



Les commits C3 et C4 sont recalculés comme s'ils avaient été écrits après C6. Ils deviennent donc différents (d'où la notation Cx’ sur le graphique ASCII). On voit maintenant que le merge des deux branches serait en _fast-forward_ (vu qu'il n'y a pas de divergence).

Quand l'utiliser
================
Sur le plan technique, c'est utilisable en remplacement des merges non fast-forward.

Dans la pratique, je ne pense pas que ce soit une bonne idée de masquer les vrais merges. Par "vrai merge", j'entends "quand il y a un conflit à résoudre". La résolution d'un conflit est un évènement intéressant puisque c'est l'occasion d'introduire des bugs… Aussi, je ne recommande pas l'utilisation de `rebase` dans ce cas.

Je le recommande dans le cas où les fichiers modifiés dans les deux branches ne sont pas les mêmes. Dans ce cas, les fichiers auraient réellement pu être modifiés les uns après les autres et avoir un historique linéaire est plus sympathique (plus facile à lire).

Pour le cas où les mêmes fichiers sont modifiés mais qu'il n'y pas de conflit (résolution automatique par `git`), c'est la zone grise, à vous de voir.

Exemple : mon workflow
======================
Version théorique
-----------------

    git fetch # récupération des changements sur le serveur
    # si fast-forwardable
    git merge origin/master
    # sinon je décide :
    # - de continuer à commiter dans mon coin
    # - de merger quand même (c'est ce que fait git pull)
    # - de rebaser mon boulot sur origin/master pour ne pas diverger
    git rebase origin/master

Quand vous faites un `git pull`, c'est exactement comme un `fetch` suivi d'un `merge`. Si vous regardez mes commits, il n'y a presque pas de commit de merge. C'est parce que je suis seul à bosser sur mes fichiers et qu'il n'y a pas de 'vrais merges' à faire. Je ne fais non jamais de `pull` mais des `fetch/merge` ou des `fetch/rebase`

Version réelle
--------------
Dans la pratique, c'est contraignant de faire un fetch, de regarder si c'est fast-forwardable et de merger si c'est le cas. C'est le boulot de pull mais je ne peux pas l'utiliser parce qu'il est possible que je veuille faire un rebase. C'est là qu'intervient l'option --ff-only.

    git pull --ff-only # récupération des changements sur le serveur et merge si fast-forwardable
    # ensuite je décide :
    # - de continuer à commiter dans mon coin
    # - de merger quand même (c'est ce que fait git pull)
    # - de rebaser mon boulot sur origin/master pour ne pas diverger
    git rebase origin/master

Et hop un petit alias pullff -> pull --ff-only.

Conclusion
==========
C'était long mais je préfère détailler comment je m'en sers exactement plutôt que de survoler la commande et de laisser des doutes.

Une dernière fois : on ne rebase pas des commits déjà publiés.

