---
title: "Publication de votre application Hello World avec Visual Studio 2017"
description: "Publication de votre application Hello World avec Visual Studio 2017"
keywords: ".NET, .NET core, application de console .NET Core, publication (.NET Core), déploiement (.NET Core)"
author: BillWagner
ms.author: wiwagn
ms.date: 10/24/2016
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a19545d3-24af-4a32-9778-cfb5ae938287
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f4a30d19e111d395088e38c4543c9dacee6105fd
ms.lasthandoff: 03/13/2017

---

# <a name="publishing-your-hello-world-application-with-visual-studio-2017"></a>Publication de votre application Hello World avec Visual Studio 2017

Dans [Création d’une application C# Hello World avec .NET Core dans Visual Studio 2017](with-visual-studio-2017.md), vous avez créé votre application console Hello World, et dans [Débogage de votre application C# Hello World avec Visual Studio 2017](debugging-with-visual-studio-2017.md), vous l’avez testée à l’aide du débogueur Visual Studio. Maintenant que vous savez qu’elle fonctionne comme prévu, vous pouvez la publier afin que les autres utilisateurs puissent l’exécuter. La publication crée le jeu de fichiers nécessaires pour exécuter votre application, et vous pouvez les déployer en les copiant sur une machine cible.

Pour publier et exécuter votre application : 

1. Assurez-vous que Visual Studio génère la version release de votre application. Si nécessaire, modifiez le paramètre de configuration de génération dans la barre d’outils de **Debug** à **Release**, comme présenté dans l'illustration suivante.

   ![Image](media/release.jpg)

1. Ouvrez une fenêtre de console. Par exemple, dans la zone **Demandez-moi quelque chose** de la barre des tâches Windows, saisissez `Command Prompt`, puis choisissez l’application de bureau **Invite de commandes** pour ouvrir la fenêtre de console.

1. Cliquez avec le bouton droit sur le projet HelloWorld (et non la solution HelloWorld) et sélectionnez **Publier** à partir du menu. Vous pouvez également sélectionner **Publier HelloWorld** à partir du menu **Build** principal de Visual Studio.

1. Lorsque la boîte de dialogue **Publier** présentée dans l'illustration suivante s’affiche, créez un nouveau profil de publication en sélectionnant **Créer un nouveau profil.**

1. Dans la boîte de dialogue **Choisir une cible de publication** présentée dans l'illustration suivante, sélectionnez le bouton **OK** pour publier votre application sur votre système de fichiers local. Il se trouve dans le sous-répertoire bin\release\PublishOutput du répertoire de projet de votre application.

1. Maintenant que vous avez créé un profil de publication, sélectionnez le bouton **Publier** situé dans la boîte de dialogue **publication** présentée dans l'illustration suivante.

   ![Image](media/publish-2.jpg)

1. Comme le montre l’illustration suivante, la sortie publiée inclut les trois fichiers suivants qui constituent votre application, et vous pouvez les déployer en les copiant sur un système cible :

      - HelloWorld.dll
   
      - HelloWorld.deps.json

      - HelloWorld.runtimeconfig.json

   Un quatrième fichier, HelloWorld.pdb, contient les symboles de débogage. Il est inutile de distribuer ce fichier avec votre application, même si vous devez l’enregistrer au cas où vous auriez à déboguer la version publiée de votre application.

   ![Image](media/pub-files.jpg)

Le processus de publication crée un déploiement dépendant du framework ; l’application publiée s’exécutera sur toutes les plateformes prises en charge par .NET Core, à la seule condition que .NET Core soit installé sur le système. Les utilisateurs peuvent exécuter votre application en émettant la commande `dotnet.exe HelloWorld.dll` à partir d’une fenêtre de console.

Pour plus d’informations sur la publication et le déploiement d’applications .NET Core, consultez [Déploiement d’applications .NET](../../core/deploying/index.md).
