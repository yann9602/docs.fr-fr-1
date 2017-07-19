---
title: "Attaques par relecture | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Attaques par relecture
Une *attaque par relecture* se produit lorsqu'un intrus copie un flux de messages entre deux correspondants et relit le flux à l'un ou plusieurs des correspondants.Sauf atténuation, les ordinateurs sujets à l'attaque traitent le flux comme messages légitimes, ce qui a des conséquences néfastes telles que des ordres redondants d'un élément.  
  
## Les liaisons peuvent être soumises aux attaques de réflexion  
 Les *attaques de réflexion* sont des relectures de messages à un expéditeur comme si elles provenaient du destinataire.La *détection de relecture* standard dans le mécanisme [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ne gère pas cela automatiquement.  
  
 Les attaques de réflexion sont atténuées par défaut car le modèle de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ajoute un ID de message signé aux messages de demande et attend un en\-tête `relates-to` signé dans les messages de réponse.Par conséquent, le message de demande ne peut pas être relu en tant que réponse.Dans les scénarios de messages fiables sécurisés, les attaques de réflexion sont atténuées pour les raisons suivantes :  
  
-   Les schémas de séquence de création et de message de réponse de séquence de création sont différents.  
  
-   Pour les séquences simplex, les messages de séquence envoyés par le client ne peuvent pas lui être relus car le client ne peut pas comprendre de tels messages.  
  
-   Pour les séquences duplex, les deux ID de séquence doivent être uniques.Par conséquent, un message de séquence sortant ne peut pas être relu en tant que message de séquence entrant \(tous les en\-têtes et corps de séquence sont également signés\).  
  
 Les seules liaisons susceptibles aux attaques de réflexion sont celles sans WS\-Addressing : des liaisons personnalisées pour lesquelles WS\-Addressing est désactivé et qui utilisent la sécurité basée sur clé symétrique.Le <xref:System.ServiceModel.BasicHttpBinding> n'utilise pas WS\-Addressing par défaut, mais il n'utilise pas la sécurité basée sur clé symétrique d'une manière qui lui permet d'être vulnérable à cette attaque.  
  
 La limitation des risques pour les liaisons personnalisées consiste à ne pas établir de contexte de sécurité ou à requérir des en\-têtes WS\-Addressing.  
  
## Batterie de serveurs Web : l'intrus relit la demande à plusieurs nœuds  
 Un client utilise un service implémenté sur une batterie de serveurs Web.Un intrus relit une demande qui a été envoyée à un nœud de la ferme à un autre nœud de la ferme.De plus, si un service est redémarré, le cache de relecture est vidé, ce qui permet à un intrus de relire la demande.\(Le cache contient des valeurs de signature de message utilisées et vues précédemment et il empêche toute relecture ; ces signatures ne peuvent donc être utilisées qu'une seule fois.Les caches de relecture ne sont pas partagés dans une batterie de serveurs Web.\)  
  
 Les solutions d'atténuation des risques sont les suivantes :  
  
-   Utilisez la sécurité de mode de message avec des jetons de contexte de sécurité avec état \(avec ou sans la conversation sécurisée activée\).[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Procédure : créer un jeton de contexte de sécurité pour une session sécurisée](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
-   Configurez le service pour utiliser la sécurité de niveau transport.  
  
## Voir aussi  
 [Considérations relatives à la sécurité](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)   
 [Divulgation d'informations](../../../../docs/framework/wcf/feature-details/information-disclosure.md)   
 [Élévation de privilège](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)   
 [Refus de service](../../../../docs/framework/wcf/feature-details/denial-of-service.md)   
 [Falsification](../../../../docs/framework/wcf/feature-details/tampering.md)   
 [Scénarios non pris en charge](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)