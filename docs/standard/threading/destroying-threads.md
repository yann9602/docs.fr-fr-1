---
title: Destruction de threads
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4a41dce5db707d0be49c283256de665d316e1a1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="destroying-threads"></a>Destruction de threads
Le <xref:System.Threading.Thread.Abort%2A> méthode est utilisée pour arrêter définitivement un thread managé. Lorsque vous appelez <xref:System.Threading.Thread.Abort%2A>, le common language runtime lève une <xref:System.Threading.ThreadAbortException> dans le thread cible, que le thread cible peut intercepter. Pour plus d'informations, consultez <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Si un thread est en cours d’exécution non managée du code lorsque son <xref:System.Threading.Thread.Abort%2A> est appelée, le runtime marque <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>. L’exception est levée lorsque le thread retourne au code managé.  
  
 Une fois qu’un thread est abandonné, il ne peut pas être redémarré.  
  
 Le <xref:System.Threading.Thread.Abort%2A> méthode n’entraîne pas le thread d’abandonner immédiatement, car le thread cible peut intercepter le <xref:System.Threading.ThreadAbortException> et d’exécution arbitraire de code dans un `finally` bloc. Vous pouvez appeler <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> si vous avez besoin d’attendre que le thread s’est terminée. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>est un appel bloquant qui ne retourne pas jusqu'à ce que le thread est en cours de l’exécution, ou un intervalle de délai d’attente facultatif a expiré. Le thread interrompu pourrait appeler le <xref:System.Threading.Thread.ResetAbort%2A> méthode ou exécuter un traitement illimité dans un `finally` bloquer, donc si vous ne spécifiez pas un délai d’attente, il n’est pas garantie que l’attente de fin.  
  
 Les threads qui attendent un appel à la <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> méthode peut être interrompue par d’autres threads qui appellent <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.  
  
## <a name="handling-threadabortexception"></a>Gestion de ThreadAbortException  
 Si vous pensez que votre thread est abandonnée, soit en tant que résultat de l’appel <xref:System.Threading.Thread.Abort%2A> à partir de votre propre code ou à la suite de décharger un domaine d’application dans lequel le thread est en cours d’exécution (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> utilise <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> pour arrêter des threads), votre thread doit gérer. le <xref:System.Threading.ThreadAbortException> et d’effectuer un traitement final dans un `finally` clause, comme indiqué dans le code suivant.  
  
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
  
 Votre code de nettoyage doit être dans le `catch` clause ou le `finally` clause, car un <xref:System.Threading.ThreadAbortException> est à nouveau levée par le système à la fin de la `finally` clause, ou à la fin de la `catch` clause s’il existe aucune `finally` clause.  
  
 Vous pouvez empêcher le système de nouveau l’exception en appelant le <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> (méthode). Toutefois, vous devez effectuer ce uniquement si votre propre code qui a provoqué le <xref:System.Threading.ThreadAbortException>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 [Utilisation des threads et du threading](../../../docs/standard/threading/using-threads-and-threading.md)
