#Déplacer/renommer des fichiers#

Comme sous Unix déplacer et renommer, c'est pareil, ça se fait avec `mv`.

##git mv##
    git mv FiChIeR.tXt fichier.txt
    git status
    # On branch master
    # Changes to be committed:
    #   (use "git reset HEAD <file>..." to unstage)
    #
    #       renamed:    FiChIeR.tXt -> fichier.txt
    #

##Ce qui se passe vraiment##
En fait, git ne traque pas explicitement les mouvements de fichiers. Il n'y a pas de données dans le dépôt git qui précise qu'un fichier a été renommé mais git est suffisamment malin pour le deviner quand même.

    mv FiChIeR.tXt fichier.txt # mv unix, pas git mv
    git add fichier.txt
    git rm FiChIeR.tXt
    git status
    # On branch master
    # Changes to be committed:
    #   (use "git reset HEAD <file>..." to unstage)
    #
    #       renamed:    FiChIeR.tXt -> fichier.txt
    #

`git mv` ne fait pas de renommage, c'est simplement un raccourci pour éviter de taper 3 commandes. La bonne nouvelle, c'est que vous pouvez renommer vos fichiers avec n'importe quel outil (par ex. `rename`) et gérer le `add`/`rm` après, tout fonctionnera comme il faut.
