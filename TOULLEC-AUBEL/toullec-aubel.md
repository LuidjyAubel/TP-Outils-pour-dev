Question 1 : code source du projet
====================

Le dossier `src` contient la classe Opération, une classe comprenant différentes fonctions permettant de réaliser des calculs mathématiques : additions, soustractions, multiplication, division ainsi qu'une fonction permettant de vérifier qu'un triplet de chiffre est un triplet pythagoricien.

Le dossier `test` contient deux classes. La classe `TestSimple` contient des tests vérifiant le bon fonctionnement de ses opérations. La classe `TestThrowable` contient des texts afin de vérifier la gestion des exeptions de ces opérations : respect des données en paramètres, cas de la division par 0.


Question 2 : commandes java
====================

| Commande | Fonction |
| -------- | -------- |
| `mkdir -p build/classes` | Permet de créer le repertoire `build/classes`
| `javac -sourcepath src -d build/classes src/com/rpouiller/Operations.java`  | Créé les classes à partir des fichiers java de `build/classes` dans le répertoire `src/com/rpouiller/Operations` |
| `echo "Main-Class: com.rpouiller.Operations" > monManifest` | Créé un fichier `monManifest` contenant le texte "Main-Class: com.rpouiller.Operations" |
| `mkdir build/jar` | Créé un répertoire `jar` dans le repertoire `build` |
| `jar cfm build/jar/Operations.jar monManifest -C build/classes .` | Génère l'archive jar des opétations dans `build/classes` |
| `java -jar build/jar/Operations.jar` | execute le fichier jar des Opérations |

Question 3 : un `build.xml` lisible et compréhensible
====================

[build.xml](./lp_od_ant/exercice/build.xml "lien vers le build.xml")

Question 4 : les propriétés
====================
Lorsqu'une même propriété est définie plusieur fois, c'est le paramètre précisé en ligne de commande qui sera retenu : `ant display_test -Dtest=DNOM`.

Les variables utilisées sont bien définies.

La documentation indique que java.class.path et baseDir, font parties des propriétés pré-définis dans ant.

Les propriétés permettant de connaitre la version de ant et de java utilisées sont respectivement : `ant.version` et `ant.java.version`.

Question 5 : généralisation du code à l'aide de propriétés
====================

Question 6 : spécification locale du classpath
====================

Question 7 : utilisation d’une bibliothèque externe
====================

**Une fois le code modifié, exécutez un `ant main`. Traduisez en français ce que signifie les messages que vous obtenez en console.**

Il y a deux erreurs liées à l'import :
Le package `org.apache.log4j` n'existe pas.

Et trois erreurs liées à l'utilisation du logger (symbole non reconnu).

**Puis modifiez les `classpath` des tâches qui en ont besoin. Quelles sont les cibles et les tâches concernées ?**

Les cibles concernées par la modification des classpath sont compile et run, les tâches concernées sont javac et java.

**Au final, les deux classpaths ainsi construits contiennent-ils la même chose ?**

Sans utiliser la copie on a un classpath contenant les librairies, avec la copie, on obtient un classpath contenant le fichier de conficuration du logger.

Question 8 : globalisation des classpath à l’aide de path
====================

Question 9: compilation des tests
====================

Le troisième test de la classe TestThrowable est éronné, la division de 10 par 5 n'est pas censée retourner une erreur.
En corrigeant l'erreur avec `expected!=ArithmeticException.class`, le code ne compile plus.

Question 10: Execution des tests
====================

Piste ? attribut `haltonerror` pour desactiver m'arrêt après erreur<br>
Probleme avec l'execution des tests affichage d'erreur même après l'ajout des dépendances dans les classpath

Question 12: Génération de la javadoc
====================

Il faut rajouter la dépendance de notre propriété `classpath` qui permet d'importer les bibliothèques nécessaires (log4j-api, log4j-core, log4j-1.2-api)

