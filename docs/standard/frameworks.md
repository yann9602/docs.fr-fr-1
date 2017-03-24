---
title: Infrastructures et cibles
description: "Explique les concepts de cibles de framework lors de l’écriture de code .NET."
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 09/19/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6ef56a2e-593d-497b-925a-1e25bb6df2e6
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: f0c1987f46bd3715c54e270c15eea4b8ee7b67e6
ms.lasthandoff: 03/13/2017

---

# <a name="frameworks-and-targets"></a>Infrastructures et cibles

L’écosystème .NET présente un concept de frameworks. Les frameworks définissent l’API que vous pouvez utiliser pour cibler une plateforme en particulier. Le .NET Framework 4.6 est l’une de ces plateformes. Les frameworks sont utilisés dans Visual Studio et d’autres IDE et éditeurs pour vous fournir l’ensemble d’API qui vous convient. Ils sont également utilisés par NuGet, pour la production et la consommation de packages NuGet, afin de vérifier que vous produisez et utilisez les packages appropriés (et les ressources sous-jacentes) pour le framework que vous ciblez. Les frameworks sont en quelque sorte une accréditation de l’écosystème .NET. Ils sont là pour vous éviter, vous et vos clients, de faire des erreurs et de voir l’exception @System.MissingMethodExceptiont les autres exceptions du même type pendant l’exécution.

## <a name="framework-versions"></a>Versions de framework

Le tableau ci-dessous définit l’ensemble des frameworks que vous pouvez utiliser, la façon dont ils sont désignés et la version de la [bibliothèque .NET Standard](library.md) qu’ils implémentent.

| Framework | Dernière version | Moniker du Framework cible | Moniker du Framework cible compact | Version .NET Standard | Métapackage |
|:--------: | :--: | :--: | :--: | :--: | :--: | :--: |
| .NET Standard | 1.6 | .NETStandard,Version=1.6 | netstandard1.6 | N/A | [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library)|
| Application .NET Core | 1.0.1 | .NETCoreApp,Version=1.0 | netcoreapp1.0 | 1.6 | [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App)|
| .NET Framework | 4.6.2 | .NETFramework,Version=4.6.2 | net462 | 1,5 | N/A |

> [!NOTE]
> Ces versions de framework sont les dernières versions stables. Certaines versions précommerciales ne sont peut-être pas décrites dans ce tableau.

## <a name="writing-about-frameworks"></a>Écrire sur les frameworks

Il existe plusieurs façons de référencer les frameworks par écrit, la plupart d’entre elles sont utilisées dans cette documentation. Elles sont décrites ci-dessous, à la fois comme une légende pour interpréter la documentation, mais aussi pour guider leur utilisation dans d’autres documents.

Dans .NET Framework 4.6.1, par exemple, les formes suivantes peuvent être utilisées :

**Référence à un produit**

Vous pouvez référencer une plateforme ou un runtime .NET.

- « .NET Framework 4.6.1 »

**Référence à un framework**

Vous pouvez référencer un framework ou le ciblage d’un framework à l’aide des formes courtes ou longues du Moniker du Framework cible. Les deux sont valides dans le cas général.

- `.NETFramework,Version=4.6.1`
- `net461`

**Référence à une famille de frameworks**

Vous pouvez référencer une famille de frameworks à l’aide des formes courtes ou longues de l’ID de framework. Les deux sont valides dans le cas général.

- `.NETFramework`
- `net`

