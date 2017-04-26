---
title: "Compatibilité des applications dans le .NET Framework 4.6 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility, .NET Framework
- application compatibility. NET Framework 4.6
ms.assetid: 7a3fd352-a8ba-4f9a-8250-951f2c994248
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 32bbbf7cb9acd71f5b8e28b7b12aab706221fab9
ms.lasthandoff: 04/18/2017

---
# <a name="application-compatibility-in-the-net-framework-46"></a>Compatibilité d'applications dans le .NET Framework 4.6
Cette rubrique fournit des liens vers des informations sur les problèmes de compatibilité des applications entre le .NET Framework 4.5.2 et 4.6. Les problèmes sont répartis en deux catégories :  
  
 [Modifications du runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)  
 Les modifications du runtime concernent toutes les applications qui s'exécutent sous le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] et qui utilisent une fonctionnalité particulière.  
  
 [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)  
 Les modifications de reciblage concernent les applications qui sont recompilées pour cibler le .NET Framework 4.5, 4.5.1, 4.5.2, ou 4.6. Elles comprennent :  
  
-   Modifications de l'environnement au moment du design. Par exemple, les outils de génération peuvent émettre des avertissements, ce qu'ils ne faisaient pas auparavant.  
  
-   Modifications de l'environnement d'exécution. Ces modifications concernent uniquement les applications qui ciblent particulièrement le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Les applications qui ciblent des versions antérieures du .NET Framework se comportent comme elles le faisaient dans ces versions.  
  
 Dans les rubriques qui décrivent les modifications du runtime et les modifications de reciblage, nous avons classé les éléments individuels en fonction de leur impact, comme suit :  
  
 Majeur  
 Il s'agit d'une modification importante qui affecte un grand nombre d'applications ou qui nécessite de modifier significativement le code.  
  
 Mineur  
 Il s'agit d'une modification qui affecte un petit nombre d'applications ou qui nécessite peu de modifications du code.  
  
 Cas limite  
 Il s'agit d'une modification qui affecte des applications dans des scénarios très spécifiques qui ne sont pas courants.  
  
 Transparent  
 Il s'agit d'une modification qui n'a pas d'effet visible pour le développeur ou l'utilisateur de l'application. L'application n'a pas besoin d'être modifiée en raison de cette modification.  
  
## <a name="see-also"></a>Voir aussi  
 [Versions et dépendances](../../../docs/framework/migration-guide/versions-and-dependencies.md)   
 [Compatibilité des applications](../../../docs/framework/migration-guide/application-compatibility.md)   
 [Compatibilité des applications dans la version 4.5](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [Compatibilité des applications dans la version 4.5.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)   
 [Compatibilité des applications dans la version 4.5.2](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)
