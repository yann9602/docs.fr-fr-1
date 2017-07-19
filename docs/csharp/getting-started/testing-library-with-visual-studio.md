---
title: "Test d’une bibliothèque de classes avec .NET Core dans Visual Studio 2017 | Microsoft Docs"
description: "Découvrez comment tester une bibliothèque de classes écrite en C# à l’aide de Visual Studio 2017"
keywords: ".NET Core, bibliothèque de classes .NET Standard, Visual Studio 2017, test unitaire"
author: BillWagner
ms.author: wiwagn
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 069ad711-3eaa-45c6-94d7-b40249cc8b99
ms.translationtype: Human Translation
ms.sourcegitcommit: fd5f6cccdc5c91eb435ba024c9c37351febc952a
ms.openlocfilehash: f07ba05a617f5e270f0e08f2006b25cecc04f05b
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---

<a id="testing-a-class-library-with-net-core-in-visual-studio-2017" class="xliff"></a>

# Test d’une bibliothèque de classes avec .NET Core dans Visual Studio 2017

Dans [Génération d’une bibliothèque de classes avec C# et .NET Core dans Visual Studio 2017](library-with-visual-studio.md), vous avez créé une bibliothèque de classes simple qui ajoute une méthode d’extension à la classe @System.String. À présent, vous allez créer un test unitaire pour vérifier qu’elle fonctionne comme prévu. Vous allez ajouter votre projet de test unitaire à la solution créée dans la rubrique précédente.

<a id="creating-a-unit-test-project" class="xliff"></a>

## Création d'un projet de test unitaire

Pour créer le projet de test unitaire, procédez comme suit :

1. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du nœud de la solution **ClassLibraryProjects** et sélectionnez **Ajouter** > **Nouveau projet**.

   <!-- Need a VS 2017 version  [!NOTE] In addition to a Unit Test project, you can also use Visual Studio to create an xUnit test project for .NET Core. For a walkthrough that includes an xUnit test project, see [Getting started with .NET Core on Windows, using Visual Studio 2015](../../core/tutorials/using-on-windows.md). --> 

1. Dans la boîte de dialogue **Ajouter un nouveau projet**, sélectionnez le nœud **.NET Core** puis choisissez le modèle de projet **Projet de test unitaire (.NET Core)**. Dans la zone de texte **Nom**, entrez « StringLibraryTest » comme nom de projet. Sélectionnez **OK** pour créer le projet de test unitaire.

   ![Boîte de dialogue Ajouter un nouveau projet](./media/testing-library-with-visual-studio/testproject.png)

1. Visual Studio crée le projet et ouvre le fichier *UnitTest1.cs* dans la fenêtre de code.

   ![Fenêtre de code Visual Studio montrant la classe du projet de test unitaire UnitTest1 par défaut et la méthode TestMethod1](./media/testing-library-with-visual-studio/unittestwindow.png)

   Le code source créé par le modèle de test unitaire effectue les opérations suivantes :

   * Il importe l’espace de noms [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) qui contient les types utilisés pour les tests unitaires.

   * Il applique l’attribut [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) à la classe `UnitTest1`. Chaque méthode de test dans une classe de test marquée avec l’attribut \[TestMethod\] est exécutée automatiquement quand le test unitaire est exécuté.

   * Elle applique l’attribut [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) pour définir `TestMethod1` comme une méthode de test qui doit être exécutée automatiquement quand le test unitaire est exécuté.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Dépendances** du projet **StringLibraryTest** puis sélectionnez **Ajouter une référence** dans le menu contextuel.

   ![Menu contextuel des dépendances de StringLibraryTest](./media/testing-library-with-visual-studio/addreference.png)

1. Dans la boîte de dialogue **Gestionnaire de références**, cochez la case en regard de **StringLibrary**. L’ajout d’une référence à l’assembly `StringLibrary` permet au compilateur de trouver les méthodes **StringLibrary**. Sélectionnez le bouton **OK**. Ceci ajoute une référence à votre projet de bibliothèque de classes `StringLibrary`.

   ![Gestionnaire de références](./media/testing-library-with-visual-studio/referencemanager.png)

<a id="adding-and-running-unit-test-methods" class="xliff"></a>

## Ajout et exécution de méthodes de test unitaire

Quand Visual Studio exécute un test unitaire, il exécute chaque méthode marquée avec l’attribut [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) dans une classe de test unitaire, la classe à laquelle l’attribut [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) est appliqué. Une méthode de test se termine quand la première défaillance survient, ou quand tous les tests contenus dans la méthode ont réussi.

Les tests les plus courants appellent des membres de la classe [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx). De nombreuses méthodes d’assertion incluent au moins deux paramètres, à savoir le résultat attendu pour le test et résultat réel du test. Certaines de ses méthodes les plus fréquemment appelées figurent dans le tableau ci-dessous.

Méthodes d’assertion | Fonction
--- | ---
`Assert.AreEqual` | Vérifie que deux valeurs ou objets sont égaux. L’assertion échoue si les valeurs ou les objets ne sont pas égaux.
`Assert.AreSame` | Vérifie que deux variables d’objet référencent le même objet. L’assertion échoue si les variables font référence à des objets différents.
`Assert.IsFalse` | Vérifie qu’une condition est `false`. L’assertion échoue si la condition est `true`.
`Assert.IsNotNull` | Vérifie qu’un objet n’est pas `null`. L’assertion échouera si l’objet est `null`.
Attribut [\[ExpectedException\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.expectedexceptionattribute.aspx) | Indique le type d’exception qu’une méthode de test est supposée lever. Le test échoue si l’exception spécifiée n’est pas levée.

Dans le test de la méthode `StringLibrary.StartsWithUpper`, vous voulez fournir une série de chaînes qui commencent par une majuscule. Vous attendez que la méthode retourne `true` dans de tels cas, et vous pouvez donc appeler la méthode [Assert.IsTrue(Booléen, Chaîne)](https://msdn.microsoft.com/library/ms243754.aspx). De même, vous voulez fournir des chaînes qui commencent par autre chose qu’un caractère majuscule. Vous attendez que la méthode retourne `false` dans de tels cas, et vous pouvez donc appeler la méthode [Assert.IsFalse(Booléen, Chaîne)](https://msdn.microsoft.com/library/ms243805.aspx).

Dans la mesure où votre méthode de bibliothèque gère les chaînes, vous voulez également vous assurer qu’elle gère correctement une [chaîne vide (`String.Empty`)](xref:System.String.Empty), une chaîne valide sans caractères et dont @System.String.Length a la valeur 0, et une chaîne `null` qui n’a pas été initialisée. Si vous appelez `StartsWithUpper` comme méthode d’extension sur une instance @System.String, il n’est pas possible de lui passer une chaîne `null`. Toutefois, vous pouvez également l’appeler directement comme méthode statique et passer un seul argument @System.String.

Vous allez définir trois méthodes, chacune appelant sa méthode [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) de façon répétée pour chaque élément d’un tableau de chaînes. Comme la méthode de test échoue dès qu’elle rencontre le premier échec, vous appelez une surcharge de méthode qui permet de passer une chaîne indiquant la valeur de chaîne utilisée dans l’appel de méthode.

Pour créer les méthodes de test:

1. Dans la fenêtre de code *UnitTest1.cs*, remplacez le code par le code suivant :

   [!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs#1)]

   Notez que votre test de caractères majuscules dans la méthode `TestStartsWithUpper` inclut la lettre majuscule grecque alpha (U+0391) et la lettre majuscule cyrillique EM (U+041C), et que le test de caractères minuscules dans la méthode `TestDoesNotStartWithUpper` inclut la lettre minuscule grecque alpha (U+03B1) et la lettre minuscule cyrillique Gué (U+0433).

1. Dans la barre de menus, sélectionnez **Fichier** > **Enregistrer UnitTest1.cs sous**. Dans la boîte de dialogue **Enregistrer le fichier sous**, cliquez sur la flèche à côté du bouton **Enregistrer**, puis choisissez **Enregistrer avec l’encodage**.

   ![Boîte de dialogue Enregistrer le fichier sous](./media/testing-library-with-visual-studio/savefileas.png)

1. Dans la boîte de dialogue **Confirmer l’enregistrement sous**, sélectionnez le bouton **Oui** pour enregistrer le fichier.

1. Dans la boîte de dialogue **Options d’enregistrement avancées**, sélectionnez **Unicode (UTF-8 avec signature) - Page de codes 65001** dans la liste déroulante **Encodage**, puis sélectionnez **OK**.

   ![Boîte de dialogue Options d’enregistrement avancées](./media/testing-library-with-visual-studio/advancedsaveoptions.png)

   Si vous ne parvenez pas à enregistrer votre code source dans un fichier encodé en UTF-8, Visual Studio peut l’enregistrer en tant que fichier ASCII. Dans ce cas, le runtime ne décode pas correctement les caractères UTF-8 en dehors de la plage ASCII, et les résultats des tests ne seront pas exacts.

1. Dans la barre de menus, sélectionnez **Test** > **Exécuter** > **Tous les Tests**. La fenêtre **Explorateur de tests** s’ouvre et montre que les tests ont réussi. Les trois tests sont listés dans la section **Tests réussis** et la section **Résumé** indique le résultat de la série de tests.

   ![Fenêtre Explorateur de tests](./media/testing-library-with-visual-studio/firsttest.png)

<a id="handling-test-failures" class="xliff"></a>

## Gestion des échecs des tests

Votre série de tests n’a rencontré aucun échec : changez-la légèrement de façon à faire échouer une des méthodes de test :

1. Modifiez le tableau `words` dans la méthode `TestDoesNotStartWithUpper` en y incluant la chaîne « Erreur ». Vous n’avez pas besoin d’enregistrer le fichier, car Visual Studio enregistre automatiquement les fichiers ouverts quand une solution est générée pour exécuter des tests.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. Exécutez le test en sélectionnant **Test** > **Exécuter** > **Tous les Tests** dans la barre de menus. La fenêtre **Explorateur de tests** indique que deux tests ont réussi et qu’un test a échoué.

   ![Fenêtre Explorateur de tests](./media/testing-library-with-visual-studio/failedtest.png)

1. Dans la section **Tests ayant échoué**, sélectionnez le test ayant échoué, `TestDoesNotStartWith`. La fenêtre **Explorateur de tests** affiche le message généré par l’assertion : « Échec de Assert.IsFalse. « Erreur » : false ; réel : True » était attendu ». En raison de l’échec, toutes les chaînes dans le tableau après « Error » n’ont pas été testées.

   ![Fenêtre Explorateur de tests montrant l’échec de l’assertion IsFalse](./media/testing-library-with-visual-studio/failedtestdetail.png)

1. Supprimez le code que vous avez ajouté (`"Error", `) et réexécutez le test. Les tests réussissent à nouveau.

<a id="testing-the-release-version-of-the-library" class="xliff"></a>

## Test de la version de la version Release de la bibliothèque

Vous avez exécuté vos tests sur la version Debug de la bibliothèque. Maintenant que vos tests ont tous réussi et que vous avez testé votre bibliothèque de façon adéquate, vous devez exécuter les tests une fois de plus sur la version Release de la bibliothèque. Un certain nombre de facteurs, notamment les optimisations du compilateur, peuvent parfois produire un comportement différent entre les versions Debug et Release.

Pour tester la version Release :

1. Dans la barre d’outils de Visual Studio, modifiez la configuration de build de **Debug** à **Release**.

   ![Barre d’outils de Visual Studio](./media/testing-library-with-visual-studio/toolbar.png)

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **StringLibrary** et sélectionnez **Générer** dans le menu contextuel pour recompiler la bibliothèque.

   ![Menu contextuel de StringLibrary](./media/testing-library-with-visual-studio/buildlibrary.png)

1. Exécutez les tests unitaires en sélectionnant **Test** > **Exécuter** > **Tous les Tests** dans la barre de menus. Les tests réussissent.

Maintenant que vous avez fini de tester votre bibliothèque, l’étape suivante consiste à la rendre accessible aux appelants. Vous pouvez la regrouper avec une ou plusieurs applications, ou vous pouvez la distribuer comme package NuGet. Pour plus d’informations, consultez [Consommation d’une bibliothèque de classes standard .NET](./consuming-library-with-visual-studio.md).

