---
title: "Comment : créer un service avec une interface de contrat"
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
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 750c3d3371970d93872fd4e4e0814913a408187a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a>Comment : créer un service avec une interface de contrat
La méthode préconisée pour créer un contrat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] consiste à utiliser une interface. Ce contrat spécifie la collection et la structure des messages requis pour accéder aux opérations offertes par le service. Cette interface définit les types d'entrée et de sortie en appliquant la classe <xref:System.ServiceModel.ServiceContractAttribute> à l'interface et la classe <xref:System.ServiceModel.OperationContractAttribute> aux méthodes que vous souhaitez exposer.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]contrats de service, consultez [concevoir des contrats de Service](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a>Création d'un contrat WCF avec une interface  
  
1.  Créez une interface à l'aide de [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C# ou tout autre langage CLR (Common Language Runtime).  
  
2.  Appliquez la classe <xref:System.ServiceModel.ServiceContractAttribute> à l'interface.  
  
3.  Définissez les méthodes dans l'interface.  
  
4.  Appliquez la classe <xref:System.ServiceModel.OperationContractAttribute> à chaque méthode qui doit être exposée dans le cadre du contrat public [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant présente une interface qui définit un contrat de service.  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 Les méthodes auxquelles la classe <xref:System.ServiceModel.OperationContractAttribute> est appliquée utilisent un modèle de message demande-réponse par défaut. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Ce modèle de message, consultez [Comment : créer un contrat demande-réponse](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Vous pouvez également créer et utiliser d’autres modèles de message en définissant les propriétés de l’attribut. Pour plus d’exemples, consultez [Comment : créer un contrat unidirectionnel](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) et [Comment : créer un contrat Duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
