---
title: "EventWaitHandle | Microsoft Docs"
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
  - "threading [.NET Framework], EventWaitHandle class"
  - "EventWaitHandle class"
  - "event wait handles [.NET Framework]"
  - "threading [.NET Framework], cross-process synchronization"
ms.assetid: 11ee0b38-d663-4617-b793-35eb6c64e9fc
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# EventWaitHandle
La classe <xref:System.Threading.EventWaitHandle> permet aux threads de communiquer les uns avec les autres par la signalisation et par l'attente de signaux.  Les handles d'attente d'événement \(également appelés événements\) sont des handles d'attente qui peuvent être signalés afin de libérer un ou plusieurs threads en attente.  Une fois signalé, un handle d'attente d'événement est réinitialisé manuellement ou automatiquement.  La classe <xref:System.Threading.EventWaitHandle> peut représenter un handle d'attente d'événement local \(événement local\) ou un handle d'attente d'événement système nommé \(événement ou événement système nommé, visible pour tous les processus\).  
  
> [!NOTE]
>  Les handles d'attente d'événement ne sont pas des événements au sens habituellement donné à ce terme dans le .NET Framework.  Aucun délégué ou gestionnaire d'événements n'est impliqué.  Le terme « événement » est utilisé pour les décrire car ils sont généralement appelés événements de système d'exploitation, et le fait de signaler le handle d'attente indique aux threads en attente qu'un événement s'est produit.  
  
 Les handles d'attente d'événement locaux et nommés utilisent des objets de synchronisation de système protégés par des wrappers <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> pour garantir que les ressources sont libérées.  Vous pouvez utiliser la méthode <xref:System.Threading.WaitHandle.System%23IDisposable%23Dispose%2A> pour libérer immédiatement les ressources lorsque vous avez terminé d'utiliser l'objet.  
  
## Handles d'attente d'événement réinitialisés automatiquement  
 Vous créez un événement de réinitialisation automatique en spécifiant <xref:System.Threading.EventResetMode?displayProperty=fullName> lorsque vous créez l'objet <xref:System.Threading.EventWaitHandle>.  Comme son nom l'indique, cet événement de synchronisation est réinitialisé automatiquement lorsqu'il est signalé, après la libération d'un seul thread en attente.  Signalez l'événement en appelant sa méthode <xref:System.Threading.EventWaitHandle.Set%2A>.  
  
 Les événements de réinitialisation automatique sont généralement utilisés afin de fournir un accès exclusif à une ressource pour un seul thread à la fois.  Un thread demande la ressource en appelant la méthode <xref:System.Threading.WaitHandle.WaitOne%2A>.  Si aucun autre thread ne maintient le handle d'attente, la méthode retourne `true` et le thread appelant contrôle la ressource.  
  
> [!IMPORTANT]
>  Comme pour tous les mécanismes de synchronisation, vous devez garantir que tous les chemins de code attendent sur le handle d'attente approprié avant d'accéder à une ressource protégée.  La synchronisation de threads est coopérative.  
  
 Si un événement de réinitialisation automatique est signalé alors qu'aucun thread n'est en attente, il reste signalé jusqu'à ce qu'un thread tente de l'attendre.  L'événement libère le thread et est immédiatement réinitialisé, bloquant les threads suivants.  
  
## Handles d'attente d'événement réinitialisés manuellement  
 Vous créez un événement de réinitialisation manuelle en spécifiant <xref:System.Threading.EventResetMode?displayProperty=fullName> lorsque vous créez l'objet <xref:System.Threading.EventWaitHandle>.  Comme son nom l'indique, cet événement de synchronisation doit être réinitialisé manuellement après avoir été signalé.  Jusqu'à sa réinitialisation, en appelant sa méthode <xref:System.Threading.EventWaitHandle.Reset%2A>, les threads qui attendent sur le handle d'événement poursuivent immédiatement l'exécution sans se bloquer.  
  
 Un événement de réinitialisation manuelle agit comme la barrière d'un corral.  Lorsque l'événement n'est pas signalé, les threads qui attendent sur celui\-ci restent bloqués, comme les chevaux dans un corral.  Lorsque l'événement est signalé, en appelant sa méthode <xref:System.Threading.EventWaitHandle.Set%2A>, tous les threads en attente sont libres de continuer.  L'événement reste signalé jusqu'à ce que sa méthode <xref:System.Threading.EventWaitHandle.Reset%2A> soit appelée.  Ainsi, l'événement de réinitialisation manuelle est la meilleure solution pour suspendre les threads qui doivent attendre qu'un thread termine une tâche.  
  
 Comme pour les chevaux qui quittent un corral, la planification, par le système d'exploitation, des threads libérés et la reprise de l'exécution prennent du temps.  Si la méthode <xref:System.Threading.EventWaitHandle.Reset%2A> est appelée avant que l'exécution de tous les threads ait repris, les threads restants sont encore une fois bloqués.  La nature des threads dont l'exécution reprend et de ceux qui sont bloqués dépend de facteurs aléatoires tels que la charge sur le système, le nombre de threads qui attendent le planificateur, etc.  Ce n'est pas un problème si le thread qui signale l'événement se termine après l'avoir signalé, ce qui correspond au modèle d'utilisation le plus courant.  Si vous souhaitez que le thread qui a signalé l'événement commence une nouvelle tâche lorsque tous les threads en attente ont repris, vous devez le bloquer jusqu'à ce que tous les threads en attente aient repris.  Sinon, il s'agit d'une condition de concurrence critique et le comportement de votre code est imprévisible.  
  
