---
title: "Modèle de programmation asynchrone"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ending asynchronous operations
- starting asynchronous operations
- beginning asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming
- stopping asynchronous operations
- asynchronous programming, beginning operations
ms.assetid: c9b3501e-6bc6-40f9-8efd-4b6d9e39ccf0
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b31383f8972ecf345366f90460d88b6be21eab99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="asynchronous-programming-model-apm"></a>Modèle de programmation asynchrone
Une opération asynchrone qui utilise le modèle de conception <xref:System.IAsyncResult> est implémentée sous la forme de deux méthodes nommées **Begin** *NomOpération* et **End** *NomOpération* qui, respectivement, commencent et terminent l’opération asynchrone *NomOpération* . Par exemple, la classe <xref:System.IO.FileStream> fournit les méthodes <xref:System.IO.FileStream.BeginRead%2A> et <xref:System.IO.FileStream.EndRead%2A> pour lire les octets d’un fichier de façon asynchrone. Ces méthodes implémentent la version asynchrone de la méthode <xref:System.IO.FileStream.Read%2A> .  
  
> [!NOTE]
>  À compter du .NET Framework 4, la bibliothèque parallèle de tâches propose un nouveau modèle pour la programmation asynchrone et parallèle. Pour plus d’informations, consultez [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) et [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).  
  
 Après avoir appelé la méthode **Begin** *NomOpération*, une application peut continuer à exécuter des instructions sur le thread appelant pendant que l’opération asynchrone se déroule sur un autre thread. Pour chaque appel à la méthode **Begin** *NomOpération*, l’application doit aussi appeler la méthode **End** *NomOpération* pour obtenir les résultats de l’opération.  
  
## <a name="beginning-an-asynchronous-operation"></a>Commencement d’une opération asynchrone  
 La méthode **Begin** *NomOpération* commence l’opération asynchrone *NomOpération* et retourne un objet qui implémente l’interface <xref:System.IAsyncResult> . Les objets<xref:System.IAsyncResult> stockent des informations sur une opération asynchrone. Le tableau suivant affiche des informations sur une opération asynchrone.  
  
|Membre|Description|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Objet spécifique à l'application facultatif qui contient les informations sur l'opération asynchrone.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|<xref:System.Threading.WaitHandle> qui peut être utilisé pour bloquer l’exécution de l’application jusqu’à ce que l’opération asynchrone se termine.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|Valeur qui indique si l’opération asynchrone s’est terminée sur le thread utilisé pour appeler la méthode **Begin** *NomOpération* plutôt que sur un thread <xref:System.Threading.ThreadPool> distinct.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Valeur qui indique si l’opération asynchrone est terminée.|  
  
 Une méthode **Begin** *NomOpération* accepte tous les paramètres déclarés dans la signature de la version synchrone de la méthode qui sont passés par valeur ou par référence. Les paramètres de sortie éventuels (« out ») ne font pas partie de la signature de la méthode **Begin** *NomOpération* . La signature de la méthode **Begin** *NomOpération* inclut aussi deux autres paramètres. Le premier définit un délégué <xref:System.AsyncCallback> qui fait référence à une méthode appelée à la fin de l’opération asynchrone. L’appelant peut spécifier `null` (`Nothing` en Visual Basic) s’il ne veut pas qu’une méthode soit appelée à la fin de l’opération. Le deuxième paramètre supplémentaire est un objet défini par l’utilisateur. Cet objet peut être utilisé pour passer des informations d’état spécifiques à l’application à la méthode appelée à la fin de l’opération asynchrone. Si une méthode **Begin** *NomOpération* accepte d’autres paramètres spécifiques à l’opération, tels qu’un tableau d’octets pour stocker des octets lus à partir d’un fichier, <xref:System.AsyncCallback> et l’objet d’état de l’application sont les derniers paramètres dans la signature de la méthode **Begin** *NomOpération* .  
  
 **Begin** *NomOpération* retourne immédiatement le contrôle au thread appelant. Si la méthode **Begin** *NomOpération* lève des exceptions, celles-ci le sont avant le lancement de l’opération asynchrone. Si la méthode **Begin** *NomOpération* lève des exceptions, la méthode de rappel n’est pas appelée.  
  
