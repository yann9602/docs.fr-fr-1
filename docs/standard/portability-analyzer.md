---
title: "Analyseur de portabilité .NET - .NET | Microsoft Docs"
description: "Découvrez comment utiliser l’outil Analyseur de portabilité .NET pour évaluer la portabilité de votre code sur les différentes implémentations de .NET."
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 07/26/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.translationtype: HT
ms.sourcegitcommit: 3155295489e1188640dae5aa5bf9fdceb7480ed6
ms.openlocfilehash: adb1971c14c8ff8c147dba378ae0e9a5bc0fb5ad
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---

# <a name="the-net-portability-analyzer"></a>Analyseur de portabilité .NET

Vous voulez que vos bibliothèques soient multiplateformes ? Vous voulez savoir quelle quantité de travail est nécessaire pour que votre application soit compatible avec d’autres implémentations de .NET ? L’[Analyseur de portabilité .NET](http://go.microsoft.com/fwlink/?LinkID=507467) est un outil qui vous donne un rapport détaillé sur la flexibilité de votre programme sur les implémentations de .NET en analysant des assemblys. L’Analyseur de portabilité est proposé sous la forme d’une extension Visual Studio et d’une application console.

## <a name="new-targets"></a>Nouvelles cibles

* [.NET Core](https://dotnetfoundation.org/net-core) : possède une conception modulaire, emploie le mode côte-à-côte et cible des scénarios multiplateformes. Le mode côte-à-côte vous permet d’adopter de nouvelles versions de .NET Core sans interrompre les autres applications.
* [ASP.NET Core](https://dotnetfoundation.org/asp-net-core) : est un framework web moderne basé sur .NET Core, qui offre donc aux développeurs les mêmes avantages.
* [Plateforme Windows universelle](https://blogs.msdn.microsoft.com/dotnet/2014/04/24/net-native-performance) : améliore les performances de vos applications Windows Store qui s’exécutent sur des machines x64 et ARM en utilisant une compilation statique de .NET Native. 
* .NET Core + extensions de plateforme : inclut les API .NET Core en plus des autres API dans l’écosystème .NET telles que WCF, ASP.NET Core, FSharp et Azure.
* .NET Standard + extensions de plateforme : inclut les API .NET Standard en plus des autres API dans l’écosystème .NET telles que WCF, ASP.NET Core, FSharp et Azure.

## <a name="how-to-use-portability-analyzer"></a>Comment utiliser l’Analyseur de portabilité

Pour commencer à utiliser l’Analyseur de portabilité .NET, vous devez tout d’abord télécharger et installer l’extension à partir de la [galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkID=507467). Elle fonctionne sur Visual Studio 2015 et Visual Studio 2017. Pour le configurer dans Visual Studio, sélectionnez **Analyser** > **Paramètres de l’Analyseur de portabilité**, puis choisissez vos plateformes cibles.

![Capture d’écran de portabilité](./media/portability-analyzer/portability-screenshot.png)

Pour analyser l’ensemble du projet, cliquez avec le bouton droit sur votre projet dans l’**Explorateur de solutions** et sélectionnez **Analyser la portabilité des assemblys**. Sinon, accédez au menu **Analyser** et sélectionnez **Analyser la portabilité des assemblys**. À partir de là, sélectionnez l’exécutable ou la DLL de votre projet.

![Explorateur de solutions de portabilité](./media/portability-analyzer/portability-solution-explorer.png)

Après avoir exécuté l’analyse, vous obtenez votre rapport de portabilité .NET. Seuls les types qui ne sont pas pris en charge par une plateforme cible s’affichent dans la liste et vous pouvez consulter les recommandations de l’onglet **Messages** dans la **Liste d’erreurs**. Vous pouvez également accéder aux zones de problèmes directement à partir de l’onglet **Messages**.

![Rapport de portabilité](./media/portability-analyzer/portability-report.png)

Vous ne voulez pas utiliser Visual Studio ? Vous pouvez également utiliser l’Analyseur de portabilité à partir de l’invite de commandes. Téléchargez l’[Analyseur de portabilité d’API](http://www.microsoft.com/download/details.aspx?id=42678).

*   Tapez la commande suivante pour analyser le répertoire actif : `\...\ApiPort.exe analyze -f .`
*   Pour analyser une liste spécifique de fichiers .dll, tapez la commande suivante : `\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`

Votre rapport de portabilité .NET est enregistré en tant que fichier Excel (*.xlsx*) dans votre répertoire actif. L’onglet **Détails** du classeur Excel contient plus d’informations.

Pour plus d’informations sur l’Analyseur de portabilité .NET, consultez la [documentation GitHub](https://github.com/Microsoft/dotnet-apiport#documentation) et la vidéo Channel 9 [A brief look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) (Aperçu rapide de l’Analyseur de portabilité .NET).

