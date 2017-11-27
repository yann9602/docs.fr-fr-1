---
title: "Traitement des messages dans le désordre"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2ffd220babe99661d8b6aaf271a566d415af5eb1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="out-of-order-message-processing"></a><span data-ttu-id="3da9c-102">Traitement des messages dans le désordre</span><span class="sxs-lookup"><span data-stu-id="3da9c-102">Out-of-Order Message Processing</span></span>
<span data-ttu-id="3da9c-103">Les services de workflow peuvent dépendre de l'ordre dans lequel sont envoyés les messages.</span><span class="sxs-lookup"><span data-stu-id="3da9c-103">Workflow services may depend on messages being sent in a specific order.</span></span> <span data-ttu-id="3da9c-104">Un service de workflow contient une ou plusieurs activités <xref:System.ServiceModel.Activities.Receive> et chaque activité <xref:System.ServiceModel.Activities.Receive> attend un message spécifique.</span><span class="sxs-lookup"><span data-stu-id="3da9c-104">A workflow service contains one or more <xref:System.ServiceModel.Activities.Receive> activities and each <xref:System.ServiceModel.Activities.Receive> activity is expecting a specific message.</span></span> <span data-ttu-id="3da9c-105">Sans garanties particulières de remise par le transport, les messages envoyés par des clients peuvent être différés et par conséquent remis dans un ordre non prévu par le service de workflow.</span><span class="sxs-lookup"><span data-stu-id="3da9c-105">Without particular transport delivery guarantees, messages sent by clients may be delayed and therefore delivered in an order the workflow service may not expect.</span></span> <span data-ttu-id="3da9c-106">L'implémentation d'un service de workflow qui ne requiert aucun ordre particulier d'envoi des messages s'effectue en principe à l'aide d'une activité Parallèle.</span><span class="sxs-lookup"><span data-stu-id="3da9c-106">Implementing a workflow service that does not require messages be sent in a specific order is normally done using a Parallel activity.</span></span> <span data-ttu-id="3da9c-107">Pour un protocole d'application plus complexe, le workflow risque de se compliquer très rapidement.</span><span class="sxs-lookup"><span data-stu-id="3da9c-107">For a more complicated application protocol, the workflow would become very complex very quickly.</span></span>  <span data-ttu-id="3da9c-108">La fonctionnalité de traitement des messages dans le désordre dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vous permet de créer un workflow de ce type, en évitant la complexité des activités Parallèles imbriquées.</span><span class="sxs-lookup"><span data-stu-id="3da9c-108">The out-of-order message processing feature in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] allows you to create such a workflow without all of the complexity of nested Parallel activities.</span></span> <span data-ttu-id="3da9c-109">Le traitement des messages dans le désordre n'est possible que sur les canaux qui prennent en charge l'objet <xref:System.ServiceModel.Channels.ReceiveContext>, comme les liaisons MSMQ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3da9c-109">Out-of-order message processing is only supported on channels that support <xref:System.ServiceModel.Channels.ReceiveContext> such as the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ bindings.</span></span>  
  
## <a name="enabling-out-of-order-message-processing"></a><span data-ttu-id="3da9c-110">Activation du traitement des messages dans le désordre</span><span class="sxs-lookup"><span data-stu-id="3da9c-110">Enabling Out-Of-Order Message Processing</span></span>  
 <span data-ttu-id="3da9c-111">Le traitement des messages dans le désordre est activé en définissant la propriété <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> à la valeur `true` dans le WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="3da9c-111">Out-of-order message processing is enabled by setting the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property to `true` on the WorkflowService.</span></span> <span data-ttu-id="3da9c-112">L'exemple suivant montre comment définir la propriété <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> dans le code.</span><span class="sxs-lookup"><span data-stu-id="3da9c-112">The following example shows how to set the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property in code.</span></span>  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 <span data-ttu-id="3da9c-113">Vous pouvez également appliquer l'attribut `AllowBufferedReceive` à un service de workflow en XAML, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3da9c-113">You can also apply the `AllowBufferedReceive` attribute to a workflow service in XAML as shown in the following example.</span></span>  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!—the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3da9c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3da9c-114">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ReceiveContext>  
 [<span data-ttu-id="3da9c-115">Services de workflow</span><span class="sxs-lookup"><span data-stu-id="3da9c-115">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="3da9c-116">Les files d’attente et les Sessions fiables</span><span class="sxs-lookup"><span data-stu-id="3da9c-116">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
