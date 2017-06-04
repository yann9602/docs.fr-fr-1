---
title: "Compatibilit&#233; d&#39;applications dans le .NET Framework&#160;4.5.2 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c6a029d-c565-4f25-b87b-b2361634bd74
caps.latest.revision: 5
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 5
---
# Compatibilit&#233; d&#39;applications dans le .NET Framework&#160;4.5.2
Cette rubrique fournit des liens vers des informations sur les problèmes de compatibilité des applications entre le .NET Framework 4.5.1 et 4.5.2.  Les problèmes sont répartis en deux catégories :  
  
 [Modifications du runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-2.md)  
 Les modifications du runtime concernent toutes les applications qui s'exécutent sous le .NET Framework 4.5.2 et qui utilisent une fonctionnalité particulière.  
  
 [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-5-2.md)  
 Les modifications de reciblage concernent les applications qui sont recompilées pour cibler le .NET Framework 4.5, 4.5.1 ou 4.5.2.  Elles comprennent :  
  
-   Modifications de l'environnement au moment du design.  Par exemple, les outils de génération peuvent émettre des avertissements, ce qu'ils ne faisaient pas auparavant.  
  
-   Modifications de l'environnement d'exécution.  Ces modifications concernent uniquement les applications qui ciblent particulièrement le .NET Framework 4.5.2.  Les applications qui ciblent des versions antérieures du .NET Framework se comportent comme elles le faisaient dans ces versions.  
  
 Dans les rubriques qui décrivent les modifications du runtime et les modifications de reciblage, nous avons classé les éléments individuels en fonction de leur impact, comme suit :  
  
 Majeur  
 Il s'agit d'une modification importante qui affecte un grand nombre d'applications ou qui nécessite de modifier significativement le code.  
  
 Mineur  
 Il s'agit d'une modification qui affecte un petit nombre d'applications ou qui nécessite peu de modifications du code.  
  
 Cas limite  
 Il s'agit d'une modification qui affecte des applications dans des scénarios très spécifiques qui ne sont pas courants.  
  
 Transparent  
 Il s'agit d'une modification qui n'a pas d'effet visible pour le développeur ou l'utilisateur de l'application.  L'application n'a pas besoin d'être modifiée en raison de cette modification.  
  
## Voir aussi  
 [Versions et dépendances](../../../docs/framework/migration-guide/versions-and-dependencies.md)   
 [Compatibilité des applications](../../../docs/framework/migration-guide/application-compatibility.md)   
 [Compatibilité des applications dans la version 4.5](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [Compatibilité des applications dans la version 4.5.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)