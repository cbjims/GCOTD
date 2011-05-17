
#Commiter#

Le commit avec Git est différent du commit avec SVN

##Comparaison rapide##
###SVN###
Premier ajout d'un fichier :

 1. `svn add fichier`
 2. `svn commit`

Ensuite pour chaque modification :

 1. `svn commit`

###Git###
Premier ajout d'un fichier :

 1. `git add fichier`
 2. `git commit`
 3. `git push #si on veut pousser vers un serveur`

Ensuite pour chaque modification :

 1. `git add fichier`
 2. `git commit`
 3. `git push #si on veut pousser vers un serveur`

On peut prendre un raccourci :

 1. `git commit -a # commitera tous les fichiers modifiés et déjà sous contrôle de version (comme SVN)`
 2. `git push #si on veut pousser vers un serveur`

##Explications##

Git fonctionne différemment : entre la copie de travail et le dépôt, il y a la _staging area_ (aussi appelée l'_index_).

`git add` ajoute un fichier dans l'index tandis que `git commit` commit l'index (et pas la copie de travail).

Cela permet de ne pas tout commiter d'un coup si vous avez corrigé deux bugs sans commiter entre les deux : 

    git add fichier1 fichier2
    git commit -m "fixes bug 125"
    git add fichier3
    git commit -m "fixes bug 129"
    
On peut également n'ajouter à l'index qu'une fraction des modifications d'un fichier (`git add -p`)

En gros, vous pouvez penser à l'index comme une zone de _préparation de commit_.

##Bonus##

 - Pour savoir ce qui sera commité : `git status`
 - Pour retirer un fichier de l'index : `git rm --cached fichier`
 - Pour plus d'infos : http://progit.org/book/ch2-2.html
