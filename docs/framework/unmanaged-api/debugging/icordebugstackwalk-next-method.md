---
title: "ICorDebugStackWalk::Next, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk.Next Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a776f215d67c381a1c08416927cabd3ccb40afa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstackwalknext-method"></a>ICorDebugStackWalk::Next, méthode
Déplace le [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objet à l’image suivante.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Next();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Le runtime s’est correctement déroulé le frame suivant (voir Remarques).|  
|E_FAIL|Le `ICorDebugStackWalk` objet n’a pas pu être avancé.|  
|CORDBG_S_AT_END_OF_STACK|La fin de la pile a été atteinte suite à ce déroulement.|  
|CORDBG_E_PAST_END_OF_STACK|Le pointeur de frame est déjà à la fin de la pile. Par conséquent, aucun frame supplémentaire n’est accessible.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Notes  
 Le `Next` méthode avance le `ICorDebugStackWalk` de l’objet au frame appelant seulement si le runtime peut dérouler le frame actuel. Dans le cas contraire, l’objet avance le frame suivant que le runtime est en mesure de dérouler.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugStackWalk, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
