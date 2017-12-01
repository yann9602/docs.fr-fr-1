---
title: "Threads de premier plan et d'arrière-plan"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42ad427fc2c1175c0d9b333aa418aea039f11a35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="foreground-and-background-threads"></a>Threads de premier plan et d'arrière-plan
Un thread managé est un thread d’arrière-plan ou un thread de premier plan. Threads d’arrière-plan sont identiques aux threads de premier plan à une exception près : un thread d’arrière-plan ne conserve pas l’environnement d’exécution managé en cours d’exécution. Une fois que tous les threads de premier plan ont été arrêtés dans un processus managé (où le fichier .exe est un assembly managé), le système arrête tous les threads d’arrière-plan et s’arrête.  
  
> [!NOTE]
>  Lorsque le runtime interrompt un thread d’arrière-plan, car le processus est en cours d’arrêt, aucune exception n’est levée dans le thread. Toutefois, lorsque les threads sont arrêtés, car le <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> méthode décharge le domaine d’application, un <xref:System.Threading.ThreadAbortException> est levée dans les threads de premier plan et arrière-plan.  
  
 Utilisez le <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> propriété pour déterminer si un thread est un thread d’arrière-plan ou au premier plan, ou pour modifier son état. Un thread peut être modifié à un thread d’arrière-plan à tout moment en définissant son <xref:System.Threading.Thread.IsBackground%2A> propriété `true`.  
  
> [!IMPORTANT]
>  L’état de premier plan ou d’arrière-plan d’un thread n’affecte pas le résultat d’une exception non gérée dans le thread. Dans le .NET Framework version 2.0, une exception non gérée dans les threads de premier plan ou d’arrière-plan entraîne l’arrêt de l’application. Consultez [Exceptions dans les Threads managés](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
 Les threads qui appartiennent au pool de threads managé (autrement dit, les threads dont <xref:System.Threading.Thread.IsThreadPoolThread%2A> propriété `true`) sont des threads d’arrière-plan. Tous les threads qui entrent dans l’environnement d’exécution managé à partir de code non managé sont marqués comme threads d’arrière-plan. Tous les threads générés en créant et en démarrant un nouvel <xref:System.Threading.Thread> objet sont par défaut des threads de premier plan.  
  
 Si vous utilisez un thread pour contrôler une activité, telle qu’une connexion de socket, définissez son <xref:System.Threading.Thread.IsBackground%2A> propriété `true` afin que le thread n’empêche pas votre processus de s’arrêter.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadAbortException>
