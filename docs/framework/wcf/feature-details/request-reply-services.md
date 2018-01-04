---
title: "Services demande-réponse"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9e8c01fa3451cbeb335c4771e287566af1c104b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="request-reply-services"></a><span data-ttu-id="ef6b5-102">Services demande-réponse</span><span class="sxs-lookup"><span data-stu-id="ef6b5-102">Request-Reply Services</span></span>
<span data-ttu-id="ef6b5-103">Les services demande-réponse sont le type de contrat d'opération par défaut dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ef6b5-103">Request-reply services are the default type of operation contract in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="ef6b5-104">Les clients effectuent des appels aux opérations de service et attendent une réponse du service.</span><span class="sxs-lookup"><span data-stu-id="ef6b5-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="ef6b5-105">Vous pouvez effectuer des appels à une opération de service de façon synchrone (le client se bloque jusqu’à ce qu’il reçoive une réponse du service ou que l’appel expire) ou de façon asynchrone (le client effectue un appel à l’opération de service, continue à fonctionner et reçoit la réponse du service sur un autre thread).</span><span class="sxs-lookup"><span data-stu-id="ef6b5-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="ef6b5-106">Pour créer un contrat de service demande-réponse, définissez votre contrat de service et appliquez la classe <xref:System.ServiceModel.OperationContractAttribute> à chaque opération, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="ef6b5-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="ef6b5-107">Il n'est pas nécessaire d'affecter <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> à la propriété `false`car il s'agit du comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="ef6b5-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef6b5-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef6b5-108">See Also</span></span>  
 [<span data-ttu-id="ef6b5-109">Services unidirectionnels</span><span class="sxs-lookup"><span data-stu-id="ef6b5-109">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)  
 [<span data-ttu-id="ef6b5-110">Services duplex</span><span class="sxs-lookup"><span data-stu-id="ef6b5-110">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
