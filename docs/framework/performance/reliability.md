---
title: "Reliability | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL Server [.NET Framework]"
  - "managed code, reliability"
  - "reliability [.NET Framework]"
  - "writing reliable code"
  - "code, reliability"
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# Reliability
Il est important que le code exécuté dans des environnements serveur tels que SQL Server assure une protection contre des exceptions asynchrones.  La fiabilité, telle qu'elle est présentée ici, ne concerne pas tant SQL Server que l'écriture de code fiable pour tout hôte qui s'exécute dans un environnement du .NET Framework version 2.0.  Toutefois, SQL Server étant le premier service qui recourt largement aux nouvelles fonctionnalités de fiabilité de la version 2.0, il est utilisé comme exemple.  
  
 Le code qui s'exécute dans SQL Server doit respecter des exigences de fiabilité plus strictes que d'autres environnements serveur.  Cela est dû à l'opération régulière de SQL Server vers le bord de la consommation de ressources.  <xref:System.OutOfMemoryException> et les exceptions <xref:System.Threading.ThreadAbortException> ne sont pas rares dans l'environnement de SQL Server.  En général, il s'agit moins d'avoir du code fiable que de permettre à du code managé de confiance totale d'échouer correctement en présence du recyclage de niveau <xref:System.AppDomain>, lequel représente le principal moyen pour le serveur de conserver la cohérence et la disponibilité des données.  
  
## Dans cette section  
 [SQL Server Programming and Host Protection Attributes](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)  
 Décrit comment l'attribut <xref:System.Security.Permissions.HostProtectionAttribute> est utilisé par SQL Server pour appliquer des restrictions à l'exécution de code managé.  
  
 [Reliability Best Practices](../../../docs/framework/performance/reliability-best-practices.md)  
 Fournit des indications pour écrire du code qui réponde aux exigences de fiabilité.  
  
 [Constrained Execution Regions](../../../docs/framework/performance/constrained-execution-regions.md)  
 Décrit la fonction et le comportement de régions d'exécution limitée.  
  
## Référence  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>