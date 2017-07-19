---
title: "Destroying Threads | Microsoft Docs"
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
  - "destroying threads"
  - "threading [.NET Framework], destroying threads"
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Destroying Threads
La méthode <xref:System.Threading.Thread.Abort%2A> sert à arrêter définitivement un thread managé.  Lorsque vous appelez <xref:System.Threading.Thread.Abort%2A>, le Common Language Runtime lève une exception <xref:System.Threading.ThreadAbortException> dans le thread cible, que celui\-ci peut intercepter.  Pour plus d'informations, consultez <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>.  
  
> [!NOTE]
>  Si un thread exécute du code non managé lors de l'appel à sa méthode <xref:System.Threading.Thread.Abort%2A>, le runtime le marque comme <xref:System.Threading.ThreadState?displayProperty=fullName>.  L'exception est levée lorsque le thread retourne dans le code managé.  
  
 Lorsqu'un thread est abandonné, il ne peut pas être redémarré.  
  
 La méthode <xref:System.Threading.Thread.Abort%2A> ne provoque pas l'abandon immédiat du thread car le thread cible peut intercepter l'exception <xref:System.Threading.ThreadAbortException> et exécuter du code arbitraire dans un bloc `finally`.  Vous pouvez appeler <xref:System.Threading.Thread.Join%2A?displayProperty=fullName> si vous devez attendre que le thread soit terminé.  <xref:System.Threading.Thread.Join%2A?displayProperty=fullName> est un appel bloquant qui n'est pas retourné tant que l'exécution du thread n'est pas terminée ou qu'un intervalle de d'attente facultatif se soit écoulé.  Le thread interrompu pourrait appeler la méthode <xref:System.Threading.Thread.ResetAbort%2A> ou exécuter un traitement illimité dans un bloc `finally` ; dès lors, si vous ne spécifiez pas de délai d'expiration, rien ne garantit que l'attente se termine.  
  
 Les threads qui attendent un appel à la méthode <xref:System.Threading.Thread.Join%2A?displayProperty=fullName> peuvent être interrompus par d'autres threads qui appellent <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName>.  
  
## Gestion de ThreadAbortException  
 Si vous pensez que votre thread sera interrompu, soit en conséquence de l'appel à <xref:System.Threading.Thread.Abort%2A> à partir de votre code utilisateur, soit en raison du déchargement d'un domaine d'application dans lequel le thread s'exécute \(<xref:System.AppDomain.Unload%2A?displayProperty=fullName> utilise <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> pour arrêter des threads\), votre thread doit gérer l'exception <xref:System.Threading.ThreadAbortException> et exécuter la fin éventuelle du traitement dans une clause `finally`, comme illustré dans le code suivant.  
  
```vb  
Try  
    ' Code that is executing when the thread is aborted.  
Catch ex As ThreadAbortException  
    ' Clean-up code can go here.  
    ' If there is no Finally clause, ThreadAbortException is  
    ' re-thrown by the system at the end of the Catch clause.   
Finally  
    ' Clean-up code can go here.  
End Try  
' Do not put clean-up code here, because the exception   
' is rethrown at the end of the Finally clause.  
```  
  
```csharp  
try   
{  
    // Code that is executing when the thread is aborted.  
}   
catch (ThreadAbortException ex)   
{  
    // Clean-up code can go here.  
    // If there is no Finally clause, ThreadAbortException is  
    // re-thrown by the system at the end of the Catch clause.   
}  
// Do not put clean-up code here, because the exception   
// is rethrown at the end of the Finally clause.  
```  
  
 Votre code de nettoyage doit figurer dans la clause `catch` ou la clause `finally`, dans la mesure où le système lève de nouveau <xref:System.Threading.ThreadAbortException> à la fin de la clause `finally` ou à la fin de la clause `catch` en l'absence d'une clause `finally`.  
  
 Vous pouvez empêcher le système de lever une nouvelle fois l'exception en appelant la méthode <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=fullName>.  Toutefois, ne le faites que dans le seul cas où votre code utilisateur a provoqué <xref:System.Threading.ThreadAbortException>.  
  
## Voir aussi  
 <xref:System.Threading.ThreadAbortException>   
 <xref:System.Threading.Thread>   
 [Using Threads and Threading](../../../docs/standard/threading/using-threads-and-threading.md)