
#Ignorer des fichiers#

Pour que certains fichiers (sauvegardes, logs, …) soient ignorés par git, vous pouvez créer un fichier contenant une liste de _patterns_ qui correspondent aux fichiers à ignorer.

## Fichier de patterns##
Ce fichier est cherché à plusieurs endroits, dans cet ordre : 

 1. `.gitignore` dans le même dossier que les fichiers à ignorer ou dans un dossier parent. Ces fichiers sont en général versionnés.
 2. `.git/info/exclude` dans le dépôt git. Ce fichier est propre à votre clone, il n'est pas versionné.
 3. le fichier spécifié par l'option `core.excludesfile` dans votre configuration.

##Syntaxe##

 - Un pattern par ligne
 - Syntaxe _glob pattern_
 - un `/` final définit un dossier
 - `!` permet d'inverser un pattern
 - Plus de détails : `man gitignore`

Exemple ([source][1]) :

    # a comment - this is ignored
    *.a       # no .a files
    !lib.a    # but do track lib.a, even though you're ignoring .a files above
    /TODO     # only ignore the root TODO file, not subdir/TODO
    build/    # ignore all files in the build/ directory
    doc/*.txt # ignore doc/notes.txt, but not doc/server/arch.txt


  [1]: http://progit.org/book/ch2-2.html#ignoring_files

##Bonus##
Les fichiers versionnés ne sont pas concernés par gitignore. Si un fichier est versionné mais que vous voulez l'ignorer maintenant, vous pouvez le déversionner sans le supprimer de votre copie de travail avec `git rm --cached fichier`
