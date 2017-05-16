---
title: Frameworks cibles | Microsoft Docs
description: "Informations concernant les frameworks cibles pour les applications et les bibliothèques .NET Core."
keywords: .NET, .NET Core, framework, TFM
author: richlander
ms.author: mairaw
ms.date: 04/27/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6ef56a2e-593d-497b-925a-1e25bb6df2e6
ms.translationtype: Machine Translation
ms.sourcegitcommit: 45835eb80642253f80ea630ae9db1ac766b72b9c
ms.openlocfilehash: 11c1f11e4f8354b7573d03e680cf4a8a16fa26d9
ms.contentlocale: fr-fr
ms.lasthandoff: 05/11/2017

---

# <a name="target-frameworks"></a>Versions cibles de .NET Framework

Les *frameworks* définissent les objets, les méthodes et les outils que vous utilisez pour créer des applications et des bibliothèques. Le .NET Framework est utilisé pour créer des applications et des bibliothèques principalement pour une exécution sur des systèmes fonctionnant sous un système d’exploitation Windows. .NET Core comprend un framework qui vous permet de créer des applications et des bibliothèques qui s’exécutent sur différents systèmes d’exploitation.

Les termes *framework* et *plateforme* peuvent parfois entraîner une certaine confusion selon la façon dont ils sont utilisés dans des phrases. Rendant les interprétations encore plus difficiles, le terme *plateforme* a des significations différentes dans des contextes différents. Par exemple, vous pouvez rencontrer « .NET Core » décrit comme étant « le framework .NET Core » dans le contexte de la création d’applications et de bibliothèques, et également décrit comme étant « la plateforme .NET Core » dans un contexte indiquant l’endroit où le code de l’application et de la bibliothèque est exécuté. Une *plateforme informatique* décrit *où et comment* une application est exécutée. Comme .NET Core exécute le code avec le [Common Language Runtime .NET Core (CoreCLR)](https://github.com/dotnet/coreclr), il est aussi une plateforme. Ceci est également vrai du .NET Framework, qui a le [Common Language Runtime (CLR)](clr.md) pour exécuter le code d’application et de bibliothèque qui a été développé avec les objets, les méthodes et les outils du framework du .NET Framework. Vous rencontrerez souvent le terme « multiplateforme » dans la documentation, mais quand vous voyez ce terme, vous devez penser « multisystème d’exploitation et multi-architecture (x86, x64, ARM) », car c’est généralement la signification que l’auteur veut lui donner.

Les objets et les méthodes des frameworks sont appelés « interfaces de programmation d’applications » (API). Les API de framework sont utilisées dans [Visual Studio](https://www.visualstudio.com/), [Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/), [Visual Studio Code](https://code.visualstudio.com/), et dans les autres environnements de développement intégrés (IDE) et éditeurs, pour vous fournir le bon ensemble d’objets et de méthodes pour le développement. Les frameworks sont également utilisés par [NuGet](https://www.nuget.org/) pour la production et la consommation de packages NuGet, dans le but de garantir que vous produisez et que vous utilisez les packages appropriés pour les frameworks que vous ciblez dans votre application ou votre bibliothèque.

Quand vous *ciblez un framework* ou que vous en ciblez plusieurs, vous avez décidé quels ensembles d’API et quelles versions de ces API vous voulez utiliser. Les frameworks sont référencés de plusieurs façons : par nom de produit, par noms courts ou longs de framework, et par famille.

## <a name="referring-to-frameworks"></a>Référence à des frameworks

Il existe plusieurs façons de faire référence à des frameworks, la plupart étant utilisées dans la documentation .NET Core. Par exemple, en prenant .NET Framework 4.6.2 comme exemple, les formats suivants sont utilisés :

**Référence à un produit**

Vous pouvez référencer une plateforme ou un runtime .NET. Les deux sont valides.

* .NET Framework 4.6.2
* .NET 4.6.2

**Référence à un framework**

Vous pouvez référencer un framework ou le ciblage d’un framework à l’aide des formes courtes ou longues du Moniker du Framework cible. Les deux sont valides.

* `.NETFramework,Version=4.6.2`
* `net462`

**Référence à une famille de frameworks**

Vous pouvez référencer une famille de frameworks à l’aide des formes courtes ou longues de l’ID de framework. Les deux sont valides.

* `.NETFramework`
* `net`

## <a name="latest-framework-versions"></a>Versions les plus récentes des frameworks

Le tableau ci-dessous définit l’ensemble des frameworks que vous pouvez utiliser, la façon dont ils sont référencés et la version de la [bibliothèque .NET Standard](library.md) qu’ils implémentent. Ces versions de framework sont les dernières versions stables. Les préversions ne sont pas mentionnées.

| Framework             | Dernière version | Moniker du Framework cible | Moniker du Framework cible compact | Version .NET Standard | Métapackage |
| :-------------------: | :------------: | :----------------------------: | :------------------------------------: | :-------------------: | :---------: |
| .NET Standard         | 1.6.1          | .NETStandard,Version=1.6       | netstandard1.6                         | N/A                   | [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) |
| Application .NET Core | 1.1.1          | .NETCoreApp,Version=1.1        | netcoreapp1.1                          | 1.6                   | [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) |
| .NET Framework        | 4.6.2          | .NETFramework,Version=4.6.2    | net462                                 | 1,5                   | N/A |

## <a name="supported-frameworks"></a>Frameworks pris en charge

Un framework est généralement référencé par un moniker de framework cible court ou *TFM* (Target Framework Moniker). Dans .NET Standard, ceci est également généralisé sous la forme *TxM* pour permettre une référence unique à plusieurs frameworks. Les clients NuGet prennent en charge les frameworks suivants. Les équivalents sont indiqués entre crochets (`[]`).

| Nom                       | Abréviation | TFMs/TxMs                                    |
| -------------------------- | ------------ | -------------------------------------------- |
| .NET Standard              | netstandard  | netstandard1.0                               |
|                            |              | netstandard1.1                               |
|                            |              | netstandard1.2                               |
|                            |              | netstandard1.3                               |
|                            |              | netstandard1.4                               |
|                            |              | netstandard1.5                               |
|                            |              | netstandard1.6                               |
| .NET Core                  | netcoreapp   | netcoreapp1.0                                |
|                            |              | netcoreapp1.1                                |
| .NET Framework             | net          | net11                                        |
|                            |              | net20                                        |
|                            |              | net35                                        |
|                            |              | net40                                        |
|                            |              | net403                                       |
|                            |              | net45                                        |
|                            |              | net451                                       |
|                            |              | net452                                       |
|                            |              | net46                                        |
|                            |              | net461                                       |
|                            |              | net462                                       |
| Windows Store              | netcore      | netcore [netcore45]                          |
|                            |              | netcore45 [win, win8]                        |
|                            |              | netcore451 [win81]                           |
| .NET Micro Framework       | netmf        | netmf                                        |
| Silverlight                | sl           | sl4                                          |
|                            |              | sl5                                          |
| Windows Phone              | wp           | wp [wp7]                                     |
|                            |              | wp7                                          |
|                            |              | wp75                                         |
|                            |              | wp8                                          |
|                            |              | wp81                                         |
|                            |              | wpa81                                        |
| Plateforme Windows universelle | uap          | uap [uap10.0]                                |
|                            |              | uap10.0 [win10] [netcore50]                  |

## <a name="deprecated-frameworks"></a>Frameworks dépréciés

Les frameworks suivants sont dépréciés. Les packages ciblant ces frameworks doivent migrer vers les versions de remplacement indiquées.

| Framework déprécié | Replacement |
| -------------------- | ----------- |
| aspnet50             | netcoreapp  |
| aspnetcore50         |             |
| dnxcore50            |             |
| dnx                  |             |
| dnx45                |             |
| dnx451               |             |
| dnx452               |             |
| dotnet               | netstandard |
| dotnet50             |             |
| dotnet51             |             |
| dotnet52             |             |
| dotnet53             |             |
| dotnet54             |             |
| dotnet55             |             |
| dotnet56             |             |
| netcore50            | uap10.0     |
| win                  | netcore45   |
| win8                 | netcore45   |
| win81                | netcore451  |
| win10                | uap10.0     |
| winrt                | netcore45   |

## <a name="precedence"></a>Priorité

Un certain nombre de frameworks sont liés à et compatibles l’un avec l’autre, mais sans être nécessairement équivalents :

| Framework                        | Peut utiliser   |
| -------------------------------- | --------- |
| uap (Plateforme Windows universelle) | win81     |
|                                  | wpa81     |
|                                  | netcore50 |
| win (Windows Store)              | winrt     |
|                                  | winrt45   |

## <a name="net-standard"></a>.NET Standard

Le [.NET Standard](https://github.com/dotnet/standard) simplifie les références entre les frameworks compatible au niveau binaire, ce qui permet à un même framework cible de référencer une combinaison d’autres frameworks. Pour plus d’informations, consultez la rubrique [Bibliothèque .NET Standard](library.md).

L’outil [Get Nearest Framework des outils Nuget](http://nugettoolsdev.azurewebsites.net/) simule la logique NuGet utilisée pour la sélection d’un framework à partir de nombreuses ressources de framework disponibles dans un package, en fonction du framework du projet. Pour utiliser l’outil, entrez un framework de projet, et un ou plusieurs frameworks du package. Sélectionnez le bouton **Submit**. L’outil indique si les frameworks du package que vous répertoriez sont compatibles avec le framework de projet que vous fournissez.

## <a name="portable-class-libraries"></a>Bibliothèques de classes portables

Pour plus d’informations sur les bibliothèques de classes portables, consultez la section [Portable Class Libraries](https://docs.microsoft.com/nuget/schema/target-frameworks#portable-class-libraries) de la rubrique *Target Framework* dans la documentation de NuGet. Stephen Cleary a créé un outil qui répertorie les bibliothèques de classes portables. Pour plus d’informations, consultez [Framework Profiles in .NET](http://blog.stephencleary.com/2012/05/framework-profiles-in-net.html).

