---
title: "CorDebugStateChange, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugStateChange
api_location: mscordbi.dll
api_type: COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da9d2bb793340aa4736e0b26ab9bf9d5ec7c546a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugstatechange-enumeration"></a>CorDebugStateChange, énumération
Représente la quantité de données mises en cache à ignorer sur la base des modifications apportées au processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugStateChange  
{  
    PROCESS_RUNNING = 0x0000001,   
    FLUSH_ALL       = 0x0000002,   
} CorDebugStateChange;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`PROCESS_RUNNING`|Le processus a atteint un nouvel état de mémoire via l'exécution en avant.|  
|`SET_CONTEXT_FLAG_UNWIND_FRAME`|La mémoire du processus peut être arbitrairement différente de ce qu'elle était précédemment.|  
  
## <a name="remarks"></a>Notes  
 Un membre de la `CorDebugStateChange` énumération est fournie en tant qu’argument quand le débogueur appelle la [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) (méthode)  
  
> [!NOTE]
>  Cette énumération est destinée à une utilisation dans des scénarios de débogage .NET Native uniquement.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
