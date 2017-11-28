---
title: "Génération d’une solution .NET Core complète sur macOS à l’aide de Visual Studio pour Mac"
description: "Cette rubrique vous guide lors de la génération d’une solution .NET Core qui inclut une bibliothèque réutilisable et un test unitaire."
keywords: .NET, .NET Core, MacOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 6945bedf-5bf3-4955-8588-83fb87511b79
ms.openlocfilehash: 60179fb0435803c3235b75ba012e588c6f1b35d3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="building-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Génération d’une solution .NET Core complète sur macOS à l’aide de Visual Studio pour Mac

Visual Studio pour Mac fournit un environnement de développement intégré (IDE) complet pour le développement d’applications .NET Core. Cette rubrique vous guide lors de la génération d’une solution .NET Core qui inclut une bibliothèque réutilisable et un test unitaire.

Ce didacticiel vous montre comment créer une application qui accepte un terme de recherche et une chaîne de texte saisis par l’utilisateur, compte le nombre de fois où le terme de recherche apparaît dans la chaîne à l’aide d’une méthode dans une bibliothèque de classes puis retourne le résultat à l’utilisateur. La solution inclut également des tests unitaires pour la bibliothèque de classes servant d’introduction aux concepts de développement avec tests (TDD). Si vous préférez poursuivre le didacticiel avec un exemple complet, téléchargez l’[exemple de solution](https://github.com/dotnet/docs/blob/master/samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter). Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Vos commentaires sont extrêmement précieux. Il existe deux moyens de transmettre vos commentaires à l’équipe de développement sur Visual Studio pour Mac :
> * Dans Visual Studio pour Mac, sélectionnez **Aide** > **Signaler un problème** dans le menu ou **Signaler un problème** sur l’écran d’accueil, ce qui ouvre une fenêtre permettant de soumettre un rapport de bogue. Vous pouvez effectuer le suivi de vos commentaires dans le portail de la [communauté des développeurs](https://developercommunity.visualstudio.com/spaces/41/index.html).
> * Pour soumettre une suggestion, sélectionnez **Aide** > **Émettre une suggestion** dans le menu ou **Émettre une suggestion** sur l’écran d’accueil, ce qui vous amène à la [page Web UserVoice de Visual Studio pour Mac](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).

## <a name="prerequisites"></a>Prérequis

- OpenSSL (s’il fonctionne avec .NET Core 1.1) : consultez la rubrique [Prérequis pour .NET Core sur Mac](../macos-prerequisites.md).
- [Kit SDK .NET Core 1.1 ou version ultérieure](https://www.microsoft.com/net/core#macos)
- [Visual Studio 2017 pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/)

Pour plus d’informations sur la configuration requise, consultez la [configuration requise de .NET Core sur Mac](../../core/macos-prerequisites.md). Pour connaître l’ensemble des exigences système de Visual Studio 2017 pour Mac, consultez la page [Exigences système de la famille de produits Visual Studio 2017 pour Mac](https://www.visualstudio.com/productinfo/vs2017-system-requirements-mac).

## <a name="building-a-library"></a>Génération d'une bibliothèque

1. Sur l’écran d’accueil, sélectionnez **Nouveau projet**. Dans la boîte de dialogue **Nouveau projet**, sous le nœud **Multiplateforme**, sélectionnez le modèle **Bibliothèque standard .NET**. Sélectionnez **Suivant**.

   ![Boîte de dialogue Nouveau projet](./media/using-on-mac-vs-full-solution/vsmacfull01.png)

1. Nommez le projet « TextUtils » (un nom court pour « Utilitaires texte ») et la solution « WordCounter ». Laissez la case **Créez un répertoire de projet dans le répertoire de la solution** cochée. Sélectionnez **Créer**.

   ![Boîte de dialogue Nouveau projet](./media/using-on-mac-vs-full-solution/vsmacfull02.png)

1. Dans la barre latérale **Solution**, développez le nœud `TextUtils` pour afficher le fichier de classe fourni par le modèle, *Class1.cs*. Cliquez avec le bouton droit sur le fichier, sélectionnez **Renommer** dans le menu contextuel puis renommez le fichier *WordCount.cs*. Ouvrez le fichier et remplacez le contenu par le code suivant :

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. Enregistrez le fichier en appliquant l’une de ces méthodes : utilisez le raccourci clavier <kbd>&#8984;</kbd>+<kbd>s</kbd>, sélectionnez **Fichier** > **Enregistrer** dans le menu ou cliquez avec le bouton droit sur l’onglet du ficher et sélectionnez **Enregistrer** dans le menu contextuel. L’image suivante présente la fenêtre de l’IDE :

   ![Fenêtre de l’IDE montrant la bibliothèque de classes TextUtils, le fichier de classe WordCount, la classe statique WordCount et la méthode GetWordCount](./media/using-on-mac-vs-full-solution/vsmacfull03.png)

1. Sélectionnez **Erreurs** dans la marge en bas de la fenêtre de l’IDE pour ouvrir le panneau **Erreurs**. Sélectionnez le bouton **Sortie de la build**.

   ![Marge inférieure de l’IDE montrant le bouton Erreurs](./media/using-on-mac-vs-full-solution/vsmacfull03b.png)

1. Sélectionnez **Générer** > **Tout générer** dans le menu.

   La solution se génère. Le panneau de sortie de la build indique que la build a réussi.

   ![Volet Sortie de la build du panneau Erreurs affichant le message de réussite de la build](./media/using-on-mac-vs-full-solution/vsmacfull04.png)

## <a name="creating-a-test-project"></a>Création d'un projet de test

Les tests unitaires effectuent des tests logiciels automatisés pendant le développement et la publication. L’infrastructure de test utilisée dans ce didacticiel est [xUnit (version 2.2.0 ou ultérieure)](https://xunit.github.io/), qui est installé automatiquement lorsque le projet de test xUnit est ajouté à la solution au cours des étapes suivantes :

1. Dans la barre latérale **Solution**, cliquez avec le bouton droit sur la solution `WordCounter`, puis sélectionnez **Ajouter** > **Ajouter un nouveau projet**.

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

   L’image suivante montre l’IDE avec le code de test unitaire en place. Faites attention à l’instruction `Assert.NotEqual`.

   ![Test unitaire initial pour vérifier GetWordCount dans la fenêtre principale de l’IDE](./media/using-on-mac-vs-full-solution/vsmacfull08.png)

   Lorsque vous utilisez TDD, il est important de faire échouer un test afin de confirmer que sa logique de test est correcte. La méthode passe le nom « Jack » (majuscule) et une chaîne avec « Jack » et « jack » (majuscules et minuscules). Si la méthode `GetWordCount` fonctionne correctement, elle retourne deux instances du mot recherché. Pour faire échouer ce test intentionnellement, vous implémentez d’abord le test en déclarant que deux instances du mot recherché « Jack » ne sont pas retournées par la méthode `GetWordCount`. Passez à l’étape suivante pour faire échouer le test intentionnellement.

1. Ouvrez le panneau **Tests unitaires** sur le côté droit de l’écran.

![Panneau Tests unitaires](./media/using-on-mac-vs-full-solution/vsmacfull_UnitTestPanel.png)

1. Cliquez sur l’icône **Ancrer** pour garder le panneau ouvert.

![Icône Ancrer du panneau Tests unitaires](./media/using-on-mac-vs-full-solution/vsmacfull_UnitTestPanelDockIcon.png)

1. Cliquez sur le bouton **Tout exécuter**.
   
   Le test échoue, ce qui est le résultat correct. La méthode de test déclare que deux instances de `inputString`, « Jack », ne sont pas retournées par la chaîne « Jack jack » fournie à la méthode `GetWordCount`. Étant donné que la méthode `GetWordCount` respecte la casse, les deux instances sont retournées. L’assertion que 2 *n’est pas égal à* 2 échoue. Il s’agit du résultat correct, et la logique de notre test est donc bonne.

   ![Échec du test](./media/using-on-mac-vs-full-solution/vsmacfull09.png)

1. Modifiez la méthode de test `IgnoreCasing` en remplaçant `Assert.NotEqual` par `Assert.Equal`. Enregistrez le fichier en utilisant le raccourci clavier <kbd>&#8984;</kbd>+<kbd>s</kbd>, **Fichier** > **Enregistrer dans le menu** ou cliquez avec le bouton droit sur l’onglet du fichier puis sélectionnez **Enregistrer** dans le menu contextuel.

   Vous vous attendez à ce que `searchWord` « Jack » retourne deux instances avec `inputString` « Jack jack » passé dans `GetWordCount`. Réexécutez le test en cliquant sur le bouton **Exécuter les tests** du panneau **Tests unitaires** ou sur le bouton **Réexécuter les tests** du panneau **Résultats des tests** en bas de l’écran. Le test est réussi. Il existe deux instances de « Jack » dans la chaîne « Jack jack » (casse ignorée) et l’assertion de test est `true`.

   ![Réussite du test](./media/using-on-mac-vs-full-solution/vsmacfull10.png)

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
       Assert.NotEqual(count, WordCount.GetWordCount(searchWord,
                                                  inputString));
   }
   ```

   `CountInstancesCorrectly` vérifie que la méthode `GetWordCount` compte correctement. `InlineData` fournit un nombre, un terme de recherche et une chaîne d’entrée à vérifier. La méthode de test s’exécute une fois pour chaque ligne de données. Notez que, là encore, vous déclarez tout d’abord un échec en utilisant `Assert.NotEqual`, même si vous savez que les nombres contenus dans les données sont corrects et que les valeurs correspondent aux nombres retournés par la méthode `GetWordCount`. L’exécution de l’étape d’échec intentionnel du test peut sembler a priori une perte de temps, mais la vérification de la logique de test en la faisant échouer est une étape importante pour valider la logique de vos tests. Lorsqu’une méthode de test réussit alors que vous pensiez qu’elle échouerait, c’est que vous avez trouvé un bogue dans la logique du test. Il est recommandé de suivre cette procédure chaque fois que vous créez une méthode de test.
   
1. Enregistrez le fichier et réexécutez les tests. Le test de la casse réussit, mais les trois tests d’énumération échouent. C’est exactement le résultat que vous attendiez.

   ![Échec du test](./media/using-on-mac-vs-full-solution/vsmacfull11.png)

1. Modifiez la méthode de test `CountInstancesCorrectly` en remplaçant `Assert.NotEqual` par `Assert.Equal`. Enregistrez le fichier. Réexécutez les tests. Tous les tests sont concluants.

   ![Réussite du test](./media/using-on-mac-vs-full-solution/vsmacfull12.png)

## <a name="adding-a-console-app"></a>Ajout d’une application console

1. Dans la barre latérale **Solution**, cliquez avec le bouton droit sur la solution `WordCounter`. Ajoutez un nouveau projet **Application console** en sélectionnant le modèle parmi les modèles **.NET Core** > **Application**. Sélectionnez **Suivant**. Nommez le projet **WordCounterApp**. Sélectionnez **Créer** pour créer le projet dans la solution.

1. Dans la barre latérale **Solutions**, cliquez avec le bouton droit sur le nœud **Dépendances** du nouveau projet **WordCounterApp**. Dans la boîte de dialogue **Modifier les références**, cochez la case **TextUtils** puis sélectionnez **OK**.

1. Ouvrez le fichier *Program.cs*. Remplacez le code par ce qui suit :

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. Pour exécuter l’application dans une fenêtre de console au lieu de l’IDE, cliquez avec le bouton droit sur le projet `WordCounterApp`, sélectionnez **Options**, puis ouvrez le nœud **Par défaut** sous **Configurations**. Cochez la case **Exécuter dans une console externe**. Laissez la case **Suspendre la sortie de la console** cochée. Avec ce paramètre, l’application est générée dynamiquement dans une fenêtre de console, ce qui vous permet de saisir des informations pour les instructions `Console.ReadLine`. Si vous laissez l’application s’exécuter dans l’IDE, vous ne verrez que le résultat des instructions `Console.WriteLine`. Les instructions `Console.ReadLine` ne fonctionnent pas dans le panneau **Sortie de l’application** de l’IDE.

   ![Fenêtre Options du projet](./media/using-on-mac-vs-full-solution/vsmacfull13.png)

1. Étant donné que la version actuelle de Visual Studio pour Mac ne peut pas effectuer les tests pendant l’exécution de la solution, vous exécutez directement l’application console. Cliquez avec le bouton droit sur le projet `WordCounterApp` et sélectionnez **Exécuter l’article** dans le menu contextuel. Si vous tentez d’exécuter l’application avec le bouton de lecture, le Test Runner et l’application ne s’exécutent pas. Pour plus d’informations sur l’état du travail pour ce problème, consultez [xunit/xamarinstudio.xunit (#60)](https://github.com/xunit/xamarinstudio.xunit/issues/60). Lorsque vous exécutez l’application, indiquez les valeurs du mot de recherche et la chaîne d’entrée à l’invite dans la fenêtre de console. L’application indique le nombre de fois où le terme de recherche apparaît dans la chaîne.

   ![Fenêtre de console montrant le terme olives recherché dans la chaîne « Iro ate olives by the lake, and the olives were wonderful. » L’application répond « Le terme de recherche olives apparaît 2 fois. »](./media/using-on-mac-vs-full-solution/vsmacfull14.png)

1. La dernière fonctionnalité à explorer est le débogage avec Visual Studio pour Mac. Définissez un point d’arrêt sur l’instruction `Console.WriteLine`. Sélectionnez dans la marge gauche de la ligne 23 : un cercle rouge apparaît en regard de la ligne de code. Vous pouvez également faire une sélection sur la ligne de code, puis sélectionner **Exécuter** > **Basculer le point d’arrêt** dans le menu.

   ![Le point d’arrêt est défini sur la ligne 23, avec l’instruction Console.WriteLine](./media/using-on-mac-vs-full-solution/vsmacfull15.png)

1. Cliquez avec le bouton droit sur le projet `WordCounterApp` . Sélectionnez **Démarrer le débogage** dans le menu contextuel. Lorsque l’application s’exécute, entrez le terme de recherche « cat » et « The dog chased the cat, but the cat escaped. » pour la chaîne à rechercher. Lorsque l’instruction `Console.WriteLine` est atteinte, l’exécution du programme s’arrête avant l’exécution de l’instruction. Dans l’onglet **Variables locales**, vous pouvez voir les valeurs `searchWord`, `inputString`, `wordCount` et `pluralChar`.

   ![L’exécution du programme s’arrête à l’instruction Console.WriteLine avec la fenêtre des variables locales indiquant les valeurs immédiatement avant l’exécution de l’instruction Console.WriteLine.](./media/using-on-mac-vs-full-solution/vsmacfull16.png)

1. Dans le volet **Immédiat**, tapez « wordCount = 999. » et appuyez sur Entrée. Cette opération affecte une valeur absurde de 999 à la variable `wordCount`, indiquant que vous pouvez remplacer les valeurs des variables pendant le débogage.

   ![Notre point d’arrêt est atteint. La valeur wordCount est remplacée par une valeur de 999 dans la fenêtre Immédiat](./media/using-on-mac-vs-full-solution/vsmacfull17.png)

1. Dans la barre d’outils, cliquez sur la flèche *Continuer*. Regardez le résultat dans la fenêtre de console. Elle affiche la valeur incorrecte de 999 que vous définissez lorsque vous déboguez l’application.

   ![Bouton Continuer de la barre d’outils](./media/using-on-mac-vs-full-solution/vsmacfull18.png)

   ![Le nombre de mots de recherche est remplacé par une valeur de 999 dans la sortie de l’application](./media/using-on-mac-vs-full-solution/vsmacfull19.png)

## <a name="see-also"></a>Voir aussi

[Notes de publication de Visual Studio 2017 pour Mac](https://www.visualstudio.com/news/releasenotes/vs2017-mac-relnotes)
