---
title: Comparaison des transactions dans COM+ et dans ServiceModel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87e3df31060a9c71e0b2868aa34373bca221fa79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>Comparaison des transactions dans COM+ et dans ServiceModel
Cette rubrique explique comment simuler le comportement d'un service COM+ transactionnel à l'aide des attributs [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fournis par l'espace de noms <xref:System.ServiceModel>.  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>Émulation de COM+ à l'aide d'attributs ServiceModel  
 Le tableau suivant compare l'énumération <xref:System.EnterpriseServices.TransactionOption> utilisée pour créer une transaction `EnterpriseServices` et la manière dont elles sont corrélées aux attributs [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournis par l'espace de noms <xref:System.ServiceModel>.  
  
|Attribut COM+|Attributs [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|<xref:System.ServiceModel.TransactionFlowAttribute> a la valeur <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> a la valeur `true`.<br /><br /> L'attribut `TransactionFlow` dans l'élément de liaison a la valeur `false`.|  
|Obligatoire|<xref:System.ServiceModel.TransactionFlowAttribute> a la valeur <xref:System.ServiceModel.TransactionFlowOption.Allowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> a la valeur `true`.<br /><br /> L'attribut `TransactionFlow` dans l'élément de liaison a la valeur `true`.|  
|Pris en charge|Il n'existe pas d'équivalent direct. En général, vous devez à la place adopter le comportement spécifié pour `Required`.|  
|Non pris en charge|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> a la valeur `false`.<br /><br /> L'attribut `TransactionFlow` dans l'élément de liaison a la valeur `false`.|  
|Disabled|Il n'existe pas d'équivalent direct. En général, vous devez à la place adopter le comportement spécifié pour `NotSupported`.|
