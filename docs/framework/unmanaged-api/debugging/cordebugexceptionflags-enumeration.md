---
title: "CorDebugExceptionFlags, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugExceptionFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugExceptionFlags
helpviewer_keywords: CorDebugExceptionFlags enumeration [.NET Framework debugging]
ms.assetid: b22687a8-e9cf-4e65-a1b0-f92a81bc524e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b25211c8e7f03cc09e8729abc44af39f0c84259
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugexceptionflags-enumeration"></a>CorDebugExceptionFlags, énumération
Fournit des informations supplémentaires sur une exception.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|Il n'existe pas d'exception.|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|L'exception peut être interceptée.<br /><br /> Le moment où se produit l'exception peut néanmoins être tel que le débogueur ne peut pas l'intercepter. Par exemple, s'il n'existe pas de code managé en dessous du rappel actif ou si l'événement d'exception provient d'un attachement juste-à-temps, l'exception ne peut pas être interceptée.|  
  
## <a name="remarks"></a>Notes  
 De nouvelles valeurs sont susceptibles d'être ajoutées dans les versions ultérieures : il est donc recommandé de préparer du code qui utilise `CorDebugExceptionFlags` pour les valeurs inattendues.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
