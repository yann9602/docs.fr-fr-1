---
title: "Comment&#160;: cr&#233;er un service avec une interface de contrat | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Comment&#160;: cr&#233;er un service avec une interface de contrat
La méthode préconisée pour créer un contrat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] consiste à utiliser une interface.Ce contrat spécifie la collection et la structure des messages requis pour accéder aux opérations offertes par le service.Cette interface définit les types d'entrée et de sortie en appliquant la classe <xref:System.ServiceModel.ServiceContractAttribute> à l'interface et la classe <xref:System.ServiceModel.OperationContractAttribute> aux méthodes que vous souhaitez exposer.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] les contrats de service, consultez [Conception de contrats de service](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### Création d'un contrat WCF avec une interface  
  
1.  Créez une interface à l'aide de [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C\# ou tout autre langage CLR \(Common Language Runtime\).  
  
2.  Appliquez la classe <xref:System.ServiceModel.ServiceContractAttribute> à l'interface.  
  
3.  Définissez les méthodes dans l'interface.  
  
4.  Appliquez la classe <xref:System.ServiceModel.OperationContractAttribute> à chaque méthode qui doit être exposée dans le cadre du contrat public [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## Exemple  
 L'exemple de code suivant présente une interface qui définit un contrat de service.  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 Les méthodes auxquelles la classe <xref:System.ServiceModel.OperationContractAttribute> est appliquée utilisent un modèle de message demande\-réponse par défaut.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] ce modèle de message, consultez [Comment : créer un contrat demande\-réponse](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).Vous pouvez également créer et utiliser d'autres modèles de message en définissant les propriétés de l'attribut.Pour obtenir d'autres exemples, consultez [Comment : créer un contrat unidirectionnel](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) et [Comment : créer un contrat duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## Voir aussi  
 <xref:System.ServiceModel.ServiceContractAttribute>   
 <xref:System.ServiceModel.OperationContractAttribute>