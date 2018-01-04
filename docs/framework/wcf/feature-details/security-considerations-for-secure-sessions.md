---
title: "Considérations sur la sécurité pour les sessions sécurisées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d5be591-9a7b-4a6f-a906-95d3abafe8db
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: be460249ed877b2f67f2d153c2aea4a3cc4d2b37
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="security-considerations-for-secure-sessions"></a>Considérations sur la sécurité pour les sessions sécurisées
Vous devez tenir compte des éléments suivants qui affectent la sécurité lors de l'implémentation de sessions sécurisées. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Considérations sur la sécurité, consultez [considérations de sécurité](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md) et [meilleures pratiques pour la sécurité](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
## <a name="secure-sessions-and-metadata"></a>Sessions sécurisées et métadonnées  
 Lorsqu'une session sécurisée est établie et que la propriété <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> a la valeur `false`, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] envoie une assertion `mssp:MustNotSendCancel` dans le cadre des métadonnées du document WSDL (Web Services Description Language) du point de terminaison de service. L'assertion `mssp:MustNotSendCancel` informe les clients que le service ne répond pas aux demandes d'annulation de session sécurisée. Lorsque la propriété <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> a la valeur `true`, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'envoie pas d'assertion `mssp:MustNotSendCancel` dans le cadre du document WSDL. Lorsqu'ils n'ont plus besoin de la session sécurisée, les clients doivent envoyer une demande d'annulation au service. Lorsqu’un client est généré à l’aide de la [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), le code client réagit en conséquence à la présence ou l’absence de la `mssp:MustNotSendCancel` assertion.  
  
## <a name="secure-conversations-and-custom-tokens"></a>Conversations sécurisées et jetons personnalisés  
 Le mélange de jetons personnalisés et de clés dérivées pose quelques problèmes en raison de la manière dont il est défini dans la spécification WS-SecureConversation. La spécification indique que `wsse:SecurityTokenReference` est un élément facultatif qui référence le jeton dérivé : «`/wsc:DerivedKeyToken/wsse:SecurityTokenReference` cet élément facultatif est utilisé pour spécifier le jeton de contexte de sécurité, de jeton de sécurité ou de clé/secret partagé utilisé pour la dérivation. Si cet élément n'est pas spécifié, il est supposé que le destinataire peut déterminer la clé partagée à partir du contexte de message. Si le contexte ne peut pas être déterminé, puis une erreur telle que `wsc:UnknownDerivationSource` doit être déclenché. »  
  
 Cela signifie que si vous souhaitez qu'un jeton personnalisé soit dérivé, vous devez encapsuler son type de clause dans un élément `SecurityTokenReference`. Il est possible de désactiver la dérivation mais la valeur par défaut consiste à dériver les clés. Si vous ne parvenez pas à encapsuler la clé, la sérialisation du jeton de clé dérivé aboutit, mais la tentative de désérialisation de ce jeton lève une exception.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour désactiver des sessions sécurisées sur une classe WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 [Considérations relatives à la sécurité](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Bonnes pratiques pour la sécurité](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)
