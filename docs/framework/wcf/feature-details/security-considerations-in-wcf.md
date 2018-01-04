---
title: "Considérations relatives à la sécurité dans WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
caps.latest.revision: "49"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f35bd56bdc69f8c57a7e46984778051b57b7a06a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="8f8a1-102">Considérations relatives à la sécurité dans WCF</span><span class="sxs-lookup"><span data-stu-id="8f8a1-102">Security Considerations in WCF</span></span>
<span data-ttu-id="8f8a1-103">Les rubriques de cette section répertorient différents éléments relatifs à la sécurité à prendre en compte lors de la conception d'une application [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f8a1-103">The topics in this section list various security-related items to consider when designing a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8f8a1-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8f8a1-104">In This Section</span></span>  
 [<span data-ttu-id="8f8a1-105">Divulgation d’informations</span><span class="sxs-lookup"><span data-stu-id="8f8a1-105">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 <span data-ttu-id="8f8a1-106">Traite des diverses manières dont les informations peuvent être divulguées ou attaquées, et de la manière de limiter ce risque.</span><span class="sxs-lookup"><span data-stu-id="8f8a1-106">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="8f8a1-107">Élévation de privilèges</span><span class="sxs-lookup"><span data-stu-id="8f8a1-107">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 <span data-ttu-id="8f8a1-108">Traite des conséquences de l'attribution à un intrus d'autorisations plus étendues celles accordées initialement, et de la manière de limiter ce risque.</span><span class="sxs-lookup"><span data-stu-id="8f8a1-108">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="8f8a1-109">Déni de service</span><span class="sxs-lookup"><span data-stu-id="8f8a1-109">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 <span data-ttu-id="8f8a1-110">Traite de ce qui arrive lorsqu'un système ne peut pas traiter des messages convenablement, et de la manière de limiter ce risque.</span><span class="sxs-lookup"><span data-stu-id="8f8a1-110">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="8f8a1-111">Falsification</span><span class="sxs-lookup"><span data-stu-id="8f8a1-111">Tampering</span></span>](../../../../docs/framework/wcf/feature-details/tampering.md)  
 <span data-ttu-id="8f8a1-112">Traite de la modification des messages ou de la remise des messages, et de la manière de limiter ce risque.</span><span class="sxs-lookup"><span data-stu-id="8f8a1-112">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="8f8a1-113">Attaques par relecture</span><span class="sxs-lookup"><span data-stu-id="8f8a1-113">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 <span data-ttu-id="8f8a1-114">Traite de ce qui arrive lorsqu'un intrus copie un flux de messages entre deux correspondants et relit le flux à l'un des correspondants ou les deux, et de la manière de limiter ce risque.</span><span class="sxs-lookup"><span data-stu-id="8f8a1-114">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="8f8a1-115">Considérations sur la sécurité pour les sessions sécurisées</span><span class="sxs-lookup"><span data-stu-id="8f8a1-115">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="8f8a1-116">Traite des éléments suivants qui affectent la sécurité lors de l'implémentation de sessions sécurisées.</span><span class="sxs-lookup"><span data-stu-id="8f8a1-116">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="8f8a1-117">Scénarios non pris en charge</span><span class="sxs-lookup"><span data-stu-id="8f8a1-117">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 <span data-ttu-id="8f8a1-118">Répertorie différents scénarios qui ne prennent pas en charge un aspect particulier de la sécurité et qui doivent être évités ou pris en compte.</span><span class="sxs-lookup"><span data-stu-id="8f8a1-118">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8f8a1-119">Référence</span><span class="sxs-lookup"><span data-stu-id="8f8a1-119">Reference</span></span>  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="8f8a1-120">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="8f8a1-120">Related Sections</span></span>  
 [<span data-ttu-id="8f8a1-121">Aide sur la sécurité et bonnes pratiques</span><span class="sxs-lookup"><span data-stu-id="8f8a1-121">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="8f8a1-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f8a1-122">See Also</span></span>  
 [<span data-ttu-id="8f8a1-123">Sécurité</span><span class="sxs-lookup"><span data-stu-id="8f8a1-123">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
