---
title: "&#201;tats des threads manag&#233;s | Microsoft Docs"
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
  - "threads (.NET Framework), états"
ms.assetid: 63890d5e-6025-4a7c-aaf0-d8bfd54b455f
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# &#201;tats des threads manag&#233;s
La propriété <xref:System.Threading.Thread.ThreadState%2A?displayProperty=fullName> fournit un masque de bits qui indique l’état actuel du thread. Un thread se trouve toujours dans au moins un des états possibles de l’énumération <xref:System.Threading.ThreadState> et peut être dans plusieurs états en même temps.  
  
> [!IMPORTANT]
>  L’état des threads n’est utile que dans quelques scénarios de débogage. Votre code ne doit jamais utiliser l’état des threads pour synchroniser les activités des threads.  
  
 Quand vous créez un thread managé, il est dans l’état <xref:System.Threading.ThreadState>. Le thread reste dans l’état <xref:System.Threading.ThreadState> jusqu’à ce qu’il soit placé dans l’état Démarré par le système d’exploitation. L’appel à <xref:System.Threading.Thread.Start%2A> informe le système d’exploitation que le thread peut être démarré ; il ne change pas l’état du thread.  
  
 Les threads non managés qui entrent l’environnement managé sont déjà dans l’état Démarré. Une fois qu’un thread est dans l’état Démarré, plusieurs actions peut le faire changer d’état. Le tableau suivant répertorie les actions qui provoquent un changement d’état, ainsi que le nouvel état correspondant.  
  
|Action|Nouvel état résultant|  
|------------|---------------------------|  
|Le constructeur de la classe <xref:System.Threading.Thread>est appelé.|<xref:System.Threading.ThreadState>|  
|Un autre thread appelle <xref:System.Threading.Thread.Start%2A?displayProperty=fullName>.|<xref:System.Threading.ThreadState>|  
|Le thread répond à <xref:System.Threading.Thread.Start%2A?displayProperty=fullName> et démarre l’exécution.|<xref:System.Threading.ThreadState>|  
|Le thread appelle <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>.|<xref:System.Threading.ThreadState>|  
|Le thread appelle <xref:System.Threading.Monitor.Wait%2A?displayProperty=fullName> sur un autre objet.|<xref:System.Threading.ThreadState>|  
|Le thread appelle <xref:System.Threading.Thread.Join%2A?displayProperty=fullName> sur un autre thread.|<xref:System.Threading.ThreadState>|  
|Un autre thread appelle <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>.|<xref:System.Threading.ThreadState>|  
|Le thread répond à une demande <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>.|<xref:System.Threading.ThreadState>|  
|Un autre thread appelle <xref:System.Threading.Thread.Resume%2A?displayProperty=fullName>.|<xref:System.Threading.ThreadState>|  
|Un autre thread appelle <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>.|<xref:System.Threading.ThreadState>|  
|Le thread répond à un <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>.|<xref:System.Threading.ThreadState>, puis <xref:System.Threading.ThreadState>|  
  
 Étant donné que l’état de <xref:System.Threading.ThreadState> a la valeur 0, il n’est pas possible d’effectuer un test de bits pour découvrir cet état. Au lieu de cela, le test suivant \(en pseudo\-code\) peut être utilisé :  
  
```  
if ((state & (Unstarted | Stopped)) == 0)   // implies Running     
```  
  
 Les threads se trouvent souvent dans plusieurs états à un moment donné. Par exemple, si un thread est bloqué sur un appel de <xref:System.Threading.Monitor.Wait%2A?displayProperty=fullName> appel et qu’un autre thread appelle <xref:System.Threading.Thread.Abort%2A> sur ce même thread, le thread sera à la fois dans l’état <xref:System.Threading.ThreadState> et dans l’état <xref:System.Threading.ThreadState> en même temps. Dans ce cas, dès que le thread retourne de l’appel à <xref:System.Threading.Monitor.Wait%2A> ou est interrompu, il reçoit <xref:System.Threading.ThreadAbortException>.  
  
 Une fois qu’un thread quitte l’état <xref:System.Threading.ThreadState> à la suite d’un appel à <xref:System.Threading.Thread.Start%2A>, il ne peut jamais revenir à l’état <xref:System.Threading.ThreadState>. Un thread ne peut jamais quitter l’état <xref:System.Threading.ThreadState>.  
  
## Voir aussi  
 <xref:System.Threading.ThreadAbortException>   
 <xref:System.Threading.Thread>   
 <xref:System.Threading.ThreadState>   
 [Threading](../../../docs/standard/threading/index.md)