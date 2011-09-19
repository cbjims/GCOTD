push.default
============

Rappel sur git push
-------------------

Pour pousser une branche vers un serveur, la version complète de la commande est : 

    git push <remote> <local-branch>:<remote-branch>

On utilise beaucoup plus souvent la forme ultra-courte : 

    git push

Mais ce n'est pas équivalent !

`git push` est équivalent à `git push origin` qui pousse toutes les branches qui possèdent une branche correspondante sur `origin`. Si vous voulez uniquement pousser la branche courante, il faut utiliser la forme explicite : 

    git push <remote> <branch>

push.default
------------
On peut changer le comportement de `push` quand aucune référence de branche n'est précisée (formes courtes).

L'option s'appelle `push.default` et peut prendre les valeurs : 

 - `nothing` : ne rien pousser.
 - `matching` : pousser toutes les branches qui ont le même nom sur le serveur. C'est la valeur par défaut.
 - `upstream` : pousser la branche courante vers sa branche upstream.
 - `tracking` : synonyme déprécié pour `upstream` (depuis v1.7.4.2)
 - `current` : pousser la branche courante vers une branche de même nom.

`upstream|tracking` ne pousse que si la branche courante "suit" une branche distante. `current` pousse la branche courante, quitte à la créer sur le serveur.

Chez moi :

    git config --global push.default tracking

