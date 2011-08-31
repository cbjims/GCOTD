git remote prune
================

Rappel sur la suppression de branche
------------------------------------

###En local (_voir GCOTD 10_)

    git branch -d <branch>

###Sur le serveur (_voir GCOTD 12_) :

    git push origin :<branch>

###Chez les autres :

Pour une raison que  j'ignore encore, la suppression d'une branche sur le serveur ne fait rien sur le dépôt des autres. C'est‑à‑dire qu'ils auront toujours une branche `origin/<branch>` après avoir `pull/fetch` les changements. **C'est à chacun de nettoyer son dépôt**.

La commande pour supprimer localement les branches qui ont été supprimées du serveur par quelqu'un d'autre : 

    git remote prune <remote>

Si vous voulez simplement vérifier s'il y a des branches à supprimer, lancez la commande en mode "simulation" :

    git remote prune <remote> --dry-run

