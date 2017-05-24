---
title: "Génération d’une solution .NET Core complète sur macOS à l’aide de Visual Studio pour Mac | Microsoft Docs"
description: "Cette rubrique vous guide lors de la génération d’une solution .NET Core qui inclut une bibliothèque réutilisable et un test unitaire."
keywords: .NET, .NET Core, MacOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 03/16/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 6945bedf-5bf3-4955-8588-83fb87511b79
ms.translationtype: Human Translation
ms.sourcegitcommit: 890c058bd09893c2adb185e1d8107246eef2e20a
ms.openlocfilehash: c1f279e4c78111350dbc8ec01d33d65773c56bb1
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---

# <a name="building-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Génération d’une solution .NET Core complète sur macOS à l’aide de Visual Studio pour Mac

Visual Studio pour Mac fournit un environnement de développement intégré (IDE) complet pour le développement d’applications .NET Core. Cette rubrique vous guide lors de la génération d’une solution .NET Core qui inclut une bibliothèque réutilisable et un test unitaire.

Ce didacticiel vous montre comment créer une application qui accepte un terme de recherche et une chaîne de texte saisis par l’utilisateur, compte le nombre de fois où le terme de recherche apparaît dans la chaîne à l’aide d’une méthode dans une bibliothèque de classes puis retourne le résultat à l’utilisateur. La solution inclut également des tests unitaires pour la bibliothèque de classes servant d’introduction aux concepts de développement avec tests (TDD). Si vous préférez poursuivre le didacticiel avec un exemple complet, téléchargez l’[exemple de solution](https://github.com/dotnet/docs/blob/master/samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter). Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Visual Studio pour Mac est un logiciel en version préliminaire. Comme avec toutes les versions préliminaires des produits Microsoft, vos commentaires sont très appréciés. Il existe deux méthodes pour transmettre vos commentaires à l’équipe de développement Visual Studio pour Mac :
> * Dans Visual Studio pour Mac, sélectionnez **Aide > Signaler un problème** dans le menu ou **Signaler un problème** dans l’écran d’accueil, qui ouvre une fenêtre vous permettant de remplir un rapport de bogue.
> * Pour soumettre une suggestion, sélectionnez **Aide > Fournir une suggestion** dans le menu ou **Four une suggestion** dans l’écran d’accueil, ce qui vous amène à la page Web [UserVoice Visual Studio pour Mac](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).

## <a name="prerequisites"></a>Prérequis

[.NET Core et OpenSSL](https://www.microsoft.com/net/core#macos)

Pour plus d’informations sur la configuration requise, consultez la [configuration requise de .NET Core sur Mac](../../core/macos-prerequisites.md).

## <a name="getting-started"></a>Bien démarrer

Si vous avez déjà installé les composants requis et Visual Studio pour Mac, ignorez cette section et passez à la [génération d’une bibliothèque](#building-a-library). Suivez ces étapes pour installer les composants requis et Visual Studio pour Mac :

1. Téléchargez et installez [.NET Core et OpenSSL](https://www.microsoft.com/net/core#macos).

1. Téléchargez le [programme d’installation de Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/). Exécutez le programme d’installation. Lisez et acceptez le contrat de licence. Lors de l’installation, vous avez la possibilité d’installer Xamarin, une technologie de développement d’application mobile multiplateforme. L’installation de Xamarin et de ses composants associés est facultative pour le développement .NET Core. Pour obtenir une vue d’ensemble du processus d’installation de Visual Studio pour Mac, consultez [Présentation de Visual Studio pour Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/). Une fois l’installation terminée, démarrez l’IDE Visual Studio pour Mac.

## <a name="building-a-library"></a>Génération d'une bibliothèque

1. Sur l’écran d’accueil, sélectionnez **Nouveau projet**. Dans la boîte de dialogue **Nouveau projet**, sous le nœud **Multiplateforme**, sélectionnez le modèle **Bibliothèque standard .NET**. Sélectionnez **Suivant**.

   ![Boîte de dialogue Nouveau projet](./media/using-on-mac-vs-full-solution/vsmacfull01.png)

1. Nommez le projet « TextUtils » (un nom court pour « Utilitaires texte ») et la solution « WordCounter ». Laissez la case **Créez un répertoire de projet dans le répertoire de la solution** cochée. Sélectionnez **Créer**.

   ![Boîte de dialogue Nouveau projet](./media/using-on-mac-vs-full-solution/vsmacfull02.png)

1. Dans la barre latérale **Solution**, développez le nœud `TextUtils` pour afficher le fichier de classe fourni par le modèle, *Class1.cs*. Cliquez avec le bouton droit sur le fichier, sélectionnez **Renommer** dans le menu contextuel puis renommez le fichier *WordCount.cs*. Ouvrez le fichier et remplacez le contenu par le code suivant :

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. Enregistrez le fichier à l’aide d’une des trois différentes méthodes : utilisez le raccourci clavier <kbd>&#8984;</kbd>+<kbd>s</kbd>, sélectionnez **Fichier > Enregistrer** dans le menu, ou cliquez avec le bouton droit sur l’onglet d’un ficher puis sélectionnez **Enregistrer** dans le menu contextuel. L’image suivante présente la fenêtre de l’IDE :

   ![Fenêtre de l’IDE montrant la bibliothèque de classes TextUtils, le fichier de classe WordCount, la classe statique WordCount et la méthode GetWordCount](./media/using-on-mac-vs-full-solution/vsmacfull03.png)

1. Sélectionnez **Erreurs** dans la marge en bas de la fenêtre de l’IDE pour ouvrir le panneau **Erreurs**. Sélectionnez le bouton **Sortie de la build**.

   ![Marge inférieure de l’IDE montrant le bouton Erreurs](./media/using-on-mac-vs-full-solution/vsmacfull03b.png)

1. Sélectionnez **Générer > Tout générer** dans le menu.

   La solution se génère. Le panneau de sortie de la build indique que la build a réussi.

   ![Volet Sortie de la build du panneau Erreurs affichant le message de réussite de la build](./media/using-on-mac-vs-full-solution/vsmacfull04.png)

## <a name="creating-a-test-project"></a>Création d'un projet de test

Les tests unitaires effectuent des tests logiciels automatisés pendant le développement et la publication. L’infrastructure de test que vous utilisez dans ce didacticiel est [xUnit](https://xunit.github.io/).

1. Dans la barre latérale **Solution**, cliquez avec le bouton droit sur la solution `WordCounter`, puis sélectionnez **Ajouter > Ajouter un nouveau projet**.

1. Dans la boîte de dialogue **Nouveau projet**, sélectionnez **Tests** dans le nœud **.NET Core**. Sélectionnez le **projet de test xUnit** puis **suivant**.

   ![Boîte de dialogue Nouveau de projet pour créer le projet de test xUnit](./media/using-on-mac-vs-full-solution/vsmacfull05.png)

1. Nommez le nouveau projet « TestLibrary » et sélectionnez **Créer**.

   ![Boîte de dialogue Nouveau projet indiquant le nom du projet](./media/using-on-mac-vs-full-solution/vsmacfull06.png)

1. Pour que la bibliothèque de test fonctionne avec la classe `WordCount`, ajoutez une référence au projet `TextUtils`. Dans la barre latérale **Solution**, cliquez avec le bouton droit sur **Dépendances** sous **TestLibrary**. Sélectionnez **Modifier les références** dans le menu contextuel.

1. Dans la boîte de dialogue **Modifier les références**, sélectionnez le projet **TextUtils** dans l’onglet **Projets**. Sélectionnez **OK**.

   ![Boîte de dialogue Modifier les références](./media/using-on-mac-vs-full-solution/vsmacfull07.png)

1. Dans le projet **TestLibrary**, renommez le fichier *UnitTest1.cs* *TextUtilsTests.cs*.

1. Ouvrez le fichier et remplacez le code par ce qui suit :

   ```csharp
   using Xunit;
   using TextUtils;
   using System.Diagnostics;

   namespace TestLibrary
   {
       public class TextUtils_GetWordCountShould
       {
           [Fact]
           public void IgnoreCasing()
           {
               var wordCount = WordCount.GetWordCount("Jack", "Jack jack");
   
               Assert.NotEqual(2, wordCount);
           }
       }
   }
   ```

   L’image suivante montre l’IDE avec le code de test unitaire en place. Faites attention à l’instruction `Assert.NotEquals`.

   ![Test unitaire initial pour vérifier GetWordCount dans la fenêtre principale de l’IDE](./media/using-on-mac-vs-full-solution/vsmacfull08.png)

   Lorsque vous utilisez TDD, il est important de faire échouer un test afin de confirmer que sa logique de test est correcte. La méthode passe le nom « Jack » (majuscule) et une chaîne avec « Jack » et « jack » (majuscules et minuscules). Si la méthode `GetWordCount` fonctionne correctement, elle retourne deux instances du mot recherché. Pour faire échouer ce test intentionnellement, vous implémentez d’abord le test en déclarant que deux instances du mot recherché « Jack » ne sont pas retournées par la méthode `GetWordCount`. Passez à l’étape suivante pour faire échouer le test intentionnellement.

1. Actuellement, Visual Studio pour Mac n’intègre pas les tests xUnit dans son Test Runner intégré : vous devez donc exécuter les tests xUnit dans la console. Cliquez avec le bouton droit sur le projet `TestLibrary` puis choisissez **Outils > Ouvrir dans Terminal** dans le menu contextuel. À l'invite de commandes, exécutez `dotnet test`.
   
   Le test échoue, ce qui est le résultat correct. La méthode de test déclare que deux instances de `inputString`, « Jack », ne sont pas retournées par la chaîne « Jack jack » fournie à la méthode `GetWordCount`. Étant donné que la méthode `GetWordCount` respecte la casse, les deux instances sont retournées. L’assertion que 2 *n’est pas égal à* 2 échoue. Il s’agit du résultat correct, et la logique de notre test est donc bonne. Laissez la fenêtre de console ouverte afin de vous préparer à modifier le test pour sa version finale à l’étape suivante.

   ![Échec du test dans la fenêtre de console. Nombre total de tests : 1 Réussite : 0 Échec : 1. La série de tests a échoué.](./media/using-on-mac-vs-full-solution/vsmacfull09.png)

1. Modifiez la méthode de test `IgnoreCasing` en remplaçant `Assert.NotEqual` par `Assert.Equal`. Enregistrez le fichier en utilisant le raccourci clavier <kbd>&#8984;</kbd>+<kbd>s</kbd>, **Fichier > Enregistrer** dans le menu, ou cliquez avec le bouton droit sur l’onglet du fichier puis sélectionnez **Enregistrer** dans le menu contextuel.

   Vous vous attendez à ce que `searchWord` « Jack » retourne deux instances avec `inputString` « Jack jack » passé dans `GetWordCount`. Dans la fenêtre de console, exécutez à nouveau `dotnet test`. Le test est réussi. Il existe deux instances de « Jack » dans la chaîne « Jack jack » (casse ignorée) et l’assertion de test est `true`.

   ![Réussite du test dans la fenêtre de console. Nombre total de tests : 1 Réussite : 1 Échec : 0. La série de tests a réussi.](./media/using-on-mac-vs-full-solution/vsmacfull10.png)

1. Le test des valeurs individuelles retournées avec un `Fact` n'est que le début de ce que vous pouvez faire avec les tests unitaires. Une autre technique puissante vous permet de tester plusieurs valeurs à l’aide d’une `Theory`. Ajoutez la méthode suivante à votre classe `TextUtils_GetWordCountShould`. Vous disposez de deux méthodes dans la classe après avoir ajouté cette méthode :

   ```csharp
   [Theory]
   [InlineData(0, "Ting", "Does not appear in the string.")]
   [InlineData(1, "Ting", "Ting appears once.")]
   [InlineData(2, "Ting", "Ting appears twice with Ting.")]
   public void CountInstancesCorrectly(int count, 
                                       string searchWord, 
                                       string inputString)
   {
       Assert.Equal(count, WordCount.GetWordCount(searchWord,
                                                  inputString));
   }
   ```

   `CountInstancesCorrectly` vérifie que la méthode `GetWordCount` compte correctement. `InlineData` fournit un nombre, un terme de recherche et une chaîne d’entrée à vérifier. La méthode de test s’exécute une fois pour chaque ligne de données. Notez que vous déclarez tout d’abord un échec en utilisant `Assert.NotEqual`, même si vous savez que les données sont correctes et que les valeurs correspondront au nombre retourné par la méthode `GetWordCount`. L’exécution de l’étape d’échec intentionnel du test peut sembler a priori une perte de temps, mais la vérification de la logique de test en la faisant échouer est une étape importante pour valider la logique de vos tests. Il peut également arriver qu’une méthode de test réussisse alors que vous pensiez qu’elle échouerait et que vous trouviez un bogue dans la logique du test. Il est recommandé de suivre cette procédure chaque fois que vous créez une méthode de test.
   
1. Enregistrez le fichier et exécutez `dotnet test` dans la fenêtre de console. Le test de la casse réussit, mais les trois tests d’énumération échouent. C’est exactement le résultat que vous attendiez.

   ![Échec du test dans la fenêtre de console. Nombre total de tests : 4 Réussite : 1 Échec : 3. La série de tests a échoué.](./media/using-on-mac-vs-full-solution/vsmacfull11.png)

1. Modifiez la méthode de test `CountInstancesCorrectly` en remplaçant `Assert.NotEqual` par `Assert.Equal`. Enregistrez le fichier. Exécutez à nouveau `dotnet test` dans la fenêtre de console. Tous les tests sont concluants.

   ![Réussite du test dans la fenêtre de console. Nombre total de tests : 4 Réussite : 4 Échec : 0. La série de tests a réussi.](./media/using-on-mac-vs-full-solution/vsmacfull12.png)

## <a name="adding-a-console-app"></a>Ajout d’une application console

1. Dans la barre latérale **Solution**, cliquez avec le bouton droit sur la solution `WordCounter`. Ajoutez un nouveau projet **Application console** en sélectionnant le modèle à partir des modèles **.NET Core > Application**. Sélectionnez **Suivant**. Nommez le projet **WordCounterApp**. Sélectionnez **Créer** pour créer le projet dans la solution.

1. Dans la barre latérale **Solutions**, cliquez avec le bouton droit sur le nœud **Dépendances** du nouveau projet **WordCounterApp**. Dans la boîte de dialogue **Modifier les références**, cochez la case **TextUtils** puis sélectionnez **OK**.

1. Ouvrez le fichier *Program.cs*. Remplacez le code par ce qui suit :

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. Pour exécuter l’application dans une fenêtre de console au lieu de l’IDE, cliquez avec le bouton droit sur le projet `WordCounterApp`, sélectionnez **Options**, puis ouvrez le nœud **Par défaut** sous **Configurations**. Cochez la case **Exécuter dans une console externe**. Laissez la case **Suspendre la sortie de la console** cochée. Avec ce paramètre, l’application est générée dynamiquement dans une fenêtre de console, ce qui vous permet de saisir des informations pour les instructions `Console.ReadLine`. Si vous laissez l’application s’exécuter dans l’IDE, vous ne verrez que le résultat des instructions `Console.WriteLine`. Les instructions `Console.ReadLine` ne fonctionnent pas dans le panneau **Sortie de l’application** de l’IDE.

   ![Fenêtre Options du projet](./media/using-on-mac-vs-full-solution/vsmacfull13.png)

1. Étant donné que la version préliminaire de Visual Studio pour Mac ne permet pas actuellement d’effectuer les tests lors de l’exécution de la solution, vous exécutez l’application console directement. Cliquez avec le bouton droit sur le projet `WordCounterApp` et sélectionnez **Exécuter l’article** dans le menu contextuel. Si vous tentez d’exécuter l’application avec le bouton de lecture, le Test Runner et l’application ne s’exécutent pas. Pour plus d’informations sur l’état du travail pour ce problème, consultez [xunit/xamarinstudio.xunit (#60)](https://github.com/xunit/xamarinstudio.xunit/issues/60). Lorsque vous exécutez l’application, indiquez les valeurs du mot de recherche et la chaîne d’entrée à l’invite dans la fenêtre de console. L’application indique le nombre de fois où le terme de recherche apparaît dans la chaîne.

   ![Fenêtre de console montrant le terme olives recherché dans la chaîne « Iro ate olives by the lake, and the olives were wonderful. » L’application répond « Le terme de recherche olives apparaît 2 fois. »](./media/using-on-mac-vs-full-solution/vsmacfull14.png)

1. La dernière fonctionnalité à explorer est le débogage avec Visual Studio pour Mac. Définissez un point d’arrêt sur l’instruction `Console.WriteLine`. Sélectionnez dans la marge gauche de la ligne 23 : un cercle rouge apparaît en regard de la ligne de code. Vous pouvez également sélectionner n’importe où sur la ligne de code puis choisir **Exécuter > Basculer le point d'arrêt** dans le menu.

   ![Le point d’arrêt est défini sur la ligne 23, avec l’instruction Console.WriteLine](./media/using-on-mac-vs-full-solution/vsmacfull15.png)

1. Cliquez avec le bouton droit sur le projet `WordCounterApp` . Sélectionnez **Démarrer le débogage** dans le menu contextuel. Lorsque l’application s’exécute, entrez le terme de recherche « cat » et « The dog chased the cat, but the cat escaped. » pour la chaîne à rechercher. Lorsque l’instruction `Console.WriteLine` est atteinte, l’exécution du programme s’arrête avant l’exécution de l’instruction. Dans l’onglet **Variables locales**, vous pouvez voir les valeurs `searchWord`, `inputString`, `wordCount` et `pluralChar`.

   ![L’exécution du programme s’arrête à l’instruction Console.WriteLine avec la fenêtre des variables locales indiquant les valeurs immédiatement avant l’exécution de l’instruction Console.WriteLine.](./media/using-on-mac-vs-full-solution/vsmacfull16.png)

1. Dans le volet **Immédiat**, tapez « wordCount = 999. » et appuyez sur Entrée. Cette opération affecte une valeur absurde de 999 à la variable `wordCount`, indiquant que vous pouvez remplacer les valeurs des variables pendant le débogage.

   ![Notre point d’arrêt est atteint. La valeur wordCount est remplacée par une valeur de 999 dans la fenêtre Immédiat](./media/using-on-mac-vs-full-solution/vsmacfull17.png)

1. Dans la barre d’outils, cliquez sur la flèche *Continuer*. Regardez le résultat dans la fenêtre de console. Elle affiche la valeur incorrecte de 999 que vous définissez lorsque vous déboguez l’application.

   ![Bouton Continuer de la barre d’outils](./media/using-on-mac-vs-full-solution/vsmacfull18.png)

   ![Le nombre de mots de recherche est remplacé par une valeur de 999 dans la sortie de l’application](./media/using-on-mac-vs-full-solution/vsmacfull19.png)

## <a name="next-steps"></a>Étapes suivantes

* Explorez les autres fonctionnalités de Visual Studio pour Mac dans un [présentation de Visual Studio pour Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/) sur le site Web du développeur Xamarin.
* Pour en savoir plus sur les fonctionnalités de Visual Studio pour Mac, reportez-vous au guide [Xamarin Studio Tour](https://developer.xamarin.com/guides/cross-platform/xamarin-studio/ide-tour/).

