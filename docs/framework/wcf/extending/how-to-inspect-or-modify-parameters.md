---
title: "Comment : inspecter ou modifier des paramètres"
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
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f1a0ef31ba074082e4c3aa8a26e6a59502a7566
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-inspect-or-modify-parameters"></a><span data-ttu-id="53c47-102">Comment : inspecter ou modifier des paramètres</span><span class="sxs-lookup"><span data-stu-id="53c47-102">How to: Inspect or Modify Parameters</span></span>
<span data-ttu-id="53c47-103">Vous pouvez inspecter ou modifier les messages entrants ou sortants d'une seule opération sur un objet client [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ou un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en implémentant l'interface <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> et en l'insérant dans l'exécution du client ou du service.</span><span class="sxs-lookup"><span data-stu-id="53c47-103">You can inspect or modify the incoming or outgoing messages for a single operation on a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client object or a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service by implementing the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface and inserting it into the client or service runtime.</span></span> <span data-ttu-id="53c47-104">En général, un comportement d'opération est utilisé pour ajouter des inspecteurs de paramètre pour une seule opération ; d'autres comportements peuvent être utilisés pour fournir un accès aisé à l'exécution à une échelle plus grande.</span><span class="sxs-lookup"><span data-stu-id="53c47-104">Typically an operation behavior is used to add parameter inspectors for a single operation; other behaviors can be used to provide easy access to the runtime at a greater scope.</span></span> <span data-ttu-id="53c47-105">Pour plus d’informations, consultez [étendant les Clients](../../../../docs/framework/wcf/extending/extending-clients.md) et [extension des répartiteurs](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="53c47-105">For more information, see [Extending Clients](../../../../docs/framework/wcf/extending/extending-clients.md) and [Extending Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span></span>  
  
### <a name="inspecting-or-modifying-parameters"></a><span data-ttu-id="53c47-106">Inspection ou modification de paramètres</span><span class="sxs-lookup"><span data-stu-id="53c47-106">Inspecting or Modifying Parameters</span></span>  
  
1.  <span data-ttu-id="53c47-107">Implémentez l'interface <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="53c47-107">Implement the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface.</span></span>  
  
2.  <span data-ttu-id="53c47-108">Implémentez un <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (en fonction de la portée requise) pour ajouter votre inspecteur de paramètre aux propriétés <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="53c47-108">Implement a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (depending upon the required scope) to add your parameter inspector to either the <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> or <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> properties.</span></span>  
  
3.  <span data-ttu-id="53c47-109">Insérez votre comportement avant d'appeler <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> ou la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> sur <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="53c47-109">Insert your behavior prior to calling <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="53c47-110">Pour plus d’informations, consultez [configuration et l’extension de l’exécution des comportements](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="53c47-110">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="53c47-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="53c47-111">Example</span></span>  
 <span data-ttu-id="53c47-112">Les exemples de code suivants affichent, dans l'ordre :</span><span class="sxs-lookup"><span data-stu-id="53c47-112">The following code examples show, in order:</span></span>  
  
-   <span data-ttu-id="53c47-113">Une implémentation de l'inspecteur de paramètre</span><span class="sxs-lookup"><span data-stu-id="53c47-113">A parameter inspector implementation.</span></span>  
  
-   <span data-ttu-id="53c47-114">L'implémentation de comportement qui insère l'inspecteur de paramètre à l'aide de <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> et <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="53c47-114">The behavior implementation that inserts the parameter inspector using a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, and an <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="53c47-115">Un fichier de configuration qui charge et exécute le comportement de point de terminaison dans une application cliente pour insérer l'inspecteur de paramètre sur le client</span><span class="sxs-lookup"><span data-stu-id="53c47-115">A configuration file that loads and runs the endpoint behavior in a client application to insert the parameter inspector on the client.</span></span>  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a><span data-ttu-id="53c47-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53c47-116">See Also</span></span>  
 [<span data-ttu-id="53c47-117">Configuration et extension de l’exécution à l’aide de comportements</span><span class="sxs-lookup"><span data-stu-id="53c47-117">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
