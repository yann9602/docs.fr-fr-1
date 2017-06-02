---
title: "Génération d’une bibliothèque de classes avec C# et .NET Core dans Visual Studio 2017"
description: "Découvrez comment créer une bibliothèque de classes écrite en C# à l’aide de Visual Studio 2017"
keywords: ".NET Core, bibliothèque de classes .NET Standard, Visual Studio 2017"
author: BillWagner
ms.author: wiwagn
ms.date: 04/17/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: c849ca26-6a25-4d35-9544-f343af88e0e7
ms.translationtype: Human Translation
ms.sourcegitcommit: 39e8e757a446b30ab18914465853138e1c239e40
ms.openlocfilehash: 1ecccb03bc28da51a580b790b5ba8dd594bb7f18
ms.contentlocale: fr-fr
ms.lasthandoff: 05/03/2017

---

# <a name="building-a-class-library-with-c-and-net-core-in-visual-studio-2017"></a>Génération d’une bibliothèque de classes avec C# et .NET Core dans Visual Studio 2017

Une *bibliothèque de classes* définit des types et des méthodes qui peuvent être appelés par une application. Une bibliothèque de classes développée à l’aide de .NET Core prend en charge la bibliothèque .NET Standard, qui permet à votre bibliothèque d’être appelée par n’importe quelle plateforme .NET qui prend en charge cette version de la bibliothèque .NET Standard. Quand vous avez terminé votre bibliothèque de classes, vous pouvez décider de la distribuer ou non comme un composant tiers, ou de l’inclure ou non dans un composant groupé avec une ou plusieurs applications.

> [!NOTE]
> Pour obtenir la liste des versions de .NET Standard et des plateformes prises en charge, consultez la page [Bibliothèque .NET Standard](../../standard/library.md).

Dans cette rubrique, vous créez une bibliothèque d’utilitaire simple qui contient une seule méthode de gestion de chaîne. Vous l’implémentez en tant que [méthode d’extension](../../csharp/programming-guide/classes-and-structs/extension-methods.md), pour pouvoir l’appeler comme s’il s’agissait d’un membre de la classe @System.String.

## <a name="creating-a-class-library-solution"></a>Création d'une solution de bibliothèque de classes

Commencez par créer une solution pour votre projet de bibliothèque de classes et ses projets connexes. Une solution Visual Studio sert simplement de conteneur pour un ou plusieurs projets. Pour créer la solution :

1. Dans la barre de menus de Visual Studio, choisissez **Fichier** > **Nouveau** > **Projet**.

1. Dans la boîte de dialogue **Nouveau projet**, développez le nœud **Autres types de projets** et sélectionnez **Solutions Visual Studio**. Nommez la solution « ClassLibraryProjects » puis sélectionnez le bouton **OK**.

   ![Boîte de dialogue Nouveau projet](./media/library-with-visual-studio/newproject.png)

## <a name="creating-the-class-library-project"></a>Création du projet de bibliothèque de classes

Créez votre projet de bibliothèque de classes :

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur la solution **ClassLibraryProjects** et, dans le menu contextuel, sélectionnez **Ajouter** > **Nouveau projet**.

1. Dans la boîte de dialogue **Ajouter un nouveau projet**, sélectionnez le nœud **.Net Core** puis choisissez le modèle de projet **Bibliothèque de classes (.NET Core)**. Dans la zone de texte **Nom**, entrez « StringLibrary » comme nom de projet. Sélectionnez **OK** pour créer le projet de bibliothèque de classes.

   ![Boîte de dialogue Ajouter un nouveau projet](./media/library-with-visual-studio/libproject.png)

   ![Fenêtre d’application Visual Studio montrant le code du modèle de bibliothèque de classes par défaut](./media/library-with-visual-studio/stringlibrary.png)

1. Remplacez le code de la fenêtre de code par le code suivant et enregistrez le fichier :

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs#1)]

   La bibliothèque de classes, `UtilityLibraries.StringLibrary`, contient une méthode nommée `StartsWithUpper`, qui retourne une valeur @System.Boolean qui indique si l’instance actuelle de la chaîne commence par une majuscule. La norme Unicode distingue les caractères minuscules des caractères majuscules. Dans .NET Core, la méthode [`Char.IsUpper`](xref:System.Char.IsUpper(System.Char)) retourne `true` si un caractère est en majuscule.

1. Dans la barre de menus, sélectionnez **Générer** > **Générer la solution**. Le projet devrait être compilé sans erreur.

   ![Volet de sortie indiquant que la génération a réussi](./media/library-with-visual-studio/buildsucceeds.png)

## <a name="next-step"></a>Étape suivante

Vous avez créé la bibliothèque correctement. Comme vous n’avez appelé aucune de ses méthodes, vous ne savez pas si elle fonctionne comme prévu. L’étape suivante du développement de votre bibliothèque consiste à la tester en utilisant un [Projet de test unitaire C#](testing-library-with-visual-studio.md).

