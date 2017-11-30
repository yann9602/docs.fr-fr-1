---
title: 'Prise en main) (F # dans Visual Studio pour Mac'
description: "Découvrez comment utiliser F # avec Visual Studio pour Mac."
keywords: visual f#, f#, programmation fonctionnelle
author: mizzle-mo
ms.author: phcart
ms.date: 02/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8db75596-19a9-4eda-b20d-a12d517c8cc1
ms.openlocfilehash: beee874e3a549531b520d4ac2150bc10dcab7725
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Prise en main) (F # dans Visual Studio pour Mac

F # et les outils Visual F # sont pris en charge dans Visual Studio pour Mac IDE.  Pour commencer, vous devez [télécharger Visual Studio pour Mac](https://www.visualstudio.com/downloads/download-visual-studio-vs), si vous n’avez pas encore.  Cet article utilise la 2017 de communauté Visual Studio pour Mac, mais vous pouvez utiliser F # avec la version de votre choix.

## <a name="installing-f"></a>Lors de l’installation) (F # #

Après avoir téléchargé Visual Studio pour Mac, vous êtes invité à choisir ce que vous souhaitez installer.  Dans le cadre de cet article nous laissant les valeurs par défaut.  Contrairement à Visual Studio pour Windows, vous n’avez pas besoin de spécifiquement installer prise en charge F #.  Appuyez sur « Installer » pour continuer.

Une fois l’installation terminée, cliquez sur « Démarrer Visual Studio ».  Vous pouvez également lancer il via Finder sur macOS.

## <a name="creating-a-console-application"></a>Création d’une application console

Un des projets dans Visual Studio pour Mac plus simples est de l’Application Console.  Voici comment faire.  Une fois ouvert Visual Studio pour Mac :

1. Sur le **fichier** menu, pointez sur **nouvelle Solution**.

2.  Dans la boîte de dialogue Nouveau projet, il existe 2 différents modèles pour une Application Console.  Il y a un sous d’autres -> .NET qui cible le .NET Framework.  L’autre modèle est sous .NET Core -> application qui cible le .NET Core.  Un modèle doit fonctionner pour les besoins de cet article.

3. Sous l’application de console, changez c# à F #.  Choisissez le **suivant** bouton Déplacer vers l’avant.  

4. Donnez un nom à votre projet et choisissez les options souhaitées pour l’application.  Notez, le volet de visualisation sur le côté de l’écran qui affiche la structure de répertoire qui sera créée en fonction des options sélectionnées.  

5. Cliquez sur **Créer**.  Vous devez maintenant voir un projet F # dans l’Explorateur de solutions.

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

Vous pouvez exécuter le code et afficher les résultats en cliquant sur **exécuter** à partir du menu de niveau supérieur, puis **démarrer sans débogage**.  Il exécute le programme sans débogage et vous permet de voir les résultats.

Vous devez maintenant voir imprimés dans la fenêtre de console Visual Studio pour Mac s’affichaient suivantes :

```
12 squared is 144!
```

Félicitations !  Vous avez créé votre premier projet F # dans Visual Studio pour Mac, écrit qu'une fonction) (F # imprimer les résultats de l’appel de cette fonction et exécutez le projet pour afficher certains résultats.

## <a name="using-f-interactive"></a>À l’aide de F # Interactive

L’une des meilleures fonctionnalités de la Visual F # pour les outils dans Visual Studio pour Mac est la fenêtre F # Interactive.  Il vous permet d’envoyer le code sur un processus dans lequel vous pouvez appeler ce code et afficher le résultat de manière interactive.

Pour commencer à l’utiliser, mettez en surbrillance le `square` fonction définie dans votre code.  Cliquez ensuite sur **modifier** à partir du menu de niveau supérieur.  Ensuite, sélectionnez **envoyer la sélection à F # Interactive**.  Il exécute le code dans la fenêtre F # Interactive.  Ou bien, vous pouvez cliquez avec le bouton droit sur la sélection et choisissez **envoyer la sélection à F # Interactive**.  Vous devriez voir la fenêtre F # Interactive par le code suivant dans celui-ci :

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

Ci-dessus définit une nouvelle fonction, `isOdd`, qui prend un `int` et vérifie s’il est impair !  Vous pouvez appeler cette fonction pour afficher sa valeur de retour avec des entrées différentes.  Vous pouvez appeler des fonctions dans les appels de fonction :

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

Il s’agit uniquement d’un aperçu en ce que vous pouvez faire avec F # Interactive.  Pour plus d’informations, consultez [de programmation Interactive avec F #](../tutorials/fsharp-interactive/index.md).

## <a name="next-steps"></a>Étapes suivantes

Si vous n’avez pas encore, consultez le [visite guidée de F #](../tour.md), qui traite de certaines fonctionnalités de base du langage F #.  Il vous donner une vue d’ensemble de certaines des fonctionnalités de F # et fournissent des exemples de code suffisamment que vous pouvez copier dans Visual Studio pour Mac et les exécuter.  Il existe également des ressources utiles externes, vous pouvez utiliser, a dans le [Guide F #](../index.md).

## <a name="see-also"></a>Voir aussi
 [Visual F#](../index.md)  
 [Présentation de F#](../tour.md)  
 [Référence du langage F #](../language-reference/index.md)  
 [Inférence de type](../language-reference/type-inference.md)  
 [Référence des symboles et l’opérateur](../language-reference/symbol-and-operator-reference/index.md)  
