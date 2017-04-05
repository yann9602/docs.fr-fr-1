---
title: "Analyseur de portabilité .NET | .NET"
description: "Découvrez comment utiliser l’outil Analyseur de portabilité .NET pour évaluer la portabilité de votre code sur les différentes plateformes .NET."
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 01/23/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: dd14dc23b14e45569f0fdb9a37954b34c4e654d1
ms.lasthandoff: 03/13/2017

---

# <a name="the-net-portability-analyzer"></a>Analyseur de portabilité .NET

Vous voulez que vos bibliothèques soient multiplateformes ? Vous voulez savoir quelle quantité de travail est nécessaire pour que votre application soit compatible avec d’autres plateformes .NET ? L’[Analyseur de portabilité .NET](http://go.microsoft.com/fwlink/?LinkID=507467) est un outil qui vous donne un rapport détaillé sur la flexibilité de votre programme sur les plateformes .NET en analysant des assemblys. L’Analyseur de portabilité est proposé sous la forme d’une extension Visual Studio 2015 et d’une application console.

## <a name="new-targets"></a>Nouvelles cibles

*   [.NET Core](https://www.dotnetfoundation.org/netcore) : possède une conception modulaire, emploie le mode côte-à-côte et cible des scénarios multiplateformes. Le mode côte-à-côte vous permet d’adopter de nouvelles versions de .NET Core sans interrompre les autres applications.
*   [ASP.NET Core](https://www.dotnetfoundation.org/aspnet-core) : est un framework web moderne basé sur .NET Core, qui offre donc aux développeurs les mêmes avantages.
*   [.NET Native](https://blogs.msdn.microsoft.com/dotnet/2014/04/24/net-native-performance) : améliore les performances de vos applications Windows Store qui s’exécutent sur des machines x64 et ARM en utilisant une compilation statique de .NET Native.

## <a name="how-to-use-portability-analyzer"></a>Guide pratique pour utiliser l’Analyseur de portabilité

Pour commencer à utiliser l’Analyseur de portabilité .NET, vous devez tout d’abord télécharger et installer l’extension à partir de la [galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkID=507467). Pour le configurer dans Visual Studio, sélectionnez **Analyser** > **Paramètres de l’Analyseur de portabilité**, puis choisissez vos plateformes cibles.

![Capture d’écran de portabilité](./media/portability-analyzer/portability-screenshot.png)

Pour analyser l’ensemble du projet, cliquez avec le bouton droit sur votre projet dans l’**Explorateur de solutions** et sélectionnez **Analyser la portabilité des assemblys**. Sinon, accédez au menu **Analyser** et sélectionnez **Analyser la portabilité des assemblys**. À partir de là, sélectionnez l’exécutable ou la DLL de votre projet.

![Explorateur de solutions de portabilité](./media/portability-analyzer/portability-solution-explorer.png)

Après avoir exécuté l’analyse, vous obtenez votre rapport de portabilité .NET. Seuls les types qui ne sont pas pris en charge par une plateforme cible s’affichent dans la liste et vous pouvez consulter les recommandations de l’onglet **Messages** dans la **Liste d’erreurs**. Vous pouvez également accéder aux zones de problèmes directement à partir de l’onglet **Messages**.

![Rapport de portabilité](./media/portability-analyzer/portability-report.png)

Vous ne voulez pas utiliser Visual Studio ? Vous pouvez également utiliser l’Analyseur de portabilité à partir de l’invite de commandes. Téléchargez l’[Analyseur de portabilité d’API](http://www.microsoft.com/download/details.aspx?id=42678).

*   Tapez la commande suivante pour analyser le répertoire actif : `\...\ApiPort.exe analyze -f .`
*   Pour analyser une liste spécifique de fichiers .dll, tapez la commande suivante : `\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`

Votre rapport de portabilité .NET est enregistré comme un fichier Excel (*.xlsx*) dans votre répertoire actif. L’onglet **Détails** du classeur Excel contient plus d’informations.

Pour plus d’informations sur l’Analyseur de portabilité .NET, consultez la [documentation GitHub](https://github.com/Microsoft/dotnet-apiport#documentation) et la vidéo Channel 9 [A brief look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) (Aperçu rapide de l’Analyseur de portabilité .NET).
