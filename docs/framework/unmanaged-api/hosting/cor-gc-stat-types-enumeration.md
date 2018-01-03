---
title: "COR_GC_STAT_TYPES (énumération)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_STAT_TYPES
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_STAT_TYPES
helpviewer_keywords: COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 86d0ce931518fa50dbd3b0d6d7f2755d19042eca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corgcstattypes-enumeration"></a>COR_GC_STAT_TYPES (énumération)
Spécifie les statistiques à enregistrer pour un garbage collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a>Notes  
 Cette énumération spécifie les statistiques de la [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure doivent être définies par [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) (méthode).  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_GC_COUNTS`|Enregistre le nombre de garbage collections effectués pour chaque génération.|  
|`COR_GC_MEMORYUSAGE`|Enregistrements d’utilisation et l’opération garbage collection taille statistiques de la mémoire.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** GCHost.idl, GCHost.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [COR_GC_STATS, structure](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
