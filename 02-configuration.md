#Configuration#

Pour sa configuration, git regarde à trois endroits : 

 1. `.git/config` : dans le dépôt courant. Ce sont vos réglages, qui ne s'appliquent qu'à ce projet.
 2. `~/.gitconfig` : dans votre `$HOME`. Ce sont vos réglages, globaux à tous vos projets
 3. `/etc/gitconfig` : dans votre système. Ce sont les réglages qui s'appliquent à tous les utilisateurs de votre machine.

La priorité de la configuration s'applique dans le même ordre : une option globale sera écrasée par une option spécifique à un dépôt.

##Régler une option##

Pour changer la valeur d'une option : `git config option valeur` :

    git config core.editor emacs #local au dépôt
    git config --global core.editor vim #global pour l'utilisateur
    git config --system core.editor nano #système

##Identité##

Avant de commiter pour la première fois, il est d'usage de configurer son identité. Chaque commit sera signé avec cette identité.

    git config --global user.name "Florian Cargoët"
    git config --global user.email fcargoet@docxa.com

##Éditeur##

Régulièrement git vous demandera de saisir du texte via un éditeur de texte. Par défaut, il prend l'éditeur par défaut du système.

Pour le changer : 

    git config --global core.editor vim

Maintenant, git lancera vim pour la saisie du message de commit.

##Quelles options ?##

`git help config` vous donnera une longue liste d'options existantes. 

 - les options `color.*` permettent de colorer l'affichage dans le terminal.
 - les options `alias.*` permettent de définir des noms alternatifs pour les commandes
 - `core.excludesfile` vous permet d'indiquer un fichier de type .gitignore pour exclure systématiquement certains fichiers

##Vérifier sa configuration##

    git config --list
    
Les valeurs peuvent apparaitre plusieurs fois (/etc/gitconfig, ~/.gitconfig…). La dernière occurence est celle prise en compte par git.

    git config options

donne la valeur d'une option en particulier.

