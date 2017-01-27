---
title: "Bien démarrer avec .NET Core sur Windows à l’aide de Visual Studio 2017"
description: "Bien démarrer avec .NET Core sur Windows à l’aide de Visual Studio 2017"
keywords: .NET, .NET Core
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: d743134a-08a3-4ff6-aab7-49f71f0568c3
translationtype: Human Translation
ms.sourcegitcommit: 71eab6216e116b99927dfeaa8ce3cf70bcc08a5e
ms.openlocfilehash: 4437f44523bcc4e8517de5b6be42a63439f817d7

---

# <a name="getting-started-with-net-core-on-windows-using-visual-studio-2017"></a>Bien démarrer avec .NET Core sur Windows à l’aide de Visual Studio 2017

par [Bertrand Le Roy](https://github.com/bleroy) et [Phillip Carter](https://github.com/cartermp)

Visual Studio 2017 fournit un environnement de développement complet pour le développement d’applications .NET Core. Les procédures décrites dans ce document expliquent comment créer une application console très simple à l’aide de Visual Studio et .NET Core.

## <a name="prerequisites"></a>Conditions préalables

Suivez les instructions stipulées dans [notre page de prérequis](../windows-prerequisites.md) pour mettre à jour votre environnement.

## <a name="getting-started"></a>Commencer

Les étapes suivantes permettent de configurer Visual Studio 2017 pour le développement d’applications console .NET Core :

1. Ouvrez Visual Studio, et dans le menu **Fichier**, choisissez **Nouveau**, puis **Projet**.

2. Dans la boîte de dialogue **Nouveau projet**, dans la liste **Modèles**, développez le nœud **Visual C#**, puis choisissez **.NET Core**. Quatre modèles de projet doivent s’afficher pour l’**Application console (.NET Core)**, le **Projet de test unitaire (.NET Core)**, la **Bibliothèque de classes (.NET Core)** et l’**Application web ASP.NET Core (.NET Core)**. Choisissez **Application console (.NET Core)**, tapez un nom pour votre projet, choisissez un emplacement, puis cliquez sur OK.

  ![Nouveau projet : application console](media/new-project-console-app.png)

3. Le projet résultant a un seul fichier C# qui génère « Hello World » dans la console.

  ![Projet de l’application console](media/console-app-solution.png)

Vous pouvez exécuter cette application en mode débogage à l’aide de F5 ou en mode release à l’aide de Ctrl+F5. Vous pouvez également définir des points d’arrêt pour interrompre l’exécution et inspecter les variables ou commencer à écrire du code plus intéressant.

Bon développement !

## <a name="what-to-do-next"></a>Que faire maintenant ?

Après cette introduction simple, vous vous demandez probablement comment créer des solutions plus avancées, avec des bibliothèques et des tests réutilisables. La rubrique [Génération d’une solution .NET Core complète sur Windows à l’aide de Visual Studio 2017](using-on-windows-vs-2017-full-solution.md) vous indique comment procéder.



<!--HONumber=Nov16_HO3-->


