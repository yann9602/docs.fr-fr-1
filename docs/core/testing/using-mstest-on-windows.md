---
title: Utiliser MSTest avec .NET Core sur Windows
description: "Comment utiliser MSTest avec .NET Core sur Windows en utilisant Visual Studio 2015"
keywords: MSTest, .NET, .NET Core
author: ncarandini
manager: wpickett
ms.date: 08/18/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: ed447641-3e85-4e50-b7ed-004630048a3e
translationtype: Human Translation
ms.sourcegitcommit: 6795f1ace77e6f4d1b2fe07e6281f4acb6d21271
ms.openlocfilehash: c9d6bb1d45b9a6cb88334050669a4c064e53d54e

---

# <a name="unit-testing-with-mstest-and-net-core-on-windows-using-visual-studio-2015"></a>Effectuer des tests unitaires avec MSTest et .NET Core sur Windows en utilisant Visual Studio 2015

Même si xUnit pourrait s’avérer être un meilleur choix quand il s’agit de cibler plusieurs plateformes, il est également possible d’utiliser MSTest avec .NET Core sur Windows.

## <a name="prerequisites"></a>Prérequis

Suivez les instructions fournies dans [Bien démarrer avec .NET Core sur Windows](../tutorials/using-on-windows.md) pour créer le projet de bibliothèque.

### <a name="writing-the-test-project-using-mstest"></a>Écriture du projet de test en utilisant MSTest

1. Dans l’Explorateur de solutions, ouvrez le menu contextuel pour le nœud **Solution** et choisissez **Ajouter**, **Nouveau dossier de solution**. Nommez le dossier « test ». 
   Il s’agit seulement d’un dossier de solution, et non d’un dossier physique.

2. Ouvrez le menu contextuel du dossier **test**, puis choisissez **Ajouter**, **Nouveau projet**. Dans la boîte de dialogue **Nouveau projet**, choisissez **Application console (.NET Core)**. Nommez-le « TestLibrary » et placez-le explicitement sous le chemin `Golden\test`. 

   > [!IMPORTANT]
   > Le projet doit être une application console, et non une bibliothèque de classes.

3. Dans le projet **TestLibrary**, ouvrez le menu contextuel du nœud **Références**, puis choisissez **Ajouter une référence**. 

4. Dans la boîte de dialogue **Gestionnaire de références**, cochez **Bibliothèque** sous le nœud **Projets**, **Solution**, puis cliquez sur **OK**. 

5. Dans le projet **TestLibrary**, ouvrez le fichier `project.json`, puis remplacez `"Library": "1.0.0-*"` par `"Library": {"target": "project"}`. 

   L’objectif est ici d’éviter que le projet `Library` soit résolu comme étant un package NuGet de même nom. Le fait de cibler explicitement « project » est l’assurance que les outils rechercheront d’abord un projet de ce nom, et non un package. 

6. Ouvrez le menu contextuel pour le nœud **Références**, puis choisissez **Gérer les packages NuGet**.

7. Choisissez « nuget.org » comme **Source de package**, puis choisissez l’onglet **Parcourir**. Cochez la case **Inclure la version préliminaire**, puis recherchez **MSTest.TestFramework** version 1.0.1-preview ou plus récente, puis cliquez sur **Installer**. 

8. Recherchez **dotnet-test-mstest** version 1.1.1-preview ou plus récente, puis cliquez sur **Installer**.

9. Modifiez `project.json` pour ajouter `"testRunner": "mstest",` après la section `"version"`.

10. Ajoutez un fichier de classe `LibraryTests.cs` au projet **TestLibrary**, ajoutez les directives `using` `Microsoft.VisualStudio.TestTools.UnitTesting;` et `using Library;` au début du fichier, puis ajoutez le code suivant à la classe :
    ```csharp
    [TestClass]
    public class LibraryTests
    {
        [TestMethod]
        public void ThingGetsObjectValFromNumber()
        {
            Assert.AreEqual(42, new Thing().Get(42));
        }
    }
    ```
    * Supprimez éventuellement le fichier `Program.cs` du projet **TestLibrary**, puis retirez `"buildOptions": {"emitEntryPoint": true},` de `project.json`.

   Vous devez maintenant être en mesure de générer la solution. 
   
11. Dans le menu **Test**, choisissez **Windows**, **Explorateur de tests** puis, dans l’Explorateur de tests, choisissez **Exécuter tout**.
   
   Le test doit réussir.



<!--HONumber=Nov16_HO1-->


