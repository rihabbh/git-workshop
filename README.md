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


Committing
----------

4. Vous êtes maintenant prêt à vous engager. Le flag `-m` vous permet de saisir un message pour accompagner le commit en même temps.


Voyons ce qui vient de se passer
----------------------------

5. Nous devrions maintenant avoir un nouveau commit. Pour voir tous les commits jusqu'à présent, afficher les logs.


Le journal doit afficher tous les commits répertoriés du plus récent au moins
récent. Vous verriez diverses informations comme le nom de l'auteur,
la date à laquelle il a été validé, un numéro SHA de validation et le message pour le
commettre.

6. Vous devriez également voir dans votre commit le plus récent, où vous avez ajouté les deux nouveaux fichiers de la section précédente. Cependant, ces informations ne sont pas disponible avec git log qui n'affiche pas les fichiers impliqué dans chaque commit. Quel autre commande vous permet de le voir ?

Une digression nécessaire
----------------------

Dans cette section, nous allons ajouter d'autres modifications et essayer de récupérer des erreurs.

 Il nous faudra ajouter du contenu dans file1.txt.

Ouvrez « file1.txt » et saisissez "Hello world"

Puis **enregistrez** le fichier

Qu'avons-nous changé ? Une commande très utile est `git diff`. C'est très
utile pour voir exactement les modifications que vous avez apportées.

     $ git diff

Vous devriez voir quelque chose comme ce qui suit :

     diff --git a/file1.txt b/file2.txt
     indice e69de29..2aedcab 100644
     --- a/alice.txt
     +++ b/alice.txt
     @@ -0,0 +1 @@
     +Hello world



Staging area à nouveau
-------------------

7. Ajoutons maintenant notre fichier modifié, « file1.txt » à la staging area. 

8. Ensuite, vérifiez le `statut`  de « file1.txt ». Est-ce dans la staging area maintenant ?

Défaire
-------

Disons que nous ne sommes pas satisfait des modification apporté dans `file1.txt`. Un avantage de la staging area est de nous permettre de reculer avant un commit - ce qui est un peu plus difficile à retirer. Rappellez vous de l'analogie du courrier : il est plus facile de retirer le courrier de la boîte en carton avant scellez qu’après.

9. Retirez `file1.txt` de la staging area

10. Comparez le « git status » maintenant au git status du précédent
section. En quoi est-ce différent ?

11. Retirez les modifications effectuées dans `file1.txt` à l'aide de `git checkout`.

Branch
-------

La plupart des grandes bases de code ont au moins deux branches : une branche « main » et une branche « développement ». La branche main est un code qui peut être déployé sur un site Web ou téléchargé par les clients. La branche de développement permet aux développeurs de travailler sur des fonctionnalités qui pourraient ne pas être exemptes de bugs. Ce n'est que lorsque tout le monde sera satisfait de la branche de développement qu'elle sera fusionnée avec la branche main.

Créer une branche dans Git est simple. La commande `git branch`, lorsqu'elle est utilisée seule, listera les branches que vous avez actuellement

    $ git branch

Le  `*` devrait indiquer la branch sur laquelle nous sommes actuellement , qui `main`.

12. Créer une nouvelle branche, à partir de `main` que vous appelerez `dev`

13. Assurez vous que la branche a bien été créer et que vous êtes dessus. 

14. Créer un fichier text.txt et committez le dans la branch `dev`.

15. Utilisiez `git diff` pour comparer la branch `dev` à `main` . Noramlement le résultat affiché devrait précisee que « test.txt » est présent sur la branche  `dev`, mais est absent sur la branche `main`.


16. Git est assez performant pour gérer vos fichiers lorsque vous basculez entre les branches. Revenez à la branche « principale »

Essayez de revenir à la branche master (Indice : c'est la même commande que celle que nous avons utilisée pour passer à la branche dev ci-dessus)
Maintenant, où est notre fichier `test.txt` ?

    $ dir
    README.md  file1.txt   file2.txt     history.txt


Comme vous pouvez le constater, le nouveau fichier que vous avez créé dans l'autre branche a disparu. Ne vous inquiétez pas, il est rangé en toute sécurité et réapparaîtra lorsque vous reviendrez à cette branche.

Maintenant, revenez à la branche dev et vérifiez que le « test.txt » est
désormais présent.


Merge
-------

Nous essayons maintenant de fusionner les 2 branches. Idéalement, vous souhaiterez fusionner deux branches ensemble une fois le travail terminé.
`git merge` vous permet de faire cela.

La fusion Git fonctionne en basculant d'abord la branche dans laquelle vous souhaitez appliqué ces changements, puis en exécutant la commande pour fusionner l'autre branche.

17. Nous voulons maintenant fusionner notre branche `dev` dans `main`. Tout d’abord, passez à la branche `main`.

Vous devez être dans la branche dans laquelle vous souhaitez fusionner *dans* et ensuite vous spécifiez toujours la branche que vous souhaitez fusionner.

À ce stade, vous pouvez également essayer `gitk` pour visualiser les changements et comment les deux branches ont fusionné


Merge Conflicts
---------------


