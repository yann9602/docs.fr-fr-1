---
title: "ICorDebugVirtualUnwinder::Next, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61f7e5afc65019f1817b15ae84ca3f7b42e3ece9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvirtualunwindernext-method"></a>ICorDebugVirtualUnwinder::Next, méthode
Avance jusqu'au contexte de l'appelant.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Next();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` en cas de réussite du déroulement ou `CORDBG_S_AT_END_OF_STACK` si le déroulement ne peut pas être effectué étant donné qu'il ne reste plus de frames.  
  
 Si un HRESULT indiquant un échec est retourné, les API ICorDebug retournent `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Notes  
 L'explorateur de pile doit vérifier sa progression vers l'avant. Ainsi, un appel à `Next` doit retourner un HRESULT indiquant un échec ou `CORDBG_S_AT_END_OF_STACK`. Retour de `S_OK` indéfiniment peut provoquer une boucle infinie.  
  
> [!NOTE]
>  Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugMemoryBuffer, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
