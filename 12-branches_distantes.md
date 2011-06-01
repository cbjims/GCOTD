Branches distantes
==================

Votre dépôt git peut être lié à d'autres dépôts, soit parce que votre dépôt est un clone, soit parce que vous avez ajouté manuellement des dépôts distants ( `git remote add` ). Ces dépôts ont des branches et nous allons voir ce qu'il est possible de faire avec.

Dans votre dépôt local, les branches distantes (de la forme `<remote>/<branch>`, par exemple `origin/master`) indiquent dans quel état sont les branches de vos dépôts distants. Vous ne pouvez pas manipuler directement ces branches. Elles sont automatiquement modifiées lorsqu'il y a un échange entre votre dépôt et le dépôt distant. Par exemple, `origin/master` pointe (localement) vers le commit vers lequel pointait la branche `master` sur le dépôt `origin` la dernière fois que vous avez communiqué avec cette branche (`push`, `pull`, `fetch`).

Si c'est un peu flou pour vous, les [illustrations du livre Pro Git](http://progit.org/book/ch3-5.html) pourront vous aider à éclaircir tout ça.

git fetch
---------

Pour récupérer les changements effectués sur le dépôt distant, faites :

    git fetch <remote> # ex : git fetch origin

Cette commande récupérera toutes les données que vous n'avez pas encore, et mettra à jour vos _pointeurs_ `origin/<branch>`. Les outils graphiques (comme `gitk`) permettent de visualiser facilement les branches locales et distantes. Ainsi, on voit si on est en avance sur la branche distante (il faut faire un `push`) ou en retard (il faut faire un `merge` ou un `rebase`).

git push
--------

`push` vous permet d'envoyer vos changements locaux sur un dépôt distant.

    git push <remote> <localbranch>:<remotebranch>
    git push <remote> <branch> # même nom de branche

git pull
--------

`pull` est en fait la combinaison d'un `fetch` et d'un `merge`.

Si vous ne voulez pas merger automatiquement la branche distante dans votre branche locale, faites manuellement le `fetch` puis décidez si vous mergez ou rebasez par exemple.

Branches suivies
----------------

Si votre branche _suit_ la branche distante, `git` sait quels `<remote>` et `<branch>` utiliser et un `git push` suffit. Par exemple, lors d'un clone, la branche `master` _suit_ automatiquement la branche `origin/master`.

Pour créer une branche locale qui suit une branche distante :

    git checkout --track origin/feature-A
    Branch feature-A set up to track remote branch refs/remotes/origin/feature-A.
    Switched to a new branch "feature-A"

Supprimer une branche distante
------------------------------

La syntaxe pour supprimer une branche est curieuse. Il s'agit en fait de `push`-er _rien_ vers la branche distante.

    git push <remote> :<branch>

On reconnait la commande `push` complète : `git push <remote> <localbranch>:<remotebranch>` avec _rien_ comme branche locale.