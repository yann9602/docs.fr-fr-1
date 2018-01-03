---
title: ICorDebugController Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController
helpviewer_keywords: ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bde0ef86ff6304c696ad8c68fc81c0a339ed6e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontroller-interface1"></a>ICorDebugController Interface1
Représente une portée, un <xref:System.Diagnostics.Process> ou un <xref:System.AppDomain>, où le contexte d'exécution du code peut être contrôlé.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|Cette méthode est obsolète.|  
|`ICorDebugController::CommitChanges`|Cette méthode est obsolète.|  
|[Continue, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|Reprend l’exécution de threads managés après un appel à [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).|  
|[Detach, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|Détache le débogueur du processus ou domaine d’application.|  
|[EnumerateThreads, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|Obtient un énumérateur pour les threads managés actifs dans le processus.|  
|[HasQueuedCallbacks, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|Obtient une valeur qui indique si des rappels managés sont actuellement en file d’attente pour le thread spécifié.|  
|[IsRunning, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|Obtient une valeur qui indique si les threads dans le processus en cours d’exécution librement.|  
|[SetAllThreadsDebugState, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|Définit l’état de débogage de tous les threads managés dans le processus.|  
|[Stop, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|Effectue un arrêt coopératif sur tous les threads qui exécutent du code managé dans le processus.|  
|[Terminate, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|Termine le processus avec le code de sortie spécifié.|  
  
## <a name="remarks"></a>Notes  
 Si `ICorDebugController` est contrôle un processus, l’étendue inclut tous les threads du processus. Si `ICorDebugController` est contrôle un domaine d’application, la portée inclut uniquement les threads de ce domaine d’application particulier.  
  
> [!NOTE]
>  Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
