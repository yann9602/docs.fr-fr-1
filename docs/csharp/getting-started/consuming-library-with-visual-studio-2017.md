---
title: "Utilisation d’une bibliothèque de classes avec .NET Core dans Visual Studio 2017"
description: "Apprenez comment appeler les membres dans une bibliothèque de classes avec Visual Studio 2017"
keywords: ".NET Core, bibliothèque de classes .NET Core, .NET Standard, distribution de bibliothèque de classes .NET Standard"
author: stevehoag
ms.author: shoag
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: d7b94076-1108-4174-94e7-a18f00072bb7
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0b42eeb0149feec09ddacba98383da3abd53bb5e
ms.lasthandoff: 03/13/2017

---

# <a name="consuming-a-class-library-with-net-core-in-visual-studio-2017"></a>Utilisation d’une bibliothèque de classes avec .NET Core dans Visual Studio 2017 #

Une fois que vous avez suivi les étapes de [Création d’une bibliothèque de classes C# avec .NET Core dans Visual Studio 2017](./library-with-visual-studio-2017.md) et [Test d’une bibliothèque de classes avec .NET Core dans Visual Studio 2017](testing-library-with-visual-studio.md) pour générer et tester votre bibliothèque de classes et que vous avez créé une version Release de la bibliothèque, l’étape suivante consiste à la rendre accessible aux appelants. Pour cela, deux solutions s'offrent à vous :

- Si la bibliothèque doit être utilisée par une solution unique (par exemple, s’il s’agit d’un composant dans une seule application de grande taille), vous pouvez simplement les inclure en tant que projet dans votre solution.

- Si la bibliothèque est généralement accessible, vous pouvez la distribuer comme package NuGet.

## <a name="including-a-library-as-a-project-in-a-solution"></a>Inclusion d’une bibliothèque en tant que projet dans une solution ##

Tout comme nous avons inclus des tests unitaires dans la même solution que notre bibliothèque de classes, nous pouvons inclure notre application dans le cadre de cette solution. Par exemple, nous allons utiliser notre bibliothèque de classes dans une application console qui invite l’utilisateur à entrer une chaîne et signale si son premier caractère est une majuscule :

1. Ouvrez la solution `ClassLibraryProjects` créée dans la rubrique [Création d’une bibliothèque de classes C# avec .NET Core dans Visual Studio 2017](./library-with-visual-studio-2017.md) rubrique et dans l’Explorateur de solutions, ouvrez le menu contextuel pour le nœud **ClassLibraryProjects** et choisissez **Ajouter**, **Nouveau projet**.

1. Dans la boîte de dialogue **Ajouter un nouveau projet**, développez les nœuds **Visual C#** et **.NET Core** et choisissez le modèle de projet **Application Console (.NET Core)**, comme le montre l’illustration suivante.

   ![Image](./media/use-library.jpg)

1. Dans la zone de texte **Nom**, entrez `ShowCase`, puis choisissez le bouton **OK**.

1. Dans l’Explorateur de solutions, ouvrez le menu contextuel du nœud de projet **ShowCase**, puis choisissez **Définir comme projet de démarrage**.

1. Initialement, notre projet n’a pas accès à notre bibliothèque de classes. Pour lui permettre d’appeler des méthodes dans notre bibliothèque de classes, dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le nœud **Dépendances** dans le projet **ShowCase** et choisissez **Ajouter une référence**.

1. Dans la boîte de dialogue **Gestionnaire de références**, choisissez **StringLibrary**, notre projet de bibliothèque de classes comme le montre l’illustration suivante, puis cliquez sur le bouton **OK**.

   ![Image](./media/add-lib-ref.jpg)

1. Dans la fenêtre de code pour le fichier « program.cs », remplacez tout le code par le code suivant :

 [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs#1)]

   Le code utilise la propriété [Console.WindowHeight](xref:System.Console.WindowHeight) pour déterminer le nombre de lignes de la fenêtre de console. Chaque fois que la propriété [Console.CursorTop](xref:System.Console.CursorTop) est supérieure ou égale au nombre total de lignes dans la fenêtre de console, le code efface la fenêtre de console et affiche à nouveau un message pour l’utilisateur.

   Le programme lui-même demande simplement à l’utilisateur de saisir une chaîne. Ensuite, il indique si la chaîne commence par une majuscule. Si l’utilisateur appuie sur la touche **Entrée** sans saisir de chaîne, la fenêtre de console se ferme et l’application se termine.

1. Si nécessaire, modifiez la barre d’outils pour compiler la version **Debug** du projet `ShowCase`, comme le montre l’illustration suivante.

   ![Image](./media/showcase-toolbar.jpg)

1. Compilez et exécutez le programme en cliquant sur la flèche verte sur le bouton **ShowCase**.

L’application qui utilise cette bibliothèque peut ensuite être déboguée et finalement publiée en suivant les étapes indiquées dans [Débogage de votre application C# Hello World avec Visual Studio 2017](debugging-with-visual-studio-2017.md) et [Publication de votre application Hello World avec Visual Studio 2017](publishing-with-visual-studio-2017.md).

## <a name="distributing-the-library-in-a-nuget-package"></a>Distribution de la bibliothèque dans un package NuGet ##

Votre bibliothèque de classes peut être rendue plus largement disponible en la publiant sous forme de package NuGet. Visual Studio ne prend pas en charge la création des packages NuGet. Pour en créer un, vous utilisez [ `dotnet.exe` l’utilitaire de ligne de commande](../../core/tools/dotnet.md) comme suit :

1. Ouvrez une fenêtre de console. Par exemple, dans la zone **Demandez-moi quelque chose** de la barre des tâches Windows, saisissez `Command Prompt`, puis choisissez l’application de bureau **Invite de commandes** pour ouvrir la fenêtre de console.

1. Accédez au répertoire de votre projet de bibliothèque. En règle générale, sauf si vous avez reconfiguré l’emplacement du fichier, il se trouve dans le répertoire `Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary`. Le répertoire contient votre code source et un fichier projet, `StringLibrary.csproj`.

1. Émettez la commande `dotnet.exe pack --no-build`. L’utilitaire `dotnet.exe` génère un package avec l’extension .nupkg.

   > [!TIP]
   > Si le répertoire contenant `dotnet.exe` ne se trouve pas dans votre chemin d’accès, vous pouvez trouver son emplacement en saisissant `where dotnet.exe` dans la fenêtre de console.

Pour plus d’informations sur la création de packages NuGet, consultez [Création d’un Package NuGet avec les outils multiplateformes](../../core/deploying/creating-nuget-packages.md).
