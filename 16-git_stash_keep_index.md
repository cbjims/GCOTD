git stash --keep-index
======================

git stash
---------
Voir [GCOTD #11](https://github.com/floriancargoet/GCOTD/blob/master/11-git_stash.md) pour un rappel.

--keep-index
------------

L'option `--keep-index` permet de ne `stasher` que les modifications non ajoutées à l'index (avec `git add`).

Il est probable que vous ne commitiez pas systématiquement toutes vos modifications. Le risque, c'est de commiter quelque chose qui ne fonctionne pas. Avec `git stash --keep-index`, vous pouvez facilement "tester votre commit" avant de le faire.

    # ... modification de foo et bar ...
    $ git add foo                  # ajout de foo uniquement
    $ git stash save --keep-index  # mettre tout le reste de côté
    # ... tester sans bar ...
    $ git commit -m 'juste foo'    # commiter un truc bien testé
    $ git stash pop                # ré-appliquer les changements


