---
title: "Négociation et délais de sécurité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: b4d0b2953a91040c37afe88d9499fd4be1970f31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="69e19-102">Négociation et délais de sécurité</span><span class="sxs-lookup"><span data-stu-id="69e19-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="69e19-103">Lorsque les clients et les services s'authentifient, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] prend en charge un mode qui permet la négociation de leurs informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="69e19-103">When clients and services authenticate, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="69e19-104">Dans un tel cas, un échange potentiellement multi-segment intervient entre le client et le service. Il permet la propagation des informations d'identification du service vers le client.</span><span class="sxs-lookup"><span data-stu-id="69e19-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="69e19-105">La propriété <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> contrôle le délai nécessaire à l'exécution de cet échange.</span><span class="sxs-lookup"><span data-stu-id="69e19-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="69e19-106">Toutefois, ce délai est appliqué uniquement lorsque l'échange nécessite plusieurs demandes-réponses.</span><span class="sxs-lookup"><span data-stu-id="69e19-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="69e19-107">Lorsque la négociation s'effectue en une seule boucle, ce délai n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="69e19-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69e19-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69e19-108">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [<span data-ttu-id="69e19-109">Comment : ensemble une inclinaison d’horloge maximale</span><span class="sxs-lookup"><span data-stu-id="69e19-109">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
