#Alias#

Marre de taper `git st` à la place de `git status` et que ça ne fonctionne pas ? Vous pourriez écrire un script pour ça, mais il y a plus simple…

Git possède son propre système d'alias, ce qui vous évitera l'écriture d'un petit script juste pour ça.

##Alias simples##
    git config --global alias.st status

Cette commande vous permet d'ajouter un alias `st` qui correspond à la commande `status`. Vous pouvez désormais taper `git st`

Evidemment, vous pouvez aussi gérer ça dans votre fichier de configuration git :

    [alias]
        st = status

Les alias gèrent les arguments donc vous pouvez parfaitement taper `git ci -m "message"` si vous avez un alias `ci = commit`
##Alias avancés##

Vous pouvez également appeler des commandes non git en les préfixant d'un point d'exclamation.

    [alias]
        example = !command

Vous pouvez également jouer avec `sh` pour changer l'ordre des arguments mais là, ça n'a plus grand chose à voir avec git.

    [alias]
        example = !sh -c 'ls $1 $0'

Vous pouvez également utiliser les alias avec `!` pour appeler des commandes git et les traiter derrière :

    [alias]
        aliases = !git config --get-regexp 'alias.*' | colrm 1 6 | sed 's/[ ]/ = /'

Voilà un alias qui liste vos alias ;-)

##Bonus##

Quelques alias relatifs aux derniers GCOTD :

    [alias]
        fix = commit --amend
        unstage = reset HEAD --
        

