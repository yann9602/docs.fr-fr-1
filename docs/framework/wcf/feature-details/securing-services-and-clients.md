---
title: "S&#233;curisation des services et des clients | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sécurité des messages (WCF)"
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 13
---
# S&#233;curisation des services et des clients
Les informations présentées dans cette section portent sur la programmation de la sécurité dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  En général, l'opération inclut la sélection d'une liaison appropriée fournie par le système, la définition des propriétés de l'élément de sécurité, puis la définition des propriétés des comportements du service qui déterminent la manière dont les informations d'identification sont récupérées pour être utilisées par le service ou le client.  Ces techniques couvrent les conditions de sécurité de la plupart des utilisateurs pour la plupart des scénarios, tel qu'indiqué dans [Scénarios de sécurité courants](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).  Si votre scénario requiert des fonctionnalités supplémentaires, consultez d'abord [Fonctionnalités de sécurité avec des liaisons personnalisées](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md) ; si aucun solution n'est fournie, consultez [Extension de la sécurité](../../../../docs/framework/wcf/extending/extending-security.md).  Si vous créez \(ou interagissez avec\) un système qui utilise des revendications riches, consultez les rubriques dans [Autorisation](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
## Dans cette section  
 [Programmation de la sécurité dans WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 Vue d'ensemble du modèle de programmation utilisé pour sécuriser des messages.  
  
 [Vue d'ensemble de la sécurité des transports](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 Vue d'ensemble de la sécurisation des messages par le biais de la couche transport.  
  
 [Sécurité des messages](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 Récapitule les raisons d'utiliser la sécurité au niveau du message dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
 [Sessions sécurisées](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 Examen des éléments à prendre en compte lors de la sécurisation d'une session [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [Utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 Explication de quelques\-unes des tâches courantes requises lors de l'utilisation de certificats X.509.  
  
## Référence  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## Rubriques connexes  
 [Concepts relatifs à la sécurité](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [Extension de la sécurité](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [Scénarios de sécurité courants](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [Liaisons et sécurité](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [Fonctionnalités de sécurité avec des liaisons personnalisées](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [Extension de la sécurité](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [Autorisation](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## Voir aussi  
 [Programmation WCF de base](../../../../docs/framework/wcf/basic-wcf-programming.md)   
 [Modèle de sécurité pour Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)