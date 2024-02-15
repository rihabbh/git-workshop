Qu'est ce que Git ?
=============

Git est un système *distribué* **de contrôle de version** [1]

[1] <a href="http://git-scm.com/about">http://git-scm.com/about</a>


Obtenir Git
-----------

Un peu de ménage ici. On suppose bien sûr que Git est installé,
(espérons-le \>= 1.7.0).

Si ce n'est pas le cas, vous pouvez l'installer à partir des téléchargements sur la page d'accueil de git ou vous pouvez
installez [l'interface graphique git de Github](https://help.github.com/articles/set-up-git/).


Installation
-----

La première chose à faire est de configurer votre identité. Cela vous identifie à
d'autres personnes qui téléchargent le projet.

    $ git config --global user.name "Your Name"
    $ git config --global user.email your.email@example.com

Commençons ce workshop
---------------------

1. Tout d'abord, clonez ce dépôt:

    - https://github.com/rihabbh/git-workshop

Vous souhaiterez peut-être créer votre propre copie du projet sur github et
clonez à partir de votre propre dépôt. Vous pouvez trouver le bouton fork en haut à droite de
l'écran sur un référentiel github, ou plus d'aide pour le faire [ici](https://help.github.com/articles/fork-a-repo/).

Une fois que vous avez cloné votre référentiel, vous devriez maintenant voir un répertoire
appelé `git-workshop`. Ceci est votre « répertoire de travail »

    $ dir git-workshop
    $ ls

Pour les curieux, vous devriez également voir le sous-répertoire `.git`. C'est
où sont conservés toutes les données et l’historique de votre référentiel.

     $ dir -a .git

Vous verrez :

            18 COMMIT_EDITMSG
            302 config
            73 description
            21 HEAD
    <DIR>   hooks
            217 index
    <DIR>   info
    <DIR>   logs
    <DIR>   objects
            112 packed-refs
    <DIR>   refs



The staging area
----------------

Maintenant, essayons d'ajouter quelques fichiers au projet. Créez quelques
des dossiers.

2. Créons deux fichiers nommés « file1.txt » et « file2.txt ».

Utilisons une analogie avec le courrier.

Dans Git, vous ajoutez d'abord du contenu à la « zone de transit » en utilisant « git add ».
C’est comme mettre les choses que vous souhaitez envoyer dans une boîte en carton.
Vous finalisez le processus et l'enregistrez dans l'index git en utilisant
`git commit`. C'est comme sceller la boîte : elle est maintenant prête à être envoyée.

3. Ajoutons les fichiers à la "staging area"

