---
title: "Utilisation d’une bibliothèque de classes avec .NET Core dans Visual Studio 2017 | Microsoft Docs"
description: "Découvrez comment appeler les membres dans une bibliothèque de classes avec Visual Studio 2017."
keywords: ".NET Core, bibliothèque de classes .NET Core, .NET Standard, distribution de bibliothèque de classes .NET Standard"
author: BillWagner
ms.author: wiwang
ms.date: 04/17/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: d7b94076-1108-4174-94e7-a18f00072bb7
ms.translationtype: Human Translation
ms.sourcegitcommit: 4437ce5d344cf06d30e31911def6287999fc6ffc
ms.openlocfilehash: 5ad07e4116c75eb9b9d513c2a4fe43dfe62660d5
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---

<a id="consuming-a-class-library-with-net-core-in-visual-studio-2017" class="xliff"></a>

# Utilisation d’une bibliothèque de classes avec .NET Core dans Visual Studio 2017

Une fois que vous avez suivi les étapes de [Création d’une bibliothèque de classes C# avec .NET Core dans Visual Studio 2017](./library-with-visual-studio.md) et [Test d’une bibliothèque de classes avec .NET Core dans Visual Studio 2017](testing-library-with-visual-studio.md) pour générer et tester votre bibliothèque de classes, et que vous avez créé une version Release de la bibliothèque, l’étape suivante consiste à la rendre accessible aux appelants. Pour cela, deux solutions s'offrent à vous :

* Si la bibliothèque doit être utilisée par une seule solution (par exemple s’il s’agit d’un composant dans une seule application de grande taille), vous pouvez l’inclure en tant que projet dans votre solution.

* Si la bibliothèque est généralement accessible, vous pouvez la distribuer comme package NuGet.

<a id="including-a-library-as-a-project-in-a-solution" class="xliff"></a>

## Inclusion d’une bibliothèque en tant que projet dans une solution

Tout comme vous avez inclus des tests unitaires dans la même solution que votre bibliothèque de classes, vous pouvez inclure votre application dans le cadre de cette solution. Par exemple, vous pouvez utiliser votre bibliothèque de classes dans une application console qui invite l’utilisateur à entrer une chaîne et indique si son premier caractère est une majuscule :

1. Ouvrez la `ClassLibraryProjects` solution que vous avez créée dans la rubrique [Création d’une bibliothèque de classes C# avec .NET Core dans Visual Studio 2017](./library-with-visual-studio.md). Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur la solution **ClassLibraryProjects** et, dans le menu contextuel, sélectionnez **Ajouter** > **Nouveau projet**.

1. Dans la boîte de dialogue **Ajouter un nouveau projet**, sélectionnez le nœud **.NET Core** puis choisissez le modèle de projet **Application console (.NET Core)**. Dans la zone de texte **Nom**, tapez « ShowCase », puis sélectionnez le bouton **OK**.

   ![Boîte de dialogue Ajouter un nouveau projet](./media/consuming-library-with-visual-studio/addnewproject.png)

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **ShowCase**, puis sélectionnez **Définir comme projet de démarrage** dans le menu contextuel.

   ![Menu contextuel de ShowCase](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. Initialement, votre projet n’a pas accès à votre bibliothèque de classes. Pour lui permettre d’appeler des méthodes dans votre bibliothèque de classes, vous créez une référence à la bibliothèque de classes. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Dépendances** du projet `ShowCase` et sélectionnez **Ajouter une référence**.

   ![Menu contextuel Dépendances de ShowCase](./media/consuming-library-with-visual-studio/addreference.png)

1. Dans la boîte de dialogue **Gestionnaire de références**, sélectionnez **StringLibrary**, votre projet de bibliothèque de classe, puis sélectionnez le bouton **OK**.

   ![Gestionnaire de références](./media/consuming-library-with-visual-studio/referencemanager.png)

1. Dans la fenêtre de code pour le fichier *Program.cs*, remplacez tout le code par le code suivant :

 [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs#1)]

   Le code utilise la propriété [Console.WindowHeight](xref:System.Console.WindowHeight) pour déterminer le nombre de lignes de la fenêtre de console. Quand la propriété [Console.CursorTop](xref:System.Console.CursorTop) est supérieure ou égale au nombre total de lignes dans la fenêtre de console, le code efface la fenêtre de console et affiche un message à l’utilisateur.

   Le programme invite l’utilisateur à entrer une chaîne. Il indique si la chaîne commence par une majuscule. Si l’utilisateur appuie sur la touche Entrée sans entrer une chaîne, l’application se termine et la fenêtre de console se ferme.

1. Si nécessaire, changez la barre d’outils pour compiler la version **Debug** du projet `ShowCase`. Compilez et exécutez le programme en sélectionnant la flèche verte sur le bouton **ShowCase**.

   ![Image](./media/consuming-library-with-visual-studio/toolbar.png)

Vous pouvez déboguer et publier l’application qui utilise cette bibliothèque en suivant les étapes de [Débogage de votre application C# Hello World avec Visual Studio 2017](debugging-with-visual-studio.md) et de [Publication de votre application Hello World avec Visual Studio 2017](publishing-with-visual-studio.md).

<a id="distributing-the-library-in-a-nuget-package" class="xliff"></a>

## Distribution de la bibliothèque dans un package NuGet

Vous pouvez rendre votre bibliothèque de classes disponible à grande échelle en la publiant sous forme de package NuGet. Visual Studio ne prend pas en charge la création des packages NuGet. Pour en créer un, vous utilisez l’[`dotnet`utilitaire de ligne de commande](../../core/tools/dotnet.md) :

1. Ouvrez une fenêtre de console. Par exemple, dans la zone de texte **Posez-moi une question** dans la barre des tâches Windows, entrez `Command Prompt` (ou `cmd` en abrégé) et ouvrez une fenêtre de console en sélectionnant l’application de poste de travail **Invite de commandes** ou en appuyant sur Entrée si elle est sélectionnée dans les résultats de la recherche.

1. Accédez au répertoire de votre projet de bibliothèque. Sauf si vous avez reconfiguré l’emplacement habituel du fichier, il se trouve dans le répertoire *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary*. Le répertoire contient votre code source et un fichier projet, *StringLibrary.csproj*.

1. Émettez la commande `dotnet pack --no-build`. L’utilitaire `dotnet` génère un package avec une extension *.nupkg*.

   > [!TIP]
   > Si le répertoire contenant *dotnet.exe* ne se trouve pas dans votre chemin, vous pouvez trouver son emplacement en entrant `where dotnet.exe` dans la fenêtre de console.

Pour plus d’informations sur la création de packages NuGet, consultez [Création d’un Package NuGet avec les outils multiplateformes](../../core/deploying/creating-nuget-packages.md).

