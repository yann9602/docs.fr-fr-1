---
title: IDefinitionIdentity, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDefinitionIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IDefinitionIdentity
helpviewer_keywords: IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a63436f107a2604fd5620854339447a4af254e52
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="idefinitionidentity-interface"></a>IDefinitionIdentity, interface
Représente la signature unique du code qui définit l’application dans la portée actuelle.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|Obtient un pointeur d’interface vers un nouveau `IDefinitionIdentity` objet qui est identique à ce `IDefinitionIdentity`, à l’exception des modifications d’attribut spécifiées.|  
|`IDefinitionIdentity::EnumAttributes`|Obtient un pointeur d’interface vers un [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) objet qui contient les attributs associés à ce `IDefinitionIdentity`.|  
|`IDefinitionIdentity::GetAttribute`|Obtient la valeur de l’attribut avec le nom spécifié dans l’espace de noms spécifié.|  
|`IDefinitionIdentity::SetAttribute`|Définit l’attribut qui porte le nom spécifié dans l’espace de noms spécifié à la valeur spécifiée.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Isolation.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
