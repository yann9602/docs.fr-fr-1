---
title: COR_ACTIVE_FUNCTION, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_ACTIVE_FUNCTION
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_ACTIVE_FUNCTION
helpviewer_keywords: COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7bb587f485427d9fd88e2f834d844ece18d336ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="coractivefunction-structure"></a>COR_ACTIVE_FUNCTION, structure
Contient des informations sur les fonctions qui sont actuellement actives dans les trames d'un thread. Cette structure est utilisée par le [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`pAppDomain`|Pointeur vers le propriétaire du domaine d’application le `ilOffset` champ.|  
|`pModule`|Pointeur vers le propriétaire du module du `ilOffset` champ.|  
|`pFunction`|Pointeur vers le propriétaire de la fonction de la `ilOffset` champ.|  
|`ilOffset`|L’offset Microsoft intermediate language (MSIL), de l’image.|  
|`flags`|Réservé pour une future extensibilité.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Structures de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
