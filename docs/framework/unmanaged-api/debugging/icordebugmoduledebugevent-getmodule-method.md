---
title: "ICorDebugModuleDebugEvent::GetModule, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b11ab8991a9f44cf2868474a8a0f6dcc1c3308c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a>ICorDebugModuleDebugEvent::GetModule, méthode
Obtient le module fusionné qui vient d’être chargé ou déchargé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppModule`  
 [out] Pointeur vers l’adresse d’un objet ICorDebugModule qui représente le module fusionné qui vient d’être chargé ou déchargé.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez appeler la [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) méthode pour déterminer si le module a été chargé ou déchargé.  
  
> [!NOTE]
>  Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugModuleDebugEvent, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
