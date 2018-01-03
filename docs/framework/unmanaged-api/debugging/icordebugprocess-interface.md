---
title: ICorDebugProcess Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess
helpviewer_keywords: ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6fa95d17e7ff6f857765ea2dd48f61b047a47b1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess-interface1"></a>ICorDebugProcess Interface1
Représente un processus qui exécute le code managé. Cette interface est une sous-classe de ICorDebugController.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ClearCurrentException, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|Efface l’exception non managée actuelle sur le thread donné.|  
|[EnableLogMessages, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|Active ou désactive l’envoi de messages de journal au débogueur.|  
|[EnumerateAppDomains, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|Énumère tous les domaines d’application dans le processus.|  
|[EnumerateObjects, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|Non implémenté.|  
|[GetHandle, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|Obtient un handle vers le processus.|  
|[GetHelperThreadID, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|Obtient l’ID de thread de système d’exploitation (OS) pour le thread d’assistance interne du débogueur.|  
|[GetID, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|Obtient l’ID de système d’exploitation (OS) du processus.|  
|[GetObject, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|Non implémenté.|  
|[GetThread, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|Obtient l’instance ICorDebugThread qui a le thread du système d’exploitation spécifié ID.|  
|[GetThreadContext, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|Obtient le contexte pour le thread donné.|  
|[IsOSSuspended, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|Détermine si le thread a été interrompu à la suite du débogueur qui arrête le processus.|  
|[IsTransitionStub, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|Détermine si une adresse est à l’intérieur d’un stub qui provoquera une transition vers du code managé.|  
|[ModifyLogSwitch, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|Définit le niveau de gravité du commutateur de journal spécifié.|  
|[ReadMemory, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|Lit la mémoire du processus.|  
|[SetThreadContext, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|Définit le contexte pour le thread donné.|  
|[ThreadForFiberCookie, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|Obsolète.|  
|[WriteMemory, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|Écrit des données dans une zone de mémoire dans le processus.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebug, interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
