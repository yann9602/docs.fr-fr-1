---
title: "CorDebugNGenPolicy, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: CorDebugNGenPolicy
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugNGenPolicy
helpviewer_keywords: CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 89767da7178319ed1add3dda0620062893487bfd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugngenpolicy-enumeration"></a>CorDebugNGenPolicy, énumération
Fournit une valeur qui détermine si un débogueur charge les images natives (NGen) depuis le cache d'images natives.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a>Membres  
  
|Nom de membre|Description|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|Dans un [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] application, l’utilisation d’images à partir du cache des images natives locales est désactivée. Dans une application de bureau, ce paramètre n’a aucun effet.|  
  
## <a name="remarks"></a>Notes  
 Le `CorDebugNGENPolicy` énumération est utilisée par le [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) (méthode). La désactivation de l’utilisation d’images à partir du cache des images natives locales fournit une expérience de débogage cohérente en vous assurant que le débogueur charge des images debuggable compilé juste-à la place des images natives optimisées.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
