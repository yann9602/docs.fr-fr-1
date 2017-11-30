---
title: "ICorDebugManagedCallback::CreateProcess, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.CreateProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bef3140717ff977fbfae813d0de89011b89ed062
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a>ICorDebugManagedCallback::CreateProcess, méthode
Notifie le débogueur lorsqu’un processus a été joint ou démarré pour la première fois.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pProcess`  
 [in] Pointeur vers un objet ICorDebugProcess qui représente le processus qui a été joint ou démarré.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode n’est pas appelée avant l’initialisation du common language runtime. La plupart de la [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) méthodes retourneront CORDBG_E_NOTREADY avant le `CreateProcess` rappel.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugManagedCallback (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
