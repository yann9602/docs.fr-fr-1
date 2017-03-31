---
title: "Test d’une bibliothèque de classes avec .NET Core dans Visual Studio 2017"
description: "Découvrez comment tester une bibliothèque de classes écrite en C# à l’aide de Visual Studio 2017"
keywords: ".NET Core, bibliothèque de classes .NET Standard, Visual Studio 2017, test unitaire"
author: stevehoag
ms.author: shoag
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 069ad711-3eaa-45c6-94d7-b40249cc8b99
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ee21799706b971f0ec13285b0771b32b4367f570
ms.lasthandoff: 03/13/2017

---

# <a name="testing-a-class-library-with-net-core-in-visual-studio-2017"></a>Test d’une bibliothèque de classes avec .NET Core dans Visual Studio 2017 #

Dans [Génération d’une bibliothèque de classes avec C# et .NET Core dans Visual Studio 2017 RC](library-with-visual-studio-2017.md), nous avons créé une bibliothèque de classes simple qui ajoute une méthode d’extension à la classe @System.String. À présent, nous allons créer un test unitaire pour nous assurer que tout fonctionne comme prévu. Nous allons ajouter notre projet de test unitaire à la solution que nous avons créée dans la rubrique précédente.

## <a name="creating-a-unit-test-project"></a>Création d'un projet de test unitaire ##

Pour créer le projet de test unitaire, procédez comme suit :

1. Dans l’Explorateur de solutions, ouvrez le menu contextuel du nœud de solution **ClassLibraryProject** et sélectionnez **Ajouter**, **Nouveau projet**.

   <!-- Need a VS 2017 version  [!NOTE] In addition to a Unit Test project, you can also use Visual Studio to create an XUnit test project for .NET Core. For a walkthrough that includes an XUnit test project, see [Getting started with .NET Core on Windows, using Visual Studio 2015](../../core/tutorials/using-on-windows.md). --> 

1. Dans la boîte de dialogue **Ajouter un nouveau projet**, développez le nœud **Visual C#** et le nœud **.NET Core**, puis choisissez le modèle de projet **Projet de test unitaire (.NET Core)** et nommez-le `StringLibraryTest`, comme le montre l’illustration suivante.

   ![Image](./media/testproject.jpg)

1. Choisissez le bouton **OK** pour créer le projet. Visual Studio crée le projet et ouvre le fichier `UnitTest1.cs` dans la fenêtre de code, comme le montre l'illustration suivante.

   ![Image](./media/unit_test_code_window.jpg)

   Le code source créé par le modèle de test unitaire effectue les opérations suivantes :

   - Il importe l’espace de noms [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) qui contient les types utilisés pour les tests unitaires.

   - Il applique l’attribut [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) à la classe `UnitTest1`. Chaque méthode de test dans une classe de test marquée avec l’attribut \[TestMethod\] sera exécutée automatiquement lorsque le test unitaire est exécuté.

   - Il applique l’attribut [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) pour définir `TestMethod1` comme une méthode de test qui doit être exécutée automatiquement lorsque le test unitaire est exécuté.

1. Dans l’Explorateur de solutions, ouvrez le menu contextuel du nœud **Dépendances** du projet **StringLibraryTest**, puis choisissez **Ajouter une référence**. Cette opération ajoute une référence à votre projet de bibliothèque de classes, `StringLibrary`. 

1. Dans la boîte de dialogue **Gestionnaire de références**, développez le nœud **Projets** et choisissez **Solution**, puis cochez la case à côté de **StringLibrary**, comme le montre l’illustration suivante. L’ajout d’une référence à l’assembly `StringLibrary` permet au compilateur de résoudre les appels aux méthodes **StringLibrary**.

   ![Image](./media/add_reference.jpg)

1. Cliquez sur le bouton **OK** pour fermer la boîte de dialogue **Gestionnaire de références**.

## <a name="adding-and-running-unit-test-methods"></a>Ajout et exécution de méthodes de test unitaire ##

Lorsque Visual Studio exécute un test unitaire, il exécute chaque méthode marquée avec l’attribut [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) dans une classe de test unitaire (la classe à laquelle l’attribut [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) est appliqué. Une méthode de test se termine lorsque la première défaillance survient, ou lorsque tous les tests contenus dans la méthode ont réussi.

Les tests les plus courants appellent des membres de la classe [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx). De nombreuses méthodes d’assertion incluent au moins deux paramètres, à savoir le résultat attendu pour le test et résultat réel du test. Parmi ses méthodes les plus fréquemment appelées :

- `Assert.AreEqual`, qui vérifie que deux valeurs ou objets sont égaux. L’assertion échoue si les valeurs ou les objets ne sont pas égaux.

- `Assert.AreSame`, qui vérifie que deux variables d’objet font référence au même objet. L’assertion échoue si les variables font référence à des objets différents.

- `Assert.IsFalse`, qui vérifie qu’une condition est fausse. L’assertion échoue si la condition est vraie.

- `Assert.IsNotNull`, qui vérifie qu’un objet n’est pas `null`. L’assertion échouera si l’objet est `null`.

En outre, l’attribut [\[ExpectedException\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.expectedexceptionattribute.aspx) peut être utilisé pour indiquer le type d’exception qu’une méthode de test est censée lever. Vous pouvez l’utiliser pour tester les conditions qui doivent aboutir à une exception. Le test échoue si l’exception spécifiée n’est pas levée.

Dans le test de la méthode `StringLibrary.StartsWithUpper`, nous voulons fournir une série de chaînes qui commencent par une majuscule. Nous prévoyons que la méthode renvoie `True` dans de tels cas, nous pouvons donc appeler la méthode [Assert.IsTrue (Boolean, String)](https://msdn.microsoft.com/library/ms243754.aspx). De même, nous voulons fournir des chaînes qui commencent par autre chose qu’un caractère en majuscule. Nous prévoyons que la méthode renvoie False dans ce cas, nous pouvons donc appeler la méthode [Assert.IsFalse (Boolean, String)](https://msdn.microsoft.com/library/ms243805.aspx).

Dans la mesure où notre méthode de bibliothèque gère les chaînes, nous souhaitons également nous assurer qu’elle gère correctement une [chaîne vide](xref:System.String.Empty) (une chaîne valide sans caractères et dont @System.String.Length a la valeur 0) et une chaîne `null` (chaîne qui n’a pas été initialisée). Si vous appelez `StartsWithUpper` comme méthode d’extension sur une instance @System.String, il n’est pas possible de lui passer une chaîne `null`. Toutefois, vous pouvez également l’appeler directement comme méthode statique et passer un seul argument @System.String.

Nous allons définir trois méthodes, chacune appelant sa méthode [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) plusieurs fois pour chaque élément dans un tableau de chaînes. Étant donné que la méthode de test échoue dès qu’elle rencontre le premier échec, nous allons appeler une surcharge de méthode qui permet de passer une chaîne qui indique la valeur de chaîne utilisée dans l’appel de méthode.

Pour créer les méthodes de test :

1. Remplacez le code de la fenêtre de code par le code suivant :

   [!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs#1)]

   Notez que notre test de caractères majuscules dans la méthode `TestStartsWithUpper` inclut la lettre majuscule grecque alpha (U + 0391) et la lettre majuscule cyrillique EM (U + 041C), et le test de caractères minuscules dans la méthode `TestDoesNotStartWithUpper` inclut la lettre minuscule grecque alpha (U + 03B1) et la lettre minuscule cyrillique Gué (U + 0433).

1. Dans la barre de menus, choisissez **Fichier**, **Enregistrer UnitTest1.cs sous...**. Dans la boîte de dialogue **Enregistrer le fichier sous**, cliquez sur la flèche à côté du bouton **Enregistrer**, puis choisissez **Enregistrer avec encodage...***.

1. Dans la boîte de dialogue Confirmer l’enregistrement sous, choisissez le bouton **Oui** pour enregistrer le fichier.

1. À partir de la liste déroulante **Encodage** de la boîte de dialogue **Options d’enregistrement avancées**, choisissez **Unicode (UTF-8 avec signature) - Page de codes 65001**, puis choisissez **OK**.

   Si vous ne parvenez pas à enregistrer votre code source dans un fichier encodé en UTF-8, Visual Studio peut l’enregistrer dans un fichier ASCII. Dans ce cas, le runtime ne décodera pas correctement les caractères en dehors de la plage ASCII, et les résultats des tests ne seront pas précis.

1. Dans la barre de menus, sélectionnez **Test**, **Exécuter**, **Tous les tests**. La fenêtre **Explorateur de tests** doit s’ouvrir et afficher que les deux tests ont réussi, comme le montre l'illustration suivante. Notez que les trois tests sont répertoriés dans la section **Tests réussis** et que la section **Résumé** indique le résultat de la série de tests.

   ![Image](./media/first_test.jpg)

## <a name="handling-test-failures"></a>Gestion des échecs des tests ##

Notre série de tests n’avait aucun échec, nous allons donc le modifier légèrement afin qu’une des méthodes de test échoue :

1. Modifiez le tableau `words` dans la méthode `TestDoesNotStartWithUpper` pour inclure la chaîne « Error », afin que l’instruction se présente comme suit :

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. Exécutez le test en choisissant **Test**, **Exécuter**, **Tous les tests**. La fenêtre **Explorateur de tests** indique maintenant que deux tests ont réussi et un a échoué, comme le montre l'illustration suivante.

   ![Image](./media/failed_test.jpg)

1. Cliquez sur le test ayant échoué, `TestDoesNotStartWith`, dans la section **Échecs de tests**. Le volet inférieur de **l’Explorateur de tests** affiche le message généré par la méthode assert : « Assert.IsFalse a échoué. Attendu pour « Error » : false ; valeur réelle : True », dans l'illustration suivante que **l’Explorateur de tests** affiche. En raison de l’échec, toutes les chaînes dans le tableau après « Error » n’ont pas été testées.

   ![Image](./media/failed_test2.jpg)

1. Supprimez le code qui a été ajouté (`"Error", `) et réexécutez le test. Cela devrait maintenant fonctionner.

## <a name="testing-the-release-version-of-the-library"></a>Test de la version de la version Release de la bibliothèque ##

Nous avons exécuté nos tests sur la version Debug de la bibliothèque. Maintenant que nos tests ont réussi et que nous avons testé correctement notre bibliothèque, nous devons exécuter les tests une fois de plus sur la version Release de la bibliothèque. Un certain nombre de facteurs, notamment les optimisations du compilateur, peuvent parfois produire un comportement différent entre les versions Debug et Release.

Pour tester la version Release :

1. Dans la barre d’outils de Visual Studio, modifiez la configuration de build de **Debug** à **Release**. L’illustration suivante montre une portion de la barre d’outils.

   ![Image](./media/lib_release.jpg)

1. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **StringLibrary** et choisissez **Générer** pour recompiler la bibliothèque.

1. Réexécutez les tests unitaires en choisissant **Test**, **Exécuter**, **Tous les tests** dans le menu de Visual Studio. Tous les tests devraient réussir.

Maintenant que vous avez fini de tester votre bibliothèque, l’étape suivante consiste à la rendre accessible aux appelants. Vous pouvez la regrouper avec une ou plusieurs applications, ou vous pouvez la distribuer comme package NuGet. Pour plus d’informations sur la procédure à suivre, consultez [Consommation d’une bibliothèque de classes standard .NET](./consuming-library-with-visual-studio-2017.md).

