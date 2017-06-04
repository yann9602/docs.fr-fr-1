---
title: "dangerousThreadingAPI MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "suspending threads"
  - "DangerousThreadingAPI MDA"
  - "managed debugging assistants (MDAs), dangerous threading operations"
  - "threading [.NET Framework], suspending"
  - "MDAs (managed debugging assistants), dangerous threading operations"
  - "Suspend method"
  - "threading [.NET Framework], managed debugging assistants"
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# dangerousThreadingAPI MDA
L'Assistant Débogage managé \(MDA, Managed Debugging Assistant\) `dangerousThreadingAPI` est activé lorsque la méthode <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> est appelée sur un thread autre que le thread courant.  
  
## Symptômes  
 Une application ne répond pas ou se bloque indéfiniment.  Les données système ou d'application peuvent se retrouver dans un état imprévisible de façon temporaire ou même après l'arrêt d'une application.  Certaines opérations ne se terminent pas comme prévu.  
  
 Les symptômes peuvent varier considérablement en raison du caractère aléatoire du problème.  
  
## Cause  
 Un thread est suspendu de façon asynchrone par un autre thread à l'aide de la méthode <xref:System.Threading.Thread.Suspend%2A>.  Il n'est pas possible de déterminer le moment le plus sûr pour suspendre un autre thread pouvant se trouver en cours d'opération.  La suspension du thread peut entraîner l'altération des données ou des invariants.  Si un thread est suspendu et n'est jamais repris à l'aide de la méthode <xref:System.Threading.Thread.Resume%2A>, l'application peut se bloquer indéfiniment et même endommager les données d'application.  Ces méthodes ont été marquées comme obsolètes.  
  
 Si les primitives de synchronisation sont détenues par le thread cible, elles restent détenues pendant la suspension.  Cela peut entraîner des interblocages si un autre thread, par exemple le thread qui exécute <xref:System.Threading.Thread.Suspend%2A>, tente d'acquérir un verrou sur la primitive.  Dans ce cas, le problème se manifeste comme un interblocage.  
  
## Résolution  
 Évitez les designs qui requièrent l'utilisation de <xref:System.Threading.Thread.Suspend%2A> et <xref:System.Threading.Thread.Resume%2A>.  Pour la coopération entre les threads, utilisez des primitives de synchronisation telles que <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex> ou l'instruction `lock` du C\#.  Si vous devez utiliser ces méthodes, réduisez la durée et la quantité de code qui s'exécute pendant que le thread est suspendu.  
  
## Effet sur le runtime  
 Ce MDA n'a aucun effet sur le CLR.  Il signale uniquement des données relatives aux opérations de thread dangereuses.  
  
## Sortie  
 Le MDA identifie la méthode de thread dangereuse qui a entraîné son activation.  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## Exemple  
 L'exemple de code suivant illustre un appel à la méthode <xref:System.Threading.Thread.Suspend%2A> qui entraîne l'activation de `dangerousThreadingAPI`.  
  
```  
using System.Threading;  
void FireMda()  
{  
    Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Suspend();   
    t.Resume();  
    t.Join();  
}  
```  
  
## Voir aussi  
 <xref:System.Threading.Thread>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [lock, instruction](../Topic/lock%20Statement%20\(C%23%20Reference\).md)