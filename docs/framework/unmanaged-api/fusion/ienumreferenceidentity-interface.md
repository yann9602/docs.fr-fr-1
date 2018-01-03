---
title: IEnumReferenceIdentity, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumReferenceIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumReferenceIdentity
helpviewer_keywords: IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d1af31c72770947c33f358a9689bac6fd95ef53c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ienumreferenceidentity-interface"></a>IEnumReferenceIdentity, interface
Sert d’énumérateur pour une collection de `IReferenceIdentity` objets.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|Obtient un pointeur d’interface vers un nouveau `IEnumReferenceIdentity` qui contient les mêmes membres que ce `IEnumReferenceIdentity`.|  
|`IEnumReferenceIdentity::Next`|Obtient le nombre spécifié de `IReferenceIdentity` objets, en commençant à la position actuelle.|  
|`IEnumReferenceIdentity::Reset`|Déplace le pointeur d’instruction au début de cette `IEnumReferenceIdentity`.|  
|`IEnumReferenceIdentity::Skip`|Déplace le pointeur d’instruction par le nombre spécifié d’éléments, en commençant à la position actuelle.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Isolation.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IReferenceIdentity, interface](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
