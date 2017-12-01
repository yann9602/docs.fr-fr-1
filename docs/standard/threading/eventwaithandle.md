---
title: EventWaitHandle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], EventWaitHandle class
- EventWaitHandle class
- event wait handles [.NET Framework]
- threading [.NET Framework], cross-process synchronization
ms.assetid: 11ee0b38-d663-4617-b793-35eb6c64e9fc
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1bd248133bd95ff05246eb36a8e250247fd7ed61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="eventwaithandle"></a>EventWaitHandle
La <xref:System.Threading.EventWaitHandle> classe permet aux threads de communiquer entre eux en signalant et en attendant des signaux. Handles d’attente d’événement (également appelés événements) sont des handles d’attente qui peuvent être signalés afin de libérer un ou plusieurs threads en attente. Une fois qu’il est signalé, un handle d’attente d’événement est réinitialisé manuellement ou automatiquement. La <xref:System.Threading.EventWaitHandle> classe peut représenter soit un événement local handle d’attente (événement local) ou le handle (nommé événement ou système, visible pour tous les processus) d’attente d’un événement système nommé.  
  
> [!NOTE]
>  Handles d’attente d’événements ne sont pas des événements dans le sens habituellement donné à ce terme dans le .NET Framework. Aucun délégué ou les gestionnaires d’événements ne sont impliqués. Le terme « événement » est utilisé pour décrire les car elles ont généralement appelés en tant qu’événements du système d’exploitation, et le fait de signaler le handle d’attente indique aux threads en attente qu’un événement s’est produit.  
  
 Les handles d’attente d’événement locaux et nommés utilisent des objets de synchronisation de système, qui sont protégés par <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> wrappers pour vous assurer que les ressources sont libérées. Vous pouvez utiliser la <xref:System.Threading.WaitHandle.Dispose%2A> méthode pour libérer les ressources immédiatement lorsque vous avez terminé à l’aide de l’objet.  
  
## <a name="event-wait-handles-that-reset-automatically"></a>Handles d’attente d’événements qui réinitialisent automatiquement  
 Vous créez un événement de réinitialisation automatique en spécifiant <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> lorsque vous créez le <xref:System.Threading.EventWaitHandle> objet. Comme son nom l’indique, cet événement de synchronisation est réinitialisé automatiquement quand il est signalé, après avoir libéré un seul thread en attente. Signaler l’événement en appelant son <xref:System.Threading.EventWaitHandle.Set%2A> (méthode).  
  
 Événements de réinitialisation automatique sont généralement utilisées pour fournir un accès exclusif à une ressource pour un seul thread à la fois. Un thread demande la ressource en appelant le <xref:System.Threading.WaitHandle.WaitOne%2A> (méthode). Si aucun autre thread ne détient le handle d’attente, la méthode retourne `true` et le thread appelant possède le contrôle de la ressource.  
  
> [!IMPORTANT]
>  Comme avec tous les mécanismes de synchronisation, vous devez vous assurer que tous les chemins de code attend la fin sur le handle d’attente approprié avant d’accéder à une ressource protégée. Synchronisation de threads est coopérative.  
  
 Si un événement de réinitialisation automatique est signalé lorsque aucun thread n’attend, il reste signalé jusqu'à ce qu’un thread tente d’attendre. L’événement libère le thread et est immédiatement réinitialisé, bloquant les threads suivants.  
  
## <a name="event-wait-handles-that-reset-manually"></a>Handles d’attente d’événement réinitialiser manuellement  
 Vous créez un événement de réinitialisation manuelle en spécifiant <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> lorsque vous créez le <xref:System.Threading.EventWaitHandle> objet. Comme son nom l’indique, cet événement de synchronisation doit être réinitialisé manuellement après avoir été signalé. Jusqu'à ce qu’elle est réinitialisée, en appelant ses <xref:System.Threading.EventWaitHandle.Reset%2A> (méthode), les threads qui attendent que le handle d’événement procéder immédiatement sans blocage.  
  
 Événement des agit comme la barrière d’un corral de réinitialisation manuelle. Lorsque l’événement n’est pas signalé, bloquent les threads qui attendent sur celui-ci, comme les chevaux dans un corral. Lorsque l’événement est signalé, en appelant ses <xref:System.Threading.EventWaitHandle.Set%2A> (méthode), tous les threads en attente sont libres de continuer. L’événement reste signalé jusqu'à ce que son <xref:System.Threading.EventWaitHandle.Reset%2A> méthode est appelée. Cela rend une façon idéale de suspendre les threads qui doivent attendre jusqu'à ce qu’un thread termine une tâche à l’événement de réinitialisation manuelle.  
  
 Comme les chevaux qui quittent un corral, le temps requis pour les threads publiées pour être planifiée par le système d’exploitation et de reprendre l’exécution. Si le <xref:System.Threading.EventWaitHandle.Reset%2A> méthode est appelée avant l’exécution de tous les threads ont repris, les threads restants sont encore une fois bloquent. Le reprendre des threads et le threads se bloquent dépend de facteurs aléatoires tels que la charge sur le système, le nombre de threads en attente pour le planificateur et ainsi de suite. Cela n’est pas un problème si le thread qui signale l’événement se termine après avoir signalé, qui est le modèle d’utilisation courants. Si vous souhaitez que le thread qui a signalé l’événement pour commencer une nouvelle tâche une fois tous les threads ont repris en attente, vous devez le bloquer jusqu'à ce que tous les threads en attente ont repris. Sinon, vous avez une condition de concurrence et le comportement de votre code est imprévisible.  
  
