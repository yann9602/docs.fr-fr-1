---
title: "Traitement ordonné des messages en mode de concurrence simple"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c50381c678a84f5602d08342d02dbf44316994c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a><span data-ttu-id="e2ccb-102">Traitement ordonné des messages en mode de concurrence simple</span><span class="sxs-lookup"><span data-stu-id="e2ccb-102">Ordered Processing of Messages in Single Concurrency Mode</span></span>
<span data-ttu-id="e2ccb-103">WCF ne garantit pas sur l’ordre dans lequel les messages sont traités, à moins que le canal sous-jacent est la session.</span><span class="sxs-lookup"><span data-stu-id="e2ccb-103">WCF makes no guarantees about the order in which messages are processed, unless the underlying channel is sessionful.</span></span>  <span data-ttu-id="e2ccb-104">Par exemple, un service WCF qui utilise MsmqInputChannel, ce qui n’est pas un canal de session, ne pourront pas traiter les messages dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="e2ccb-104">For instance, a WCF service that uses MsmqInputChannel, which is not a sessionful channel, will fail to process messages in order.</span></span> <span data-ttu-id="e2ccb-105">Il existe certains cas où un développeur peut le comportement de traitement des commandes en mais que vous souhaitez pas utiliser des sessions.</span><span class="sxs-lookup"><span data-stu-id="e2ccb-105">There are some circumstances where a developer may want the in order processing behavior but not want to use sessions.</span></span> <span data-ttu-id="e2ccb-106">Cette rubrique décrit comment configurer ce comportement lorsqu'un service s'exécute en mode de concurrence simple.</span><span class="sxs-lookup"><span data-stu-id="e2ccb-106">This topic describes how to configure this behavior when a service is running in Single Concurrency Mode.</span></span>  
  
## <a name="in-order-message-processing"></a><span data-ttu-id="e2ccb-107">Traitement des messages dans l'ordre</span><span class="sxs-lookup"><span data-stu-id="e2ccb-107">In-order Message Processing</span></span>  
 <span data-ttu-id="e2ccb-108">Un nouvel attribut nommé <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> a été ajouté à la classe <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e2ccb-108">A new attribute called <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> has been added to the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="e2ccb-109">Lorsque <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> a la valeur true et <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> a la valeur <xref:System.ServiceModel.ConcurrencyMode.Single> les messages envoyés au service sont traités dans l'ordre.</span><span class="sxs-lookup"><span data-stu-id="e2ccb-109">When <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> is set to true and <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to <xref:System.ServiceModel.ConcurrencyMode.Single> messages sent to the service will be processed in order.</span></span> <span data-ttu-id="e2ccb-110">L'extrait de code suivant illustre comment définir ces attributs.</span><span class="sxs-lookup"><span data-stu-id="e2ccb-110">The following code snippet illustrates how to set these attributes.</span></span>  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <span data-ttu-id="e2ccb-111">Si une autre valeur est affectée à la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>, une exception <xref:System.InvalidOperationException> est levée.</span><span class="sxs-lookup"><span data-stu-id="e2ccb-111">If <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to any other value, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2ccb-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2ccb-112">See Also</span></span>  
 [<span data-ttu-id="e2ccb-113">Sessions, instanciation et accès concurrentiel</span><span class="sxs-lookup"><span data-stu-id="e2ccb-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [<span data-ttu-id="e2ccb-114">Concurrence</span><span class="sxs-lookup"><span data-stu-id="e2ccb-114">Concurrency</span></span>](../../../../docs/framework/wcf/samples/concurrency.md)
