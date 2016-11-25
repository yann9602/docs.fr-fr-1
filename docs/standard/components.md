---
title: Composants architecturaux de .NET
description: "Décrit les principaux composants architecturaux de .NET tels que la bibliothèque .NET Standard, les runtimes .NET et les outils."
keywords: ".NET, bibliothèque .NET Standard, .NET Standard, .NET Core, .NET Framework, Xamarin, MSBuild, C#, F#, VB, compilateurs"
author: cartermp
manager: wpickett
ms.author: cartermp
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 2e38e9d9-8284-46ee-a15f-199adc4f26f4
translationtype: Human Translation
ms.sourcegitcommit: 254e89abefd28419bd2f36a047e4df939f7ff8da
ms.openlocfilehash: d0cd8f44876038167db23e7fd1e5a893460f3d73

---

# <a name="net-architectural-components"></a>Composants architecturaux de .NET

.NET est constitué de plusieurs composants clés.  Il possède une bibliothèque standard, appelée bibliothèque .NET Standard, qui est un grand ensemble d’API s’exécutant partout.  Cette bibliothèque standard est implémentée par trois runtimes .NET : .NET Framework, .NET Core et Mono pour Xamarin.  Les langages .NET s’exécutent aussi sur n’importe quel runtime .NET.  En outre, il existe sur chaque plateforme des outils qui vous permettent de générer des projets.  Ces outils sont les mêmes, quel que soit le runtime que vous choisissez.

Voici une présentation graphique de chacun des composants de .NET mentionnés précédemment et de son positionnement.

![Tous les composants architecturaux de .NET réunis](media/components.png)

Voici une brève explication de chacun des composants clés illustrés ci-dessus.  

## <a name="net-standard-library"></a>Bibliothèque .NET Standard

La bibliothèque .NET Standard est un ensemble d’API implémentées par un runtime .NET.

Plus formellement, il s’agit d’une spécification d’API .NET qui constituent un ensemble cohérent de contrats par rapport auxquels vous compilez votre code.  Ces contrats ont des implémentations sous-jacentes pour chaque runtime .NET.  Cela permet la portabilité entre les différents runtimes .NET ; votre code peut dès lors « s’exécuter partout ».

La bibliothèque .NET Standard est également une cible de génération, et est appelée le .NET Standard.  Actuellement, vous pouvez cibler .NET Standard 1.0-1.6.  Si votre code cible une version du .NET Standard, il peut s’exécuter sur n’importe quel runtime .NET qui implémente cette version.

Pour plus d’informations sur la bibliothèque .NET Standard et sur le ciblage du .NET Standard, consultez [Bibliothèque .NET Standard](library.md).

## <a name="net-runtimes"></a>Runtimes .NET

Il existe 3 runtimes .NET principaux que Microsoft développe et gère activement : .NET Core, .NET Framework et Mono pour Xamarin.

### <a name="net-core"></a>.NET Core

.NET Core est un runtime multiplateforme optimisé pour les charges de travail serveur.  Il implémente la bibliothèque .NET Standard, ce qui signifie que tout code qui cible le .NET Standard peut s’exécuter sur .NET Core.  Il s’agit du runtime utilisé par ASP.NET Core et la plateforme Windows universelle (UWP).  Il est moderne, efficace, et est conçu pour gérer les charges de travail serveur et cloud à grande échelle.

Pour en savoir plus sur .NET Core, consultez le [Guide .NET Core](../core/index.md).

### <a name="net-framework"></a>.NET Framework

.NET Framework est le runtime .NET historique qui existe depuis 2002.  Les développeurs .NET actuels l’ont toujours utilisé dans sa forme d’origine.  Il implémente la bibliothèque .NET Standard, ce qui signifie que tout code qui cible .NET Standard peut s’exécuter sur le .NET Framework.  Il contient des API supplémentaires spécifiques à Windows, notamment des API pour le développement bureautique Windows avec Windows Forms et WPF.  .NET Framework est optimisé pour la génération d’applications de bureau Windows.

Pour en savoir plus sur le .NET Framework, consultez [.NET Framework Guide](../framework/index.md) (Guide du .NET Framework).

### <a name="mono-for-xamarin"></a>Mono pour Xamarin

Mono est le runtime utilisé par les applications Xamarin.  Il implémente la bibliothèque .NET Standard, ce qui signifie que tout code qui cible .NET Standard peut s’exécuter sur les applications Xamarin.  Il contient des API supplémentaires pour iOS, Android, Xamarin.Forms et Xamarin.Mac.  Il est optimisé pour la génération d’applications mobiles sur iOS et Android.

Pour en savoir plus sur Mono, consultez la [documentation Mono](http://www.mono-project.com/docs/).

## <a name="net-tooling-and-common-infrastructure"></a>Outils .NET et infrastructure commune

Les différentes implémentations de .NET bénéficient des outils pour .NET.  Elles incluent entre autres :

* Les langages .NET et leurs compilateurs
* Les composants d’exécution, tels que le JIT et le Garbage Collector
* Système de projet .NET (parfois appelé « csproj », « vbproj » ou « fsproj »)
* MSBuild, moteur de génération utilisé pour générer les projets
* NuGet, gestionnaire de package de Microsoft pour .NET
* L’interface CLI .NET, interface de ligne de commande permettant de générer des projets .NET multiplateformes
* Outils d’orchestration de génération open source, tels que CAKE et FAKE

Le principal avantage est que vous disposez d’une grande quantité d’outils et d’une infrastructure commune pour toute « version » de .NET avec laquelle vous choisissez de générer vos applications.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus, consultez les rubriques suivantes :

* [Bibliothèque .NET Standard](library.md)
* [Guide .NET Core](../core/index.md)
* [.NET Framework Guide](../framework/index.md) (Guide du .NET Framework)
* [Guide C#](../csharp/index.md)
* [Guide F#](../csharp/index.md)
* [VB.NET Guide](../csharp/index.md) (Guide VB.NET)


<!--HONumber=Nov16_HO3-->


