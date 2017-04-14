---
title: "Guide de migration vers .NET Framework&#160;4.6 et&#160;4.5  | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework, migrer des applications vers"
  - "migration, .NET Framework"
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
caps.latest.revision: 56
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
---
# Guide de migration vers .NET Framework&#160;4.6 et&#160;4.5 
Si vous avez créé votre application à l’aide d’une version antérieure du .NET Framework, vous pouvez généralement la mettre à niveau aisément vers .NET Framework 4.5, 4.5.1 ou 4.6. Ouvrez votre projet dans Visual Studio. Si votre projet a été créé dans une version antérieure, la boîte de dialogue **Compatibilité des projets** s'ouvre automatiquement. Pour plus d’informations sur la mise à niveau d’un projet dans Visual Studio 2013, consultez [Comment : mettre à niveau des projets créés dans des versions antérieures de Visual Studio](http://msdn.microsoft.com/library/vstudio/ms185327\(v=vs.100\).aspx) et [Portage, migration et mise à niveau des projets Visual Studio](../Topic/Porting,%20Migrating,%20and%20Upgrading%20Visual%20Studio%20Projects.md).  
  
 Toutefois, certaines modifications dans le .NET Framework nécessitent des modifications dans le code. Vous pouvez également bénéficier des nouvelles fonctionnalités de .NET Framework 4.5, de ses versions intermédiaires ou de .NET Framework 4.6. Le fait d'apporter ces types de modifications à votre application pour une nouvelle version du .NET Framework est généralement appelé *migration*. Si la migration de votre application n'est pas nécessaire, vous pouvez l'exécuter dans le .NET Framework 4.5 ou ses versions ultérieures sans la recompiler.  
  
## Ressources de migration  
 Consultez les documents suivants avant de migrer votre application à partir des versions antérieures du .NET Framework vers la version 4.5, 4.5.1 ou 4.5.2 :  
  
-   Consultez [Versions et dépendances](../../../docs/framework/migration-guide/versions-and-dependencies.md) pour comprendre la version CLR sous\-jacente à chaque version du .NET Framework et pour passer en revue les instructions qui vous permettront de cibler correctement vos applications.  
  
-   Passez en revue [Compatibilité des applications](../../../docs/framework/migration-guide/application-compatibility.md) pour découvrir les modifications d’exécution et de reciblage susceptibles d’affecter votre application, et la manière de les gérer.  
  
-   Passez en revue [Éléments obsolètes dans la bibliothèque de classes](../../../docs/framework/whats-new/whats-obsolete.md) pour déterminer les types ou membres rendus obsolètes dans votre code et les alternatives recommandées.  
  
-   Consultez [Nouveautés](../../../docs/framework/whats-new/index.md) pour obtenir la description des nouvelles fonctionnalités que vous pouvez ajouter à votre application.  
  
## Voir aussi  
 [Compatibilité des applications dans la version 4.5.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)   
 [Compatibilité des applications dans la version 4.5](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [Migration à partir du .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)   
 [Compatibilité des versions](../../../docs/framework/migration-guide/version-compatibility.md)   
 [Versions et dépendances](../../../docs/framework/migration-guide/versions-and-dependencies.md)   
 [Comment : configurer une application pour prendre en charge le .NET Framework 4 ou 4.5](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)   
 [Nouveautés](../../../docs/framework/whats-new/index.md)   
 [Éléments obsolètes dans la bibliothèque de classes](../../../docs/framework/whats-new/whats-obsolete.md)   
 [Version du .NET Framework et informations de l’assembly](http://go.microsoft.com/fwlink/?LinkId=201701)   
 [Politique de support pour Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=196607)