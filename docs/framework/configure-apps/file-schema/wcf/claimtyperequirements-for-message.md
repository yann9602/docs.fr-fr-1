---
title: '&lt;claimTypeRequirements&gt; de &lt;message&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 158aad6a6a11bb889df74e1222a8881a1c38803f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltclaimtyperequirementsgt-for-ltmessagegt"></a><span data-ttu-id="f36f9-102">&lt;claimTypeRequirements&gt; de &lt;message&gt;</span><span class="sxs-lookup"><span data-stu-id="f36f9-102">&lt;claimTypeRequirements&gt; for &lt;message&gt;</span></span>
<span data-ttu-id="f36f9-103">Spécifie une collection de types de revendications requis.</span><span class="sxs-lookup"><span data-stu-id="f36f9-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="f36f9-104">La collection est utilisée par le service pour spécifier toutes les revendications obligatoires et facultatives qui doivent se trouver dans le jeton émis que le client utilise pour accéder au service.</span><span class="sxs-lookup"><span data-stu-id="f36f9-104">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="f36f9-105">Le service expose les types de revendication obligatoires dans les métadonnées si la publication WSDL est activée mais WCF ne requiert pas que le jeton émis contienne les types de revendication spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f36f9-105">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="f36f9-106">Les services qui souhaitent appliquer l'obligation de présence des types de revendication obligatoires doivent le faire à l'aide de la stratégie d'autorisation.</span><span class="sxs-lookup"><span data-stu-id="f36f9-106">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="f36f9-107">Sur les clients fédérés, cette collection contient la liste des revendications obligatoires et facultatives envoyée au service d’émission de jeton de sécurité dans la demande de jeton émis du client.</span><span class="sxs-lookup"><span data-stu-id="f36f9-107">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f36f9-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f36f9-108">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
