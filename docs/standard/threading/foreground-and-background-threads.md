---
title: "Foreground and Background Threads | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "threading [.NET Framework], foreground"
  - "threading [.NET Framework], background"
  - "foreground threads"
  - "background threads"
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Foreground and Background Threads
Un thread managé peut se trouver soit à l'arrière\-plan, soit au premier plan.  Les threads d'arrière\-plan sont identiques aux threads de premier plan avec une exception : un thread d'arrière\-plan ne gardera pas l'environnement d'exécution managé actif.  Une fois que tous les threads de premier plan ont été arrêtés dans un processus managé \(où le fichier .exe est un assembly managé\), le système arrête tous les threads d'arrière\-plan et s'arrête.  
  
> [!NOTE]
>  Lorsque le runtime arrête un thread d'arrière\-plan parce que le processus s'arrête, aucune exception n'est levée dans le thread.  Toutefois, lorsque les threads sont arrêtés parce que la méthode <xref:System.AppDomain.Unload%2A?displayProperty=fullName> décharge le domaine d'application, une <xref:System.Threading.ThreadAbortException> est levée dans les threads de premier plan et d'arrière\-plan.  
  
 Utilisez la propriété <xref:System.Threading.Thread.IsBackground%2A?displayProperty=fullName> pour déterminer si un thread est un thread d'arrière\-plan ou de premier plan, ou pour modifier son état.  Un thread peut être à tout moment changé en thread d'arrière\-plan si sa propriété <xref:System.Threading.Thread.IsBackground%2A> a la valeur `true`.  
  
> [!IMPORTANT]
>  L'état de premier plan ou d'arrière\-plan d'un thread n'affecte pas le résultat d'une exception non gérée dans le thread.  Dans le .NET Framework version 2.0, une exception non gérée dans des threads de premier plan ou d'arrière\-plan entraîne la fin de l'application.  Consultez [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
 Les threads qui appartiennent au pool de threads managé \(c'est\-à\-dire les threads dont la propriété <xref:System.Threading.Thread.IsThreadPoolThread%2A> est `true`\) sont des threads d'arrière\-plan.  Tous les threads qui entrent dans l'environnement d'exécution managé à partir du code non managé sont marqués comme threads d'arrière\-plan.  Tous les threads générés en créant et en démarrant un nouvel objet <xref:System.Threading.Thread> sont par défaut des threads de premier plan.  
  
 Si vous utilisez un thread pour contrôler une activité, telle qu'une connexion de socket, affectez `true` à sa propriété <xref:System.Threading.Thread.IsBackground%2A> afin que le thread n'empêche pas votre processus de s'arrêter.  
  
## Voir aussi  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=fullName>   
 <xref:System.Threading.Thread>   
 <xref:System.Threading.ThreadAbortException>