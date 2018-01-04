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
ms.workload: dotnet
ms.openlocfilehash: 6fbee18d31cb1774300c14587b0f7d973a4996ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="security-negotiation-and-timeouts"></a>Négociation et délais de sécurité
Lorsque les clients et les services s'authentifient, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] prend en charge un mode qui permet la négociation de leurs informations d'identification. Dans un tel cas, un échange potentiellement multi-segment intervient entre le client et le service. Il permet la propagation des informations d'identification du service vers le client. La propriété <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> contrôle le délai nécessaire à l'exécution de cet échange. Toutefois, ce délai est appliqué uniquement lorsque l'échange nécessite plusieurs demandes-réponses. Lorsque la négociation s'effectue en une seule boucle, ce délai n'est pas utilisé.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [Guide pratique pour définir une variation d’horloge maximale](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
