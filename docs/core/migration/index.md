---
title: Migration .NET Core au format csproj | Microsoft Docs
description: Migration .NET Core de project.json vers csproj
keywords: .NET, .NET Core, migration .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/13/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 1feadf3d-3cfc-41dd-abb5-a4fc303a7b53
translationtype: Human Translation
ms.sourcegitcommit: fae5eabac7d1aac577c5c7a27e306c8c7ea8b418
ms.openlocfilehash: 73ab5a9bdd957e6d9394a3be0aa55f554ee7a86a
ms.lasthandoff: 03/16/2017

---

# <a name="migrating-net-core-projects-to-the-csproj-format"></a>Migration de projets .NET Core au format csproj

Ce document couvre les scénarios de migration pour les projets .NET Core et passe en revue les trois scénarios de migration suivants :

1. [Migration à partir du schéma valide le plus récent de *project.json* vers *csproj*](#migration-from-projectjson-to-csproj)
2. [Migration à partir de DNX vers csproj](#migration-from-dnx-to-csproj)
3. [Migration de projets csproj .NET Core RC3 et antérieurs vers le format final](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

## <a name="migration-from-projectjson-to-csproj"></a>Migration de project.json vers csproj
La migration à partir de *project.json* vers *.csproj* peut être effectuée à l’aide de l’une des méthodes suivantes :

- [Visual Studio 2017](#visual-studio-2017)
- [Outil de ligne de commande dotnet migrate](#dotnet-migrate)
 
Les deux méthodes utilisant le même moteur sous-jacent pour migrer les projets, les résultats obtenus sont donc identiques dans les deux cas. Dans la plupart des cas, l’utilisation de l’une de ces deux méthodes pour migrer *project.json* vers *csproj* suffit et aucune autre modification manuelle du fichier projet n’est nécessaire. Le fichier *.csproj* obtenu porte le même nom que le répertoire le contenant.

### <a name="visual-studio-2017"></a>Visual Studio 2017

Quand vous ouvrez un fichier *.xproj* ou un fichier solution qui fait référence à des fichiers *.xproj*, la boîte de dialogue **Mise à niveau définitive** s’affiche. La boîte de dialogue affiche les projets à migrer. Si vous ouvrez un fichier solution, tous les projets spécifiés dans le fichier solution sont répertoriés. Passez en revue la liste des projets à migrer, puis sélectionnez **OK**.

![Boîte de dialogue Mise à niveau définitive indiquant la liste des projets à migrer](media/one-way-upgrade.jpg)

Visual Studio migre les projets choisis automatiquement. Quand vous migrez une solution, si vous ne choisissez pas tous les projets, la même boîte de dialogue s’affiche pour vous demander de mettre à niveau les projets restants de cette solution.

Les fichiers qui ont été migrés (*project.json*, *global.json*, *.xproj* et le fichier solution) sont déplacés vers un dossier de *sauvegarde*. Le fichier solution qui est migré est mis à niveau vers Visual Studio 2017 et vous ne pourrez pas l’ouvrir dans les versions précédentes de Visual Studio. Un fichier nommé *UpgradeLog.htm* qui contient un rapport de migration est également enregistré et automatiquement ouvert.

> [!IMPORTANT]
> Les nouveaux outils n’étant pas disponibles dans Visual Studio 2015, vous ne pouvez pas migrer vos projets à l’aide de cette version de Visual Studio.

### <a name="dotnet-migrate"></a>dotnet migrate

Dans le scénario de ligne de commande, vous pouvez utiliser la commande [`dotnet migrate`](../tools/dotnet-migrate.md). Elle migre un projet, une solution ou un ensemble de dossiers dans cet ordre, selon ceux qui ont été trouvés. Quand vous migrez un projet, le projet et toutes ses dépendances sont migrés.

Les fichiers qui ont été migrés (*project.json*, *global.json* et *.xproj*) sont déplacés vers un dossier de *sauvegarde*.

> [!NOTE]
> Si vous utilisez VS Code, la commande `dotnet migrate` ne modifie pas les fichiers spécifiques à VS Code comme `tasks.json`. Ces fichiers doivent être modifiés manuellement. Cela s’applique également si vous utilisez Project Ryder ou un éditeur ou environnement de développement intégré (IDE) autre que Visual Studio. 

Consultez la page [Mappage entre propriétés project.json et csproj](../tools/project-json-to-csproj.md) pour afficher une comparaison des formats project.json et csproj.

### <a name="common-issues"></a>Problèmes courants

- Si vous obtenez une erreur du type « Aucun fichier exécutable correspondant à la commande dotnet migrate n’a été trouvé » :

Exécutez `dotnet --version` pour afficher la version que vous utilisez. [`dotnet migrate`](../tools/dotnet-migrate.md) nécessite la CLI .NET Core RC3 ou version ultérieure.
Cette erreur s’affiche si un fichier *global.json* figure dans le répertoire actif ou parent et que la version `sdk` est une version antérieure.

## <a name="migration-from-dnx-to-csproj"></a>Migration à partir de DNX vers csproj
Si vous utilisez encore DNX pour le développement .NET Core, votre processus de migration doit être effectué en deux étapes :

1. Utilisez les [conseils de migration DNX existants](from-dnx.md) pour la migration à partir de DNX vers la CLI prenant en charge project-json.
2. Suivez les étapes de la section précédente pour la migration de *project.json* vers *.csproj*.  

> [!NOTE]
> DNX a été officiellement déprécié lors de la version Preview 1 de la CLI .NET Core. 

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>Migration de formats csproj .NET Core antérieurs vers le format csproj final
Le format csproj .NET Core est modifié et évolue avec chaque nouvelle version préliminaire des outils. Comme il n’existe aucun outil pour migrer votre fichier projet des versions antérieures de csproj vers la dernière version, vous devez modifier manuellement le fichier projet. Les étapes réelles dépendent de la version du fichier projet que vous migrez. Voici quelques conseils à prendre en compte en fonction des modifications apportées entre les versions :

* Supprimez la propriété de version des outils de l’élément `<Project>`, si elle existe. 
* Supprimez l’espace de noms XML (`xmlns`) de l’élément `<Project>`.
* S’il n’existe pas, ajoutez l’attribut `Sdk` à l’élément `<Project>` et affectez-lui la valeur `Microsoft.NET.Sdk` ou `Microsoft.NET.Sdk.Web`. Cet attribut spécifie que le projet utilise le SDK à utiliser. `Microsoft.NET.Sdk.Web` est utilisé pour les applications web.
* Supprimez les instructions `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` et `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` en haut et en bas du projet. Ces instructions d’importation étant indiquées implicitement par le SDK, il est inutile qu’elles figurent dans le projet. 
* Si des éléments `<PackageReference>` `Microsoft.NETCore.App` ou `NETStandard.Library` figurent dans votre projet, vous devez les supprimer. Ces références de package sont [indiquées implicitement par le SDK](https://aka.ms/sdkimplicitrefs). 
* Supprimez l’élément `<PackageReference>` `Microsoft.NET.Sdk`, s’il existe. La référence SDK est fournie par l’attribut `Sdk` sur l’élément `<Project>`. 
* Supprimez les modèles [Glob](https://en.wikipedia.org/wiki/Glob_(programming)) qui sont [indiqués implicitement par le SDK](../tools/csproj.md#default-compilation-includes-in-net-core-projects). En laissant ces modèles Glob dans votre projet, une erreur se produit lors de la génération, car les éléments de compilation sont dupliqués. 

Une fois ces étapes effectuées, votre projet doit être entièrement compatible avec le format csproj .NET Core final. 

Pour obtenir des exemples antérieurs et postérieurs à la migration de l’ancien format csproj vers le nouveau, consultez l’article [Updating Visual Studio 2017 RC – .NET Core Tooling improvements](https://blogs.msdn.microsoft.com/dotnet/2016/12/12/updating-visual-studio-2017-rc-net-core-tooling-improvements/) sur le blog .NET.

