---
title: "EMemoryAvailable, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EMemoryAvailable
api_location: mscoree.dll
api_type: COM
f1_keywords: EMemoryAvailable
helpviewer_keywords: EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c378f2cd9b033e578ff15472a10a6dc295ad6539
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ememoryavailable-enumeration"></a>EMemoryAvailable, énumération
Contient des valeurs qui indiquent la quantité de mémoire physique disponible sur l’ordinateur. Ces valeurs mappent logiquement aux événements de haute et basse mémoire retournée à partir de la `CreateMemoryResourceNotification` fonction dans l’API Win32.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|Beaucoup de mémoire physique est disponible.|  
|`eMemoryAvailableLow`|Très peu de mémoire physique est disponible.|  
|`eMemoryAvailableNeutral`|La mémoire physique disponible est neutre.|  
  
## <a name="remarks"></a>Remarques  
 Cette valeur est passée par l’hôte pour le common language runtime (CLR) en utilisant un appel à la [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
