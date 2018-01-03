---
title: "ICorDebugModule::EnableClassLoadCallbacks, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.EnableClassLoadCallbacks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5aa4add6dcaf662f1b5ec48b1243f012a6ae1f1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a>ICorDebugModule::EnableClassLoadCallbacks, méthode
Contrôle si le [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) et [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) sont appelés pour ce module.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bClassLoadCallbacks`  
 [in] Définissez cette valeur sur `true` pour activer le common language runtime (CLR) pour appeler le `ICorDebugManagedCallback::LoadClass` et `ICorDebugManagedCallback::UnloadClass` méthodes lorsque leurs événements associés se produisent.  
  
 La valeur par défaut est `false` pour les modules non dynamiques. La valeur est toujours `true` pour les modules dynamiques et ne peut pas être modifié.  
  
## <a name="remarks"></a>Notes  
 Le `ICorDebugManagedCallback::LoadClass` et `ICorDebugManagedCallback::UnloadClass` rappels sont toujours activées pour les modules dynamiques et ne peut pas être désactivées.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
    
 
