---
title: "Comment : créer un contrat unidirectionnel"
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
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f93247a96501359bcda8d2956308e6570c597f93
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-one-way-contract"></a><span data-ttu-id="e82b5-102">Comment : créer un contrat unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="e82b5-102">How to: Create a One-Way Contract</span></span>
<span data-ttu-id="e82b5-103">Cette rubrique décrit les étapes de base pour créer des méthodes qui utilisent un contrat unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="e82b5-103">This topic shows the basic steps to create methods that use a one-way contract.</span></span> <span data-ttu-id="e82b5-104">De telles méthodes appellent des opérations sur un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] à partir d'un client mais n'attendent pas de réponse.</span><span class="sxs-lookup"><span data-stu-id="e82b5-104">Such methods invoke operations on a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service from a client but do not expect a reply.</span></span> <span data-ttu-id="e82b5-105">Ce type de contrat peut être utilisé, par exemple, pour publier des notifications destinées à de nombreux abonnés.</span><span class="sxs-lookup"><span data-stu-id="e82b5-105">This type of contract can be used, for example, to publish notifications to many subscribers.</span></span> <span data-ttu-id="e82b5-106">Vous pouvez également utiliser des contrats unidirectionnels lors de la création d'un contrat duplex (bidirectionnel), qui autorise des clients et des serveurs à communiquer l'un l'autre indépendamment, afin qu'ils puissent initialiser des appels.</span><span class="sxs-lookup"><span data-stu-id="e82b5-106">You can also use one-way contracts when creating a duplex (two-way) contract, which allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="e82b5-107">Notamment, cela peut permettre au serveur d'effectuer des appels unidirectionnels au client, que le client peut traiter en tant qu'événements.</span><span class="sxs-lookup"><span data-stu-id="e82b5-107">This can allow, in particular, the server to make one-way calls to the client that the client can treat as events.</span></span> <span data-ttu-id="e82b5-108">Pour plus d'informations à propos de la spécification de méthodes unidirectionnelles, consultez la propriété <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> et la classe <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e82b5-108">For detailed information about specifying one-way methods, see the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property and the <xref:System.ServiceModel.OperationContractAttribute> class.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e82b5-109">Création d’une application cliente pour un contrat duplex, consultez [Comment : accéder aux Services avec unidirectionnel et contrats demande-réponse](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="e82b5-109"> creating a client application for a duplex contract, see [How to: Access Services with One-Way and Request-Reply Contracts](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md).</span></span> <span data-ttu-id="e82b5-110">Pour obtenir un exemple fonctionnel, consultez le [unidirectionnel](../../../../docs/framework/wcf/samples/one-way.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="e82b5-110">For a working sample, see the [One-Way](../../../../docs/framework/wcf/samples/one-way.md) sample.</span></span>  
  
### <a name="to-create-a-one-way-contract"></a><span data-ttu-id="e82b5-111">Pour créer un contrat unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="e82b5-111">To create a one-way contract</span></span>  
  
1.  <span data-ttu-id="e82b5-112">Créez le contrat de service en appliquant la classe <xref:System.ServiceModel.ServiceContractAttribute> à l'interface qui définit les méthodes que le service doit implémenter.</span><span class="sxs-lookup"><span data-stu-id="e82b5-112">Create the service contract by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface that defines the methods the service is to implement.</span></span>  
  
2.  <span data-ttu-id="e82b5-113">Indiquez les méthodes qu'un client peut appeler dans l'interface en appliquant la classe <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e82b5-113">Indicate which methods in the interface a client can invoked by applying the <xref:System.ServiceModel.OperationContractAttribute> class to them.</span></span>  
  
3.  <span data-ttu-id="e82b5-114">Désignez des opérations qui ne doivent avoir aucune sortie (aucune valeur de retour et aucun paramètre ref ou de sortie) en tant qu'unidirectionnelles en affectant à la propriété <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="e82b5-114">Designate operations that must have no output (no return value and no out or ref parameters) as one-way by setting the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true`.</span></span> <span data-ttu-id="e82b5-115">Notez que les opérations qui retiennent la classe <xref:System.ServiceModel.OperationContractAttribute> satisfont un contrat de demande-réponse par défaut parce que la propriété <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> est par défaut `false`.</span><span class="sxs-lookup"><span data-stu-id="e82b5-115">Note that the operations that carry the <xref:System.ServiceModel.OperationContractAttribute> class satisfy a request-reply contract by default because the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property is `false` by default.</span></span> <span data-ttu-id="e82b5-116">Vous devez donc spécifier explicitement la valeur `true` pour la propriété d'attribut si vous souhaitez un contrat unidirectionnel pour la méthode.</span><span class="sxs-lookup"><span data-stu-id="e82b5-116">So you must explicitly specify the value of the attribute property to be `true` if you want a one-way contract for the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e82b5-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="e82b5-117">Example</span></span>  
 <span data-ttu-id="e82b5-118">L'exemple de code suivant définit un contrat pour un service qui inclut plusieurs méthodes unidirectionnelles.</span><span class="sxs-lookup"><span data-stu-id="e82b5-118">The following code example defines a contract for a service that includes several one-way methods.</span></span> <span data-ttu-id="e82b5-119">Toutes les méthodes ont des contrats unidirectionnels sauf `Equals`, qui a comme valeur par défaut la demande-réponse et retourne un résultat.</span><span class="sxs-lookup"><span data-stu-id="e82b5-119">All of the methods have one-way contracts except `Equals`, which defaults to request-reply and returns a result.</span></span>  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e82b5-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e82b5-120">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="e82b5-121">Conception et implémentation de services</span><span class="sxs-lookup"><span data-stu-id="e82b5-121">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [<span data-ttu-id="e82b5-122">Guide pratique pour définir un contrat de service</span><span class="sxs-lookup"><span data-stu-id="e82b5-122">How to: Define a Service Contract</span></span>](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [<span data-ttu-id="e82b5-123">Session</span><span class="sxs-lookup"><span data-stu-id="e82b5-123">Session</span></span>](../../../../docs/framework/wcf/samples/session.md)  
 [<span data-ttu-id="e82b5-124">Comment : créer un contrat Duplex</span><span class="sxs-lookup"><span data-stu-id="e82b5-124">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
