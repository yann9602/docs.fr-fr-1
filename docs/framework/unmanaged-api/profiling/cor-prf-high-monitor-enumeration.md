---
title: "COR_PRF_MODULE_FLAGS, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1df931796b32b6bea49e8b69da02d39e6a4803e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="corprfhighmonitor-enumeration"></a>COR_PRF_MODULE_FLAGS, énumération
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Fournit des indicateurs en plus de celles disponibles dans le [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) énumération que le profileur peut spécifier à la [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) méthode lors de son chargement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES     = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED     = 0x00000002,     
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE       = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH      = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE           = 0  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|Aucun indicateur n'est défini.|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|Contrôles du [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) rappel pour l’ajout de références d’assembly durant le parcours de fermeture de référence assembly CLR.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|Contrôles du [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) rappel des mises à jour dans le flux de symbole associé à un module en mémoire.|  
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui requièrent des images à profil optimisé. Il correspond à la `COR_PRF_REQUIRE_PROFILE_IMAGE` indicateur dans le [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) énumération.|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui peuvent être définis une fois que le profileur est attaché à une application en cours d'exécution.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui peuvent être définis uniquement lors de l'initialisation. Les tentatives de modification d'un ou plusieurs de ces indicateurs autre part génèrent une valeur `HRESULT`, qui indique un échec.|  
  
## <a name="remarks"></a>Remarques  
 Le `COR_PRF_HIGH_MONITOR` indicateurs sont utilisés avec la `pdwEventsHigh` paramètre de la [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) et [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) méthodes.  
  
 En commençant par le [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)], la valeur de la `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` est passée de 0 à `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0 x 00000002).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 [COR_PRF_MONITOR, énumération](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 [Icorprofilerinfo5, Interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
