---
title: "Architecture RC4 des outils en ligne de commande .NET Core │ Microsoft Docs"
description: "RC4 apporte certaines modifications à l’organisation en couches des outils .NET Core globaux."
keywords: "CLI, extensibilité, commandes personnalisées, .NET Core"
author: blackdwarf
ms.date: 11/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 7fff0f61-ac23-42f0-9661-72a7240a4456
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: 305d046c698ca9f7ebb5ac56387cfef00145393e

---

# <a name="high-level-overview-of-changes-in-cli-rc4"></a>Vue d’ensemble générale des modifications de l’interface CLI RC4

[!INCLUDE[preview-warning](../../../includes/warning.md)]

Ce document décrit de façon générale les modifications qu’apporte le passage de `project.json` à MSBuild et au système de projet `csproj`. Il décrit la nouvelle organisation en couches des outils, les nouveaux éléments disponibles et leur place dans la vue d’ensemble. La lecture de cet article doit vous aider à mieux comprendre tous les éléments qui composent les outils .NET Core après le passage à MSBuild et `csproj`. 

## <a name="moving-away-from-projectjson"></a>Abandon de project.json
La principale modification apportée aux outils RC4 pour .NET Core est certainement le [passage de project.json à csproj](https://blogs.msdn.microsoft.com/dotnet/2016/05/23/changes-to-project-json/) comme système de projet. La version RC4 des outils en ligne de commande est la première version des outils en ligne de commande .NET Core qui ne contient aucune prise en charge pour project.json. Cela signifie qu’elle ne peut pas servir à générer, exécuter ou publier des bibliothèques et des applications basées sur project.json. Pour utiliser cette version des outils, vous devez migrer vos projets existants ou en démarrer de nouveaux. 

Dans le cadre de ce passage, le moteur de génération personnalisé qui a été développé pour générer des projets project.json a été remplacé par un moteur de génération mature et entièrement compatible appelé [MSBuild](https://github.com/Microsoft/msbuild). MSBuild est un moteur connu dans la communauté .NET, car c’est une technologie clé depuis la première version Release de la plateforme. Bien sûr, comme il doit générer des applications .NET Core, MSBuild a été porté vers .NET Core et peut être utilisé sur n’importe quelle plateforme sur laquelle s’exécute .NET Core. Une des principales promesses de .NET Core réside dans une pile de développement multiplateforme, et nous avons veillé à ce que cette évolution n’entrave pas cette promesse.

> [!NOTE]
> Si vous débutez avec MSBuild et souhaitez en savoir plus, vous pouvez commencer par lire l’article [Concepts de MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-concepts). 

## <a name="the-tooling-layers"></a>Les couches des outils
Le fait de quitter le système de projet existant et de changer de moteur de génération suscite naturellement la question de savoir si l’une ou l’autre de ces modifications change l’organisation en couches globale de l’ensemble de l’écosystème des outils .NET Core. Existe-t-il de nouvelles parties et composants ?

Commençons par un rappel rapide de l’organisation en couches de Preview 2, comme l’illustre l’image suivante :

![Architecture générale des outils Preview 2](media/p2-arch.png)

L’organisation en couches des outils est assez simple. En bas, nous avons les outils en ligne de commande .NET Core qui constituent la base. Tous les autres outils généraux tels que Visual Studio ou VS Code dépendent de l’interface de ligne de commande et s’appuient sur celle-ci pour générer des projets, restaurer des dépendances, etc. Cela signifie que, par exemple, si Visual Studio souhaite effectuer une opération de restauration, il appelle la commande `dotnet restore` dans l’interface de ligne de commande. 

Avec le passage au nouveau système de projet, le schéma précédent change : 

![Architecture générale des outils RC4](media/p3-arch.png)

La principale différence est que l’interface de ligne de commande n’est plus la couche de base, ce rôle étant rempli par le « composant SDK partagé ». Ce composant SDK partagé est un ensemble de cibles et de tâches associées chargées de la compilation de votre code, de sa publication, de l’empaquetage des packages NuGet, etc. Le SDK lui-même est open source et est disponible sur GitHub dans le [dépôt SDK](https://github.com/dotnet/sdk). 

> [!NOTE]
> Une « cible » est un terme MSBuild qui indique une opération nommée que MSBuild peut appeler. Elle est généralement associée à une ou plusieurs tâches qui exécutent une logique que la cible est supposée effectuer. MSBuild prend en charge plusieurs cibles prédéfinies telles que `Copy` ou `Execute`, et permet aussi aux utilisateurs d’écrire leurs propres tâches à l’aide de code managé et de définir des cibles pour exécuter ces tâches. Pour plus d’informations, consultez [Tâches MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-tasks). 

Tous les ensembles d’outils utilisent désormais le composant SDK partagé et ses cibles, interface de ligne de commande incluse. Par exemple, la prochaine version de Visual Studio n’appellera pas la commande `dotnet restore` pour restaurer les dépendances des projets .NET Core, mais utilisera directement la cible « Restore ». Comme il s’agit de cibles de MSBuild, vous pouvez également utiliser MSBuild sous forme brute pour les exécuter à l’aide de la commande [dotnet msbuild](dotnet-msbuild.md). 

### <a name="rc4-cli-commands"></a>Commandes CLI RC4
Le composant SDK partagé signifie que la plupart des commandes CLI existantes ont été réimplémentées comme cibles et tâches MSBuild. Que cela signifie-t-il pour les commandes CLI et votre utilisation de l’ensemble d’outils ? 

Sur le plan pratique, la manière dont vous utilisez l’interface de ligne de commande ne change pas. L’interface de ligne de commande reprend les commandes de base de la version Release Preview 2 :

* `new`
* `restore`
* `run` 
* `build`
* `publish`
* `test`
* `pack` 

Ces commandes font toujours ce que vous attendez d’elles (créer un projet, le générer, le publier, l’empaqueter, etc.). La plupart des options ne sont pas modifiées et sont toujours disponibles. Vous pouvez consulter les écrans d’aide des commandes (à l’aide de `dotent <command> --help`) ou la documentation de la version RC4 sur ce site pour vous familiariser avec les modifications apportées. 

Du point de vue de l’exécution, les commandes CLI construisent, à partir de leurs paramètres, un appel à MSBuild « brut » qui définit les propriétés nécessaires et exécute la cible souhaitée. Pour mieux illustrer ce propos, considérons la commande suivante : 

    `dotnet publish -o pub -c Release`
    
Cette commande publie une application dans un dossier `pub` à l’aide de la configuration « Release ». En interne, cette commande se traduit par l’appel MSBuild suivant : 

    `dotnet msbuild /t:Publish /p:OutputPath=pub /p:Configuration=Release`

La principale exception à cette règle sont les commandes `new` et `run`, car elles n’ont pas été implémentées comme cibles de MSBuild. 

## <a name="conclusion"></a>Conclusion 
Ce document a décrit de façon générale les modifications qui affectent l’architecture générale et le fonctionnement des outils de l’interface de ligne de commande dans la version RC4. Il a introduit la notion de composant SDK partagé et a expliqué le fonctionnement des commandes CLI dans la version RC4, d’un point de vue technique.


<!--HONumber=Feb17_HO2-->


