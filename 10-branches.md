Branches
========

Les branches sont une fonctionnalité classique des VCS qui permet de gérer la divergence du code. Dans `git`, les branches sont très légères et très simples à utiliser, ce qui incite beaucoup à s'en servir. Pour bien comprendre la gestion des branches, je recommande la lecture du [chapitre 3 du livre Pro Git](http://progit.org/book/ch3-0.html).

Ici, je me contenterai de lister les commandes utiles sans expliquer leur fonctionnement ni les bonnes pratiques.

Créer une branche
-----------------

    git branch nom_de_la_branche # création
    git checkout nom_de_la_branche # se déplacer sur la branche

Deux en un :

    git checkout -b nom_de_la_branche

Supprimer une branche
---------------------

    git branch -d nom_de_la_branche

Lister les branches
----i--------------

    git branch # listing simple
    git branch -v # listing avec log du dernier commit

Fusionner deux branches
-----------------------

    git checkout branche_cible
    git merge branche_source

Si le code sur la branche cible n'a pas divergé depuis la création de la branche, le `merge` sera un _merge fast forward_ (pas de commit correspondant au `merge`). S'il y a divergence, `git` créera un commit de `merge`.

Pour empêcher le fast forward et forcer la création d'un commit de `merge` : 

    git merge --no-ff branche_source

Pour ne pas faire automatiquement le commit (pour changer le message par défaut, pour ajouter des modifications…) :

    git merge branche_source --no-commit

Résolution des conflits
-----------------------
Le merge n'est pas automatique s'il y a un conflit entre les deux branches. Il faut alors finir le merge manuellement puis commiter quand le conflit est résolu. Une possibilité à ce stade est d'utiliser un outil de merge (`meld` par exemple).

    git mergetool


