---
title: "Fonctionnalités de sécurité avec des liaisons personnalisées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 2f26e68b9654ccd565328003596e324558f7505f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="security-capabilities-with-custom-bindings"></a>Fonctionnalités de sécurité avec des liaisons personnalisées
Vous pouvez effectuer la plupart des tâches de sécurité courantes en utilisant l’une des liaisons fournies par le système. Toutefois, si vous avez besoin de plus de contrôle, vous pouvez créer une liaison personnalisée à l'aide de <xref:System.ServiceModel.Channels.SecurityBindingElement>, comme expliqué dans les rubriques suivantes. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]liaisons personnalisées, consultez [des liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Modes d’authentification SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 Décrit les modes d’authentification possibles avec une liaison personnalisée.  
  
 [Guide pratique pour créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 Décrit les étapes de base pour créer une liaison personnalisée avec un élément de sécurité.  
  
 [Guide pratique pour créer un SecurityBindingElement pour un mode d’authentification spécifié](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 Décrit comment créer un élément de sécurité pour un mode d'authentification spécifié.  
  
 [Guide pratique pour désactiver des sessions sécurisées sur une classe WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 Décrit comment désactiver des sessions sécurisées lors de la création d'un service FS.  
  
 [Guide pratique pour activer la détection de relecture des messages](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 Décrit comment déterminer le moment où une attaque par relecture se produit.  
  
 [Guide pratique pour créer une information d’identification de prise en charge](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 Décrit comment fournir des informations d'identification de prise en charge à un service, si ce dernier en a besoin.  
  
 [Guide pratique pour configurer une confirmation de signature](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 Décrit les étapes permettant de confirmer des signatures lors de la signature numérique de messages.  
  
 [Guide pratique pour définir une variation d’horloge maximale](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 Décrit comment définir la différence de temps maximale autorisée entre un service et un client.  
  
 [Guide pratique pour désactiver le chiffrement des signatures numériques](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 Décrit les avantages de la désactivation du chiffrement des signatures numériques en matière de performances.  
  
## <a name="reference"></a>Référence  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Présentation du niveau de protection](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [Sécurisation des services et des clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Liaisons et sécurité](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [Vue d’ensemble de la sécurité](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Liaisons fournies par le système](../../../../docs/framework/wcf/system-provided-bindings.md)
