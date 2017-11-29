---
title: 'Mise en route avec F # dans le Code de Visual Studio avec Ionide'
description: "Découvrez comment utiliser F # avec Code Visual Studio et la suite de plug-in Ionide."
keywords: 'Visual f #, f #, fonctionnelle de programmation, .NET, Visual Studio Code, vscode, Ionide'
author: cartermp
ms.author: phcart
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 49775139-082e-442f-b5a2-dd402399b5d2
ms.openlocfilehash: 336316eaf474f4c10d63657f178ce4a336ad7a54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="getting-started-with-f-in-visual-studio-code-with-ionide"></a>Mise en route avec F # dans le Code de Visual Studio avec Ionide

Vous pouvez écrire F # dans [Visual Studio Code](https://code.visualstudio.com) avec la [plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), afin d’obtenir une expérience d’IDE inter-plateformes et léger optimale avec IntelliSense et refactorisations du code de base.  Visitez [Ionide.io](http://ionide.io) pour en savoir plus sur la suite de plug-in.

## <a name="prerequisites"></a>Conditions préalables

F # 4.0 ou version ultérieure doit être installé sur votre ordinateur pour Ionide.

Vous devez également disposer [git installé](https://git-scm.com/download) et disponible sur votre chemin d’accès permettent d’utiliser des modèles de projet Ionide.  Vous pouvez vérifier qu’il est correctement installé en tapant `git` à une pression de prompt.and commande **entrée**.

### <a name="windows"></a>Windows

Si vous êtes sous Windows, vous avez deux options pour l’installation de F #.

Si vous avez déjà installé Visual Studio et que vous n’avez pas F #, vous pouvez [installer les outils Visual F #](get-started-visual-studio.md#installing-f).  Cela installe tous les composants nécessaires pour écrire, compiler et exécuter du code F #.

Si vous préférez ne pas installer Visual Studio, utilisez les instructions suivantes :

1. Installer [.NET Framework 4.5 ou version ultérieure](https://www.microsoft.com/en-US/download/details.aspx?id=30653) si vous utilisez Windows 7.  Si vous utilisez Windows 8 ou une version ultérieure, vous n’avez pas besoin pour ce faire.

2. Installer le Kit de développement logiciel Windows pour votre système d’exploitation :

    * [Windows 10 SDK](https://dev.windows.com/en-US/downloads/windows-10-sdk)
    * [Windows 8.1 SDK](http://msdn.microsoft.com/windows/desktop/bg162891)
    * [Windows 8 SDK](http://msdn.microsoft.com/windows/hardware/hh852363.aspx)
    * [Windows 7 SDK](http://www.microsoft.com/download/details.aspx?id=8279)

3. Installer le [Microsoft Build Tools 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48159).  Vous devez également installer [Microsoft Build Tools 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40760).

4. Installer le [outils Visual F #](https://www.microsoft.com/en-us/download/details.aspx?id=48179).

Sur Windows 64 bits, le compilateur et les outils se trouvent ici :

```
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsc.exe
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsi.exe
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsiAnyCpu.exe
```

Sur Windows 32 bits, les outils du compilateur se trouvent ici :

```
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsc.exe
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsi.exe
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsiAnyCpu.exe
```

Ionide détecte automatiquement le compilateur et les outils, mais si elle n’est pas pour une raison quelconque (par exemple, les outils Visual F # a été installés dans un répertoire différent), vous pouvez ajouter manuellement le dossier qui contient (`...\Microsoft SDKs\F#\4.0`) à votre chemin d’accès.

### <a name="macos"></a>MacOS

Sur Mac OS, utilise Ionide [Mono](http://www.mono-project.com).  Le moyen le plus simple pour installer Mono sur macOS est via Homebrew.  Tapez simplement la commande suivante dans votre terminal :

```
brew install mono
```

### <a name="linux"></a>Linux

Sur Linux, Ionide utilise également [Mono](http://www.mono-project.com).  Si vous êtes sur Debian ou Ubuntu, vous pouvez utiliser les éléments suivants :

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a>L’installation de Visual Studio Code et le plug-in Ionide

Vous pouvez installer Visual Studio Code, à partir de la [code.visualstudio.com](https://code.visualstudio.com) site Web.  Après cela, il existe deux façons de trouver le plug-in Ionide :

1. Utilisez la Palette de commandes (Ctrl + Maj + P sur Windows, ⌘ + MAJ + P sur macOS, Ctrl + Maj + P sur Linux) et tapez la commande suivante :

    ```
    >ext install Ionide
    ```

2. Cliquez sur l’icône des Extensions et recherchez « Ionide » :

    ![](media/getting-started-vscode/vscode-ext.png)

Le plug-in uniquement requis pour la prise en charge F # dans Visual Studio Code est [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).  Toutefois, vous pouvez également installer [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) et pour obtenir [faux](http://fsharp.github.io/FAKE/) prennent en charge et [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) pour obtenir [Paket](https://fsprojects.github.io/Paket/) prennent en charge.  FAUX et Paket sont des outils de communauté supplémentaires F # pour générer des projets et la gestion des dépendances, respectivement.

## <a name="creating-your-first-project-with-ionide"></a>Créer votre premier projet avec Ionide

Pour créer un projet F #, ouvrez Visual Studio Code dans un nouveau dossier (vous pouvez appeler comme vous le souhaitez).

![](media/getting-started-vscode/vscode-open-dir.png)

Ensuite, ouvrez la Palette de commandes (Ctrl + Maj + P sur Windows, ⌘ + MAJ + P sur macOS, Ctrl + Maj + P sur Linux) et tapez la commande suivante :

```
>f#: New Project
```

Il est alimenté par le [FORGE](https://github.com/fsharp-editing/Forge) projet.  Vous devez voir quelque chose de similaire à :

![](media/getting-started-vscode/vscode-new-proj.png)

> [!NOTE]
Si vous ne voyez pas la commande ci-dessus, essayez d’actualiser les modèles en exécutant la commande suivante dans la Palette de commandes : `>F#: Refresh Project Templates`.

Sélectionnez « F #: nouveau projet » en appuyant sur **entrée**, s’affiche alors à cette étape :

![](media/getting-started-vscode/vscode-proj-type.png)

Il sélectionne un modèle pour un type de projet spécifique.  Régi par de nombreuses options sont, par exemple un [FsLab](http://fslab.org) modèle pour la science des données ou [Suave](https://suave.io) modèle de programmation du Web.  Cet article utilise la `classlib` modèle, par conséquent, mettez en surbrillance qui et appuyez sur **entrée**.  Vous allez ensuite atteindre l’étape suivante :

![](media/getting-started-vscode/vscode-new-dir.png)

Cela vous permet de créer le projet dans un répertoire différent, si vous le souhaitez.  Laissez ce champ vide pour l’instant.  Il créera le projet dans le répertoire actif.  Une fois que vous appuyez sur **entrée**, vous allez atteindre l’étape suivante :

![](media/getting-started-vscode/vscode-proj-name.png)

Cela vous permet de nommer votre projet.  F # utilise [casse Pascal](http://c2.com/cgi/wiki?PascalCase) pour les noms de projet.  Cet article utilise `ClassLibraryDemo` comme nom.  Une fois que vous avez entré le nom souhaité pour votre projet, appuyez sur **entrée**.

Si vous avez suivi les étapes précédentes, vous devez obtenir Visual Studio Code espace de travail sur le côté gauche pour ressembler à ceci :

![](media/getting-started-vscode/vscode-new-proj-explorer.png)

Ce modèle génère quelques éléments qui que vous seront utiles :

1. F # de projet, sous la `ClassLibraryDemo` dossier.
2. La structure de répertoire correct pour l’ajout de packages via [ `Paket` ](http://fsprojects.github.io/Paket/).
3. Un inter-plateformes générer le script avec [ `FAKE` ](http://fsharp.github.io/FAKE/).
4. Le `paket.exe` exécutable qui peut récupérer des packages et résoudre les dépendances pour vous.
5. A `.gitignore` fichier si vous souhaitez ajouter ce projet au contrôle de code source basée sur Git.

## <a name="writing-some-code"></a>Écrire du code

Ouvrez le *ClassLibraryDemo* dossier.  Vous devez voir les fichiers suivants :

1. `ClassLibraryDemo.fs`, un fichier d’implémentation F # avec une classe définie.
2. `CassLibraryDemo.fsproj`, un fichier de projet F # est utilisé pour générer ce projet.
3. `Script.fsx`, un fichier de script F # qui charge le fichier source.
4. `paket.references`, un fichier Paket qui spécifie les dépendances du projet.

Ouvrez `Script.fsx`et ajoutez le code suivant à la fin de celle-ci :

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Cette fonction convertit un mot à un formulaire de [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).  L’étape suivante consiste à évaluer à l’aide de F # Interactive (FSI).

Mettez en surbrillance de la fonction entière (il doit être 11 lignes).  Une fois qu’il est mis en surbrillance, maintenez la **Alt** clé, puis appuyez sur **entrée**.  Vous remarquerez une fenêtre contextuelle ci-dessous, et il doit afficher quelque chose comme ceci :

![](media/getting-started-vscode/vscode-fsi.png)

Cela a trois opérations :

1. Il a démarré le processus FSI.
2. Il envoyé le code que vous avez sélectionnée sur le processus FSI.
3. Le processus FSI évaluer le code que vous avez envoyé via.

Étant donné que ce que vous avez envoyé via a été un [fonction](../language-reference/functions/index.md), vous pouvez maintenant appeler cette fonction avec FSI !  Dans la fenêtre interactive, tapez ce qui suit :

```fsharp
toPigLatin "banana";;
```

Vous devez voir le résultat suivant :

```fsharp
val it : string = "ananabay"
```

Maintenant, essayons avec une voyelle en tant que la première lettre. Entrez les informations suivantes :

```fsharp
toPigLatin "apple";;
```

Vous devez voir le résultat suivant :

```fsharp
val it : string = "appleyay"
```

La fonction semble fonctionner comme prévu.  Félicitations, vous venez d’écriture de votre première fonction) (F # dans Visual Studio Code et il évaluée avec FSI.

>[!NOTE]
Comme vous l’avez peut-être remarqué, les lignes de FSI sont terminent par `;;`.  Il s’agit, car FSI vous permet d’entrer plusieurs lignes.  Le `;;` à la fin informe FSI lorsque le code est terminé.

## <a name="explaining-the-code"></a>Explique le code

Si vous n’êtes pas sûr de ce que le code est en fait, Voici un pas à pas.

Comme vous pouvez le voir, `toPigLatin` est une fonction qui prend un mot en entrée et la convertit en une représentation sous forme de Pig-Latin de ce mot.  Les règles pour ce sont les suivantes :

Si le premier caractère dans un mot commence par une voyelle, ajoutez « hourra » à la fin du mot.  Si elle ne commence pas par une voyelle, déplacez le premier caractère à la fin du mot et ajoutez-y « ay ».

Vous avez peut-être remarqué les éléments suivants dans FSI :

```
val toPigLatin : word:string -> string
```

Cela indique que `toPigLatin` est une fonction qui accepte un `string` en tant qu’entrée (appelé `word`), ainsi qu’un autre `string`.  Il s’agit du [signature de type de la fonction](https://fsharpforfunandprofit.com/posts/function-signatures/), un élément fondamental de F #, qui est la clé pour comprendre le code F #.  Vous pouvez également constater si vous pointez sur la fonction dans le Code de Visual Studio.

Dans le corps de la fonction, vous pouvez remarquer que les deux parties distinctes :

1. Une fonction interne, appelée `isVowel`, qui détermine si un caractère donné (`c`) est une voyelle en vérifiant si elle correspond à un des modèles fournis via [recherche de correspondance](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. Un [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) qui vérifie si le premier caractère est une voyelle et construit une valeur de retour de caractères d’entrée selon que le premier caractère de l’expression était une voyelle ou non :

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

Le flux de `toPigLatin` est donc :

Vérifiez si le premier caractère du mot d’entrée est une voyelle.  S’il s’agit, attachez « hourra » à la fin du mot.  Sinon, déplacez le premier caractère à la fin du mot et « ay » lui ajouter.

Il existe une dernière chose à noter à ce sujet : il n’existe aucune instruction explicite à retourner à partir de la fonction, contrairement à nombreux autres langages très utiles.  Cela est que F # est basé sur une Expression, et la dernière expression dans le corps d’une fonction est la valeur de retour.  Car `if..then..else` lui-même est une expression, le corps de la `then` bloc ou le corps de la `else` bloc s’affichera en fonction de la valeur d’entrée.

## <a name="moving-your-script-code-into-the-implementation-file"></a>Déplacement de votre code de script dans le fichier d’implémentation

Les sections précédentes de cet article présenté une première étape dans l’écriture de code F # courants : écrire une fonction initiale et l’exécuter interactivement avec FSI.  Il s’agit en tant que le développement piloté par les REPL, où REPL représente « Boucle en lecture-évaluation-impression ».  Il s’agit d’un excellent moyen de faire des essais avec des fonctionnalités jusqu'à ce que vous ayez un élément de travail.

L’étape suivante de développement piloté par REPL consiste à déplacer de code opérationnel dans un fichier d’implémentation F #.  Il peut ensuite être compilé par le compilateur F # dans un assembly qui peut être exécuté.

Pour commencer, ouvrez `ClassLibraryDemo.fs`.  Vous remarquerez que du code existe déjà dans.  Continuer et supprimer la définition de classe, mais veillez à laisser le [ `namespace` ](../language-reference/namespaces.md) déclaration en haut.

Ensuite, créez un nouveau [ `module` ](../language-reference/modules.md) appelé `PigLatin` et copiez le `toPigLatin` fonction en tant que tel dans celui-ci :

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

Il s’agit d’une des nombreuses méthodes que vous pouvez organiser les fonctions dans le code F # et une approche courante si vous souhaitez également appeler votre code à partir de c# ou Visual Basic.

Ensuite, ouvrez le `Script.fsx` à nouveau de fichiers et supprimez la totalité de `toPigLatin` de fonctionner, mais veillez à conserver les deux lignes suivantes dans le fichier :

```
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

La première ligne est nécessaire pour écrire un script pour charger de FSI `ClassLibraryDemo.fs`.  La deuxième ligne est une commodité : omettant est facultative, mais vous devez taper `open ClassLibraryDemo` dans une fenêtre FSI si vous souhaitez mettre le `ToPigLatin` module dans la portée.

Ensuite, dans la fenêtre FSI, appelez la fonction avec le `PigLatin` module que vous avez défini précédemment :

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

Opération réussie  Vous obtenez les mêmes résultats qu’avant, mais maintenant chargé à partir d’un fichier d’implémentation F #.  La principale différence ici est que les fichiers de code source F # sont compilés dans des assemblys qui peuvent être exécutées n’importe où, pas seulement dans FSI.

## <a name="summary"></a>Résumé

Dans cet article, vous avez appris :

1. Comment configurer le Code de Visual Studio avec Ionide.
2. Comment créer votre premier projet F # avec Ionide.
3. Comment utiliser F # script pour écrire votre première fonction) (F # dans Ionide puis l’exécuter dans FSI.
4. Comment migrer votre code de script pour le code source F #, puis appelez ce code à partir de FSI.

Vous êtes désormais équipés pour écrire du code F # beaucoup plus à l’aide de Code Visual Studio et Ionide.

## <a name="troubleshooting"></a>Résolution des problèmes

Voici quelques manières que vous pouvez résoudre certains problèmes que vous pouvez rencontrer :

1. Pour obtenir les fonctionnalités de Ionide de modification du code, vos fichiers F # doivent être enregistrés sur disque et à l’intérieur d’un dossier qui est ouvert dans l’espace de travail de Visual Studio Code.
2. Si vous avez apporté des modifications à votre système ou installé des composants requis de Ionide avec Code Visual Studio ouvert, redémarrez Visual Studio Code.
3. Vérifiez que vous pouvez utiliser le compilateur F # et F # interactive à partir de la ligne de commande sans un chemin d’accès qualifié complet.  Vous pouvez le faire en tapant `fsc` dans une ligne de commande pour le compilateur F #, et `fsi` ou `fsharpi` pour Visual F # outils sur Windows et Mono sur Mac/Linux, respectivement.
4. Si vous avez des caractères non valides dans les répertoires de votre projet, Ionide peut ne pas fonctionner.  Renommer les répertoires de votre projet si c’est le cas.
5. Si aucun des commandes Ionide ne fonctionnent pas, vérifiez votre [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) pour voir si vous les remplacez par inadvertance.
6. Si Ionide est rompue sur votre ordinateur et qu’aucun d'entre eux a résolu votre problème, essayez de supprimer le `ionide-fsharp` répertoire sur votre ordinateur et réinstallez la suite de plug-in.

Ionide est un projet open source créé et géré par les membres de la Communauté F #.  Veuillez signaler des problèmes et n’hésitez pas à contribuer à la [Ionide-VSCode : référentiel GitHub de FSharp](https://github.com/ionide/ionide-vscode-fsharp).

Si vous avez un problème de rapport, veuillez suivre [les instructions pour l’obtention de journaux à utiliser lors de la déclaration d’un problème](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).

Vous pouvez également demander à pour plus d’informations à partir de la Ionide développeurs et de F # dans le [Ionide Gitter canal](https://gitter.im/ionide/ionide-project).

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur F # et les fonctionnalités du langage, consultez [visite guidée de F #](../tour.md).

## <a name="see-also"></a>Voir aussi

[Présentation de F#](../tour.md)

[Informations de référence du langage F#](../language-reference/index.md)

[Fonctions](../language-reference/functions/index.md)

[Modules](../language-reference/modules.md)

[Espaces de noms](../language-reference/namespaces.md)

[Ionide-VSCode : FSharp](https://github.com/ionide/ionide-vscode-fsharp)
