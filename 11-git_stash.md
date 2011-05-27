git stash
=========

Vous avez des changements non commités et vous voulez changer de branche. Que va t-il se passer pour vos changements si vous le faites ? 

Vos changements vont vous suivre et ce n'est pas forcément ce que vous voulez. Il suffit d'imaginer que vous développiez sur la branche _feature-A_ et qu'un bug critique soit à fixer sur _master_ avant que vous ayez fini et que votre code soit commitable. Vous n'avez certainement pas envie d'emmener ces changements avec vous sur _master_ !

`git stash` est là pour gérer ce genre de cas. Cette commande permet de mettre de coté vos changements afin de remettre votre _working tree_ sur le dernier commit.

git stash save 
--------------

`save` met vos changements de coté. Vous pouvez préciser un message pour distinguer votre `save` des précédents (car oui, vous pouvez `stash`-er plusieurs fois). Par défaut le message est `WIP on <branch_name>: <last_commit_info>`, par exemple `WIP on master: 115d851 fixed bug #43`.

    git stash save
    git stash save message
    git stash # par défaut, l'action est 'save'

git stash list
--------------

Pour lister tout ce que vous avez mis de coté :

    git stash list
    stash@{0}: WIP on master: 115d851 fixed bug #43
    stash@{1}: WIP on master: 115d851 fixed bug #43
    stash@{2}: WIP on master: 115d851 fixed bug #43

`stash@{0}` est l'id de votre stash, il servira à récupérer vos changements. On voit l'intérêt de personnaliser le message de stash quand on en stocke plusieurs.

git stash show
--------------

Pour savoir ce qui est stocké dans un stash en particulier : 

    git stash show stash@{1}
    index.html |    1 +
    1 files changed, 1 insertions(+), 0 deletions(-)

    git stash show -v stash@{1}
    diff --git a/index.html b/index.html
    index e69de29..c96852f 100644
    --- a/index.html
    +++ b/index.html
    @@ -0,0 +1 @@
    +<html>

git stash apply
---------------

Ça y est, vous avez mis de coté vos changements, vous avez changé de branche, corrigé le bug, commité, et vous êtes revenu sur votre branche de départ. Il est temps de ressortir les changements que vous aviez mis de coté !

    git stash apply stash@{0} # attention à l'échappement si nécessaire stash@\{0\}
    git stash apply # par défaut le dernier stocké

Et voilà, vos changements sont revenus !

git stash pop
-------------

`pop` est similaire à `apply` sauf qu'il prend forcément le dernier de la pile et le supprime de la liste dans la foulée. Avec `apply`, il faut supprimer à la main les stashes qui ne sont plus utiles avec `git stash drop stash_id`

Résumé
------

Les deux commandes les plus utiles : 

    git stash
    git stash pop
