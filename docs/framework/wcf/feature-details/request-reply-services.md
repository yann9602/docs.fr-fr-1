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
ms.openlocfilehash: 3f60f7b2fadec39ce4a6bec462e81dd8424c15bc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="request-reply-services"></a><span data-ttu-id="2f594-102">Services demande-réponse</span><span class="sxs-lookup"><span data-stu-id="2f594-102">Request-Reply Services</span></span>
<span data-ttu-id="2f594-103">Les services demande-réponse sont le type de contrat d'opération par défaut dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2f594-103">Request-reply services are the default type of operation contract in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="2f594-104">Les clients effectuent des appels aux opérations de service et attendent une réponse du service.</span><span class="sxs-lookup"><span data-stu-id="2f594-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="2f594-105">Vous pouvez effectuer des appels à une opération de service de façon synchrone (le client se bloque jusqu'à ce qu'il reçoive une réponse du service ou que l'appel expire) ou de façon asynchrone (le client effectue un appel à l'opération de service, continue à fonctionner et reçoit la réponse du service sur un autre thread).</span><span class="sxs-lookup"><span data-stu-id="2f594-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="2f594-106">Pour créer un contrat de service demande-réponse, définissez votre contrat de service et appliquez la classe <xref:System.ServiceModel.OperationContractAttribute> à chaque opération, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="2f594-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="2f594-107">Il n'est pas nécessaire d'affecter <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> à la propriété `false`car il s'agit du comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="2f594-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f594-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f594-108">See Also</span></span>  
 [<span data-ttu-id="2f594-109">Services monodirectionnels</span><span class="sxs-lookup"><span data-stu-id="2f594-109">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)  
 [<span data-ttu-id="2f594-110">Services duplex</span><span class="sxs-lookup"><span data-stu-id="2f594-110">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
