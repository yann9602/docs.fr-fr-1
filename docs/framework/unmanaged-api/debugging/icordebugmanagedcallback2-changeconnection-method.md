---
title: "ICorDebugManagedCallback2::ChangeConnection, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.ChangeConnection
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ba7e84c11f2fc8619b7046e222a742ee3298554
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a>ICorDebugManagedCallback2::ChangeConnection, méthode
Notifie le débogueur que l’ensemble des tâches associées à la connexion spécifiée a changé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pProcess`  
 [in] Pointeur vers un objet « ICorDebugProcess » qui représente le processus contenant la connexion qui a changé.  
  
 `dwConnectionId`  
 [in] ID de la connexion qui a changé.  
  
## <a name="remarks"></a>Notes  
 A `ChangeConnection` rappel sera déclenché dans les cas suivants :  
  
-   Lorsqu’un débogueur est attaché à un processus qui contient les connexions. Dans ce cas, le runtime génère et distribuer un [ICorDebugManagedCallback2::CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) événement et un `ChangeConnection` événement pour chaque connexion dans le processus. A `ChangeConnection` événement est généré pour chaque connexion existante, indépendamment de si l’ensemble de la connexion de tâches a été modifié depuis sa création.  
  
-   Lorsqu’un hôte appelle [ICLRDebugManager::SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) dans les [API d’hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
 Le débogueur doit analyser tous les threads dans le processus pour récupérer les nouvelles modifications.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugManagedCallback2, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
