---
title: "Comment : autoriser des demandes de métadonnées au cours de l'autorisation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b388a7517dbab8d30df51bfffac0058ded04bda
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a>Comment : autoriser des demandes de métadonnées au cours de l'autorisation
Pendant l'autorisation personnalisée, il peut être nécessaire d'autoriser le traitement d'une demande de métadonnées. La rubrique suivante présente les étapes de validation d'une telle demande.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] autorisation, consultez [autorisation](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
### <a name="to-allow-metadata-requests-during-authorization"></a>Pour autoriser les demandes de métadonnées pendant l'autorisation  
  
1.  Créez une extension de la classe <xref:System.ServiceModel.ServiceAuthorizationManager>.  
  
2.  Remplacez la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>. La méthode retourne la valeur `true` ou `false` selon que l'autorisation est accordée ou non. Les informations relatives à la procédure en cours se trouvent dans le <xref:System.ServiceModel.OperationContext> passé comme paramètre à la méthode.  
  
3.  Dans la substitution, vérifiez le nom de contrat, l'espace de noms et l'action comme illustré dans l'exemple suivant. Si les conditions sont valides, retournez `true.`  
  
4.  Utilisez le point d'extensibilité pour employer la classe. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Comment : créer un gestionnaire d’autorisation personnalisé pour un Service](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre une substitution de la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>.  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [Autorisation](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Gestion des revendications et autorisation avec le modèle d’identité](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
