---
title: Mutex
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wait handles
- threading [.NET Framework], Mutex class
- Mutex class, about Mutex class
- threading [.NET Framework], cross-process synchronization
ms.assetid: 9dd06e25-12c0-4a9e-855a-452dc83803e2
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a1d69c1b943d15b9ad8c80b4d7dbafebc54990ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mutexes"></a>Mutex
Vous pouvez utiliser un <xref:System.Threading.Mutex> objet pour fournir un accès exclusif à une ressource. Le <xref:System.Threading.Mutex> classe utilise davantage de ressources système que le <xref:System.Threading.Monitor> classe, mais il peut être marshalés entre des limites de domaine d’application, il peut être utilisé avec les attentes multiples, et il peut être utilisé pour synchroniser des threads dans des processus différents. Pour consulter une comparaison des mécanismes de synchronisation gérés, consultez [Vue d’ensemble des primitives de synchronisation](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Pour des exemples de code, consultez la documentation de référence pour le <xref:System.Threading.Mutex.%23ctor%2A> constructeurs.  
  
## <a name="using-mutexes"></a>Utilisation de mutex  
 Un thread appelle la <xref:System.Threading.WaitHandle.WaitOne%2A> méthode d’un mutex pour demander la propriété. L’appel est bloqué jusqu'à ce que le mutex soit disponible, ou jusqu'à ce que le délai d’expiration facultatif s’écoule. L’état d’un mutex est signalé si aucun thread ne le possède.  
  
 Un thread libère un mutex en appelant son <xref:System.Threading.Mutex.ReleaseMutex%2A> (méthode). Les mutex ont une affinité de thread. Cela signifie que le mutex ne peut être libéré que par le thread qui le possède. Si un thread libère un mutex qu’il ne possède pas le cas, un <xref:System.ApplicationException> est levée dans le thread.  
  
 Car le <xref:System.Threading.Mutex> dérive de la classe <xref:System.Threading.WaitHandle>, vous pouvez également appeler la méthode statique <xref:System.Threading.WaitHandle.WaitAll%2A> ou <xref:System.Threading.WaitHandle.WaitAny%2A> méthodes de <xref:System.Threading.WaitHandle> à demander la propriété d’un <xref:System.Threading.Mutex> en combinaison avec d’autres handles d’attente.  
  
 Si un thread possède un <xref:System.Threading.Mutex>, ce thread peut spécifier le même <xref:System.Threading.Mutex> dans les appels d’attente-demande répétés sans bloquer son exécution ; Toutefois, il doit libérer le <xref:System.Threading.Mutex> autant de fois pour libérer de la propriété.  
  
## <a name="abandoned-mutexes"></a>Mutex abandonnés  
 Si un thread se termine sans libérer un <xref:System.Threading.Mutex>, le mutex est dit abandonné. Cela indique souvent une grave erreur de programmation, car la ressource que le mutex protège peut être laissée dans un état incohérent. Dans le .NET Framework version 2.0, un <xref:System.Threading.AbandonedMutexException> est levée dans le thread suivant qui acquiert le mutex.  
  
> [!NOTE]
>  Dans les versions de .NET Framework 1.0 et 1.1, un abandonné <xref:System.Threading.Mutex> est défini sur l’état signalé et la prochaine en attente obtient la propriété thread. Si aucun thread n’est en attente, le <xref:System.Threading.Mutex> reste dans un état signalé. Aucune exception n'est levée.  
  
 Si le mutex est développé au niveau système, et qu’il est abandonné, cela peut indiquer qu’une application a été arrêtée soudainement (par exemple, à l’aide du Gestionnaire des tâches de Windows).  
  
## <a name="local-and-system-mutexes"></a>Mutex système et locaux  
 Il existe deux types de mutex : les mutex locaux et les mutex système nommés. Si vous créez un <xref:System.Threading.Mutex> de l’objet à l’aide d’un constructeur qui accepte un nom, il est associé à un objet de système d’exploitation de ce nom. Les mutex système nommés sont visibles partout dans le système d’exploitation, et peuvent être utilisés pour synchroniser les activités de processus. Vous pouvez créer plusieurs <xref:System.Threading.Mutex> les objets qui représentent le même les mutex système nommé, et vous pouvez utiliser la <xref:System.Threading.Mutex.OpenExisting%2A> mutex système nommé de méthode pour ouvrir un existant.  
  
 Un mutex local existe uniquement dans votre processus. Il peut être utilisé par n’importe quel thread de votre processus qui a une référence à la variable locale <xref:System.Threading.Mutex> objet. Chaque <xref:System.Threading.Mutex> objet est un mutex local séparé.  
  
### <a name="access-control-security-for-system-mutexes"></a>Sécurité du contrôle d'accès pour les mutex système  
 La version 2.0 de .NET Framework permet de demander et de définir la sécurité de contrôle d’accès Windows pour les objets système nommé. Il est recommandé de protéger les mutex système dès leur création, car les objets système sont globaux et peuvent donc être verrouillés par un code autre que le vôtre.  
  
 Pour plus d’informations sur la sécurité de contrôle d’accès pour les mutex, consultez le <xref:System.Security.AccessControl.MutexSecurity> et <xref:System.Security.AccessControl.MutexAccessRule> classes, les <xref:System.Security.AccessControl.MutexRights> énumération, le <xref:System.Threading.Mutex.GetAccessControl%2A>, <xref:System.Threading.Mutex.SetAccessControl%2A>, et <xref:System.Threading.Mutex.OpenExisting%2A> méthodes de la <xref:System.Threading.Mutex> classe et le <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> constructeur.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.Mutex.%23ctor%2A>  
 <xref:System.Security.AccessControl.MutexSecurity>  
 <xref:System.Security.AccessControl.MutexAccessRule>  
 [Thread](../../../docs/standard/threading/index.md)  
 [Fonctionnalités et objets de threading](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Moniteurs](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 [Threads et threading](../../../docs/standard/threading/threads-and-threading.md)
