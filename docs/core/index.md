---
title: .NET Core
description: .NET Core
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: f2b312cb-f80c-4b0d-9101-93908f06a6fa
translationtype: Human Translation
ms.sourcegitcommit: d97a1501ad25b683cbb5d7fbd8bd1b137f7f4046
ms.openlocfilehash: 132551673f97142a90513d43d7690867c3d00295
ms.lasthandoff: 04/10/2017

---

# <a name="net-core"></a>.NET Core

> Découvrez les [didacticiels « Bien démarrer »](getting-started.md) pour apprendre à créer une application .NET Core simple. Il suffit de quelques minutes pour créer votre première application et la rendre opérationnelle.

.NET Core est une plateforme de développement généraliste qui est tenue à jour par Microsoft et la communauté .NET sur [GitHub](https://github.com/dotnet/core). Cette multiplateforme prend en charge Windows, macOS et Linux. Elle peut être utilisée dans des scénarios d’appareil, de cloud et d’incorporation/IoT. 

Voici les caractéristiques qui définissent le mieux .NET Core :

- **Souplesse de déploiement :** peut être inclus dans votre application ou installé côte à côte à l’échelle d’un utilisateur ou de l’ordinateur.
- **Multiplateforme :** s’exécute sur Windows, macOS et Linux ; peut être porté sur d’autres systèmes d’exploitation. Au fil du temps, les scénarios pris en charge associant [systèmes d’exploitation](https://github.com/dotnet/core/blob/master/roadmap.md), processeurs et applications se multiplieront, qu’ils soient proposés par Microsoft, d’autres sociétés ou des individus.
- **Outils en ligne de commande :** tous les scénarios de produit peuvent être mis en œuvre au niveau de la commande. 
- **Compatibilité :** .NET Core est compatible avec le .NET Framework, Xamarin et Mono, via la [bibliothèque .NET Standard](../standard/library.md).
- **Open Source :** la plateforme .NET Core est open source et utilise des licences MIT et Apache 2. La documentation est concédée sous licence [CC-BY](https://creativecommons.org/licenses/by/4.0/). .NET Core est un projet [.NET Foundation](https://dotnetfoundation.org/).
- **Support Microsoft :** le support technique de .NET Core est assuré par Microsoft, via le [Support .NET Core](https://www.microsoft.com/net/core/support/)

## <a name="composition"></a>Composition

.NET Core est constitué des composants suivants :

- Un [runtime .NET](https://github.com/dotnet/coreclr), qui fournit un système de type, un chargement d’assembly, un récupérateur de mémoire, une interopérabilité native et d’autres services de base. 
- Un ensemble de [bibliothèques de frameworks](https://github.com/dotnet/corefx), qui fournissent des types de données primitives, des types de composition d’applications et des utilitaires essentiels. 
- Un [ensemble d’outils SDK](https://github.com/dotnet/cli) et des [compilateurs de langage](https://github.com/dotnet/roslyn) qui permettent d’assurer un développement de base, disponibles dans le [SDK .NET Core](sdk.md).
- L’hôte d’application « dotnet », qui sert à lancer les applications .NET Core. Il sélectionne et héberge le runtime, fournit une stratégie de chargement d’assembly et lance l’application. Ce même hôte sert aussi à lancer les outils du SDK à peu près de la même façon.

### <a name="languages"></a>Langages

Les langages C# et F# (et bientôt Visual Basic) peuvent être utilisés pour écrire des applications et des bibliothèques pour .NET Core. Les compilateurs s’exécutent sur .NET Core, ce qui vous permet de développer pour .NET Core où qu’il s’exécute. En règle générale, les compilateurs s’utilisent non pas directement, mais indirectement via les outils du SDK.

Les compilateurs C# et F# et les outils .NET Core sont ou peuvent être intégrés dans plusieurs éditeurs de texte et environnements IDE, dont Visual Studio, [Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp), Sublime Text et Vim, ce qui fait du développement .NET Core une option dans votre environnement de codage et système d’exploitation préférés. Nous devons en partie cette intégration aux bonnes gens du [projet OmniSharp](http://www.omnisharp.net/).

### <a name="net-apis-and-compatibility"></a>API .NET et compatibilité

.NET Core peut être considéré comme une version multiplateforme du .NET Framework, située au niveau de la couche des bibliothèques de classes de base du .NET Framework. Il implémente la spécification de la [bibliothèque .NET Standard](../standard/library.md). .NET Core propose un sous-ensemble d’API disponibles dans le .NET Framework ou Mono/Xamarin. Dans certains cas, les types ne sont pas entièrement implémentés (certains membres ne sont pas disponibles ou ont été déplacés).

Examinez la [feuille de route .NET Core](https://github.com/dotnet/core/blob/master/roadmap.md) pour en savoir plus sur la feuille de route des API .NET Core.

### <a name="relationship-to-the-net-standard-library"></a>Relation avec la bibliothèque .NET Standard

La [bibliothèque .NET Standard](../standard/library.md) est une spécification d’API qui décrit l’ensemble cohérent d’API .NET que les développeurs peuvent s’attendre à trouver dans chaque implémentation de .NET. Les implémentations .NET doivent implémenter cette spécification pour être considérées comme une bibliothèque .NET Standard conforme et pour prendre en charge les bibliothèques qui ciblent la bibliothèque .NET Standard. 

.NET Core implémente la bibliothèque .NET Standard et donc prend en charge les bibliothèques .NET Standard.

### <a name="workloads"></a>Charges de travail

En soi, .NET Core inclut un modèle d’application unique (les applications console) qui s’avère utile pour les outils, les services locaux et les jeux basés sur du texte. D’autres modèles d’application ont été construits par-dessus .NET Core pour étendre ses fonctionnalités, à savoir :

- [ASP.NET Core](https://docs.microsoft.com/aspnet/core/)
- [Plateforme Windows universelle (UWP) Windows 10](https://developer.microsoft.com/windows)
- [Xamarin.Forms](https://www.xamarin.com/forms)

### <a name="open-source"></a>Open Source

[.NET Core](https://github.com/dotnet/core) est open source (licence MIT) et a contribué à [.NET Foundation](https://dotnetfoundation.org) à l’initiative de Microsoft en 2014. Il compte parmi les projets les plus actifs de .NET Foundation. Les particuliers et les entreprises sont libres de l’adopter, que ce soit à des fins personnelles, éducatives ou commerciales. Diverses sociétés utilisent .NET Core à travers des applications, des outils, de nouvelles plateformes et des services d’hébergement. Certaines de ces sociétés contribuent de façon significative à .NET Core sur GitHub et fournissent des conseils sur l’orientation des produits dans le cadre du groupe de travail appelé le [.NET Foundation Technical Steering Group](https://dotnetfoundation.org/blog/tsg-welcome).

## <a name="acquisition"></a>Acquisition

.NET Core est distribué de deux façons principales : sous forme de packages sur NuGet.org et comme distributions autonomes.

### <a name="distributions"></a>Distributions

Vous pouvez télécharger .NET Core dans la page de [prise en main de .NET Core](https://www.microsoft.com/net/core).

- La distribution *Microsoft .NET Core* comprend le runtime CoreCLR, les bibliothèques associées, un hôte d’application console et le lanceur d’application `dotnet`. Elle est décrite par le métapackage [`Microsoft.NETCore.App`](https://www.nuget.org/packages/Microsoft.NETCore.App).
- La distribution *Microsoft .NET Core SDK* comprend .NET Core et un ensemble d’outils permettant de restaurer les packages NuGet et de compiler et générer des applications. 

En règle générale, le SDK .NET Core est installé en premier, préalablement au développement .NET Core. Vous pouvez choisir d’installer des builds .NET Core supplémentaires (peut-être en préversion).

### <a name="packages"></a>Packages

- Les [packages .NET Core](packages.md) contiennent le runtime et les bibliothèques (assemblys et implémentations de référence) .NET Core, par exemple, [System.Net.Http](https://www.nuget.org/packages/System.Net.Http/).
- Les [métapackages .NET Core](packages.md) décrivent les différentes couches et les différents modèles d’application en référençant l’ensemble approprié de packages de bibliothèque avec version.

## <a name="architecture"></a>Architecture

.NET Core est une implémentation .NET multiplateforme. Les principales enjeux architecturaux propres à .NET Core sont de fournir des implémentations spécifiques aux plateformes prises en charge.

### <a name="environments"></a>Environnements

.NET Core est pris en charge par Microsoft sur Windows, macOS et Linux. Sur Linux, Microsoft prend essentiellement en charge .NET Core s’exécutant sur les familles de distributions Red Hat Enterprise Linux (RHEL) et Debian.

.NET Core prend actuellement en charge les processeurs X64. Sur Windows, X86 est également pris en charge. ARM64 et ARM32 le seront prochainement.

La [feuille de route .NET Core](https://github.com/dotnet/core/blob/master/roadmap.md) fournit des informations plus détaillées sur la prise en charge présente et à venir des environnements de charges de travail, de systèmes d’exploitation et de processeurs.

D’autres sociétés ou groupes peuvent prendre en charge .NET Core pour d’autres types d’applications et environnements.

### <a name="designed-for-adaptability"></a>Conçu pour l’adaptabilité

.NET Core a été créé comme un produit très similaire aux autres produits .NET mais aussi unique. Il a été conçu pour offrir une grande capacité d’adaptation aux nouvelles plateformes, nouvelles charges de travail et avec les nouvelles chaînes d’outils de compilation. Des projets de portage sur plusieurs systèmes d’exploitation et processeurs sont en cours, et bien d’autres pourraient suivre. Un exemple est le projet [LLILC](https://github.com/dotnet/llilc), qui est un prototype précoce de compilation native pour .NET Core via le compilateur [LLVM](http://llvm.org/).

Le produit est divisé en plusieurs composants, ce qui permet d’adapter les différentes parties à de nouvelles plateformes, selon des calendriers différents. Le runtime et les bibliothèques de base spécifiques à la plateforme doivent être portés individuellement. Les bibliothèques indépendantes de la plateforme doivent fonctionner en l’état sur toutes les plateformes, de par leur construction. Il existe une tendance à vouloir réduire le nombre d’implémentations spécifiques à la plateforme pour optimiser l’efficacité des développeurs, qui préfèrent utiliser du code C# indépendant de la plateforme chaque fois que tout ou partie d’un algorithme ou d’une API peut être implémentée de cette façon.

Il est fréquent que des personnes s’interrogent sur la façon dont .NET Core est implémenté afin de prendre en charge plusieurs systèmes d’exploitation. Elles demandent généralement s’il existe des implémentations distinctes ou si la [compilation conditionnelle](https://en.wikipedia.org/wiki/Conditional_compilation) est utilisée. La réponse est les deux à la fois, avec une forte préférence pour la compilation conditionnelle.

Comme le montre le graphique ci-dessous, l’essentiel de [CoreFX](https://github.com/dotnet/corefx) consiste en du code indépendant de la plateforme qui est partagé entre toutes les plateformes. Le code indépendant de la plateforme peut être implémenté en tant qu’assembly portable unique et utilisé sur toutes les plateformes.

![CoreFX : lignes de code par plateforme](../images/corefx-platforms-loc.png)

Les implémentations Windows et Unix sont de taille équivalente. L’implémentation Windows est plus volumineuse, car CoreFX implémente des fonctionnalités propres à Windows, telles que [Microsoft.Win32.Registry](https://github.com/dotnet/corefx/tree/master/src/Microsoft.Win32.Registry), mais n’implémente pas encore de concepts propres à Unix. Vous pouvez aussi constater que la majorité des implémentations Linux et macOS sont partagées dans une implémentation Unix, alors que les implémentations spécifiques à Linux et macOS sont à peu près de taille équivalente.


.NET Core contient à la fois des bibliothèques spécifiques aux plateformes et des bibliothèques indépendantes des plateformes. Cette caractéristique peut être illustrée à travers les exemples suivants :

- [CoreCLR](https://github.com/dotnet/coreclr) est spécifique à la plateforme. Reposant sur C/C++, il est spécifique à la plateforme de par sa construction.
- [System.IO](https://github.com/dotnet/corefx/tree/master/src/System.IO) et [System.Security.Cryptography.Algorithms](https://github.com/dotnet/corefx/tree/master/src/System.Security.Cryptography.Algorithms) sont spécifiques à la plateforme, vu que les API de stockage et de chiffrement sont très différentes sur chaque système d’exploitation. 
- [System.Collections](https://github.com/dotnet/corefx/tree/master/src/System.Collections) et [System.Linq](https://github.com/dotnet/corefx/tree/master/src/System.Linq) sont indépendants de la plateforme, vu qu’ils créent et exploitent des structures de données.

## <a name="comparisons-to-other-net-platforms"></a>Comparaison avec les autres plateformes .NET

Il est peut-être plus facile d’appréhender la taille et la forme de .NET Core en le comparant aux plateformes .NET existantes. 

### <a name="comparison-with-net-framework"></a>Comparaison avec le .NET Framework

La plateforme .NET a été annoncée pour la première fois par Microsoft en 2000 et a depuis évolué. Le .NET Framework a été le premier produit .NET à avoir été conçu par Microsoft au cours de cette période de plus 15 ans. 

Les principales différences entre .NET Core et le .NET Framework sont les suivantes : 

- **Modèles d’application** : .NET Core ne prend pas en charge tous les modèles d’application .NET Framework, en partie parce que bon nombre d’entre eux reposent sur des technologies Windows, telles que WPF (reposant sur DirectX). Les modèles d’application console et ASP.NET Core sont pris en charge à la fois par .NET Core et par le .NET Framework. 
- **API** : .NET Core a beaucoup d’API en commun avec le .NET Framework, mais en moins grand nombre et avec une factorisation différente (les noms d’assembly sont différents ; la forme de type diffère dans les cas types). En général, ces différences exigent actuellement des modifications pour porter la source vers .NET Core. .NET Core implémente l’API de [bibliothèque .NET Standard](../standard/library.md), qui croîtra au fil du temps pour inclure un plus grand nombre d’API BCL du .NET Framework.
- **Sous-systèmes** : .NET Core implémente un sous-ensemble des sous-systèmes du .NET Framework, avec l’objectif d’une implémentation et d’un modèle de programmation plus simples. Par exemple, la sécurité d’accès du code (CAS) n’est pas pris en charge, alors que la réflexion l’est.
- **Plateformes** : le .NET Framework prend en charge Windows et Windows Server, tandis que .NET Core prend aussi en charge macOS et Linux.
- **Open Source** : .NET Core est open source, alors que seul un [sous-ensemble en lecture seule du .NET Framework](https://github.com/microsoft/referencesource) l’est.

Bien que .NET Core soit unique et présente des différences de taille par rapport au .NET Framework et aux autres plateformes .NET, il est simple de partager du code, que ce soit au moyen de techniques de partage de source ou de fichiers binaires. 

### <a name="comparison-with-mono"></a>Comparaison avec Mono

[Mono](http://www.mono-project.com/) est la première implémentation .NET multiplateforme et [open source](https://github.com/mono/mono) ; elle a vu le jour en 2004. Elle peut être considérée comme un clone communautaire du .NET Framework. L’équipe du projet Mono s’est appuyée sur les [normes .NET](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) libres (notamment ECMA 335) publiées par Microsoft pour proposer une implémentation compatible.

Les principales différences entre .NET Core et Mono sont les suivantes :

- **Modèles d’application** : Mono ne prend en charge qu’un sous-ensemble des modèles d’application du .NET Framework (par exemple, Windows Forms) et quelques autres (par exemple, [Xamarin.iOS](https://www.xamarin.com/platform)) via le produit Xamarin. .NET Core ne les prend pas en charge.
- **API** : Mono prend en charge un [sous-ensemble étendu](http://docs.go-mono.com/?link=root%3a%2fclasslib) des API du .NET Framework, en utilisant les mêmes noms d’assembly et la même factorisation.
- **Plateformes** : Mono prend en charge un grand nombre de plateformes et de processeurs.
- **Open Source** : Mono et .NET Core utilisent tous deux une licence MIT et sont des projets .NET Foundation.
- **Priorité** : les plateformes mobiles sont la principale priorité de Mono depuis quelques années, alors que .NET Core accorde la priorité aux charges de travail cloud.

