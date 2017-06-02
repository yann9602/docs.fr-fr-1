---
title: "Sessions s&#233;curis&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
caps.latest.revision: 14
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 14
---
# Sessions s&#233;curis&#233;es
Les sessions fiables sont l'une des fonctionnalités de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ; elles garantissent que les messages sont reçus dans l'ordre dans lequel ils ont été envoyés.Les rubriques de cette section traitent des implications de sécurité à considérer lors de la création d'une session fiable.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les sessions fiables, consultez [Utilisation de sessions](../../../../docs/framework/wcf/using-sessions.md).  
  
> [!NOTE]
>  Lorsque l'emprunt d'identité est requis sur Windows XP, utilisez une session sécurisée sans jeton de contexte de sécurité avec état \(SCT\).Lorsque des SCT avec état sont utilisés avec l'emprunt d'identité, une <xref:System.InvalidOperationException> est levée.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Scénarios non pris en charge](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## Dans cette section  
  
|||  
|-|-|  
|[Conversations sécurisées et sessions sécurisées](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|Les termes « conversations sécurisées » et « sessions sécurisées » sont synonymes.Cette rubrique explique le fonctionnement d'une conversation sécurisée et quand et pourquoi utiliser le modèle.|  
|[Comment : créer une session sécurisée](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|Présente les étapes essentielles de la création d'une session sécurisée.|  
|[Procédure : créer un jeton de contexte de sécurité pour une session sécurisée](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|Présente les étapes nécessaires à la création d'une batterie de serveurs Web qui maintiendra l'état et les sessions avec les clients.|  
|[Considérations sur la sécurité pour les sessions sécurisées](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|Décrit des considérations spéciales relatives aux sessions sécurisées.|  
  
## Référence  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## Rubriques connexes  
 [Sessions, instanciation et accès concurrentiel](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [Conception et implémentation de services](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## Voir aussi  
 [Comment : activer la détection de relecture des messages](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)   
 [Attaques par relecture](../../../../docs/framework/wcf/feature-details/replay-attacks.md)   
 [Comment : créer un service qui requiert des sessions](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)