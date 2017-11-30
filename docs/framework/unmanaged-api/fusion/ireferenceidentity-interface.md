---
title: IReferenceIdentity, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IReferenceIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IReferenceIdentity
helpviewer_keywords: IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 35c6152836adf02d541bacd149ed9ac053765ba6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity, interface
Représente une référence à la signature unique d’un objet de code.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|Obtient un pointeur d’interface vers un nouveau `IReferenceIdentity` instance qui est identique à ce `IReferenceIdentity`, à l’exception des modifications d’attribut spécifiées.|  
|`IReferenceIdentity::EnumAttributes`|Obtient un pointeur d’interface vers un `IEnumIDENTITY_ATTRIBUTE` instance qui contient les attributs associés à ce `IReferenceIdentity`.|  
|`IReferenceIdentity::GetAttribute`|Obtient la valeur de l’attribut dans l’espace de noms spécifié, avec le nom spécifié.|  
|`IReferenceIdentity::SetAttribute`|Définit l’attribut qui possède l’espace de noms et le nom spécifié à la valeur spécifiée.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Isolation.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IEnumIDENTITY_ATTRIBUTE (Interface)](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
