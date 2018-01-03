---
title: "CorDebugJITCompilerFlagsDeprecated, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugJITCompilerFlagsDeprecated
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugJITCompilerFlagsDeprecated
helpviewer_keywords: CorDebugJITCompilerFlagsDeprecated enumeration [.NET Framework debugging]
ms.assetid: af15e2ca-6be1-472b-bd36-03644a1e3ddd
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4cb7836ec572a5c9df4e6a52fce1cefd02d647f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugjitcompilerflagsdeprecated-enumeration"></a>CorDebugJITCompilerFlagsDeprecated, énumération
Cette énumération est obsolète. Utilisez le `CORDEBUG_JIT_DEFAULT` membre de la [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) énumération à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugJITCompilerFlagsDeprecated {  
    CORDEBUG_JIT_TRACK_DEBUG_INFO  = 0x1  
} CorDebugJITCompilerFlagsDeprecated;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`CORDEBUG_JIT_TRACK_DEBUG_INFO`|Utilisez plutôt `CORDEBUG_JIT_DEFAULT`.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :** 1.0, 1.1  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
