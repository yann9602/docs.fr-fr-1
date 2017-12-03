---
title: "Comment : appeler des opérations de façon asynchrone à l'aide d'une fabrication de canal"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8e0ef2dbd52e6628e7b784c50d2ce29306216772
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a><span data-ttu-id="18dbb-102">Comment : appeler des opérations de façon asynchrone à l'aide d'une fabrication de canal</span><span class="sxs-lookup"><span data-stu-id="18dbb-102">How to: Call Operations Asynchronously Using a Channel Factory</span></span>
<span data-ttu-id="18dbb-103">Cette rubrique décrit comment un client peut accéder de façon asynchrone à une opération de service lors de l'utilisation d'une application cliente basée sur <xref:System.ServiceModel.ChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="18dbb-103">This topic covers how a client can access a service operation asynchronously when using a <xref:System.ServiceModel.ChannelFactory%601>-based client application.</span></span> <span data-ttu-id="18dbb-104">(Lors de l'utilisation d'un objet <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> pour appeler un service, vous pouvez utiliser le modèle d'appel asynchrone commandé par événement.</span><span class="sxs-lookup"><span data-stu-id="18dbb-104">(When using a <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> object to invoke a service you can use the event-driven asynchronous calling model.</span></span> <span data-ttu-id="18dbb-105">Pour plus d’informations, consultez [Comment : appeler les opérations de Service asynchrone](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="18dbb-105">For more information, see [How to: Call Service Operations Asynchronously](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="18dbb-106">Pour plus d’informations sur le modèle d’appel asynchrone basé sur des événements, consultez [programmation multithread avec le modèle asynchrone basé sur événement](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md).)</span><span class="sxs-lookup"><span data-stu-id="18dbb-106">For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md).)</span></span>  
  
 <span data-ttu-id="18dbb-107">Le service dans cette rubrique implémente l'interface `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="18dbb-107">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="18dbb-108">Le client peut appeler les opérations sur cette interface de façon asynchrone, ce qui signifie que des opérations telles que `Add` sont divisées en deux méthodes : `BeginAdd` et `EndAdd`, la première initiant l'appel et la seconde récupérant le résultat au terme de l'opération.</span><span class="sxs-lookup"><span data-stu-id="18dbb-108">The client can call the operations on this interface asynchronously, which means that operations like `Add` are split into two methods, `BeginAdd` and `EndAdd`, the former of which initiates the call and the latter of which retrieves the result when the operation completes.</span></span> <span data-ttu-id="18dbb-109">Pour obtenir un exemple montrant comment implémenter une opération de façon asynchrone dans un service, consultez [Comment : implémenter une opération de Service asynchrone](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="18dbb-109">For an example showing how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="18dbb-110">Pour plus d’informations sur les opérations synchrones et asynchrones, consultez [synchrone et asynchrone des opérations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="18dbb-110">For details about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="18dbb-111">Procédure</span><span class="sxs-lookup"><span data-stu-id="18dbb-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="18dbb-112">Pour appeler des opérations de service WCF de façon asynchrone</span><span class="sxs-lookup"><span data-stu-id="18dbb-112">To call WCF service operations asynchronously</span></span>  
  
1.  <span data-ttu-id="18dbb-113">Exécutez le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) outil avec la `/async` option comme indiqué dans la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="18dbb-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with the `/async` option as shown in the following command.</span></span>  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     <span data-ttu-id="18dbb-114">Cela génère une version cliente asynchrone du contrat de service pour l'opération.</span><span class="sxs-lookup"><span data-stu-id="18dbb-114">This generates an asynchronous client version of the service contract for the operation.</span></span>  
  
2.  <span data-ttu-id="18dbb-115">Créez une fonction de rappel à appeler au terme de l'opération asynchrone en vous conformant à l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="18dbb-115">Create a callback function to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3.  <span data-ttu-id="18dbb-116">Pour accéder de façon asynchrone à une opération de service, créez le client, puis appelez la méthode `Begin[Operation]` (par exemple, `BeginAdd`) et spécifiez une fonction de rappel en vous conformant à l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="18dbb-116">To access a service operation asynchronously, create the client and call the `Begin[Operation]` (for example, `BeginAdd`) and specify a callback function, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     <span data-ttu-id="18dbb-117">Lors de l'exécution de la fonction de rappel, le client appelle la méthode `End<operation>` (par exemple, `EndAdd`) pour récupérer le résultat.</span><span class="sxs-lookup"><span data-stu-id="18dbb-117">When the callback function executes, the client calls `End<operation>` (for example, `EndAdd`) to retrieve the result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18dbb-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="18dbb-118">Example</span></span>  
 <span data-ttu-id="18dbb-119">Le service utilisé avec le code client utilisé dans la procédure précédente implémente l'interface `ICalculator` comme affiché dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="18dbb-119">The service that is used with the client code that is used in the preceding procedure implements the `ICalculator` interface as shown in the following code.</span></span> <span data-ttu-id="18dbb-120">Du côté service, les opérations `Add` et `Subtract` du contrat sont appelées de façon synchrone par le temps d'exécution [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], bien que les étapes clientes précédentes soient appelées de façon asynchrone sur le client.</span><span class="sxs-lookup"><span data-stu-id="18dbb-120">On the service side, the `Add` and `Subtract` operations of the contract are invoked synchronously by the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] run time, even though the preceding client steps are invoked asynchronously on the client.</span></span> <span data-ttu-id="18dbb-121">Les opérations `Multiply` et `Divide` sont utilisées pour appeler de façon asynchrone le service du côté service, même si le client les appelle de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="18dbb-121">The `Multiply` and `Divide` operations are used to invoke the service asynchronously on the service side, even if the client invokes them synchronously.</span></span> <span data-ttu-id="18dbb-122">Cet exemple affecte la propriété <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> à `true`.</span><span class="sxs-lookup"><span data-stu-id="18dbb-122">This example sets the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property to `true`.</span></span> <span data-ttu-id="18dbb-123">Ce paramètre de propriété, ainsi que l'implémentation du modèle asynchrone du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] indiquent au temps d'exécution d'appeler l'opération de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="18dbb-123">This property setting, in combination with the implementation of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] asynchronous pattern, tells the run time to invoke the operation asynchronously.</span></span>  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="18dbb-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18dbb-124">See Also</span></span>  
 [<span data-ttu-id="18dbb-125">Contrat de service : Exemple asynchrone</span><span class="sxs-lookup"><span data-stu-id="18dbb-125">Service Contract: Asynchronous Sample</span></span>](http://msdn.microsoft.com/en-us/833db946-f511-4f64-a26f-2759a11217c7)
