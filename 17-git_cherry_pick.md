git cherry-pick
===============

`cherry-pick` permet de récupérer un commit sur une branche et de l'appliquer sur la branche courante.

Exemple
-------

 - Vous préparez une release sur une branche dédiée (par exemple `release-v2`). 
 - Votre branche de développement (`dev`) a bien avancé depuis la création de votre branche de release. 
 - `dev` contient un commit intéressant (une correction de bug par exemple) mais contient également des fonctionnalités que vous ne voulez pas livrer. 

Le `merge` n'est pas envisageable puisqu'on ne veut pas livrer les nouvelles fonctionnalités. Plutôt que de corriger le bug une seconde fois dans la branche `release-v2`, il est possible d'extraire uniquement le commit intéressant.

    # on identifie le commit intéressant
    $ git checkout dev
    $ git log --pretty=oneline --abbrev-commit
    f044867 some work in progress
    2c71e5f yet another feature
    e589930 fixed bug #42          <-- c'est celui là !
    8f73a66 added awesome feature
    # on l'applique sur release-v2
    $ git checkout release-v2
    $ git cherry-pick e589930

Bonus
-----
`man git-cherry-pick` donne quelques exemples intéressants avec du cherry picking de plusieurs commits à la fois.

    git cherry-pick ..master
    git cherry-pick master~4 master~2
    git rev-list --reverse master -- README | git cherry-pick -n --stdin


