---
title: 'Prise en main) (F # dans Visual Studio'
description: "Découvrez comment utiliser F # avec Visual Studio."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 02/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8db75596-19a9-4eda-b20d-a12d517c8cc1
ms.openlocfilehash: 944bbbba6a26634ace269d86cbbdde9ef9de7bcd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="get-started-with-f-in-visual-studio"></a>Prise en main) (F # dans Visual Studio

F # et les outils Visual F # sont pris en charge dans l’IDE de Visual Studio.  Pour commencer, vous devez [télécharger Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs), si vous n’avez pas encore.  Cet article utilise Visual Studio 2017 Community Edition, mais vous pouvez utiliser F # avec la version de votre choix.

## <a name="installing-f"></a>Lors de l’installation) (F # #

Si vous téléchargez Visual Studio pour la première fois, il sera tout d’abord installer le programme d’installation de Visual Studio.  Installer une version de Visual Studio 2017 du programme d’installation. Si vous avez déjà installé, cliquez sur **modifier**.

Vous verrez ensuite une liste de charges de travail. Vous pouvez installer F # par le biais des charges de travail suivants :

|Charge de travail|Action|
|--------|------|
| Développement multiplateforme .NET Core | Aucune action - F # n’est installée par défaut |
| Développement web et ASP.NET | Aucune action - F # n’est installée par défaut |
| Développement Azure | Aucune action - F # n’est installée par défaut |
| Développement mobile en .NET | Aucune action - F # n’est installée par défaut |
| Applications de science des données et analytiques | Aucune action - F # n’est installée par défaut |
| Développement .NET Desktop | Sélectionnez **prise en charge de bureau langage F #** à partir de la droite |
| Traitement et stockage de données | Sélectionnez **prise en charge de bureau langage F #** à partir de la droite |

Ensuite, cliquez sur **modifier** dans l’angle inférieur droit.  Ceci installe tout ce dont vous avez sélectionné.  Vous pouvez ensuite ouvrir Visual Studio 2017 avec prise en charge linguistique F # en cliquant sur **lancer**.

## <a name="creating-a-console-application"></a>Création d’une application console

Un des projets dans Visual Studio plus simples est de l’Application Console.  Voici comment faire.  Une fois Visual Studio ouvert :

1. Sur le **fichier** menu, pointez sur **nouveau**, puis choisissez **projet**.

2.  Dans le nouveau projet de boîte de dialogue, sous **modèles**, vous devez voir **Visual F #**.  Choisissez cette option pour afficher les modèles F #.

3. Sélectionnez **.NET Core application Console** ou **application Console**.

3. Choisissez le **OK** bouton permettant de créer le projet F # !  Vous devez maintenant voir un projet F # dans l’Explorateur de solutions.

## <a name="writing-your-code"></a>L’écriture de votre code.

Nous pouvons commencer à écrire du code tout d’abord.  Assurez-vous que le `Program.fs` fichier est ouvert, puis remplacez son contenu par les éléments suivants :

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

Dans l’exemple de code précédent, une fonction `square` a été défini qui accepte une entrée nommée `x` et multiplie par lui-même.  Étant donné que F # utilise [l’inférence de Type](../language-reference/type-inference.md), le type de `x` n’a pas besoin d’être spécifiés.  Le compilateur F # comprend les types où la multiplication est valide et affectera un type à `x` selon la façon dont `square` est appelée.  Si vous pointez sur `square`, vous devez voir les éléments suivants :

```
val square: x:int -> int
```

C’est ce que l'on appelle la signature de type de la fonction.  Il peut être lu comme suit : « carrée est une fonction qui accepte un entier nommé x et produit un entier ».  Notez que le compilateur a donné `square` le `int` type pour le moment - il s’agit, car la multiplication n’est pas générique sur *tous les* types, mais plutôt générique entre un ensemble fermé de types.  Le compilateur F # prélevé `int` sur ce point, mais il ajuste la signature de type si vous appelez `square` avec un autre type d’entrée, comme un `float`.

Une autre fonction, `main`, est défini, ce qui est décoré avec le `EntryPoint` attribut pour indiquer au compilateur F # que l’exécution du programme doit commencer de là.  Il suit la même convention que les autres [les langages de programmation de style C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), où les arguments de ligne de commande peuvent être passés à cette fonction, et un code d’entier est retourné (généralement `0`).

Il se trouve dans cette fonction que nous appelons le `square` fonction avec un argument de `12`.  Le compilateur F # puis assigne le type de `square` être `int -> int` (autrement dit, une fonction qui prend un `int` et produit un `int`).  L’appel à `printfn` est une fonction d’impression mis en forme qui utilise une chaîne de format, semblable aux langages de programmation de style C, les paramètres qui correspondent à celles spécifiées dans la chaîne de format, puis imprime le résultat et une nouvelle ligne.

## <a name="running-your-code"></a>Exécution de votre code

Vous pouvez exécuter le code et afficher les résultats en appuyant sur **ctrl-f5**.  Il exécute le programme sans débogage et vous permet de voir les résultats.  Vous pouvez également choisir la **déboguer** menu de niveau supérieur d’élément dans Visual Studio et choisissez **démarrer sans débogage**.

Vous devez maintenant voir ce qui suit imprimé dans la fenêtre de console Visual Studio de s’afficher :

```
12 squared is 144!
```

Félicitations !  Vous avez créé votre premier projet F # dans Visual Studio, écrit qu'une fonction) (F # imprimer les résultats de l’appel de cette fonction et exécutez le projet pour afficher certains résultats.

## <a name="using-f-interactive"></a>À l’aide de F # Interactive

L’une des meilleures fonctionnalités de la Visual F # pour les outils dans Visual Studio est la fenêtre F # Interactive.  Il vous permet d’envoyer le code sur un processus dans lequel vous pouvez appeler ce code et afficher le résultat de manière interactive.

Pour commencer à l’utiliser, mettez en surbrillance le `square` fonction définie dans votre code.  Ensuite, maintenez la **Alt** clé et appuyez sur **entrée**.  Il exécute le code dans la fenêtre F # Interactive.  Vous devriez voir la fenêtre F # Interactive par le code suivant dans celui-ci :

```
>

val square : x:int -> int

>
```

Cela montre la même signature de fonction pour le `square` (fonction), vous l’avez vu précédemment lorsque vous pointez sur la fonction.  Étant donné que `square` est maintenant défini dans le processus interactif F #, vous pouvez l’appeler avec des valeurs différentes :

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

Cela exécute la fonction, lie le résultat à un nouveau nom `it`et affiche le type et la valeur de `it`.  Notez que vous devez mettre fin à chaque ligne avec `;;`.  Voici comment F # Interactive sait quand votre appel de fonction est terminée.  Vous pouvez également définir de nouvelles fonctions dans F # Interactive :

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

Ci-dessus définit une nouvelle fonction, `isOdd`, qui prend un `int` et vérifie s’il est impair ! Vous pouvez appeler cette fonction pour afficher sa valeur de retour avec des entrées différentes.  Vous pouvez appeler des fonctions dans les appels de fonction :

```
> isOdd (square 15);;
val it : bool = true
```

Vous pouvez également utiliser le [avant de canal opérateur](../language-reference/symbol-and-operator-reference/index.md) à la valeur de pipeline dans les deux fonctions :

```
> 15 |> square |> isOdd;;
val it : bool = true
```

L’opérateur avant de canal et bien plus encore, sont traités dans des didacticiels ultérieurs.

Il s’agit uniquement d’un aperçu en ce que vous pouvez faire avec F # Interactive. Pour plus d’informations, consultez [de programmation Interactive avec F #](../tutorials/fsharp-interactive/index.md).

## <a name="next-steps"></a>Étapes suivantes

Si vous n’avez pas encore, consultez le [visite guidée de F #](../tour.md), qui traite de certaines fonctionnalités de base du langage F #.  Il vous donner une vue d’ensemble de certaines des fonctionnalités de F # et fournissent des exemples de code suffisamment que vous pouvez copier dans Visual Studio et exécuter.  Il existe également des ressources utiles externes, vous pouvez utiliser, a dans le [Guide F #](../index.md).

## <a name="see-also"></a>Voir aussi
 [Visual F#](index.md)  
 [Présentation de F#](../tour.md)  
 [Référence du langage F #](../language-reference/index.md)  
 [Inférence de type](../language-reference/type-inference.md)  
 [Référence des symboles et l’opérateur](../language-reference/symbol-and-operator-reference/index.md)  
