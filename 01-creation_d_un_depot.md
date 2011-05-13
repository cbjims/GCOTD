#Création d'un dépôt#

Aujourd'hui, on va voir deux façons de créer un dépôt :

 * Soit vous voulez forker un dépôt existant, on utilisera `git clone`
 * Soit vous voulez créer un _nouveau dépôt vide_, on utilisera `git init`

##git clone##

Le dépôt existe (sur github, gitorious, votre serveur public…) et vous avez son adresse (http, git ou ssh) :

    git clone git://github.com/floriancargoet/Workflow-demonstration.git
    cd Workflow-demonstration
    #now you can code

##git init##

Vous n'êtes pas un copieur et vous voulez créer un dépôt vide :

    mkdir MyRepository
    cd MyRepository
    git init
    #now you can code

Maintenant vous pouvez coder.
