git push -u
===========

Quand on veut envoyer une branche locale sur un dépôt distant, il suffit de la pousser avec `git push <remote> <branch>`. Par exemple `git push origin feature-a`.

Par défaut, la branche locale ne suit pas la branche distante que l'on vient de créer. Il faudra donc préciser "`origin feature-a`" à chaque fois que l'on fera un `push` ou un `pull`. Pour éviter ça, on peut dire à git que la branche locale doit _suivre_ la branche distante.

Le plus simple est de le faire dès le premier push : 

    git push -u origin feature-a
    # alternative
    git push --set-upstream origin feature-a

Si on a oublié, on peut le faire après coup en ajoutant dans le fichier .git/config :
             
    [branch "feature-a"]
        remote = origin
        merge = refs/heads/feature-a