## Fonctionnalités communes aux événements automatiques et manuels  
 En général, un ou plusieurs threads se bloquent sur un <xref:System.Threading.EventWaitHandle> jusqu'à ce qu'un thread débloqué appelle la méthode <xref:System.Threading.EventWaitHandle.Set%2A>, qui libère l'un des threads en attente \(dans le cas d'événements de réinitialisation automatique\) ou la totalité de ceux\-ci \(dans le cas d'événements de réinitialisation manuelle\).  Un thread peut signaler un <xref:System.Threading.EventWaitHandle> puis se bloquer sur celui\-ci, comme une opération atomique, en appelant la méthode <xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=fullName> statique.  
  
 Les objets <xref:System.Threading.EventWaitHandle> peuvent être utilisés avec les méthodes <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=fullName> et <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=fullName> statiques.  Étant donné que les classes <xref:System.Threading.EventWaitHandle> et <xref:System.Threading.Mutex> dérivent de <xref:System.Threading.WaitHandle>, vous pouvez utiliser ces deux classes avec ces méthodes.  
  
### Événements nommés  
 Le système d'exploitation Windows permet aux handles d'attente d'événement d'avoir des noms.  Un événement nommé est à l'échelle du système.  Cela signifie qu'une fois que l'événement nommé est créé, il est visible pour tous les threads de tous les processus.  Par conséquent, les événements nommés peuvent être utilisés pour synchroniser les activités des processus ainsi que des threads.  
  
 Vous pouvez créer un objet <xref:System.Threading.EventWaitHandle> qui représente un événement système nommé en utilisant l'un des constructeurs spécifiant un nom d'évènement.  
  
> [!NOTE]
>  Étant donné que les événements nommés sont à l'échelle du système, il est possible que plusieurs objets <xref:System.Threading.EventWaitHandle> représentent le même événement nommé.  Chaque fois que vous appelez un constructeur ou la méthode <xref:System.Threading.EventWaitHandle.OpenExisting%2A>, un objet <xref:System.Threading.EventWaitHandle> est créé.  La spécification du même nom à plusieurs reprises crée différents objets qui représentent le même événement nommé.  
  
 Il est conseillé d'être prudent lors de l'utilisation d'événements nommés.  Étant donné qu'ils sont à l'échelle du système, un autre processus utilisant le même nom peut bloquer vos threads de manière inattendue.  Un code nuisible en exécution sur le même ordinateur pourrait l'utiliser comme base d'une attaque par déni de service.  
  
 Utilisez la sécurité du contrôle d'accès pour protéger un objet <xref:System.Threading.EventWaitHandle> qui représente un événement nommé, en utilisant de préférence un constructeur qui spécifie un objet <xref:System.Security.AccessControl.EventWaitHandleSecurity>.  Vous pouvez également appliquer la sécurité du contrôle d'accès à l'aide de la méthode <xref:System.Threading.EventWaitHandle.SetAccessControl%2A>, mais la période entre la création du handle d'attente d'événement et le moment où il est protégé présente des risques.  La protection des événements à l'aide de la sécurité du contrôle d'accès empêche les attaques malveillantes mais ne résout pas le problème des collisions de nom involontaires.  
  
> [!NOTE]
>  Contrairement à la classe <xref:System.Threading.EventWaitHandle>, les classes dérivées <xref:System.Threading.AutoResetEvent> et <xref:System.Threading.ManualResetEvent> ne peuvent représenter que des handles d'attente locaux.  Elles ne peuvent pas représenter des événements système nommés.  
  
## Voir aussi  
 <xref:System.Threading.EventWaitHandle>   
 <xref:System.Threading.WaitHandle>   
 <xref:System.Threading.AutoResetEvent>   
 <xref:System.Threading.ManualResetEvent>   
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)