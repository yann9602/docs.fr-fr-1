---
title: "Débogage de votre application C# Hello World avec Visual Studio 2017"
description: "Découvrez comment déboguer une application Hello World écrite en C# avec Visual Studio 2017"
keywords: ".NET Core, application de console .NET Core, débogage de .NET Core"
author: BillWagner
ms.author: wiwagn
ms.date: 10/24/2016
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: cb213625-cc60-438b-9b9e-49aed0e4a974
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6a6a461984c140d180cf70cd7a1a33818a40b451
ms.lasthandoff: 03/13/2017

---

# <a name="debugging-your-c-hello-world-application-with-visual-studio-2017"></a>Débogage de votre application C# Hello World avec Visual Studio 2017 #

Pour l’instant, vous avez suivi la procédure de [Génération d’une application C# Hello World avec .NET Core dans Visual Studio 2017 RC](.\with-visual-studio-2017.md) pour créer et exécuter une application de console simple. Une fois que vous avez écrit et compilé une application, vous pouvez commencer à la tester. Visual Studio inclut un ensemble complet d’outils de débogage qui vous permettent de tester et dépanner votre application. Nous allons en examiner quelques-uns lors du débogage de notre application.

## <a name="debugging-in-debug-mode"></a>Débogage en mode débogage ##

Le mode Debug est une des deux configurations de build par défaut de Visual Studio. (L’autre est le mode Release). La configuration de build actuelle s’affiche sur la barre d’outils. L’illustration suivante montre que notre application va être compilée en mode Debug.

   ![Image](./media/debugmode.jpg)

Vous devez toujours commencer par tester votre programme en mode Debug. La plupart des optimisations du compilateur désactivent le mode Debug et fournissent des informations plus détaillées dans le fichier de base de données de symboles (fichiers .pdb) généré par le processus de génération.

## <a name="setting-a-breakpoint"></a>Définition d'un point d'arrêt ##

Nous allons exécuter notre programme en mode Debug et essayer quelques fonctionnalités de débogage :

1. Définissez un point d’arrêt en plaçant le curseur sur la ligne `Console.WriteLine("\nHello, {0}, on {1:d} at {1:t}", name, date);` et en cliquant dans la marge de gauche de la fenêtre de code ou en choisissant l’élément de menu **Debug**, **Point d’arrêt**. (Un point d’arrêt interrompt temporairement l’exécution de l’application *avant* la ligne sur laquelle le point d’arrêt est exécuté.) Comme le montre l’illustration suivante, Visual Studio affiche la ligne sur laquelle le point d’arrêt est défini en la mettant en surbrillance et en affichant un cercle rouge dans la marge de gauche.

   ![Image](./media/setbreakpoint_2017.jpg)

1. Exécutez le programme en mode Debug en sélectionnant le bouton « HelloWorld » avec la flèche verte dans la barre d’outils, en appuyant sur F5 ou en choisissant **Debug**, **Démarrer le débogage**.

1. Entrez une chaîne dans la fenêtre de console lorsque le programme vous invite à entrer un nom, puis appuyez sur Entrée.

1. L’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant l’exécution de la méthode `Console.WriteLine`. Visual Studio doit ressembler à l’illustration suivante. Notez que la fenêtre **Automatique** affiche les valeurs des variables utilisées autour de la ligne actuelle. (La fenêtre **Variables locales** affiche les valeurs des variables définies dans la méthode en cours d’exécution.)

   ![Image](./media/breakpoint_2017.jpg)

1. Essayons de modifier la valeur des variables pour voir comment cela affecte notre programme. Si la **fenêtre Exécution** n’est pas visible, affichez-la en choisissant l’élément de menu **Debug**, **Fenêtres**, **Exécution**. La **fenêtre Exécution** vous permet d’interagir avec l’application que vous déboguez.

1. Elle permet de modifier interactivement la valeur des variables. Entrez `name = "Yuma"` dans la fenêtre Exécution et appuyez sur la touche Entrée.

1. Entrez `date = new DateTime(2016,11,01,11,59,00)` dans la fenêtre Exécution et appuyez sur la touche Entrée.

   L’image suivante présente la **fenêtre immédiate** :

   ![Image](./media/immediatewindow.jpg)

   Notez que la fenêtre affiche la valeur de la variable de chaîne et les propriétés de la valeur @System.DateTime. En outre, la valeur des variables est mise à jour dans les fenêtres **Automatiques** et **Variables locales**.

1. Continuez l’exécution du programme en sélectionnant le bouton **Continuer** dans la barre d’outils, ou en choisissant l’élément de menu **Debug**, **Continuer**. La fenêtre de console résultante doit être similaire à l’image suivante. Notez que les valeurs affichées dans la fenêtre de console correspondent également aux modifications que nous avons apportées à la **fenêtre Exécution**.

   ![Image](./media/changed.jpg)

1. Appuyez sur n’importe quelle touche pour quitter l’application et terminer le mode Debug.

## <a name="setting-a-conditional-breakpoint"></a>Définition d’un point d'arrêt conditionnel ##

Nous savons maintenant que notre programme affiche correctement la chaîne entrée par l’utilisateur. Mais que se passe-t-il si l’utilisateur n’effectue aucune entrée ? Nous pouvons tester cela et dans le même temps utiliser une autre fonctionnalité de débogage, la possibilité de définir un point d’arrêt conditionnel.

Pour définir un point d’arrêt conditionnel et voir ce qu’il se passe lorsque l’utilisateur n’entre pas de chaîne, procédez comme suit :

1. Cliquez avec le bouton droit sur le point rouge qui représente le point d’arrêt. Dans le menu contextuel, sélectionnez **Conditions...** pour ouvrir la boîte de dialogue **Paramètres de point d’arrêt** présentée dans l’illustration suivante.

   ![Image](./media/breakpoint_settings.jpg)

1. Dans la zone de texte « e.g. x == 5 », entrez les informations suivantes :

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Ici, nous allons tester une condition de code. Nous pouvons également spécifier un nombre d’accès, qui interrompt l’exécution du programme jusqu’à ce qu’une instruction soit exécutée un nombre spécifié de fois, ou une condition de filtre, qui interrompt l’exécution du programme en fonction d’attributs tels que l’identificateur du thread, le nom du processus et le nom du thread.

1. Choisissez le bouton **Fermer** pour fermer la boîte de dialogue.

1. Exécutez le programme en mode débogage.

1. Dans la fenêtre de console, appuyez sur la touche Entrée lorsque vous êtes invité à entrer votre nom.

1. Étant donné que la condition que nous avons spécifiée a été satisfaite (`name` a la valeur `null` ou [String.Empty](xref:System.String.Empty)), l’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant que la méthode `Console.WriteLine` s’exécute.

1. Choisissez la fenêtre **Variables locales**, qui présente les valeurs des variables locales pour la méthode en cours d’exécution, dans notre cas la méthode `Main`.

1. Notez que la valeur de la variable `name` est « », ou [String.Empty](xref:System.String.Empty). Confirmez cela en entrant l’instruction suivante dans la **fenêtre Exécution** :

   ```csharp
   ? name == String.Empty
   ```

   L’illustration suivante affiche le résultat.

   ![Image](./media/emptystring.jpg)

1. Sélectionnez le bouton **Continuer** dans la barre d’outils pour continuer l’exécution du programme.

1. Appuyez sur une touche pour fermer la fenêtre de console et quitter le mode débogage.

1. Désactivez le point d’arrêt en cliquant sur le point dans la marge gauche de la fenêtre de code, ou en choisissant l’élément de menu **Debug**, **Point d’arrêt**.

## <a name="stepping-through-a-program"></a>Exécution pas à pas d’un programme ##

Visual Studio vous permet également de parcourir un programme ligne par ligne et de contrôler son exécution. En règle générale, vous définissez un point d’arrêt et utilisez cette fonctionnalité pour suivre le déroulement du programme sur une petite portion de son code. Étant donné que notre programme est petit, cependant, analysons la totalité du programme pas à pas en procédant comme suit :

1. Dans la barre de menus, choisissez **Débogage**, **Pas à pas détaillé**, ou appuyez sur la touche F11. Visual Studio met en surbrillance et affiche une flèche en regard de la ligne qui sera exécutée ensuite, comme le montre l'illustration suivante.

   ![Image](./media/step_into.jpg)

   À ce stade, la fenêtre **Automatiques** montre que notre programme n’a défini qu’une seule variable, `args`. Étant donné que nous n’avons pas passé d’arguments de ligne de commande au programme, sa valeur est un tableau de chaînes vide. En outre, Visual Studio a ouvert une fenêtre de console vide.

1. Choisissez **Débogage**, **Pas à pas détaillé**, ou appuyez sur la touche F11. Visual Studio met désormais en surbrillance la ligne suivante à exécuter. Comme le montre l'illustration, il lui a fallu 3 millisecondes pour exécuter le code entre la dernière instruction et celle-ci. `args` reste la seule variable déclarée, et la fenêtre de console est toujours vide.

   ![Image](./media/step_into_2.jpg)

1. Choisissez **Débogage**, **Pas à pas détaillé**, ou appuyez sur la touche F11. Visual Studio identifie l’instruction qui inclut l’attribution de la variable `name`. La fenêtre **Automatiques** fenêtre montre que `name` est `null`, et la fenêtre de console affiche la chaîne « What is your name? ».

1. Répondez à l’invite en entrant une chaîne dans la fenêtre de console et en appuyant sur Entrée. La console ne répond pas, et la chaîne que vous entrez ne s’affiche pas dans la fenêtre de console, mais la méthode [Console.ReadLine](xref:System.Console.ReadLine) capture néanmoins votre entrée.

1. Choisissez **Débogage**, **Pas à pas détaillé**, ou appuyez sur la touche F11. Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `date`. La fenêtre **Automatiques** montre la valeur de propriété [DateTime.Now](xref:System.DateTime.Now) et la valeur retournée par l’appel à la méthode [Console.ReadLine](xref:System.Console.ReadLine). La fenêtre de console affiche également la chaîne entrée lorsque vous y avez été invité par la console.

1. Choisissez **Débogage**, **Pas à pas détaillé**, ou appuyez sur la touche F11. La fenêtre **Automatiques** affiche désormais la valeur de la variable `date` après l’affectation de la propriété [DateTime.Now](xref:System.DateTime.Now). La fenêtre de console est inchangée.

1. Choisissez **Débogage**, **Pas à pas détaillé**, ou appuyez sur la touche F11. Visual Studio appelle la méthode [Console.WriteLine](xref:System.Console.WriteLine(System.String,System.Object,System.Object)). Les valeurs des variables `date` et `name` apparaissent dans la fenêtre **Automatiques** et la fenêtre de console affiche la chaîne mise en forme.

1. Choisissez **Debug**, **Pas à pas sortant**, ou appuyez sur MAJ et la touche F11. Cela arrête l’exécution pas à pas. La fenêtre de console affiche un message et attend que vous appuyiez sur une touche.

1. Appuyez sur une touche pour fermer la fenêtre de console et quitter le mode débogage.

## <a name="building-a-release-version"></a>Génération d'une version Release ##

Une fois que vous avez testé la version Debug de votre application, vous devez également compiler et tester la version Release. La version Release intègre des optimisations de compilateur parfois susceptibles d’affecter le comportement d’une application. Par exemple, les optimisations du compilateur qui sont conçues pour améliorer les performances peuvent créer des conditions de concurrence critique dans les applications asynchrones ou multithreads.

Pour générer et tester la version Release de votre application de console, modifiez la configuration de build dans la barre d’outils de **Debug** à **Release**, comme illustré dans l'illustration suivante.

![Image](./media/release.jpg)

Lorsque vous appuyez sur F5 ou choisissez **Générer la solution** à partir du menu **Build**, Visual Studio compile la version Release de votre application de console pour la tester. Vous pouvez ensuite exécuter et tester comme vous l’aviez fait pour la version Debug.

Une fois que vous avez terminé de déboguer votre application, l’étape suivante consiste à publier une version distribuable de votre application. Pour plus d’informations sur la procédure à suivre, consultez [Publication de l’application C# Hello World avec Visual Studio 2017](./publishing-with-visual-studio-2017.md).

