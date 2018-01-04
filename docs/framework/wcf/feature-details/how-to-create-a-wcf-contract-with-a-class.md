---
title: "Comment : créer un contrat Windows Communication Foundation à l'aide d'une classe"
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
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 44418d9d7ec88ea5cd340312fd1ebe42ef8d20a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="b8c07-102">Comment : créer un contrat Windows Communication Foundation à l'aide d'une classe</span><span class="sxs-lookup"><span data-stu-id="b8c07-102">How to: Create a Windows Communication Foundation Contract with a Class</span></span>
<span data-ttu-id="b8c07-103">La méthode préconisée pour créer un contrat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] consiste à utiliser une interface.</span><span class="sxs-lookup"><span data-stu-id="b8c07-103">The preferred way of creating a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] contract is by using an interface.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="b8c07-104">[Comment : définir un contrat de Service](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="b8c07-104"> [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span> <span data-ttu-id="b8c07-105">Une autre solution, présentée dans cette rubrique, consiste à créer une classe, à appliquer l'attribut <xref:System.ServiceModel.ServiceContractAttribute> directement sur celle-ci, puis l'attribut <xref:System.ServiceModel.OperationContractAttribute> sur chacune des méthodes de la classe qui font partie du contrat.</span><span class="sxs-lookup"><span data-stu-id="b8c07-105">An alternative, outlined here, is to create a class and then apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the class directly and the <xref:System.ServiceModel.OperationContractAttribute> attribute to each of the methods in the class that are part of the contract.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="b8c07-106">`[ServiceContract]` et `[ServiceContractAttribute]` produisent le même résultat.</span><span class="sxs-lookup"><span data-stu-id="b8c07-106">`[ServiceContract]` and `[ServiceContractAttribute]` do the same thing.</span></span> <span data-ttu-id="b8c07-107">La même chose est vraie pour `[OperationContract]` et `[OperationContractAttribute]`.</span><span class="sxs-lookup"><span data-stu-id="b8c07-107">The same thing it true for `[OperationContract]` and `[OperationContractAttribute]`.</span></span> <span data-ttu-id="b8c07-108">Dans chaque cas le précédent est abrégé pour le dernier.</span><span class="sxs-lookup"><span data-stu-id="b8c07-108">In each case the former is shorthand for the latter.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b8c07-109">contrats de service, consultez [concevoir des contrats de Service](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="b8c07-109"> service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="b8c07-110">Création d'un contrat Windows Communication Foundation à l'aide d'une classe</span><span class="sxs-lookup"><span data-stu-id="b8c07-110">Creating a Windows Communication Foundation contract with a class</span></span>  
  
1.  <span data-ttu-id="b8c07-111">Créez une classe à l'aide de [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C# ou tout autre langage CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="b8c07-111">Create a new class using [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C#, or any other common language runtime language.</span></span>  
  
2.  <span data-ttu-id="b8c07-112">Appliquez la classe <xref:System.ServiceModel.ServiceContractAttribute> à la classe.</span><span class="sxs-lookup"><span data-stu-id="b8c07-112">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the class.</span></span>  
  
3.  <span data-ttu-id="b8c07-113">Créez des méthodes dans la classe.</span><span class="sxs-lookup"><span data-stu-id="b8c07-113">Create methods in the class.</span></span>  
  
4.  <span data-ttu-id="b8c07-114">Appliquez la classe <xref:System.ServiceModel.OperationContractAttribute> à chaque méthode qui doit être exposée dans le cadre du contrat public [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b8c07-114">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8c07-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="b8c07-115">Example</span></span>  
 <span data-ttu-id="b8c07-116">L'exemple de code suivant présente une classe qui définit un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="b8c07-116">The following code example shows a class that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <span data-ttu-id="b8c07-117">Les méthodes auxquelles la classe <xref:System.ServiceModel.OperationContractAttribute> est appliquée utilisent un modèle de message demande-réponse par défaut.</span><span class="sxs-lookup"><span data-stu-id="b8c07-117">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b8c07-118">Ce modèle de message, consultez [Comment : créer un contrat demande-réponse](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="b8c07-118"> this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="b8c07-119">Vous pouvez également créer et utiliser d’autres modèles de message en définissant les propriétés de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="b8c07-119">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="b8c07-120">Pour plus d’exemples, consultez [Comment : créer un contrat unidirectionnel](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) et [Comment : créer un contrat Duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="b8c07-120">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8c07-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8c07-121">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
