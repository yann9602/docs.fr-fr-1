---
title: "CorDebugIlToNativeMappingTypes, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugIlToNativeMappingTypes
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugIlToNativeMappingTypes
helpviewer_keywords: CorDebugIIToNativeMappingTypes enumeration [.NET Framework debugging]
ms.assetid: c35e2919-42c3-4ba0-ae28-443c35f66f93
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 03046ebb678df64ad3d151aaadba313645417979
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a>CorDebugIlToNativeMappingTypes, énumération
Indique si une plage particulière d’instructions natives, représentée par une instance de la structure COR_DEBUG_IL_TO_NATIVE_MAP, correspond à une région de code spéciale.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`NO_MAPPING`|La plage d’instructions natives ne correspond pas à n’importe quelle région de code spéciale.|  
|`PROLOG`|La plage d’instructions natives correspond au prologue.|  
|`EPILOG`|La plage d’instructions natives correspond à l’épilogue.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [GetILToNativeMapping, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)  
 [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
