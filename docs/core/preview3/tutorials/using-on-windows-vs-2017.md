---
title: "Bien démarrer avec .NET Core sur Windows à l’aide de Visual Studio 2017 │ Microsoft Docs"
description: "Bien démarrer avec .NET Core sur Windows à l’aide de Visual Studio 2017"
keywords: .NET, .NET Core
author: bleroy
ms.author: mairaw
ms.date: 01/18/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 613c65d0-f773-41b8-ba0e-83f6a82a0b30
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: cc2c2853bc31e161d1fe0de4edc71d15281c6d24

---

# <a name="getting-started-with-net-core-on-windows-using-visual-studio-2017-net-core-tools-rc4"></a>Bien démarrer avec .NET Core sur Windows à l’aide de Visual Studio 2017 (outils .NET Core RC4)

> [!WARNING]
> Cette rubrique s’applique aux outils .NET Core RC4. Pour la version Visual Studio 2015 - Outils .NET Core Preview 2, consultez la rubrique [Bien démarrer avec .NET Core sur Windows à l’aide de Visual Studio 2015](../../tutorials/using-on-windows.md).

Visual Studio 2017 fournit un environnement de développement complet pour le développement d’applications .NET Core. Les procédures décrites dans ce document expliquent comment créer une application console très simple à l’aide de Visual Studio et .NET Core.

## <a name="prerequisites"></a>Conditions préalables

Suivez les instructions stipulées dans [notre page de prérequis](../windows-prerequisites.md) pour mettre à jour votre environnement.

## <a name="getting-started"></a>Commencer

Les étapes suivantes permettent de configurer Visual Studio 2017 pour le développement d’applications console .NET Core :

1. Ouvrez Visual Studio, et dans le menu **Fichier**, choisissez **Nouveau**, puis **Projet**.

2. Dans la boîte de dialogue **Nouveau projet**, dans la liste **Modèles**, développez le nœud **Visual C#**, puis choisissez **.NET Core**. Cinq modèles de projet doivent s’afficher pour l’**Application console (.NET Core)**, la **Bibliothèque de classes (.NET Standard)**, le **Projet de test unitaire (.NET Core)**, la **Bibliothèque de classes (.NET Core)** et l’**Application web ASP.NET Core (.NET Core)**. Choisissez **Application console (.NET Core)**, tapez un nom pour votre projet, choisissez un emplacement, puis cliquez sur OK.

  ![Nouveau projet : application console](media/new-project-console-app.png)

3. Le projet résultant a un seul fichier C# qui génère « Hello World » dans la console.

  ![Projet de l’application console](media/console-app-solution.png)

Vous pouvez exécuter cette application en mode débogage à l’aide de F5 ou en mode release à l’aide de Ctrl+F5. Vous pouvez également définir des points d’arrêt pour interrompre l’exécution et inspecter les variables ou commencer à écrire du code plus intéressant.

Bon développement !

## <a name="next-steps"></a>Étapes suivantes

Après cette introduction simple, vous vous demandez probablement comment créer des solutions plus avancées, avec des bibliothèques et des tests réutilisables. La rubrique [Génération d’une solution .NET Core complète sur Windows à l’aide de Visual Studio 2017](using-on-windows-vs-2017-full-solution.md) vous indique comment procéder.



<!--HONumber=Feb17_HO2-->


