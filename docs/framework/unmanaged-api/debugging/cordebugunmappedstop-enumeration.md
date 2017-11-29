---
title: "CorDebugUnmappedStop, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugUnmappedStop
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugUnmappedStop
helpviewer_keywords: CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e75c827533a921c4cab31b2e8b0996dffa532fe2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugunmappedstop-enumeration"></a>CorDebugUnmappedStop, énumération
Spécifie le type de code non mappé qui peut déclencher un arrêt dans l'exécution du code par l'exécution pas à pas.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugUnmappedStop {  
    STOP_NONE               = 0x0,  
    STOP_PROLOG             = 0x01,  
    STOP_EPILOG             = 0x02,  
    STOP_NO_MAPPING_INFO    = 0x04,  
    STOP_OTHER_UNMAPPED     = 0x08,  
    STOP_UNMANAGED          = 0x10,  
    STOP_ALL                = 0xffff,  
} CorDebugUnmappedStop;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`STOP_NONE`|N’arrêtez pas dans n’importe quel type de code non mappé.|  
|`STOP_PROLOG`|Arrêter dans le code de prologue.|  
|`STOP_EPILOG`|Arrêter dans le code d’épilogue.|  
|`STOP_NO_MAPPING_INFO`|Arrêter dans le code qui ne possède aucune information de mappage.|  
|`STOP_OTHER_UNMAPPED`|Arrêter dans le code non mappé qui ne tient pas dans le prologue, épilogue, informations de mappage non ou catégorie non managé.|  
|`STOP_UNMANAGED`|Arrêter en code non managé. Cette valeur est valide uniquement avec le débogage d’interopérabilité.|  
|`STOP_ALL`|Arrêter tous les types de code non mappé.|  
  
## <a name="remarks"></a>Remarques  
 Utilisez le [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) pour définir les indicateurs qui spécifient le code non mappé dans lequel l’exécution pas à pas s’arrête.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
