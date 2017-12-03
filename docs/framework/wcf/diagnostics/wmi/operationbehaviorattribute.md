---
title: OperationBehaviorAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: da0bc2ac9a4283ec9b23a1d4767f664de071ef47
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute
OperationBehaviorAttribute  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe OperationBehaviorAttribute ne définit pas de méthodes.  
  
## <a name="properties"></a>Propriétés  
 La classe OperationBehaviorAttribute a les propriétés suivantes :  
  
### <a name="autodisposeparameters"></a>AutoDisposeParameters  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 État de la fonctionnalité d'élimination automatique pour les paramètres.  
  
### <a name="impersonation"></a>Emprunt d'identité  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Indique le niveau d'emprunt d'identité de l'appelant pris en charge par l'opération.  
  
### <a name="releaseinstancemode"></a>ReleaseInstanceMode  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Indique à quel moment il convient de recycler l'objet lors de l'appel d'une opération.  
  
### <a name="transactionautocomplete"></a>TransactionAutoComplete  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Indique s'il convient de valider automatiquement la transaction actuelle si aucune exception non traitée ne se produit.  
  
### <a name="transactionscoperequired"></a>TransactionScopeRequired  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Indique si l'opération nécessite une transaction.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
