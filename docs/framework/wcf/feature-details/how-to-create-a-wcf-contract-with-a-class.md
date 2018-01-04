---
title: "Comment : créer un contrat Windows Communication Foundation à l'aide d'une classe"
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
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 44418d9d7ec88ea5cd340312fd1ebe42ef8d20a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>Comment : créer un contrat Windows Communication Foundation à l'aide d'une classe
La méthode préconisée pour créer un contrat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] consiste à utiliser une interface. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Comment : définir un contrat de Service](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md). Une autre solution, présentée dans cette rubrique, consiste à créer une classe, à appliquer l'attribut <xref:System.ServiceModel.ServiceContractAttribute> directement sur celle-ci, puis l'attribut <xref:System.ServiceModel.OperationContractAttribute> sur chacune des méthodes de la classe qui font partie du contrat.  
  
> [!WARNING]
>  `[ServiceContract]` et `[ServiceContractAttribute]` produisent le même résultat. La même chose est vraie pour `[OperationContract]` et `[OperationContractAttribute]`. Dans chaque cas le précédent est abrégé pour le dernier.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]contrats de service, consultez [concevoir des contrats de Service](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>Création d'un contrat Windows Communication Foundation à l'aide d'une classe  
  
1.  Créez une classe à l'aide de [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C# ou tout autre langage CLR (Common Language Runtime).  
  
2.  Appliquez la classe <xref:System.ServiceModel.ServiceContractAttribute> à la classe.  
  
3.  Créez des méthodes dans la classe.  
  
4.  Appliquez la classe <xref:System.ServiceModel.OperationContractAttribute> à chaque méthode qui doit être exposée dans le cadre du contrat public [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant présente une classe qui définit un contrat de service.  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 Les méthodes auxquelles la classe <xref:System.ServiceModel.OperationContractAttribute> est appliquée utilisent un modèle de message demande-réponse par défaut. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Ce modèle de message, consultez [Comment : créer un contrat demande-réponse](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Vous pouvez également créer et utiliser d’autres modèles de message en définissant les propriétés de l’attribut. Pour plus d’exemples, consultez [Comment : créer un contrat unidirectionnel](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) et [Comment : créer un contrat Duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
