---
title: "Fonctionnalit&#233;s de s&#233;curit&#233; avec des liaisons personnalis&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
caps.latest.revision: 11
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 11
---
# Fonctionnalit&#233;s de s&#233;curit&#233; avec des liaisons personnalis&#233;es
Vous pouvez effectuer la plupart des tâches de sécurité courantes en utilisant l'une des liaisons fournies par le système.Toutefois, si vous avez besoin de plus de contrôle, vous pouvez créer une liaison personnalisée à l'aide de <xref:System.ServiceModel.Channels.SecurityBindingElement>, comme expliqué dans les rubriques suivantes.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les liaisons personnalisées, consultez [Liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## Dans cette section  
 [Modes d'authentification SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 Décrit les modes d'authentification possibles avec une liaison personnalisée.  
  
 [Comment : créer une liaison personnalisée à l'aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 Décrit les étapes de base pour créer une liaison personnalisée avec un élément de sécurité.  
  
 [Comment : créer un SecurityBindingElement pour un mode d'authentification spécifié](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 Décrit comment créer un élément de sécurité pour un mode d'authentification spécifié.  
  
 [Comment : désactiver des sessions sécurisées sur une classe WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 Décrit comment désactiver des sessions sécurisées lors de la création d'un service FS.  
  
 [Comment : activer la détection de relecture des messages](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 Décrit comment déterminer le moment où une attaque par relecture se produit.  
  
 [Comment : créer une information d'identification de prise en charge](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 Décrit comment fournir des informations d'identification de prise en charge à un service, si ce dernier en a besoin.  
  
 [Comment : configurer une confirmation de signature](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 Décrit les étapes permettant de confirmer des signatures lors de la signature numérique de messages.  
  
 [Comment : définir une inclinaison de l'horloge maximale](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 Décrit comment définir la différence de temps maximale autorisée entre un service et un client.  
  
 [Comment : désactiver le chiffrement des signatures numériques](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 Décrit les avantages de la désactivation du chiffrement des signatures numériques en matière de performances.  
  
## Référence  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## Rubriques connexes  
 [Fonctionnement des niveaux de protection](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [Sécurisation des services et des clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## Voir aussi  
 [Liaisons et sécurité](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)   
 [Vue d'ensemble de la sécurité](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [Liaisons fournies par le système](../../../../docs/framework/wcf/system-provided-bindings.md)