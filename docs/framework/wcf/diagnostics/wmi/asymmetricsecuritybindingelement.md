---
title: AsymmetricSecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 82e5365a440d103727f354e682d0ebecb5f46a46
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="asymmetricsecuritybindingelement"></a>AsymmetricSecurityBindingElement
AsymmetricSecurityBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe AsymmetricSecurityBindingElement ne définit pas de méthodes.  
  
## <a name="properties"></a>Propriétés  
 La classe AsymmetricSecurityBindingElement a les propriétés suivantes :  
  
### <a name="messageprotectionorder"></a>MessageProtectionOrder  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Ordre de chiffrement et de signature des messages de cette liaison.  
  
### <a name="requiresignatureconfirmation"></a>RequireSignatureConfirmation  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Si la liaison requiert la confirmation de signature.  
  
## <a name="requirements"></a>Configuration requise  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
