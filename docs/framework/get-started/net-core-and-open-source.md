---
title: .NET Core et Open-Source
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
caps.latest.revision: 8
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 3155295489e1188640dae5aa5bf9fdceb7480ed6
ms.openlocfilehash: db4689ee58b48fad2e3696e5e64aa187710f4868
ms.contentlocale: fr-fr
ms.lasthandoff: 08/05/2017

---
# <a name="net-core-and-open-source"></a>.NET Core et Open-Source
Cette rubrique fournit une vue d’ensemble de .NET Core et vous montre comment trouver plus d’informations. Pour connaître la liste complète des rubriques de .NET Core, consultez le [Guide .NET Core](../../core/index.md).
  
<a name="BKMK_WhatisNETCore"></a>   
## <a name="what-is-net-core"></a>Qu'est-ce que le .NET Core ?  
 Le .NET Core est une implémentation multiplateforme, modulaire et open source à but général de .NET Standard. Il dispose en grande partie des mêmes API que le .NET Framework (mais .NET Core est un ensemble plus petit) et comprend le runtime, le framework, le compilateur et les outils qui prennent en charge une variété de systèmes d’exploitation et de cibles de processeurs. L’implémentation .NET Core a été essentiellement motivée par les charges de travail ASP.NET Core, mais aussi par la nécessité et l’envie d’avoir une implémentation plus moderne. Elle peut être utilisée aussi bien dans le cloud que sur des appareils et des systèmes embarqués/IoT.  
  
 Pour commencer avec le .NET Core, visitez la [page d’accueil de .NET Core](https://www.microsoft.com/net/core).  
  
 Les principales caractéristiques de .NET Core sont les suivantes :  
  
-   **Multiplateforme.** .NET Core fournit des fonctionnalités clés permettant d’implémenter les composants d’application dont vous avez besoin et de réutiliser le code, quelle que soit votre plateforme cible. Il prend actuellement en charge les trois principaux systèmes d’exploitation : Windows, Linux et Mac OS. Vous pouvez écrire des applications et des bibliothèques qui s’exécutent telles quelles sur les systèmes d’exploitation pris en charge. Pour afficher la liste des systèmes d’exploitation pris en charge, consultez la [feuille de route .NET Core](https://github.com/dotnet/core/blob/master/roadmap.md).
  
-   **Open source.** .NET Core est l’un des nombreux projets placés sous l’intendance de [.NET Foundation](http://www.dotnetfoundation.org/) et disponible sur [GitHub](https://github.com/).  .NET Core, en tant que projet open source, encourage un processus de développement plus transparent et soutient une communauté active et engagée.  
  
-   **Déploiement flexible.** Il existe deux méthodes principales pour déployer votre application : le déploiement dépendant du framework ou le déploiement autonome. Avec le déploiement dépendant du framework, seules vos dépendances d’application et tierces sont installées. Votre application dépend de la présence d’une version de .NET Core à l’échelle du système.  Avec le déploiement autonome, la version de .NET Core utilisée pour générer votre application est également déployée avec les dépendances d’application et tierces, et peut s’exécuter côte à côte avec d’autres versions.    Pour plus d’informations, consultez [Déploiement d’applications .NET Core](../../core/deploying/index.md).

-   **Modulaire :** .NET Core est modulaire, car il est publié via NuGet dans des packages d’assembly plus petits. Au lieu d’un assembly volumineux contenant la plupart des fonctionnalités principales, le .NET Core est disponible sous forme de petits packages axés sur les fonctionnalités. Cela nous permet d’avoir un modèle de développement plus agile et vous permet d’optimiser votre application en choisissant seulement les packages NuGet dont vous avez besoin. Les avantages d’une petite zone de surface d’application offrent une sécurité accrue, une maintenance réduite, des performances améliorées et une réduction des coûts dans un modèle de paiement basé uniquement sur votre utilisation.  
  
## <a name="the-net-core-platform"></a>La plateforme .NET Core  
 La plateforme .NET Core est constituée de plusieurs composants, dont les compilateurs managés, le runtime, les bibliothèques de classes de base et de nombreux modèles d’application comme ASP.NET Core. Vous pouvez en savoir plus sur les différents composants et approfondir en consultant les dépôts [GitHub](https://github.com/) suivants :  
  
-   [.NET Core](https://github.com/dotnet/core)  
  
-   [CoreFX – Les bibliothèques fondamentales de .NET Core](https://github.com/dotnet/corefx)  
  
-   [CoreCLR – Le runtime .NET Core](https://github.com/dotnet/coreclr)  
  
-   [CLI – Les outils en ligne de commande de .NET Core](https://github.com/dotnet/cli)  
  
-   [Roslyn – .NET Compiler Platform](https://github.com/dotnet/roslyn)  
  
-   [ASP.NET Core](https://github.com/aspnet/home)  
  
## <a name="see-also"></a>Voir aussi  
 [Page d’accueil de .NET Core](https://www.microsoft.com/net/core)   
 [Guide .NET Core](../../core/index.md)   
 [Documentation ASP.NET Core](/aspnet/core/)

