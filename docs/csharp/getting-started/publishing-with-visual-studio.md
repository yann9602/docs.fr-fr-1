---
title: "Publication de votre application Hello World avec Visual Studio 2017"
description: "La publication crée l’ensemble des fichiers qui sont nécessaires pour exécuter votre application."
keywords: ".NET, .NET Core, application console, publication, déploiement"
author: BillWagner
ms.author: wiwagn
ms.date: 04/17/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a19545d3-24af-4a32-9778-cfb5ae938287
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2b1edd9ea1c4307a4709e4fa2661c271d5f1fe91
ms.contentlocale: fr-fr
ms.lasthandoff: 08/11/2017

---

# <a name="publishing-your-hello-world-application-with-visual-studio-2017"></a>Publication de votre application Hello World avec Visual Studio 2017

Dans [Génération d’une application C# Hello World avec .NET Core dans Visual Studio 2017](with-visual-studio.md), vous avez créé une application console Hello World. Dans [Débogage de votre application C# Hello World avec Visual Studio 2017](debugging-with-visual-studio.md), vous l’avez testée à l’aide du débogueur Visual Studio. Maintenant que vous savez qu’elle fonctionne comme prévu, vous pouvez la publier afin que les autres utilisateurs puissent l’exécuter. La publication crée l’ensemble des fichiers nécessaires pour exécuter votre application ; vous pouvez les déployer en les copiant sur une machine cible.

Pour publier et exécuter votre application : 

1. Vérifiez que Visual Studio génère la version release de votre application. Si nécessaire, modifiez le paramètre de configuration de la génération dans la barre d’outils de **Debug** en **Release**.

   ![Barre d’outils de Visual Studio](media/publishing-with-visual-studio/toolbar.png)

1. Cliquez avec le bouton droit sur le projet **HelloWorld** (et non pas sur la solution HelloWorld) et sélectionnez **Publier** dans le menu. Vous pouvez également sélectionner **Publier HelloWorld** à partir du menu **Build** principal de Visual Studio.

   ![Barre d’outils de Visual Studio](media/publishing-with-visual-studio/publish1.png)

1. Dans la fenêtre de publication de **HelloWorld**, le dossier de sortie de la publication par défaut est fourni pour vous dans la zone de texte **Choisir un dossier**. Sélectionnez le bouton **Publier**.

   ![Barre d’outils de Visual Studio](media/publishing-with-visual-studio/publishwindow.png)

1. Ouvrez une fenêtre de console. Par exemple, dans la zone de texte **Posez-moi une question** dans la barre des tâches Windows, entrez `Command Prompt` (ou `cmd` en abrégé) et ouvrez une fenêtre de console en sélectionnant l’application de poste de travail **Invite de commandes** ou en appuyant sur Entrée si elle est sélectionnée dans les résultats de la recherche.

1. Accédez à l’application publiée dans le sous-répertoire `bin\release\PublishOutput` du répertoire de projet de votre application. Comme le montre l’illustration suivante, la sortie publiée comprend les quatre fichiers suivants :

      * *HelloWorld.deps.json*
      * *HelloWorld.dll*
      * *HelloWorld.pdb* (facultatif pour le déploiement)
      * *HelloWorld.runtimeconfig.json*

   Le fichier *HelloWorld.pdb* contient les symboles de débogage. Vous n’êtes pas obligé de déployer ce fichier avec votre application, même si vous devez l’enregistrer au cas où vous auriez à déboguer la version publiée de votre application.

   ![Fenêtre de console affichant les fichiers publiés](media/publishing-with-visual-studio/publishedfiles.png)

Le processus de publication crée un déploiement dépendant du framework ; qui est un type de déploiement où l’application publiée s’exécute sur toutes les plateformes prises en charge par .NET Core, avec .NET Core installé sur le système. Les utilisateurs peuvent exécuter votre application en émettant la commande `dotnet HelloWorld.dll` à partir d’une fenêtre de console.

Pour plus d’informations sur la publication et le déploiement d’applications .NET Core, consultez [Déploiement d’applications .NET](../../core/deploying/index.md).

