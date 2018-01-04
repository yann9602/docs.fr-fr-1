---
title: "Comment : créer un service qui requiert des sessions"
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
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1fba00b6b8aed8e27d5f16612bb77191f6674abe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="33914-102">Comment : créer un service qui requiert des sessions</span><span class="sxs-lookup"><span data-stu-id="33914-102">How to: Create a Service That Requires Sessions</span></span>
<span data-ttu-id="33914-103">Les sessions créent un état partagé entre deux ou plusieurs points de terminaison activant des fonctionnalités utiles telles que les rappels, la sécurité en cascade et des associations entre clients et instances de service.</span><span class="sxs-lookup"><span data-stu-id="33914-103">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="33914-104">sessions [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] les applications, consultez [à l’aide de Sessions](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="33914-104"> sessions in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] applications, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="33914-105">Pour spécifier qu’un contrat requiert que sa liaison prenne en charge des sessions</span><span class="sxs-lookup"><span data-stu-id="33914-105">To specify that a contract require its binding to support sessions</span></span>  
  
1.  <span data-ttu-id="33914-106">Créez un contrat de service qui contient au moins une opération.</span><span class="sxs-lookup"><span data-stu-id="33914-106">Create a service contract with at least one operation.</span></span> <span data-ttu-id="33914-107">Pour obtenir un exemple montrant comment créer un contrat de service, consultez [Comment : définir un contrat de Service](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="33914-107">For an example of how to create a service contract, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2.  <span data-ttu-id="33914-108">Modifiez le <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> qui déclare le contrat en affectant à la propriété <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> la valeur :</span><span class="sxs-lookup"><span data-stu-id="33914-108">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    -   <span data-ttu-id="33914-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> si ce contrat doit être exécuté dans une session.</span><span class="sxs-lookup"><span data-stu-id="33914-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> if this contract must be run within a session.</span></span>  
  
    -   <span data-ttu-id="33914-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> si ce contrat peut être exécuté dans une session.</span><span class="sxs-lookup"><span data-stu-id="33914-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> if this contract can be run within a session.</span></span>  
  
    -   <span data-ttu-id="33914-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> si ce contrat ne doit pas être exécuté dans une session.</span><span class="sxs-lookup"><span data-stu-id="33914-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> if this contract must not be run within a session.</span></span>  
  
3.  <span data-ttu-id="33914-112">Configurez votre point de terminaison de service pour utiliser une liaison qui prend en charge des sessions.</span><span class="sxs-lookup"><span data-stu-id="33914-112">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="33914-113">L'exemple de configuration suivant montre l'utilisation de <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, qui prend en charge une session de messagerie WS`-`Reliable.</span><span class="sxs-lookup"><span data-stu-id="33914-113">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]   
  
## <a name="example"></a><span data-ttu-id="33914-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="33914-114">Example</span></span>  
 <span data-ttu-id="33914-115">Le code d'exemple suivant indique comment utiliser une spécification de session au niveau du contrat et utiliser un fichier de configuration pour prendre en charge cette spécification avec la liaison <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="33914-115">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)] 
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]      
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]     
  
## <a name="see-also"></a><span data-ttu-id="33914-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33914-116">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>  
 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
