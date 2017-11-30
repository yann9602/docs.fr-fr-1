---
title: "ICorDebugController::HasQueuedCallbacks, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.HasQueuedCallbacks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 81830cbadcf9fb359b8e1a74cd47f9d18543c29c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a>ICorDebugController::HasQueuedCallbacks, méthode
Obtient une valeur qui indique si des rappels managés sont actuellement en file d’attente pour le thread spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pThread`  
 [in] Pointeur vers un objet « ICorDebugThread » qui représente le thread.  
  
 `pbQueued`  
 [out] Un pointeur vers une valeur qui est `true` si des rappels managés sont actuellement en file d’attente pour le thread spécifié ; sinon, `false`.  
  
 Si null est spécifié pour le `pThread` paramètre, `HasQueuedCallbacks` retournera `true` s’il n’y rappels managés en file d’attente pour n’importe quel thread.  
  
## <a name="remarks"></a>Remarques  
 Les rappels sont distribués un par un, chaque fois [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) est appelée. Le débogueur peut contrôler cet indicateur si elle souhaite créer un rapport de plusieurs événements de débogage qui se produisent simultanément.  
  
 Lorsque les événements de débogage sont en attente, ils ont déjà eu lieu, donc le débogueur doit vider la file d’attente entière pour vous assurer de l’état de l’élément débogué. (Appeler `ICorDebugController::Continue` pour vider la file d’attente.) Par exemple, si la file d’attente contient deux événements de débogage sur le thread *X*, et le débogueur suspend le thread *X* après le premier événement de débogage, puis appelle `ICorDebugController::Continue`, le deuxième événement de débogage pour thread *X* sera distribué bien que le thread a été suspendu.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 
