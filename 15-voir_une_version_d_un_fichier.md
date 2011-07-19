Voir une version particulière d'un fichier
==========================================

Il arrive qu'on veuille voir le contenu d'un fichier tel qu'il est/était dans une révision particulière (il y a 3 versions, dans une branche, avant de le modifier localement…).

Au lieu de faire un `git diff`, pénible à lire, ou un `git checkout` pour récupérer le fichier, vous pouvez juste l'afficher avec :

    git show <référence>:<fichier>

`<référence>` étant un identifiant de commit, de branche, de tag… et `<fichier>` le chemin (depuis la racine du dépôt) vers votre fichier.

Exemples
========

    #le fichier site/index.html avant que je le modifie localement
    git show HEAD:site/index.html
    #le fichier site/index.html il y a 5 révisions
    git show HEAD~5:site/index.html
    #le fichier site/index.html dans le commit '935fdf'
    git show 935fdf:site/index.html
    #le fichier site/index.html dans la branche 'stable'
    git show stable:site/index.html
    #…

