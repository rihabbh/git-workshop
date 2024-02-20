Partie II
======================


Nous avons commencé à collecter des anecdotes sur les voitures, le seul problème est que certaines d'entre elles sont impossibles à vérifier !

Nous devrons nous débarrasser des commits qui ajoutent ces histoires. Pour ce faire, nous allons essayer quelques options différentes.

Les commits
-----------
Il y a plusieurs commits dans l'ordre, nous avons été prudents et n'avons ajouté qu'une seule anecdote à la fois à notre timeline. Malheureusement, l'anecdote n°2 n'est pas vérifiable, donc nous allons devoir nous en débarrasser. 

La méthode par défaut
-------------------
1. Supprimez l'histoire du fichier.
2. Effectuez un nouveau commit.

C'est bien mais...
-------------------
Parfois, ce n'est pas pratique, comme s'il y avait un commit avec des milliers de changements. Dans ce cas, nous devrons savoir comment amener Git à faire le sale boulot.

Nous devrons d’abord découvrir quel commit a ajouté l’anecdote, puis nous devrons annuler ou supprimer ce commit d’une manière ou d’une autre.

Nous allons essayer différentes manières, avant d'essayer chaque méthode, créer une nouvelle branche (par exemple, `git checkout -b revert_1`) afin de pouvoir revenir à cet exemple plus tard.


La méthode Revert
-----------------
1. Trouvez le commit qui a ajouté l'anecdote 2.
2. Utilisez `git revert <commithash>` pour annuler le commit
3. Votre retour va provoquer un conflit de fusion puisque le fichier a été modifié au même endroit depuis que nous avons écrit l'histoire de George Gamow. Résolvez ce conflit comme dans le didacticiel de fusion.
4. Pour voir vos options, exécutez `git status`. Fondamentalement, vous pouvez soit abandonner, soit continuer.
5. Après avoir résolu le conflit, exécutez `git add <file>` pour indiquer à git la modification à apporter, puis exécutez `git revert --continue` pour appliquer la validation de restauration.
6. Nous avons terminé ! Mais nous avons également un commit de plus dans notre historique et nous avons dû effectuer un travail manuel. Si nous travaillons sur une branche que nous n'avons partagée avec personne d'autre, nous pouvons nettoyer notre historique/masquer notre erreur.

La méthode cherry-pick
----------------------
1. Obtenez une liste des commits après le commit de l'anecdote n°2, ce sont les commits que nous allons sélectionner
2. Recherchez le commit qui est le parent du commit de l'anecdote n°2.
3. Créez une nouvelle branche basée sur ce commit de départ, vous pouvez le faire en extrayant le commit puis en extrayant une nouvelle branche.
4. Choisissez chaque commit de votre liste dans l'ordre dans lequel vous souhaitez qu'ils apparaissent
5. Nous avons terminé ! Mais c'était beaucoup de travail...

La méthode de Rebase Interactive
-----------------------------
Il s’agit de la méthode la plus complexe mais la plus puissante. Vous souhaiterez peut-être la répéter plusieurs fois et essayer toutes les options qu’elle vous propose. La méthode de base est la suivante :

1. Comme précédemment, nous devons trouver le commit qui est le parent du commit de l'anecdote n°2.
2. Exécutez `git rebase --interactive <commithash>`
3. Vous allez obtenir une liste de commits, ce sont les commits qui vont être appliqués séquentiellement au sha de base.
4. Supprimez la ligne contenant le commit de l'anecdote n°2.
5. Enregistrez et quittez. Les commits doivent s’appliquer dans l’ordre.


Bravo!
---------
Jetez un œil à votre `git reflog` et essayez de retracer toutes les modifications que vous avez apportées.