## <a name="features-common-to-automatic-and-manual-events"></a>Fonctionnalités communes aux événements automatiques et manuels  
 En général, un ou plusieurs threads se bloquent sur un <xref:System.Threading.EventWaitHandle> jusqu'à ce qu’un thread débloqué appelle la <xref:System.Threading.EventWaitHandle.Set%2A> méthode, ce qui libère l’un des threads en attente (dans le cas des événements à réinitialisation automatique) ou tous les (manuel dans le cas d’événements de réinitialisation). Un thread peut signaler un <xref:System.Threading.EventWaitHandle> et bloquer ensuite sur celui-ci, comme une opération atomique, en appelant la méthode statique <xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=nameWithType> (méthode).  
  
 <xref:System.Threading.EventWaitHandle>objets peuvent être utilisés avec la méthode statique <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> et <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> méthodes. Étant donné que la <xref:System.Threading.EventWaitHandle> et <xref:System.Threading.Mutex> dérivent de classes <xref:System.Threading.WaitHandle>, vous pouvez utiliser les deux classes avec ces méthodes.  
  
### <a name="named-events"></a>Événements nommés  
 Le système d’exploitation Windows permet de handles d’attente d’événement d’avoir des noms. Un événement nommé est au niveau du système. Autrement dit, une fois l’événement nommé est créé, il est visible pour tous les threads de tous les processus. Par conséquent, les événements nommés peuvent être utilisés pour synchroniser les activités de processus, ainsi que des threads.  
  
 Vous pouvez créer un <xref:System.Threading.EventWaitHandle> objet qui représente un événement système nommé à l’aide d’un des constructeurs qui spécifient un nom d’événement.  
  
> [!NOTE]
>  Étant donné que les événements nommés sont à l’échelle du système, il est possible d’avoir plusieurs <xref:System.Threading.EventWaitHandle> objets qui représentent le même événement de nommé. Chaque fois que vous appelez un constructeur, ou le <xref:System.Threading.EventWaitHandle.OpenExisting%2A> (méthode), un nouveau <xref:System.Threading.EventWaitHandle> objet est créé. En spécifiant le même nom à plusieurs reprises crée plusieurs objets qui représentent le même événement nommé.  
  
 Avec prudence dans à l’aide de ces événements. Car elles sont au niveau du système, un autre processus qui utilise le même nom peut bloquer vos threads de manière inattendue. Du code malveillant exécuté sur le même ordinateur pourrait s'en servir pour une attaque par déni de service.  
  
 Utiliser la sécurité de contrôle d’accès pour protéger un <xref:System.Threading.EventWaitHandle> objet qui représente un événement nommé, de préférence à l’aide d’un constructeur qui spécifie un <xref:System.Security.AccessControl.EventWaitHandleSecurity> objet. Vous pouvez également appliquer la sécurité du contrôle d’accès à l’aide du <xref:System.Threading.EventWaitHandle.SetAccessControl%2A> (méthode), mais cela laisse une fenêtre de vulnérabilité entre l’heure de création du handle d’attente de l’événement et le moment où il est protégé. La protection des événements avec le contrôle d’accès sécurité empêche les attaques malveillantes, mais elle ne résout pas le problème des collisions de noms involontaires.  
  
> [!NOTE]
>  Contrairement à la <xref:System.Threading.EventWaitHandle> (classe), les classes dérivées <xref:System.Threading.AutoResetEvent> et <xref:System.Threading.ManualResetEvent> pouvez handles d’attente représentent uniquement locale. Ils ne peut pas représenter des événements système nommé.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
