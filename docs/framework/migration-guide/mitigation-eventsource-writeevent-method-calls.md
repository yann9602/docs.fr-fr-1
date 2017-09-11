---
title: "Atténuation : appels de la méthode EventSource.WriteEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 327a9fdb-ba8e-40f7-89e5-4c89b46e594f
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 270f89183bced5d07598b1731f18acf90ec9715a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-eventsourcewriteevent-method-calls"></a><span data-ttu-id="fa60d-102">Atténuation : appels de la méthode EventSource.WriteEvent</span><span class="sxs-lookup"><span data-stu-id="fa60d-102">Mitigation: EventSource.WriteEvent Method Calls</span></span>
<span data-ttu-id="fa60d-103">[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] impose un contrat entre une méthode d'événement ETW dans une classe dérivée de <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> et la méthode <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> de sa classe de base.</span><span class="sxs-lookup"><span data-stu-id="fa60d-103">The [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] enforces a contract between an ETW event method in a class that is derived from <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> and  the <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> method of its base class.</span></span> <span data-ttu-id="fa60d-104">La méthode d'événement ETW doit passer à la méthode <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> l'ID d'événement suivi des mêmes arguments que ceux passés à la méthode d'événement.</span><span class="sxs-lookup"><span data-stu-id="fa60d-104">The ETW event method must pass the <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> method the event ID followed by the same arguments that were passed to the event method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="fa60d-105">Impact</span><span class="sxs-lookup"><span data-stu-id="fa60d-105">Impact</span></span>  
 <span data-ttu-id="fa60d-106">Une méthode d'événement ETW définie de la façon suivante rompt le contrat :</span><span class="sxs-lookup"><span data-stu-id="fa60d-106">An ETW event method defined in the following way breaks the contract:</span></span>  
  
```  
[Event(2, Level = EventLevel.Informational)]  
public void Info2(string message)  
{  
   base.WriteEvent(2, message, "-");  
}  
```  
  
 <span data-ttu-id="fa60d-107">Lorsque ce contrat est violé, une exception <xref:System.IndexOutOfRangeException> est levée au moment de l'exécution si un objet <xref:System.Diagnostics.Tracing.EventListener> lit les données <xref:System.Diagnostics.Tracing.EventSource> dans le processus.</span><span class="sxs-lookup"><span data-stu-id="fa60d-107">When this contract is violated, an <xref:System.IndexOutOfRangeException> exception is thrown at run time if an <xref:System.Diagnostics.Tracing.EventListener> object reads <xref:System.Diagnostics.Tracing.EventSource> data in process.</span></span>  
  
 <span data-ttu-id="fa60d-108">La définition de cette méthode d'événement ETW doit suivre le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="fa60d-108">The definition for this ETW event method should follow this pattern:</span></span>  
  
```  
[Event(2, Level = EventLevel.Informational)]  
public void Info2(string message)  
{  
   base.WriteEvent(2, message);  
}  
```  
  
## <a name="mitigation"></a><span data-ttu-id="fa60d-109">Atténuation</span><span class="sxs-lookup"><span data-stu-id="fa60d-109">Mitigation</span></span>  
 <span data-ttu-id="fa60d-110">Vous devez modifier le code existant pour respecter le modèle requis.</span><span class="sxs-lookup"><span data-stu-id="fa60d-110">You must modify existing code to conform to the required pattern.</span></span>  
  
 <span data-ttu-id="fa60d-111">Vous pouvez réduire la quantité de code à modifier en définissant deux méthodes pour appeler la méthode <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> , comme suit :</span><span class="sxs-lookup"><span data-stu-id="fa60d-111">You can minimize the amount of code that you have to change by defining two methods for calling the <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> method, as follows:</span></span>  
  
```  
[NonEvent]  
public void Info2(string message)  
{  
   Info2Internal(message, "-");  
}  
  
public void Info2Internal(string message, string prefix)  
{  
   WriteEvent(2, message, prefix);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa60d-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa60d-112">See Also</span></span>  
 [<span data-ttu-id="fa60d-113">Modifications du runtime</span><span class="sxs-lookup"><span data-stu-id="fa60d-113">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)

