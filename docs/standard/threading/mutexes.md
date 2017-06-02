---
title: "Mutexes | Microsoft Docs"
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
  - "wait handles"
  - "threading [.NET Framework], Mutex class"
  - "Mutex class, about Mutex class"
  - "threading [.NET Framework], cross-process synchronization"
ms.assetid: 9dd06e25-12c0-4a9e-855a-452dc83803e2
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Mutexes
Vous pouvez utiliser un objet <xref:System.Threading.Mutex> pour fournir l'accès exclusif à une ressource.  La classe <xref:System.Threading.Mutex> utilise plus de ressources de système que la classe <xref:System.Threading.Monitor>, mais elle peut être marshalée à travers des limites de domaine d'application, elle peut être utilisée avec les attentes multiples, et elle peut être utilisée pour synchroniser des threads dans des processus différents.  Pour une comparaison de mécanismes de synchronisation managés, consultez [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Pour des exemples de code, consultez la documentation de référence pour les constructeurs <xref:System.Threading.Mutex.%23ctor%2A>.  
  
## Utilisation de mutex  
 Un thread appelle la méthode <xref:System.Threading.WaitHandle.WaitOne%2A> d'un mutex pour demander la propriété.  L'appel est bloqué jusqu'à ce que le mutex soit disponible ou jusqu'à ce que l'intervalle de délai d'expiration facultatif s'écoule.  L'état d'un mutex est signalé si aucun thread ne le possède.  
  
 Un thread libère un mutex en appelant sa méthode <xref:System.Threading.Mutex.ReleaseMutex%2A>.  Les mutex ont l'affinité du thread ; c'est\-à\-dire que le mutex peut être libéré uniquement par le thread qui le possède.  Si un thread libère un mutex qu'il ne possède pas, une <xref:System.ApplicationException> est levée dans le thread.  
  
 Étant donné que la classe <xref:System.Threading.Mutex> dérive de <xref:System.Threading.WaitHandle>, vous pouvez également appeler les méthodes <xref:System.Threading.WaitHandle.WaitAll%2A> ou <xref:System.Threading.WaitHandle.WaitAny%2A> statiques de <xref:System.Threading.WaitHandle> pour demander la propriété d'un <xref:System.Threading.Mutex> dans la combinaison avec d'autres handles d'attente.  
  
 Si un thread possède un <xref:System.Threading.Mutex>, ce thread peut spécifier le même <xref:System.Threading.Mutex> des appels d'attente\-demande répétés sans bloquer son exécution ; il doit libérer le <xref:System.Threading.Mutex> autant de fois en libérer la propriété.  
  
## Mutex abandonnés  
 Si un thread se termine sans libérer de <xref:System.Threading.Mutex>, le mutex est dit abandonné.  Cela indique souvent une grave erreur de programmation car la ressource que le mutex protège peut être laissée dans un état incohérent.  Dans .NET Framework version 2.0, une <xref:System.Threading.AbandonedMutexException> est levée dans le thread suivant qui acquiert le mutex.  
  
> [!NOTE]
>  Dans .NET Framework versions 1.0 et 1.1, un <xref:System.Threading.Mutex> abandonné a pour valeur l'état signalé et le prochain thread en attente obtient la propriété.  Si aucun thread n'attend, le <xref:System.Threading.Mutex> reste dans un état signalé.  Aucune exception n'est levée.  
  
 Dans le cas d'un mutex à l'échelle du système, un mutex abandonné peut indiquer qu'une application s'est arrêtée soudainement \(par exemple, à l'aide du Gestionnaire des tâches de Windows\).  
  
## Mutex locaux et système  
 Les mutex sont de deux types : les mutex locaux et les mutex de systèmes nommés.  Si vous créez un objet <xref:System.Threading.Mutex> à l'aide d'un constructeur qui accepte un nom, il est associé à un objet de système d'exploitation portant ce nom.  Les mutex de système nommé sont visibles dans la totalité du système d'exploitation et peuvent être utilisés pour synchroniser les activités de processus.  Vous pouvez créer plusieurs objets <xref:System.Threading.Mutex> qui représentent le même mutex de système nommé ; vous pouvez également utiliser la méthode <xref:System.Threading.Mutex.OpenExisting%2A> pour ouvrir un mutex de système nommé existant.  
  
 Un mutex local existe uniquement dans le cadre du processus concerné.  Il peut être utilisé par tout thread du processus doté d'une référence à l'objet <xref:System.Threading.Mutex> local.  Chaque objet <xref:System.Threading.Mutex> constitue un mutex local séparé.  
  
### Accéder à la sécurité du contrôle pour les mutex de système  
 .NET Framework version 2.0 fournit la capacité de demander et définir la sécurité du contrôle d'accès Windows pour les objets de système nommé.  La protection de mutex de système du moment de création est recommandée parce que les objets système sont globaux et par conséquent peuvent être verrouillés par code autre que votre propre code.  
  
 Pour plus d'information sur la sécurité du contrôle d'accès pour mutex, consultez les classes <xref:System.Security.AccessControl.MutexSecurity> et <xref:System.Security.AccessControl.MutexAccessRule>, l'énumération <xref:System.Security.AccessControl.MutexRights>, les méthodes <xref:System.Threading.Mutex.GetAccessControl%2A>, <xref:System.Threading.Mutex.SetAccessControl%2A> et <xref:System.Threading.Mutex.OpenExisting%2A> de la classe <xref:System.Threading.Mutex> et le constructeur <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29>.  
  
## Voir aussi  
 <xref:System.Threading.Mutex>   
 <xref:System.Threading.Mutex.%23ctor%2A>   
 <xref:System.Security.AccessControl.MutexSecurity>   
 <xref:System.Security.AccessControl.MutexAccessRule>   
 [Threading](../../../docs/standard/threading/index.md)   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)   
 [Moniteurs](../Topic/Monitors.md)   
 [Threads and Threading](../../../docs/standard/threading/threads-and-threading.md)