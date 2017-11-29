---
title: "CorDebugMDAFlags, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugMDAFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugMDAFlags
helpviewer_keywords: CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 827825e4012b421caa4e05702a6f1a1b863ac69d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugmdaflags-enumeration"></a>CorDebugMDAFlags, énumération
Spécifie l'état du thread sur lequel l'Assistant Débogage managé est déclenché.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|Le thread sur lequel l’Assistant Débogage MANAGÉ a été lancé, a glissé depuis l’Assistant Débogage MANAGÉ a été déclenché.|  
  
## <a name="remarks"></a>Remarques  
 Lorsque la pile des appels ne décrit plus où l’Assistant Débogage MANAGÉ a été lancé à l’origine, le thread est considéré comme *glissé*. Il s’agit d’une circonstance exceptionnelle provoquée par l’exécution du thread d’une opération non valide en quittant.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
