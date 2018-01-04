---
title: COR_GC_STATS, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_STATS
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_STATS
helpviewer_keywords: COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02a775be4976760b354a492e7252a67ef04eace9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corgcstats-structure"></a>COR_GC_STATS, structure
Fournit des statistiques sur le mécanisme de garbage collection du common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;   
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;   
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`Flags`|Indique les valeurs de champ doivent être calculées et retournés.|  
|`ExplicitGCCount`|Indique le nombre de garbage collection qui ont été forcés par demande externe.|  
|`GenCollectionsTaken`|Indique le nombre de garbage collections effectué pour chaque génération.|  
|`CommittedKBytes`|Nombre total de kilo-octets validés dans tous les tas.|  
|`ReservedKBytes`|Nombre total de kilo-octets réservés dans tous les tas.|  
|`Gen0HeapSizeKBytes`|La taille, en kilo-octets, du tas de génération zéro.|  
|`Gen1HeapSizeKBytes`|La taille, en kilo-octets, du tas de génération une.|  
|`Gen2HeapSizeKBytes`|La taille, en kilo-octets, du tas de génération deux.|  
|`LargeObjectHeapSizeKBytes`|La taille, en kilo-octets, du tas des objets volumineux.|  
|`KBytesPromotedFromGen0`|La taille, en kilo-octets, des objets promus de la génération zéro à la génération 1.|  
|`KBytesPromotedFromGen1`|La taille, en kilo-octets, des objets promus de la génération 1 à la génération 2.|  
  
## <a name="remarks"></a>Notes  
 Le [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) méthode requiert le `Flags` champ le `COR_GC_STATS` structure soit définie sur une ou plusieurs valeurs de la [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) énumération pour spécifier les les statistiques doivent être définies.  
  
 Le tableau suivant mappe les statistiques fournies par cette structure et les deux [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) des valeurs d’énumération `COR_GC_COUNTS` et `COR_GC_MEMORYUSAGE`.  
  
|Spécifié par COR_GC_COUNTS|Spécifié par COR_GC_MEMORYUSAGE|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 Un exemple de l’utilisation est la suivante :  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** GCHost.idl  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Structures d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [Gestion automatique de la mémoire](../../../../docs/standard/automatic-memory-management.md)  
 [Nettoyage de la mémoire](../../../../docs/standard/garbage-collection/index.md)
