---
title: IDefinitionAppId, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDefinitionAppId
api_location: fusion.dll
api_type: COM
f1_keywords: IDefinitionAppId
helpviewer_keywords: IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 247edbe300bbb93ddbdd4260109999fd33b08006
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId, interface
Représente un identificateur unique pour le code qui définit l’application dans la portée actuelle.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|Obtient une chaîne mise en forme qui représente le code dans cette `IDefinitionAppId` objet.|  
|`IDefinitionAppId::put_Codebase`|Définit le code de ce `IDefinitionAppId` mis en forme de l’objet spécifié à la valeur de chaîne.|  
|`IDefinitionAppId::EnumAppPath`|Obtient un pointeur d’interface vers un [IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) objet qui contient les assemblys dans le chemin d’accès d’application actuel.|  
|`IDefinitionAppId::SetAppPath`|Définit le chemin d’accès de l’application pour l’assembly dans la portée actuelle avec la valeur référencée par le [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) objet.|  
|`IDefinitionAppId::get_SubscriptionId`|Obtient un pointeur vers une représentation sous forme de chaîne de l’identificateur de jeton pour un abonnement à cette `IDefinitionAppId` objet.|  
|`IDefinitionAppId::put_SubscriptionId`|Définit l’identificateur de jeton pour un abonnement à cette `IDefinitionAppId` objet à la valeur de chaîne spécifiée.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Isolation.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
