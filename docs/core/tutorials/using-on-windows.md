---
title: "Bien démarrer avec .NET Core sur Windows"
description: "Bien démarrer avec .NET Core sur Windows à l’aide de Visual Studio 2015"
keywords: .NET, .NET Core
author: bleroy
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: d743134a-08a3-4ff6-aab7-49f71f0568c3
translationtype: Human Translation
ms.sourcegitcommit: 54da8aebd64e86c064214074bc261f72c3b0aedc
ms.openlocfilehash: 299d479ce74a0e1f41ff42a0e6619f4964788194

---

# <a name="getting-started-with-net-core-on-windows-using-visual-studio-2015"></a>Bien démarrer avec .NET Core sur Windows à l’aide de Visual Studio 2015

par [Bertrand Le Roy](https://github.com/bleroy) et [Phillip Carter](https://github.com/cartermp)

Visual Studio 2015 fournit un environnement de développement complet pour le développement d’applications .NET Core. Les procédures figurant dans ce document décrivent les étapes nécessaires pour créer un certain nombre de solutions .NET Core standard ou des solutions incluant des composants .NET Core à l’aide de Visual Studio. Les scénarios présentés incluent le test et l’utilisation de bibliothèques tierces qui n’ont pas été explicitement générées pour la version la plus récente de .NET Core. 

## <a name="prerequisites"></a>Prérequis

Suivez les instructions stipulées dans [notre page de prérequis](../windows-prerequisites.md) pour mettre à jour votre environnement.

## <a name="getting-started"></a>Commencer

Les étapes suivantes permette de configurer Visual Studio 2015 pour le développement .NET Core :

1. Ouvrez Visual Studio, et dans le menu **Fichier**, choisissez **Nouveau**, puis **Projet**.

2. Dans la boîte de dialogue **Nouveau projet**, dans la liste **Modèles**, développez le nœud **Visual C#**, puis choisissez **.NET Core**. Trois nouveaux modèles de projet doivent s’afficher pour la **Bibliothèque de classes (.NET Core)**, l’**Application console (.NET Core)** et l’**Application web ASP.NET Core (.NET Core)**.

<a name="a-solution-using-only-net-core-projects"></a>Une solution utilisant uniquement des projets .NET Core
----------------------------------------

### <a name="writing-the-library"></a>Écriture de la bibliothèque

1. Dans Visual Studio, choisissez **Fichier**, **Nouveau**, **Projet**. Dans la boîte de dialogue **Nouveau projet**, développez le nœud **Visual C#**, choisissez le nœud **.NET Core**, puis choisissez **Bibliothèque de classes (.NET Core)**. 

2. Nommez le projet « Library » et la solution « Golden ». Laissez l’option **Créer le répertoire pour la solution** activée. Cliquez sur **OK**.

3. Dans l’Explorateur de solutions, ouvrez le menu contextuel du nœud **Références**, puis choisissez **Gérer les packages NuGet**.

4. Choisissez « nuget.org » comme **Source de package**, puis choisissez l’onglet **Parcourir**. Recherchez **Newtonsoft.Json**. Cliquez sur **Installer**. 

5. Ouvrez le menu contextuel du nœud **Références**, puis choisissez **Restaurer les packages**.

6. Renommer le fichier `Class1.cs` en `Thing.cs`. Acceptez le renommage de la classe. Supprimez le constructeur et ajoutez une méthode : `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`

7. Dans le menu **Générer** , choisissez **Générer la solution**.

   La solution doit se générer sans erreur.

### <a name="writing-the-test-project"></a>Écriture du projet de test

1. Dans l’Explorateur de solutions, ouvrez le menu contextuel du nœud **Solution** et choisissez **Ajouter**, **Nouveau dossier de solution**. Nommez le dossier « test ». 
   Il s’agit seulement d’un dossier de solution, et non d’un dossier physique.

2. Ouvrez le menu contextuel du dossier **test**, puis choisissez **Ajouter**, **Nouveau projet**. Dans la boîte de dialogue **Nouveau projet**, choisissez **Application console (.NET Core)**. Nommez-le « TestLibrary » et placez-le explicitement sous le chemin `Golden\test`. 

> [!IMPORTANT]
> Le projet doit être une application console, et non une bibliothèque de classes.

3. Dans le projet **TestLibrary**, ouvrez le menu contextuel du nœud **Références**, puis choisissez **Ajouter une référence**. 

4. Dans la boîte de dialogue **Gestionnaire de références**, cochez **Bibliothèque** sous le nœud **Projets**, **Solution**, puis cliquez sur **OK**. 

5. Dans le projet **TestLibrary**, ouvrez le fichier `project.json`, puis remplacez `"Library": "1.0.0-*"` par `"Library": {"target": "project", "version": "1.0.0-*"}`. 

   L’objectif est ici d’éviter que le projet `Library` soit résolu comme étant un package NuGet de même nom. Le fait d’attribuer explicitement à la cible la valeur « project » est l’assurance que les outils rechercheront d’abord un projet de ce nom, et non un package. 
   
6. Dans le projet **TestLibrary**, ouvrez le menu contextuel du nœud **Références**, puis choisissez **Restaurer les packages**.

7. Ouvrez le menu contextuel du nœud **Références**, puis choisissez **Gérer les packages NuGet**.

8. Choisissez « nuget.org » comme **Source de package**, puis choisissez l’onglet **Parcourir**. Cochez la case **Inclure la version préliminaire**, puis recherchez **xUnit** version 2.2.0 ou plus récente, puis cliquez sur **Installer**. 

9. Recherchez **dotnet-test-xunit** version 2.2.0 ou plus récente, puis cliquez sur **Installer**.

10. Modifiez le fichier `project.json`, et remplacez `"imports": "dnxcore50"` par `"imports": [ "dnxcore50", "portable-net45+win8" ]`. 

   Cela permet au projet de restaurer d’utiliser correctement les bibliothèques xunit : ces bibliothèques ont été compilées pour être utilisées avec des profils portables qui incluent « portable-net45+win8 », mais pas .NET Core, qui n’existait pas au moment de leur génération. `import` assouplit les vérifications de versions des outils au moment de la génération. Vous pouvez maintenant restaurer les packages sans erreur.

11. Modifiez `project.json` pour ajouter `"testRunner": "xunit",` après la section `"frameworks"`.

12. Ajoutez un fichier de classe `LibraryTests.cs` au projet **TestLibrary**, ajoutez les directives `using` `using Xunit;` et `using Library;` au début du fichier, puis ajoutez le code suivant à la classe :
    ```csharp
    [Fact]
    public void ThingGetsObjectValFromNumber() {
        Assert.Equal(42, new Thing().Get(42));
    }
    ```
    * Supprimez éventuellement le fichier `Program.cs` du projet **TestLibrary**, puis retirez `"buildOptions": {"emitEntryPoint": true},` de `project.json`.

   Vous devez maintenant être en mesure de générer la solution. 
   
13. Dans le menu **Test**, choisissez **Windows**, **Explorateur de tests** puis, dans l’Explorateur de tests, choisissez **Exécuter tout**.
   
   Le test doit réussir.

### <a name="writing-the-console-app"></a>Écriture de l’application console

1. Dans l’Explorateur de solutions, ouvrez le menu contextuel du dossier `src`ajoutez un nouveau projet **Application console (.NET Core)**. Nommez-le « App », puis définissez l’emplacement sur `Golden\src`.

2. Dans le projet **App**, ouvrez le menu contextuel du nœud **Références**, puis choisissez **Ajouter**, **Référence**. 

3. Dans la boîte de dialogue **Gestionnaire de références**, cochez **Bibliothèque** sous le nœud **Projets**, **Solution**, puis cliquez sur **OK**.

4. Dans le projet **App**, ouvrez le fichier `project.json`, puis remplacez `"Library": "1.0.0-*"` par `"Library": {"target": "project"}`.

5. Ouvrez le menu contextuel du nœud **Références**, puis choisissez **Restaurer les packages**.

6. Ouvrez le menu contextuel du nœud **App**, puis choisissez **Définir comme projet de démarrage**.

7. Ouvrez le fichier `Program.cs`, ajoutez une directive `using Library;` en haut du fichier, puis ajoutez `Console.WriteLine($"The answer is {new Thing().Get(42)}");` à la méthode `Main`.

8. Définissez un point d’arrêt après la ligne que vous venez d’ajouter.

9. Appuyez sur F5 pour exécuter l’application.

   L’application doit se générer sans erreur et atteindre le point d’arrêt. Vous pouvez également vérifier que la sortie de l’application est « The answer is 42. ».

<a name="a-mixed-net-core-library-and-net-framework-application"></a>Une bibliothèque .NET Core avec une application .NET Framework
--------------------------------------------------------

En partant de la solution obtenue avec le script précédent, procédez comme suit :

1. Dans l’Explorateur de solutions, ouvrez le fichier `project.json` du projet **Library**, puis remplacez `"frameworks": {
    "netstandard1.6" }` par `"frameworks": {
    "netstandard1.4" }`.

2. Dans le projet **Library**, ouvrez le menu contextuel du nœud **Références**, puis choisissez **Restaurer les packages**.

   La solution doit toujours se générer et fonctionner exactement comme auparavant : le test doit réussir et l’application console doit s’exécuter et pouvoir être déboguée.

3. Dans le projet **Library**, ouvrez le menu contextuel, puis choisissez **Générer**.

4. Dans l’Explorateur de solutions, ouvrez le menu contextuel du dossier `src`, puis choisissez **Ajouter**. , **Nouveau projet**.

5. Dans la boîte de dialogue **Nouveau projet**, choisissez le nœud **Visual C#**, puis choisissez **Application console**.

> [!IMPORTANT]
> Veillez à choisir une application console standard, et pas la version .NET Core. Dans cette section, vous allez utiliser la bibliothèque à partir d’une application .NET Framework.

6. Nommez le projet « FxApp » et définissez l’emplacement sur `Golden\src`.

7. Dans le projet **FxApp**, ouvrez le menu contextuel du nœud **Références**, puis choisissez **Ajouter une référence**.

8. Dans la boîte de dialogue **Gestionnaire de références**, choisissez **Parcourir**, accédez à l’emplacement du fichier `Library.dll` généré (sous le chemin ..Golden\src\Library\bin\Debug\netstandard1.4), puis cliquez sur **Ajouter**. 

   Comme autre moyen de référencer du code .NET Core à partir du .NET Framework, vous pouvez également créer un package de la bibliothèque et référencer ce package.

9. Ouvrez le menu contextuel du nœud **Références**, puis choisissez **Gérer les packages NuGet**.

10. Choisissez « nuget.org » comme **Source de package**, puis choisissez l’onglet **Parcourir**. Cochez la case **Inclure la version préliminaire**, puis recherchez **Newtonsoft.Json**. Cliquez sur **Installer**. 

11. Dans le projet **FxApp**, ouvrez le fichier `Program.cs`, ajoutez une directive `using Library;` en haut du fichier, puis ajoutez `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` à la méthode `Main` du programme.

12. Définissez un point d’arrêt après la ligne que vous venez d’ajouter.

13. Définissez **FxApp** comme application de démarrage pour la solution.

14. Appuyez sur F5 pour exécuter l'application.

   L’application doit se générer et atteindre le point d’arrêt. La sortie de l’application doit être « The answer is 42. ».
   
   > [!TIP]
   > Sur la plateforme Windows, vous pouvez utiliser MSTest. Vous trouverez des informations complémentaires dans le [document qui traite de l’utilisation de MSTest sur Windows](../testing/using-mstest-on-windows.md).

<a name="moving-a-library-from-netstandard-14-to-13"></a>Déplacement d’une bibliothèque de netstandard 1.4 vers 1.3
--------------------------------------------

1. Dans l’Explorateur de solutions, ouvrez le fichier `project.json` dans le projet **Library**.

2. Remplacez `frameworks": { "netstandard1.4" }` par `frameworks": { "netstandard1.3" }`.

3. Dans le projet **Library**, ouvrez le menu contextuel du nœud **Références**, puis choisissez **Restaurer les packages**.

4. Dans le menu **Générer**, choisissez **Générer une bibliothèque**.

5. Supprimez la référence `Library` du projet **FxApp**, puis rajoutez-la à l’aide du chemin ..Golden\src\Library\bin\Debug\netstandard1.3. Elle référence désormais la version 1.3.

6. Appuyez sur F5 pour exécuter l'application.

   Tout doit continuer à fonctionner comme avant. Vérifiez que la sortie de l’application est « The answer is 42. », que le point d’arrêt a été atteint et que les variables peuvent être inspectées.

<a name="a-mixed-pcl-library-and-net-framework-application"></a>Une bibliothèque PCL avec une application .NET Framework
--------------------------------------------------

Fermez la solution précédente si elle a été ouverte : vous allez commencer un nouveau script à partir de cette section.

### <a name="writing-the-library"></a>Écriture de la bibliothèque

1. Dans Visual Studio, choisissez **Fichier**, **Nouveau**, **Projet**. Dans la boîte de dialogue **Nouveau projet**, développez le nœud **Visual C#**, puis choisissez **Bibliothèque de classes (portable pour iOS, Android et Windows)**. 

2. Nommez le projet « PCLLibrary » et la solution « GoldenPCL ». Laissez l’option **Créer le répertoire pour la solution** activée. Cliquez sur **OK**.

3. Dans l’Explorateur de solutions, ouvrez le menu contextuel du nœud **Références**, puis choisissez **Gérer les packages NuGet**.

4. Choisissez « nuget.org » comme **Source de package**, puis choisissez l’onglet **Parcourir**. Cochez la case **Inclure la version préliminaire**, puis recherchez **Newtonsoft.Json**. Cliquez sur **Installer**. 

5. Renommez la classe « Thing » et ajoutez une méthode : `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`

6. Dans le menu **Générer**, choisissez **Générer la solution**, puis vérifiez que la solution se génère.

### <a name="writing-the-console-app"></a>Écriture de l’application console

1. Dans l’Explorateur de solutions, ouvrez le menu contextuel du nœud **Solution 'GoldenPCL'**, puis choisissez **Ajouter**, **Nouveau projet**. Dans la boîte de dialogue **Nouveau projet**, développez le nœud **Visual C#**, choisissez **Application console**, puis nommez le projet « App ». 

2. Dans le projet **App**, ouvrez le menu contextuel du nœud **Références**, puis choisissez **Ajouter**, **Référence**. 

3. Dans la boîte de dialogue **Gestionnaire de références**, choisissez **Parcourir**, accédez à l’emplacement du fichier `PCLLibrary.dll` généré (sous le chemin ..\GoldenPCL\PCLLibrary\bin\Debug), puis cliquez sur **Ajouter**. 

4. Dans le projet **App**, ouvrez le fichier `Program.cs`, ajoutez une directive `using PCLLibrary;` en haut du fichier, puis ajoutez `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` à la méthode `Main` du programme.

5. Définissez un point d’arrêt après la ligne que vous venez d’ajouter.

6. Dans l’Explorateur de solutions, ouvrez le menu contextuel du nœud **App**, puis choisissez **Définir comme projet de démarrage**.

7. Appuyez sur F5 pour exécuter l'application.

   L’application doit se générer, s’exécuter et atteindre le point d’arrêt après avoir généré la sortie « The answer is 42. ».

<a name="moving-a-pcl-to-a-netstandard-library"></a>Déplacement d’une bibliothèque de classes portable vers une bibliothèque NetStandard
-------------------------------------
Les outils de bibliothèque de classes portable peuvent modifier automatiquement votre bibliothèque de classes portable pour cibler .NET Standard. 

1.  Double-cliquez sur le nœud « Propriétés » pour ouvrir la page de propriétés du projet

2.  Sous l’en-tête « Ciblage », cliquez sur le lien hypertexte « Cibler .NET Platform Standard »

3.  Cliquez sur « Oui » quand vous êtes invité à confirmer l’opération

Les outils sélectionnent automatiquement la version de .NET Standard qui inclut toutes les cibles initiales de votre bibliothèque de classes portable. Vous pouvez cibler une version différente de .NET Standard à l’aide de la liste déroulante .NET Standard dans la page de propriétés du projet.
 
* Si vous aviez précédemment un fichier packages.config, vous pouvez être invité à désinstaller tous les packages installés avant la conversion.

### <a name="manually-edit-projectjson-to-target-net-standard-from-an-existing-portable-class-library"></a>Modifiez manuellement project.json pour cibler .NET Standard à partir d’une bibliothèque de classes portable existante

1.  Si votre fichier project.json contient « dnxcore50 » dans l’élément « support », supprimez-le

2.  Supprimez la dépendance sur « Microsoft.NETCore »

3.  Modifiez la dépendance sur « Microsoft.NETCore.Portable.Compatibility » en remplaçant la version « 1.0.0 » par la version « 1.0.1 »

4.  Ajoutez une dépendance sur « NETStandard.Library » version « 1.6.0 »

5.  Dans l’élément « frameworks », supprimez le framework « dotnet » (et l’élément « imports » qu’elle contient)

6.  Ajoutez ` "netstandard1.x” : { } ` à l’élément frameworks, où x est remplacé par la version de .NET Standard que vous voulez cibler

### <a name="example-projectjson"></a>Exemple de fichier project.json

Ce fichier project.json inclut des clauses supports pour UWP et .NET 4.6, et cible netstandard1.3 :
```
{
  "supports": {
    "net46.app": {},
    "uwp.10.0.app": {},
  },
  "dependencies": {
    "NETStandard.Library": "1.6.0",
    "Microsoft.NETCore.Portable.Compatibility": "1.0.1"
  },
  "frameworks": {
    "netstandard1.3" : {}
  }
}
```





<!--HONumber=Nov16_HO1-->


