---
title: "ICorDebugManagedCallback::BreakpointSetError, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.BreakpointSetError
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::BreakpointSetError
helpviewer_keywords:
- BreakpointSetError method [.NET Framework debugging]
- ICorDebugManagedCallback::BreakpointSetError method [.NET Framework debugging]
ms.assetid: f2b773a4-c4d0-429c-9717-51d6e2ed86af
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8d8d75261a0ac1211ec54252b698a2a1b17ccac2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a>ICorDebugManagedCallback::BreakpointSetError, méthode
Notifie le débogueur que le common language runtime n’a pas pu lier correctement un point d’arrêt a été défini avant une fonction compilée juste-à-temps (JIT).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pAppDomain`  
 [in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application qui contient le point d’arrêt non lié.  
  
 `pThread`  
 [in] Pointeur vers un objet ICorDebugThread qui représente le thread qui contient le point d’arrêt non lié.  
  
 `pBreakpoint`  
 [in] Pointeur vers un objet ICorDebugBreakpoint qui représente le point d’arrêt non lié.  
  
 `dwError`  
 [in] Entier qui indique l’erreur.  
  
## <a name="remarks"></a>Remarques  
 Le point d’arrêt donné ne sera jamais atteint. Le débogueur doit désactiver et lier de nouveau.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugManagedCallback (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
