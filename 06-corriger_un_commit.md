#Corriger un commit#

Vous avez fini votre petit bout de code, vous êtes content, vous commitez et… #!@%!! vous avez oublié d'ajouter un nouveau fichier ! Ou alors vous avez fait une terrible faute dans votre message de commit… Si vous ne l'avez pas encore `push`-é, il est tout à fait possible de corriger cela !

##git commit --amend##

Juste après votre commit, faites vos corrections (édition, `git add`, `git reset HEAD fichier`…) puis :

    git commit --amend

Votre éditeur de commit s'ouvrira (comme d'habitude) mais le message de commit sera pré-rempli avec le précédent. Vous pouvez alors corriger/compléter le message et terminer votre commit.

Le mauvais commit sera remplacé par le tout nouveau tout beau. Comme cette opération modifie l'historique, il faut éviter de l'utiliser sur un commit que vous venez de publier (`push`).

##Bonus##

Avec `--amend`, vous pouvez utiliser `--reset-author`. Cela sert à supprimer les informations de l'auteur du commit et à les remplacer par les vôtres. C'est utile quand les options `user.name` et `user.email` étaient mal configurées.
