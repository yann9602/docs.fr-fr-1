---
title: "Corrélation demande-réponse"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 29286950cfef7d8e3e2c453bbdcc307c26e641de
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="request-reply-correlation"></a><span data-ttu-id="3b4d6-102">Corrélation demande-réponse</span><span class="sxs-lookup"><span data-stu-id="3b4d6-102">Request-Reply Correlation</span></span>
<span data-ttu-id="3b4d6-103">Corrélation demande-réponse est utilisée avec un <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire pour implémenter une opération bidirectionnelle dans un service de workflow et avec un <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> paire qui appelle une opération bidirectionnelle dans un autre site Web service.</span><span class="sxs-lookup"><span data-stu-id="3b4d6-103">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="3b4d6-104">Lors de l'appel d'une opération bidirectionnelle dans un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], le service peut être soit un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] basé sur un code impératif traditionnel, soit un service de workflow.</span><span class="sxs-lookup"><span data-stu-id="3b4d6-104">When invoking a two-way operation in a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, the service can be either a traditional imperative code-based [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service or it can be a workflow service.</span></span> <span data-ttu-id="3b4d6-105">Pour utiliser la corrélation demande-réponse, une liaison bidirectionnelle doit être utilisée, telle que <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="3b4d6-105">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="3b4d6-106">Qu'il s'agisse d'appeler ou d'implémenter une opération bidirectionnelle, les étapes d'initialisation de la corrélation sont similaires ; elles sont présentées dans cette section.</span><span class="sxs-lookup"><span data-stu-id="3b4d6-106">Whether invoking or implementing a two-way operation, the correlation initialization steps are similar and are covered in this section.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a><span data-ttu-id="3b4d6-107">Utilisation de la corrélation dans une opération bidirectionnelle avec Receive/SendReply</span><span class="sxs-lookup"><span data-stu-id="3b4d6-107">Using Correlation in a Two-Way Operation with Receive/SendReply</span></span>  
 <span data-ttu-id="3b4d6-108">A <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire est utilisée pour implémenter une opération bidirectionnelle dans un service de workflow.</span><span class="sxs-lookup"><span data-stu-id="3b4d6-108">A <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used to implement a two-way operation in a workflow service.</span></span> <span data-ttu-id="3b4d6-109">L'exécution utilise la corrélation demande-réponse pour vérifier que la réponse est distribuée à l'appelant approprié.</span><span class="sxs-lookup"><span data-stu-id="3b4d6-109">The runtime uses request-reply correlation to ensure that the reply is dispatched to the correct caller.</span></span> <span data-ttu-id="3b4d6-110">Lorsqu'un workflow est hébergé à l'aide de <xref:System.ServiceModel.Activities.WorkflowServiceHost>, ce qui est le cas des services de workflow, l'initialisation de la corrélation par défaut est suffisante.</span><span class="sxs-lookup"><span data-stu-id="3b4d6-110">When a workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, which is the case for workflow services, then the default correlation initialization is sufficient.</span></span> <span data-ttu-id="3b4d6-111">Dans ce scénario, un <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire est utilisée par un flux de travail, et aucune configuration de corrélation spécifique est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="3b4d6-111">In this scenario, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is used by a workflow, and no specific correlation configuration is required.</span></span>  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
### <a name="explicitly-initializing-request-reply-correlation"></a><span data-ttu-id="3b4d6-112">Initialisation explicite de la corrélation demande-réponse</span><span class="sxs-lookup"><span data-stu-id="3b4d6-112">Explicitly Initializing Request-Reply Correlation</span></span>  
 <span data-ttu-id="3b4d6-113">Si d'autres opérations bidirectionnelles existent en parallèle, la corrélation doit être configurée de manière explicite.</span><span class="sxs-lookup"><span data-stu-id="3b4d6-113">If other two-way operations are in parallel, then correlation should be explicitly configured.</span></span> <span data-ttu-id="3b4d6-114">Cela est possible en spécifiant un <xref:System.ServiceModel.Activities.CorrelationHandle> et <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, ou en plaçant le <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> à l’intérieur d’un <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="3b4d6-114">This can be done by specifying a <xref:System.ServiceModel.Activities.CorrelationHandle> and <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, or by placing the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> inside of a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="3b4d6-115">Dans cet exemple, la corrélation demande-réponse est configurée sur un <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire.</span><span class="sxs-lookup"><span data-stu-id="3b4d6-115">In this example, request-reply correlation is configured on a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair.</span></span>  
  
```csharp  
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder",  
    CorrelationInitializers =  
    {  
        new RequestReplyCorrelationInitializer  
        {  
            CorrelationHandle = RRHandle  
        }  
    }  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
 <span data-ttu-id="3b4d6-116">Au lieu de configurer la corrélation de manière explicite, une activité <xref:System.ServiceModel.Activities.CorrelationScope> peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="3b4d6-116">Instead of explicitly configuring the correlation, a <xref:System.ServiceModel.Activities.CorrelationScope> activity can be used.</span></span> <span data-ttu-id="3b4d6-117"><xref:System.ServiceModel.Activities.CorrelationScope> fournit un <xref:System.ServiceModel.Activities.CorrelationHandle> implicite aux activités de messagerie qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="3b4d6-117"><xref:System.ServiceModel.Activities.CorrelationScope> provides an implicit <xref:System.ServiceModel.Activities.CorrelationHandle> to the messaging activities that it contains.</span></span> <span data-ttu-id="3b4d6-118">Dans cet exemple, un <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire est contenue dans un <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="3b4d6-118">In this example, a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is contained inside a <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span> <span data-ttu-id="3b4d6-119">Aucune configuration de corrélation explicite n'est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="3b4d6-119">No explicit correlation configuration is required.</span></span>  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
CorrelationScope s = new CorrelationScope  
{  
    Body = new Sequence  
    {  
        Activities =   
        {  
            StartOrder,  
            // Activities that create the reply.  
            ReplyToStartOrder  
        }  
    }  
};  
  
// Construct a workflow using the CorrelationScope.  
```  
  
 <span data-ttu-id="3b4d6-120">Si nécessaire, des corrélations supplémentaires peuvent être configurées à l'aide de la propriété <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> des activités de messagerie respectives utilisant les types `CorrelationInitializer` souhaités.</span><span class="sxs-lookup"><span data-stu-id="3b4d6-120">If additional correlations are required then they can be configured using the <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> property of the respective messaging activities using the desired `CorrelationInitializer` types.</span></span>  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a><span data-ttu-id="3b4d6-121">Utilisation de la corrélation dans une opération bidirectionnelle avec Send/ReceiveReply</span><span class="sxs-lookup"><span data-stu-id="3b4d6-121">Using Correlation in a Two-Way Operation with Send/ReceiveReply</span></span>  
 <span data-ttu-id="3b4d6-122">Alors que le <xref:System.ServiceModel.Activities.Receive> activité peut uniquement être utilisée dans un service de workflow hébergé par <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> paire peut être utilisée dans n’importe quel flux de travail qui doit appeler une méthode sur un service Web.</span><span class="sxs-lookup"><span data-stu-id="3b4d6-122">While the <xref:System.ServiceModel.Activities.Receive> activity can only be used in a workflow service hosted by <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> and the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair can be used in any workflow that must invoke a method on a Web service.</span></span> <span data-ttu-id="3b4d6-123">Si le workflow est hébergé à l'aide de l'objet <xref:System.ServiceModel.Activities.WorkflowServiceHost>, la corrélation par défaut décrite dans la section précédente s'applique, mais si ce n'est pas le cas, la corrélation doit être configurée soit de manière explicite à l'aide des objets <xref:System.ServiceModel.Activities.CorrelationInitializer> et <xref:System.ServiceModel.Activities.CorrelationHandle> souhaités, soit en utilisant la gestion de handle implicite de l'objet <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="3b4d6-123">If the workflow is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost> then the default correlation described in the previous section applies, but if not, then correlation must be configured either explicitly using the desired <xref:System.ServiceModel.Activities.CorrelationInitializer> and <xref:System.ServiceModel.Activities.CorrelationHandle>, or by using the implicit handle management of the <xref:System.ServiceModel.Activities.CorrelationScope>.</span></span>  
  
 <span data-ttu-id="3b4d6-124">Lorsque vous utilisez **ajouter une référence de Service** sur un service avec des opérations bidirectionnelles, les activités générées encapsulent un <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> paire d’activités en interne avec la corrélation demande/réponse explicitement spécifié.</span><span class="sxs-lookup"><span data-stu-id="3b4d6-124">When using **Add Service Reference** on a service with two-way operations, activities are generated that wrap a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair activity internally with the Request/Reply correlation explicitly specified.</span></span>
