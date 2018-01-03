---
title: "ICorDebugManagedCallback2::CreateConnection, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.CreateConnection
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e0037f72e51683e5b1d62ad7ecb9aa185f53370
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2createconnection-method"></a>ICorDebugManagedCallback2::CreateConnection, méthode
Notifie le débogueur qu’une nouvelle connexion a été créée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pProcess`  
 [in] Un pointeur vers un objet « ICorDebugProcess » qui représente le processus dans lequel la connexion a été créée.  
  
 `dwConnectionId`  
 [in] L’ID de la nouvelle connexion.  
  
 `pConnName`  
 [in] Pointeur vers le nom de la nouvelle connexion.  
  
## <a name="remarks"></a>Notes  
 A `CreateConnection` rappel sera déclenché dans les cas suivants :  
  
-   Lorsqu’un débogueur est attaché à un processus qui contient les connexions. Dans ce cas, le runtime génère et distribuer un `CreateConnection` événement et un [ICorDebugManagedCallback2::ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) événement pour chaque connexion dans le processus.  
  
-   Lorsqu’un hôte appelle [ICLRDebugManager::BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) dans les [API d’hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugManagedCallback2, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
