---
title: "Guide de migration vers le .NET Framework 4.7, 4.6 et 4.5 "
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0c1f9ffd1df3861c2e9b000faccae381b04295dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="migration-guide-to-the-net-framework-47-46-and-45"></a>Guide de migration vers le .NET Framework 4.7, 4.6 et 4.5 
Si vous avez créé votre application à l’aide d’une version antérieure du .NET Framework, vous pouvez en général la mettre à niveau facilement vers .NET Framework 4.5 et ses versions intermédiaires (4.5.1 et 4.5.2), .NET Framework 4.6 et ses versions intermédiaires (4.6.1 et 4.6.2) ou .NET Framework 4.7 et sa version intermédiaire, .NET Framework 4.7.1. Ouvrez votre projet dans Visual Studio. Si votre projet a été créé dans une version antérieure de Visual Studio, la boîte de dialogue **Compatibilité des projets** s’ouvre automatiquement. Pour plus d’informations sur la mise à niveau d’un projet dans Visual Studio, consultez [Porter, migrer et mettre à niveau des projets Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) et [Ciblage et compatibilité de la plateforme Visual Studio 2017](https://www.visualstudio.com/en-us/productinfo/vs2017-compatibility-vs).  
  
 Toutefois, certaines modifications dans le .NET Framework nécessitent des modifications dans le code. Vous pouvez également bénéficier des nouvelles fonctionnalités de .NET Framework 4.5 et ses versions intermédiaires, de .NET Framework 4.6 et ses versions intermédiaires, ainsi que de .NET Framework 4.7 et sa version intermédiaire, .NET Framework 4.7.1. Le fait d’apporter ces types de modifications à votre application pour obtenir une nouvelle version du .NET Framework est généralement appelé *migration*. Si la migration de votre application n’est pas nécessaire, vous pouvez l’exécuter dans .NET Framework 4.5 ou une version ultérieure sans la recompiler.  
  
## <a name="migration-resources"></a>Ressources de migration  
 Consultez les documents suivants avant de migrer votre application à partir des versions antérieures du .NET Framework vers la version 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7 ou 4.7.1 :  
  
-   Consultez [Versions et dépendances](../../../docs/framework/migration-guide/versions-and-dependencies.md) pour comprendre la version CLR sous-jacente à chaque version du .NET Framework, et pour passer en revue les instructions qui vous permettront de cibler correctement vos applications.  
  
-   Consultez [Compatibilité des applications](../../../docs/framework/migration-guide/application-compatibility.md) pour découvrir les modifications d’exécution et de reciblage susceptibles d’affecter votre application, et savoir comment les gérer.  
  
-   Consultez [Éléments obsolètes dans la bibliothèque de classes](../../../docs/framework/whats-new/whats-obsolete.md) pour déterminer les types ou membres rendus obsolètes dans votre code, et les alternatives recommandées.  
  
-   Consultez [Nouveautés](../../../docs/framework/whats-new/index.md) pour obtenir la description des nouvelles fonctionnalités que vous pouvez ajouter à votre application.  
  
## <a name="see-also"></a>Voir aussi  
 [Compatibilité des applications](../../../docs/framework/migration-guide/application-compatibility.md)  
 [Migration à partir du .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)  
 [Compatibilité des versions](../../../docs/framework/migration-guide/version-compatibility.md)  
 [Versions et dépendances](../../../docs/framework/migration-guide/versions-and-dependencies.md)  
 [Guide pratique pour configurer une application en vue de prendre en charge le .NET Framework 4 ou 4.5](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)  
 [Nouveautés](../../../docs/framework/whats-new/index.md)  
 [Éléments obsolètes dans la bibliothèque de classes](../../../docs/framework/whats-new/whats-obsolete.md)  
 [Version du .NET Framework et informations de l’assembly](http://go.microsoft.com/fwlink/?LinkId=201701)  
 [Politique de support de Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=196607) [Problèmes de migration du .NET Framework 4](net-framework-4-migration-issues.md)
