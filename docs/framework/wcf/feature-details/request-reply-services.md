---
title: "Services demande-r&#233;ponse | Microsoft Docs"
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
  - "contrats (WCF), services demande-réponse"
  - "contrats demande-réponse (WCF)"
  - "WCF (WCF), services demande-réponse"
  - "Windows Communication Foundation (WCF), services demande-réponse"
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Services demande-r&#233;ponse
Les services demande\-réponse sont le type de contrat d'opération par défaut dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].Les clients effectuent des appels aux opérations de service et attendent une réponse du service.Vous pouvez effectuer des appels à une opération de service de façon synchrone \(le client se bloque jusqu'à ce qu'il reçoive une réponse du service ou que l'appel expire\) ou de façon asynchrone \(le client effectue un appel à l'opération de service, continue à fonctionner et reçoit la réponse du service sur un autre thread\).  
  
 Pour créer un contrat de service demande\-réponse, définissez votre contrat de service et appliquez la classe <xref:System.ServiceModel.OperationContractAttribute> à chaque opération, tel qu'indiqué dans l'exemple de code suivant.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
  
```  
  
 Il n'est pas nécessaire d'affecter `false` à la propriété <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>car il s'agit du comportement par défaut.  
  
## Voir aussi  
 [Services monodirectionnels](../../../../docs/framework/wcf/feature-details/one-way-services.md)   
 [Services duplex](../../../../docs/framework/wcf/feature-details/duplex-services.md)