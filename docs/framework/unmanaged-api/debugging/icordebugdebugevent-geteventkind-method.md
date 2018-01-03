---
title: "ICorDebugDebugEvent::GetEventKind, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25bb63f1b1fa759cd6d61a71682b803e3320f22d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdebugeventgeteventkind-method"></a>ICorDebugDebugEvent::GetEventKind, méthode
Indique le type d'événement représenté par cet objet `ICorDebugDebugEvent`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pDebugEventKind  
 Un pointeur vers un [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) membre d’énumération qui indique le type d’événement.  
  
## <a name="remarks"></a>Notes  
 En fonction de la valeur de `pDebugEventKind`, vous pouvez appeler `QueryInterface` pour obtenir une interface d'événement de débogage plus précise qui fournit des données supplémentaires.  
  
> [!NOTE]
>  Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugDebugEvent, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
