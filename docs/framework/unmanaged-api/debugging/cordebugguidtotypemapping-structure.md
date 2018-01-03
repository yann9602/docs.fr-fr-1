---
title: CorDebugGuidToTypeMapping, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: CorDebugGuidToTypeMapping
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugGuidToTypeMapping
helpviewer_keywords: CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecdadc96c0fb850fef13ba978fc97eef91dadd65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugguidtotypemapping-structure"></a>CorDebugGuidToTypeMapping, structure
Mappe un [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID à son objet ICorDebugType correspondant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`iid`|Le GUID de la mise en cache [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.|  
|`pType`|Pointeur vers un objet ICorDebugType qui fournit des informations sur le type de mise en cache.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Structures de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
