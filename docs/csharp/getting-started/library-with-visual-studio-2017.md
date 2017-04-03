---
title: "Génération d’une bibliothèque de classes avec C# et .NET Core dans Visual Studio 2017"
description: "Découvrez comment créer une bibliothèque de classes écrite en C# à l’aide de Visual Studio 2017"
keywords: ".NET Core, bibliothèque de classes .NET Standard, Visual Studio 2017"
author: stevehoag
ms.author: shoag
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: c849ca26-6a25-4d35-9544-f343af88e0e7
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 28fa60cdcf8e0056314af271208759eadd8503a5
ms.lasthandoff: 03/13/2017

---

# <a name="building-a-class-library-with-c-and-net-core-in-visual-studio-2017"></a>Génération d’une bibliothèque de classes avec C# et .NET Core dans Visual Studio 2017 #

Une bibliothèque de classes définit des types et méthodes qui peuvent être appelés à partir de n’importe quelle application. Une bibliothèque de classes développée à l’aide de .NET Core prend en charge la bibliothèque .NET Standard, qui permet à votre bibliothèque d’être appelée par n’importe quelle plateforme .NET qui prend en charge cette version de la bibliothèque .NET Standard. Lorsque vous avez terminé votre bibliothèque de classes, vous pouvez décider de la distribuer ou non comme un composant tiers, ou de l’inclure ou non dans un composant qui est fourni avec une ou plusieurs applications.

> [!NOTE]
> Pour obtenir la liste des versions de .NET Standard et des plateformes prises en charge, consultez la page [Bibliothèque .NET Standard](../../standard/library.md).

Dans cette rubrique, nous allons créer une bibliothèque d’utilitaire simple qui contient simplement une méthode de gestion de chaîne. Nous allons l’implémenter en tant que [méthode d’extension](../../csharp/programming-guide/classes-and-structs/extension-methods.md) afin qu’elle puisse être appelée comme s’il s’agissait d’un membre de la classe @System.String.

## <a name="creating-a-class-library-solution"></a>Création d'une solution de bibliothèque de classes ##

Commençons par créer une solution pour notre projet de bibliothèque de classes et ses projets connexes. Une solution Visual Studio sert simplement de conteneur pour un ou plusieurs projets. Pour créer la solution :

1. Dans la barre de menus de Visual Studio, choisissez **Fichier**, **Nouveau**, **Projet**.

1. Dans la boîte de dialogue **Nouveaux projets**, développez le nœud **Autres types de projets**, puis choisissez **Solutions Visual Studio**, comme le montre l’illustration suivante.

   ![Image](./media/solution.jpg)

1. Nommez la solution « ClassLibraryProjects », puis choisissez le bouton **OK**. L’illustration suivante affiche le résultat.

   ![Image](./media/vs_with_solution.jpg)

## <a name="creating-the-class-library-project"></a>Création du projet de bibliothèque de classes ##

Nous pouvons maintenant créer notre projet de bibliothèque de classes :

1. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du nœud **ClassLibraryProjects** et sélectionnez **Ajouter**, **Nouveau projet**.

1. Dans la boîte de dialogue **Ajouter nouveau projet**, choisissez le nœud **.Net Core**, puis choisissez le modèle de projet **Bibliothèque de classes (.NET Standard)**.

1. Dans la zone de texte **Nom**, saisissez « StringLibrary » comme nom de projet, comme le montre l'illustration suivante.

   ![Image](./media/lib_project.jpg)

1. Choisissez **OK** pour créer le projet de bibliothèque de classes. L’illustration suivante affiche le résultat.

   ![Image](./media/class_library.jpg)

1. Remplacez le code de la fenêtre de code par le code suivant :

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs#1)]

   La bibliothèque de classes, `UtilityLibraries.StringLibrary`, contient une méthode nommée `StartsWithUpper`, qui retourne une valeur @System.Boolean qui indique si l’instance actuelle de la chaîne commence par une majuscule. Les caractères qui sont en majuscule sont définis par la norme Unicode. Dans .NET Core, la méthode [Char.IsUpper](xref:System.Char.IsUpper(System.Char)) renvoie `true` si un caractère est en majuscule.

1. Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**. Le projet devrait être compilé sans erreur.

## <a name="the-next-step"></a>L’étape suivante ##

Jusqu’ici, nous avons créé la bibliothèque avec succès. Mais comme nous n’avons encore appelé aucune de ses méthodes, nous ne savons pas si elle fonctionne comme prévu. L’étape suivante dans le développement de notre bibliothèque consiste à la tester en utilisant un [Test unitaire de projet C#](testing-library-with-visual-studio.md).



