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
# <a name="security-considerations-in-wcf"></a>Considérations relatives à la sécurité dans WCF
Les rubriques de cette section répertorient différents éléments relatifs à la sécurité à prendre en compte lors de la conception d'une application [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [Divulgation d’informations](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 Traite des diverses manières dont les informations peuvent être divulguées ou attaquées, et de la manière de limiter ce risque.  
  
 [Élévation de privilèges](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 Traite des conséquences de l'attribution à un intrus d'autorisations plus étendues celles accordées initialement, et de la manière de limiter ce risque.  
  
 [Déni de service](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 Traite de ce qui arrive lorsqu'un système ne peut pas traiter des messages convenablement, et de la manière de limiter ce risque.  
  
 [Falsification](../../../../docs/framework/wcf/feature-details/tampering.md)  
 Traite de la modification des messages ou de la remise des messages, et de la manière de limiter ce risque.  
  
 [Attaques par relecture](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 Traite de ce qui arrive lorsqu'un intrus copie un flux de messages entre deux correspondants et relit le flux à l'un des correspondants ou les deux, et de la manière de limiter ce risque.  
  
 [Considérations sur la sécurité pour les sessions sécurisées](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)  
 Traite des éléments suivants qui affectent la sécurité lors de l'implémentation de sessions sécurisées.  
  
 [Scénarios non pris en charge](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 Répertorie différents scénarios qui ne prennent pas en charge un aspect particulier de la sécurité et qui doivent être évités ou pris en compte.  
  
## <a name="reference"></a>Référence  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Aide sur la sécurité et bonnes pratiques](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité](../../../../docs/framework/wcf/feature-details/security.md)
