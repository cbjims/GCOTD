Voir l'historique
=================

Pour regarder l'historique d'un dépôt, c'est très simple :

    git log

`git log` possède de nombreuses options. Voici les plus utiles :

    git log <PATH> # affiche l'historique pour le chemin spécifié
    git log -p # affiche un diff pour chaque commit
    git log -3 # se limite aux 3 derniers commits (-N pour les N derniers)
    git log --stat # affiche quels fichiers sont impactés
     [...]
     README         |    7 +++++++
     my-software.sh |    3 +++
     2 files changed, 10 insertions(+), 0 deletions(-)

git log --pretty=format
-----------------------

L'option `--pretty` est suffisamment riche pour y consacrer un paragraphe entier.

Avec un format prédéfini :

    git log --pretty=oneline
    8b869b1dd7fac6a2c590a85e9e2a37918a35aacd added yet another feature
    8b83e9401943bb246287bb6e449d867caf6ddeaf fixes bug #1
    681ad51f3b85fdd6a792013f8f329f9d147d7506 added a french version and a new feature (renaming)

Les autres formats prédéfinis (mais moins utiles que `oneline`) : `email`, `full`, `fuller`, `medium`, `raw`, `short`.

Avec un format personnalisé :

    git log --pretty=format:"%h - %an, %ar : %s"
    8b869b1 - Florian Cargoët, 12 days ago : added yet another feature
    8b83e94 - Florian Cargoët, 13 days ago : fixes bug #1
    681ad51 - Florian Cargoët, 13 days ago : added a french version and a new feature (renaming)

Parmi les nombreux formats disponibles (liste extraite du livre Pro Git) :

    Option	Description of Output
    %H	Commit hash
    %h	Abbreviated commit hash
    %T	Tree hash
    %t	Abbreviated tree hash
    %P	Parent hashes
    %p	Abbreviated parent hashes
    %an	Author name
    %ae	Author e-mail
    %ad	Author date (format respects the --date= option)
    %ar	Author date, relative
    %cn	Committer name
    %ce	Committer email
    %cd	Committer date
    %cr	Committer date, relative
    %s	Subject
    

Bonus
-----

 - `--graph` pour représenter les branches
 - `--abbrev-commit` pour un SHA1 réduit
 - `--relative-date` pour des dates du style "13 days ago"
 - `--since` pour faire des trucs du genre `git log --since "3 weeks"` !