## <a name="ending-an-asynchronous-operation"></a>Fin d’une opération asynchrone  
 La méthode **End** *NomOpération* met fin à l’opération asynchrone *NomOpération*. La valeur de retour de la méthode **End** *NomOpération* est du même type que celui retourné par son équivalent synchrone et est spécifique à l’opération asynchrone. Par exemple, la méthode <xref:System.IO.FileStream.EndRead%2A> retourne le nombre d’octets lus à partir d’un <xref:System.IO.FileStream> et la méthode <xref:System.Net.Dns.EndGetHostByName%2A> retourne un objet <xref:System.Net.IPHostEntry> qui contient des informations sur un ordinateur hôte. La méthode **End** *NomOpération* accepte les paramètres de sortie (« out ») ou de référence (« ref ») éventuellement déclarés dans la signature de la version synchrone de la méthode. En plus des paramètres de la méthode synchrone, la méthode **End** *NomOpération* inclut aussi un paramètre <xref:System.IAsyncResult> . Les appelants doivent passer l’instance retournée par l’appel correspondant à la méthode **Begin** *NomOpération*.  
  
 Si l’opération asynchrone représentée par le <xref:System.IAsyncResult> objet n’est pas terminée lorsque **fin** *NomOpération* est appelée, **fin**  *NomOpération* bloque le thread appelant jusqu'à ce que l’opération asynchrone est terminée. Les exceptions levées par l’opération asynchrone sont levées à partir de la méthode **End** *NomOpération* . Le fait d’appeler plusieurs fois la méthode **End** *NomOpération* avec le même objet <xref:System.IAsyncResult> a des effets indéfinis. De même, l’appel de la méthode **End** *NomOpération* avec un <xref:System.IAsyncResult> qui n’a pas été retourné par la méthode Begin associée n’est pas non plus défini.  
  
> [!NOTE]
>  Pour l’un ou l’autre des scénarios indéfinis, les implémenteurs doivent envisager de lever <xref:System.InvalidOperationException>.  
  
> [!NOTE]
>  Les implémenteurs de ce modèle de conception doivent informer l’appelant que l’opération asynchrone s’est terminée en attribuant à <xref:System.IAsyncResult.IsCompleted%2A> la valeur true, en appelant la méthode de rappel asynchrone (s’il en été spécifiée une) et en signalant <xref:System.IAsyncResult.AsyncWaitHandle%2A>.  
  
 Plusieurs options de conception s’offrent aux développeurs d’applications pour ce qui est de l’accès aux résultats de l’opération asynchrone. L’option appropriée varie selon que l’application peut exécuter ou non des instructions pendant que l’opération se termine. Si une application ne peut pas effectuer de tâches supplémentaires tant qu’elle n’a pas reçu les résultats de l’opération asynchrone, l’application doit être bloquée en attendant que les résultats soient disponibles. Pour la bloquer en attendant la fin de l’opération asynchrone, vous pouvez utiliser l’une des approches suivantes :  
  
-   Appelez la méthode **End** *NomOpération* à partir du thread principal de l’application, ce qui bloque l’exécution de l’application tant que l’opération n’est pas terminée. Pour obtenir un exemple illustrant cette technique, consultez [bloque l’exécution d’applications en mettant fin à une opération asynchrone](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
-   Utilisez <xref:System.IAsyncResult.AsyncWaitHandle%2A> pour bloquer l’exécution de l’application en attendant qu’une ou plusieurs opérations soient terminées. Pour obtenir un exemple illustrant cette technique, consultez [Blocking Application Execution Using an AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Les applications qui ne doivent pas être bloquées pendant que l’opération se termine peuvent utiliser l’une des approches suivantes :  
  
-   Interrogez l’état d’achèvement de l’opération en vérifiant périodiquement la propriété <xref:System.IAsyncResult.IsCompleted%2A> et en appelant la méthode **End** *NomOpération* quand l’opération est terminée. Pour obtenir un exemple illustrant cette technique, consultez [Polling for the Status of an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
-   Utilisez un délégué <xref:System.AsyncCallback> pour spécifier la méthode à appeler quand l’opération se termine. Pour obtenir un exemple illustrant cette technique, consultez [Using an AsyncCallback Delegate to End an Asynchronous Operation](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle asynchrone basé sur les événements (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Appel de méthodes synchrones de façon asynchrone](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 [Utilisation d'un délégué AsyncCallback et objet d'état](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
