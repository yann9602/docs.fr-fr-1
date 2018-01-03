---
title: "ICorDebugThread4::HadUnhandledException, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread4.HadUnhandledException Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a79d06f0a65facfbaa821d3dd6af547fd3d0305
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread4hadunhandledexception-method"></a>ICorDebugThread4::HadUnhandledException, méthode
Indique si le thread a déjà eu une exception non gérée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppBlockingObjectEnum`  
 [out] Un pointeur vers l’adresse d’une énumération ordonnée de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Le thread a eu une exception non gérée depuis sa création.|  
|S_FALSE|Le thread n’a jamais eu une exception non gérée.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode indique si le thread a déjà eu une exception non gérée. Au moment où le rappel d’exception non gérée est déclenché ou JIT natif est initialisé, cette méthode retourne toujours S_OK. Il n’existe aucune garantie que les [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) méthode retournera l’exception non gérée ; Toutefois, il est si le processus n’a pas encore repris après avoir obtenu le rappel d’exception non gérée, ou à le JIT natif. En outre, il est possible (bien que peu probable) d’avoir plusieurs threads avec une exception non gérée au moment JIT natif est déclenchée. Dans ce cas il n’existe aucun moyen pour déterminer quelle exception a déclenché le JIT.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugThread4, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
