git grep
========

`git grep` permet de chercher dans votre dépôt, un peu comme le grep classique : 

    git grep pattern

Quelques options pratiques
--------------------------

 * `--cached` : pour chercher dans l'index
 * `-n` : pour afficher les numéros de lignes
 * `--name-only` : pour n'afficher que le nom des fichiers
 * `--open-files-in-pager <pager>` : pour ouvrir directement dans un pager (`less`, `vi`…) les fichiers correspondants, le curseur positionné à la première occurrence du pattern
 * `<tree>` : pour chercher sur un commit/branche/tag en particulier plutôt que sur la version courante

Chercher dans tout l'historique
-------------------------------

`git grep` ne permet pas de chercher dans tout l'historique mais comme on peut chercher dans un commit particulier, il est facile de contourner cette limite avec le shell : 

    git rev-list --all | while read revision; do
        git grep <option> <pattern> $revision                 
    done

Attention, c'est assez gourmand. `git rev-list` liste les commits du plus récent vers le plus vieux, donc on peut en général arrêter la recherche avec un CTRL-C quand on voit que ça stagne. Sinon, `git rev-list --max-count 50 --all` peut faire l'affaire.

