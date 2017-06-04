---
title: "Comment&#160;: autoriser des demandes de m&#233;tadonn&#233;es au cours de l&#39;autorisation | Microsoft Docs"
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
  - "autorisation de demandes de métadonnées au cours de l'autorisation (WCF)"
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Comment&#160;: autoriser des demandes de m&#233;tadonn&#233;es au cours de l&#39;autorisation
Pendant l'autorisation personnalisée, il peut être nécessaire d'autoriser le traitement d'une demande de métadonnées.La rubrique suivante présente les étapes de validation d'une telle demande.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] l'autorisation, consultez [Autorisation](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
### Pour autoriser les demandes de métadonnées pendant l'autorisation  
  
1.  Créez une extension de la classe <xref:System.ServiceModel.ServiceAuthorizationManager>.  
  
2.  Substituez la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>.La méthode retourne la valeur `true` ou `false` selon que l'autorisation est accordée ou non.Les informations relatives à la procédure en cours se trouvent dans le <xref:System.ServiceModel.OperationContext> passé comme paramètre à la méthode.  
  
3.  Dans la substitution, vérifiez le nom de contrat, l'espace de noms et l'action comme illustré dans l'exemple suivant.Si les conditions sont valides, retournez `true.`  
  
4.  Utilisez le point d'extensibilité pour employer la classe.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Comment : créer un gestionnaire d'autorisations personnalisé pour un service](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).  
  
## Exemple  
 L'exemple suivant illustre une substitution de la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>.  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## Voir aussi  
 <xref:System.ServiceModel.ServiceAuthorizationManager>   
 [Autorisation](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)   
 [Gestion des revendications et autorisation avec le modèle d'identité](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)