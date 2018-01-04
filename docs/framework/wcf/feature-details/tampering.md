---
title: Falsification
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ee041de1a9e009ca68ecc8bba8bc2fa06ba6ca3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="tampering"></a><span data-ttu-id="9353a-102">Falsification</span><span class="sxs-lookup"><span data-stu-id="9353a-102">Tampering</span></span>
<span data-ttu-id="9353a-103">*Falsification* est le fait de modifier un message, ou la remise d’un message et à l’aide de ce message modifié à un usage autre que celles prévues pour.</span><span class="sxs-lookup"><span data-stu-id="9353a-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="9353a-104">Ne pas désactiver WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="9353a-104">Do Not Disable WS-Addressing</span></span>  
 <span data-ttu-id="9353a-105">La spécification WS-Addressing fournit des en-têtes d'adresse sur chaque message, ce qui permet au destinataire d'un message de vérifier l'expéditeur de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="9353a-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="9353a-106">Vous pouvez désactiver cette fonctionnalité en affectant <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> à la propriété <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="9353a-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="9353a-107">Si le mode de sécurité a la valeur Message et que WS-Addressing est désactivé, un intrus peut prendre la demande d'un client et l'envoyer à un autre service, le deuxième service n'ayant aucun moyen de détecter que le message est provenu du client d'origine.</span><span class="sxs-lookup"><span data-stu-id="9353a-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="9353a-108">En effet, le premier service peut prétendre qu'il est un client lorsqu'il parle au deuxième service.</span><span class="sxs-lookup"><span data-stu-id="9353a-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="9353a-109">Pour atténuer ce risque, n'affectez jamais <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> à la propriété <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> et évitez d'utiliser <xref:System.ServiceModel.Channels.MessageVersion>, tel que la propriété statique <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A>, qui affecte <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> à la propriété <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="9353a-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9353a-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9353a-110">See Also</span></span>  
 [<span data-ttu-id="9353a-111">Considérations relatives à la sécurité</span><span class="sxs-lookup"><span data-stu-id="9353a-111">Security Considerations</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [<span data-ttu-id="9353a-112">Divulgation d’informations</span><span class="sxs-lookup"><span data-stu-id="9353a-112">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [<span data-ttu-id="9353a-113">Élévation de privilèges</span><span class="sxs-lookup"><span data-stu-id="9353a-113">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [<span data-ttu-id="9353a-114">Déni de service</span><span class="sxs-lookup"><span data-stu-id="9353a-114">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [<span data-ttu-id="9353a-115">Scénarios non pris en charge</span><span class="sxs-lookup"><span data-stu-id="9353a-115">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [<span data-ttu-id="9353a-116">Attaques par relecture</span><span class="sxs-lookup"><span data-stu-id="9353a-116">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
