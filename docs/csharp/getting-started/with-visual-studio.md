---
title: "Génération d’une application C# Hello World avec .NET Core dans Visual Studio 2017"
description: "Découvrez comment créer une application de console .NET Core simple à l’aide de Visual Studio 2017."
keywords: .NET Core, application de console .NET Core, Visual Studio 2017
author: stevehoag
ms.author: shoag
ms.date: 03/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 97aa50bf-bdf8-416d-a56c-ac77504c14ea
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f1a20f399b4ab34986d700622ff3bf3859b001bd
ms.lasthandoff: 03/13/2017

---

# <a name="building-a-c-hello-world-application-with-net-core-in-visual-studio-2017"></a>Génération d’une application C# Hello World avec .NET Core dans Visual Studio 2017 #

Cette rubrique fournit une introduction pas à pas pour la création, le débogage et la publication d’une application de console .NET Core à l’aide de Visual Studio 2017. Visual Studio 2017 fournit un environnement de développement complet pour la création d’applications .NET Core. Tant que l’application ne dispose pas de toutes les dépendances spécifiques à la plateforme, l’application elle-même peut s’exécuter sur n’importe quelle plateforme cible de .NET Core et sur tout système qui dispose de .NET Core.

## <a name="prerequisites"></a>Conditions préalables ##

- [Visual Studio 2017](https://www.visualstudio.com/downloads/), avec la charge de travail « Développement multiplateforme .Net Core » installée. 

Pour plus d’informations, consultez la section [Visual Studio 2017](../../core/windows-prerequisites.md) dans la rubrique Conditions préalables de Windows.

## <a name="a-simple-hello-world-application"></a>Une simple application Hello World ##

Commençons par créer une application de console « Hello World » simple. Procédez comme suit :

1. Lancez Visual Studio, et dans le menu **Fichier**, choisissez **Nouveau** > **Projet**. Dans la boîte de dialogue **Nouveau projet**, développez le nœud **Visual C#** dans le volet de gauche, puis choisissez le nœud **.NET Core**.

2. Dans le volet droit, choisissez **Application console (.NET Core)**. Entrez le nom du projet, `HelloWorld`, et assurez-vous que la case **Créer un répertoire pour la solution** est cochée, comme présenté dans l'illustration suivante.

   ![Capture d’écran de la boîte de dialogue Nouveau projet avec une application de console sélectionnée](./media/with-visual-studio/vs_newproject.jpg)
   
3. Sélectionnez le bouton **OK** . Visual Studio affiche son environnement de développement avec sa fenêtre de code, comme le montre l'illustration suivante. Le modèle d’application console C# pour .NET Core définit automatiquement une classe, `Program`, avec une méthode unique, `Main`, qui accepte un tableau de @System.String comme argument. `Main` est le point d’entrée de l’application. Cette méthode est appelée automatiquement par le runtime lors du lancement de l’application. Tous les arguments de ligne de commande fournis au lancement de l’application sont disponibles dans le tableau *args*.

   ![Visual Studio et le nouveau projet HelloWorld](./media/with-visual-studio/vs_devenv.jpg)

   Le modèle crée une application « Hello world » très simple, qui appelle la méthode @System.Console.WriteLine (System.String) pour afficher la chaîne littérale « Hello World! » sur la fenêtre de console. En sélectionnant le bouton « HelloWorld » avec la flèche verte dans la barre d’outils, vous pouvez maintenant exécuter le programme en mode débogage. Si vous le faites, cependant, la fenêtre de console est seulement visible pendant un intervalle de temps très court avant sa fermeture. Cela se produit car `Main` se termine et l’application se termine dès que l’instruction unique de la méthode `Main` s’exécute.

4. Faisons faire une pause à notre application existante avant de la laisser fermer la fenêtre de console. Ajoutez le code suivant immédiatement après l’appel à la méthode @System.Console.WriteLine (System.String) :

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```
   Ce code invite l’utilisateur à appuyer sur une touche, puis arrête le programme jusqu'à ce que l’utilisateur appuie sur une touche.

5. Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**. Cela compile votre programme en IL, un langage intermédiaire qui est ensuite converti en code binaire par un compilateur juste-à-temps (JIT).

6. Exécutez le programme en sélectionnant le bouton « HelloWorld » avec la flèche verte dans la barre d’outils. Le résultat est affiché dans l’illustration suivante.

   ![Image](./media/with-visual-studio/simple_hello.jpg)

7. Appuyez sur une touche pour fermer la fenêtre.

## <a name="enhancing-the-hello-world-application"></a>Amélioration de l’application Hello World ##

Améliorons notre application pour inviter l’utilisateur à saisir son nom puis l’afficher avec la date et l’heure dans la fenêtre de console. Pour modifier et tester le programme, procédez comme suit :

1. Entrez le code C# suivant dans la fenêtre de code immédiatement après le crochet ouvrant qui suit la ligne `public static void Main(string[] args)` et avant le premier crochet fermant.

   [!CODE [GettingStarted#1](../../../samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   L’illustration suivante affiche le la fenêtre du code résultant.

   ![Le programme modifié en cours d’exécution](./media/with-visual-studio/codewindow.jpg)

   Ce code affiche « What is your name? ». dans la console et attend que l’utilisateur entre une chaîne suivie de la touche Entrée. Il stocke cette chaîne dans une variable nommée `name`. Elle récupère également la valeur de la propriété@System.DateTime.Now, qui contient l’heure locale actuelle et l’assigne à une variable nommée `date`. Elle utilise ensuite une [chaîne de format composite](../../standard/base-types/composite-format.md) pour afficher ces valeurs dans la console.

2. Recompilez le programme en choisissant **Build** > **Générer la solution**. Cela compile votre programme en IL, un langage intermédiaire qui est ensuite converti en code binaire par un compilateur juste-à-temps (JIT).

3. Exécutez le programme en mode débogage dans Visual Studio en sélectionnant la flèche verte dans la barre d’outils, en appuyant sur F5 ou en choisissant l’élément de menu **Debug** > **Démarrer le débogage**. Une fois que vous répondez aux invites en entrant un nom et appuyez sur Entrée, la fenêtre de console doit ressembler à ce qui suit :

   ![Le programme modifié en cours d’exécution](./media/with-visual-studio/console.jpg)

4. Appuyez sur une touche pour fermer la fenêtre de console. Cela termine le mode débogage.

Vous avez maintenant créé et exécuté votre application simple. Pour développer une application professionnelle, il existe encore quelques étapes supplémentaires à suivre pour finaliser votre application :

- Pour plus d’informations sur le débogage de votre application, consultez [Débogage de l’application Hello World](debugging-with-visual-studio-2017.md)

- Pour plus d’informations sur le développement et la publication d’une version distribuable de votre application, consultez [Publication de l’application Hello World](publishing-with-visual-studio-2017.md).

## <a name="related-topics"></a>Rubriques connexes ##

Au lieu d’une application console, vous pouvez également créer une bibliothèque de classes .NET Core et Visual Studio 2017. Pour une introduction pas à pas, consultez [Génération d’une bibliothèque de classes avec C# et .NET Core dans Visual Studio 2017](library-with-visual-studio-2017.md).

Vous pouvez également développer une application de console .NET Core sur Mac, Linux et Windows à l’aide de Visual Studio Code, un éditeur de code téléchargeable gratuitement. Pour obtenir un didacticiel pas à pas, consultez [Bien démarrer avec Visual Studio](with-visual-studio-code.md).

