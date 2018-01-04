---
title: "Comment : appeler des opérations de service WCF de façon asynchrone"
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
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f8a22a5a5b9f388cdfb7b5e5edfa0a54b628aa0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="af83b-102">Comment : appeler des opérations de service WCF de façon asynchrone</span><span class="sxs-lookup"><span data-stu-id="af83b-102">How to: Call WCF Service Operations Asynchronously</span></span>
<span data-ttu-id="af83b-103">Cette rubrique présente comment un client peut accéder de façon asynchrone à une opération de service.</span><span class="sxs-lookup"><span data-stu-id="af83b-103">This topic covers how a client can access a service operation asynchronously.</span></span> <span data-ttu-id="af83b-104">Le service dans cette rubrique implémente l'interface `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="af83b-104">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="af83b-105">Le client peut appeler les opérations sur cette interface de manière asynchrone à l'aide du modèle d'appel asynchrone commandé par événement.</span><span class="sxs-lookup"><span data-stu-id="af83b-105">The client can call the operations on this interface asynchronously by using the event-driven asynchronous calling model.</span></span> <span data-ttu-id="af83b-106">(Pour plus d’informations sur le modèle d’appel asynchrone basé sur des événements, consultez [programmation multithread avec le modèle asynchrone basé sur événement](http://go.microsoft.com/fwlink/?LinkId=248184)).</span><span class="sxs-lookup"><span data-stu-id="af83b-106">(For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=248184)).</span></span> <span data-ttu-id="af83b-107">Pour obtenir un exemple qui montre comment implémenter une opération de façon asynchrone dans un service, consultez [Comment : implémenter une opération de Service asynchrone](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="af83b-107">For an example that shows how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="af83b-108">Pour plus d’informations sur les opérations synchrones et asynchrones, consultez [synchrone et asynchrone des opérations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="af83b-108">For more information about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af83b-109">Le modèle d'appel asynchrone commandé par événement n'est pas pris en charge lorsqu'il utilise un <xref:System.ServiceModel.ChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="af83b-109">The event-driven asynchronous calling model is not supported when using a <xref:System.ServiceModel.ChannelFactory%601>.</span></span> <span data-ttu-id="af83b-110">Pour plus d’informations sur les appels asynchrones à l’aide de la <xref:System.ServiceModel.ChannelFactory%601>, consultez [Comment : appeler opérations de façon asynchrone en utilisant une fabrique de canaux](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="af83b-110">For information about making asynchronous calls using the <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="af83b-111">Procédure</span><span class="sxs-lookup"><span data-stu-id="af83b-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="af83b-112">Pour appeler des opérations de service WCF de façon asynchrone</span><span class="sxs-lookup"><span data-stu-id="af83b-112">To call WCF service operations asynchronously</span></span>  
  
1.  <span data-ttu-id="af83b-113">Exécuter la [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) outil à la fois avec la `/async` et le `/tcv:Version35` commande options ensemble, comme indiqué dans la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="af83b-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with both the `/async` and the `/tcv:Version35` command options together as shown in the following command.</span></span>  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     <span data-ttu-id="af83b-114">Cette opération génère en plus des opérations asynchrones basées sur les délégués standard et des opérations synchrones, un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui contient :</span><span class="sxs-lookup"><span data-stu-id="af83b-114">This generates, in addition to the synchronous and standard delegate-based asynchronous operations, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class that contains:</span></span>  
  
    -   <span data-ttu-id="af83b-115">Deux <`operationName` > `Async` operations pour une utilisation avec l’approche appel asynchrone basé sur des événements.</span><span class="sxs-lookup"><span data-stu-id="af83b-115">Two <`operationName`>`Async` operations for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="af83b-116">Exemple :</span><span class="sxs-lookup"><span data-stu-id="af83b-116">For example:</span></span>  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    -   <span data-ttu-id="af83b-117">Événements d’opération s’est terminée sous la forme <`operationName` > `Completed` pour une utilisation avec l’approche appel asynchrone basé sur des événements.</span><span class="sxs-lookup"><span data-stu-id="af83b-117">Operation completed events of the form <`operationName`>`Completed` for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="af83b-118">Exemple :</span><span class="sxs-lookup"><span data-stu-id="af83b-118">For example:</span></span>  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    -   <span data-ttu-id="af83b-119"><xref:System.EventArgs?displayProperty=nameWithType>types pour chaque opération (sous la forme <`operationName`>`CompletedEventArgs`) pour une utilisation avec l’approche appel asynchrone basé sur des événements.</span><span class="sxs-lookup"><span data-stu-id="af83b-119"><xref:System.EventArgs?displayProperty=nameWithType> types for each operation (of the form <`operationName`>`CompletedEventArgs`) for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="af83b-120">Exemple :</span><span class="sxs-lookup"><span data-stu-id="af83b-120">For example:</span></span>  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2.  <span data-ttu-id="af83b-121">Dans l'application d'appel, créez une méthode de rappel à appeler au terme de l'opération asynchrone en vous conformant à l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="af83b-121">In the calling application, create a callback method to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3.  <span data-ttu-id="af83b-122">Avant d’appeler l’opération, utilisez un nouveau générique <xref:System.EventHandler%601?displayProperty=nameWithType> de type <`operationName` > `EventArgs` pour ajouter la méthode de gestionnaire (créée à l’étape précédente) à la <`operationName` > `Completed` événement.</span><span class="sxs-lookup"><span data-stu-id="af83b-122">Prior to calling the operation, use a new generic <xref:System.EventHandler%601?displayProperty=nameWithType> of type <`operationName`>`EventArgs` to add the handler method (created in the preceding step) to the <`operationName`>`Completed` event.</span></span> <span data-ttu-id="af83b-123">Appelez ensuite la <`operationName` > `Async` (méthode).</span><span class="sxs-lookup"><span data-stu-id="af83b-123">Then call the <`operationName`>`Async` method.</span></span> <span data-ttu-id="af83b-124">Exemple :</span><span class="sxs-lookup"><span data-stu-id="af83b-124">For example:</span></span>  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="af83b-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="af83b-125">Example</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af83b-126">Les règles de conception pour le modèle asynchrone basé sur les événements stipulent que si plusieurs valeurs sont retournées, une valeur est retournée comme la propriété `Result` et les autres sont retournées comme les propriétés sur l'objet <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="af83b-126">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="af83b-127">Il en découle que si un client importe des métadonnées à l'aide des options de commande asynchrone basées sur les événements et que l'opération retourne plusieurs valeurs, l'objet <xref:System.EventArgs> par défaut retourne une valeur comme la propriété `Result` et le reste sont des propriétés de l'objet <xref:System.EventArgs>. Pour recevoir l'objet message comme la propriété `Result` et que les valeurs retournées sur cet objet soient des propriétés, utilisez l'option de commande `/messageContract`.</span><span class="sxs-lookup"><span data-stu-id="af83b-127">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="af83b-128">Cette opération génère une signature qui retourne le message de réponse comme la propriété `Result` sur l'objet <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="af83b-128">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="af83b-129">Toutes les valeurs de retour internes sont ensuite des propriétés de l'objet de message de réponse.</span><span class="sxs-lookup"><span data-stu-id="af83b-129">All internal return values are then properties of the response message object.</span></span>  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="af83b-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af83b-130">See Also</span></span>  
 [<span data-ttu-id="af83b-131">Guide pratique pour implémenter une opération de service asynchrone</span><span class="sxs-lookup"><span data-stu-id="af83b-131">How to: Implement an Asynchronous Service Operation</span></span>](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
