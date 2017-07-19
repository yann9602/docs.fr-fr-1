---
title: "Consid&#233;rations sur la s&#233;curit&#233; pour les sessions s&#233;curis&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d5be591-9a7b-4a6f-a906-95d3abafe8db
caps.latest.revision: 14
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 14
---
# Consid&#233;rations sur la s&#233;curit&#233; pour les sessions s&#233;curis&#233;es
Vous devez tenir compte des éléments suivants qui affectent la sécurité lors de l'implémentation de sessions sécurisées.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les considérations sur la sécurité, consultez [Considérations relatives à la sécurité](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md) et [Meilleures pratiques pour la sécurité](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
## Sessions sécurisées et métadonnées  
 Lorsqu'une session sécurisée est établie et que la propriété <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> a la valeur `false`, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] envoie une assertion `mssp:MustNotSendCancel` dans le cadre des métadonnées du document WSDL \(Web Services Description Language\) du point de terminaison de service.L'assertion `mssp:MustNotSendCancel` informe les clients que le service ne répond pas aux demandes d'annulation de session sécurisée.Lorsque la propriété <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> a la valeur `true`, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'envoie pas d'assertion `mssp:MustNotSendCancel` dans le cadre du document WSDL.Lorsqu'ils n'ont plus besoin de la session sécurisée, les clients doivent envoyer une demande d'annulation au service.Lorsqu'un client est généré à l'aide de [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), le code client réagit de façon adéquate à la présence ou absence de l'assertion `mssp:MustNotSendCancel`.  
  
## Conversations sécurisées et jetons personnalisés  
 Le mélange de jetons personnalisés et de clés dérivées pose quelques problèmes en raison de la manière dont il est défini dans la spécification WS\-SecureConversation.La spécification indique que `wsse:SecurityTokenReference` est un élément facultatif qui fait référence au jeton dérivé : “`/wsc:DerivedKeyToken/wsse:SecurityTokenReference`. Cet élément facultatif est utilisé pour spécifier le jeton de contexte de sécurité, le jeton de sécurité ou la clé\/le secret partagé utilisé pour la dérivation.Si cet élément n'est pas spécifié, il est supposé que le destinataire peut déterminer la clé partagée à partir du contexte de message.Si le contexte ne peut pas être déterminé, une erreur telle que `wsc:UnknownDerivationSource` doit être déclenchée. »  
  
 Cela signifie que si vous souhaitez qu'un jeton personnalisé soit dérivé, vous devez encapsuler son type de clause dans un élément `SecurityTokenReference`.Il est possible de désactiver la dérivation mais la valeur par défaut consiste à dériver les clés.Si vous ne parvenez pas à encapsuler la clé, la sérialisation du jeton de clé dérivé aboutit, mais la tentative de désérialisation de ce jeton lève une exception.  
  
## Voir aussi  
 [Comment : désactiver des sessions sécurisées sur une classe WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)   
 [Considérations relatives à la sécurité](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)   
 [Meilleures pratiques pour la sécurité](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)