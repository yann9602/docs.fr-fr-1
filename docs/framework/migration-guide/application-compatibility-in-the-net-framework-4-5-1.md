---
title: "Compatibilité des applications dans le .NET Framework 4.5.1 | Microsoft Docs"
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
- application compatibility,.NET Framework 4.5.1
- application compatibility,.NET Framework
ms.assetid: 2b07b729-e2bf-4925-8b83-9c9ee6c48612
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9f90929c7181e5a615b9c7fb757c49367f40bc85
ms.lasthandoff: 04/18/2017

---
# <a name="application-compatibility-in-the-net-framework-451"></a>Compatibilité d'applications dans le .NET Framework 4.5.1
Cette rubrique fournit des liens vers des informations sur les problèmes de compatibilité des applications entre le .NET Framework 4.5 et 4.5.1. Les problèmes sont répartis en deux catégories :  
  
 [Modifications du runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)  
 Les modifications du runtime concernent toutes les applications qui s'exécutent sous le [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] et qui utilisent une fonctionnalité particulière.  
  
 [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-5-1.md)  
 Les modifications de reciblage concernent les applications qui sont recompilées pour cibler le [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]. Elles comprennent :  
  
-   Modifications de l'environnement au moment du design. Par exemple, les outils de génération peuvent émettre des avertissements, ce qu'ils ne faisaient pas auparavant.  
  
-   Modifications de l'environnement d'exécution. Ces modifications concernent uniquement les applications qui ciblent particulièrement le [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]. Les applications qui ciblent des versions antérieures du .NET Framework se comportent comme elles le faisaient dans ces versions.  
  
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
 [Compatibilité des applications dans la version 4.5.2](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)
