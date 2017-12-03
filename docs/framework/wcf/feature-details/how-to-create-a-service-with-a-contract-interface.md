---
title: "Comment : créer un service avec une interface de contrat"
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
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2cf3938f96674b07a7938861e217a93babd83101
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a><span data-ttu-id="2e951-102">Comment : créer un service avec une interface de contrat</span><span class="sxs-lookup"><span data-stu-id="2e951-102">How to: Create a Service with a Contract Interface</span></span>
<span data-ttu-id="2e951-103">La méthode préconisée pour créer un contrat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] consiste à utiliser une interface.</span><span class="sxs-lookup"><span data-stu-id="2e951-103">The preferred way to create a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] contract is by using an interface.</span></span> <span data-ttu-id="2e951-104">Ce contrat spécifie la collection et la structure des messages requis pour accéder aux opérations offertes par le service.</span><span class="sxs-lookup"><span data-stu-id="2e951-104">This contract specifies the collection and structure of messages required to access the operations the service offers.</span></span> <span data-ttu-id="2e951-105">Cette interface définit les types d'entrée et de sortie en appliquant la classe <xref:System.ServiceModel.ServiceContractAttribute> à l'interface et la classe <xref:System.ServiceModel.OperationContractAttribute> aux méthodes que vous souhaitez exposer.</span><span class="sxs-lookup"><span data-stu-id="2e951-105">This interface defines the input and output types by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface and the <xref:System.ServiceModel.OperationContractAttribute> class to the methods that you want to expose.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="2e951-106">contrats de service, consultez [concevoir des contrats de Service](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="2e951-106"> service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a><span data-ttu-id="2e951-107">Création d'un contrat WCF avec une interface</span><span class="sxs-lookup"><span data-stu-id="2e951-107">Creating a WCF contract with an interface</span></span>  
  
1.  <span data-ttu-id="2e951-108">Créez une interface à l'aide de [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C# ou tout autre langage CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="2e951-108">Create a new interface using [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C#, or any other common language runtime language.</span></span>  
  
2.  <span data-ttu-id="2e951-109">Appliquez la classe <xref:System.ServiceModel.ServiceContractAttribute> à l'interface.</span><span class="sxs-lookup"><span data-stu-id="2e951-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
3.  <span data-ttu-id="2e951-110">Définissez les méthodes dans l'interface.</span><span class="sxs-lookup"><span data-stu-id="2e951-110">Define the methods in the interface.</span></span>  
  
4.  <span data-ttu-id="2e951-111">Appliquez la classe <xref:System.ServiceModel.OperationContractAttribute> à chaque méthode qui doit être exposée dans le cadre du contrat public [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e951-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e951-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="2e951-112">Example</span></span>  
 <span data-ttu-id="2e951-113">L'exemple de code suivant présente une interface qui définit un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="2e951-113">The following code example shows an interface that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <span data-ttu-id="2e951-114">Les méthodes auxquelles la classe <xref:System.ServiceModel.OperationContractAttribute> est appliquée utilisent un modèle de message demande-réponse par défaut.</span><span class="sxs-lookup"><span data-stu-id="2e951-114">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="2e951-115">Ce modèle de message, consultez [Comment : créer un contrat demande-réponse](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="2e951-115"> this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="2e951-116">Vous pouvez également créer et utiliser d’autres modèles de message en définissant les propriétés de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="2e951-116">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="2e951-117">Pour plus d’exemples, consultez [Comment : créer un contrat unidirectionnel](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) et [Comment : créer un contrat Duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="2e951-117">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e951-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e951-118">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
