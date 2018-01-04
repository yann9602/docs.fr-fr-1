---
title: ICLRTask, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask
helpviewer_keywords: ICLRTask interface [.NET Framework hosting]
ms.assetid: b3a44df3-578a-4451-b55e-70c8e7695f5e
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6fcce85e56abae561b05364a925fdb6b55825669
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtask-interface"></a>ICLRTask, interface
Fournit des méthodes qui permettent à l’hôte pour effectuer des demandes du common language runtime (CLR), ou pour fournir une notification au CLR sur la tâche associée.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Abort, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-abort-method.md)|Demande que le CLR abandonne la tâche qui en cours `ICLRTask` représente l’instance.|  
|[ExitTask, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)|Notifie le CLR que la tâche associée actuel `ICLRTask` instance se termine et tente de se fermer correctement.|  
|[GetMemStats, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)|Obtient des informations statistiques sur l’utilisation des ressources mémoire par la tâche représentée par le `ICLRTask` instance.|  
|[LocksHeld, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-locksheld-method.md)|Obtient le nombre de verrous actuellement maintenus sur la tâche.|  
|[NeedsPriorityScheduling, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-needspriorityscheduling-method.md)|Obtient une valeur indiquant si l’hôte doit attribuer une priorité élevée à la replanification de la tâche représentée par le `ICLRTask` instance.|  
|[Reset, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-reset-method.md)|Informe le CLR que l’hôte a terminé une tâche et permet au Runtime de réutiliser l’actuel `ICLRTask` instance pour représenter une autre tâche.|  
|[RudeAbort, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-rudeabort-method.md)|Provoque le CLR abandonner la tâche représentée par le `ICLRTask` instance immédiatement, sans garantie que les finaliseurs seront exécutées.|  
|[SetTaskIdentifier, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)|Définit un identificateur unique pour la tâche représentée par le `ICLRTask` instance, à utiliser dans le débogage.|  
|[SwitchIn, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchin-method.md)|Notifie le CLR que la tâche est représentée par le `ICLRTask` instance est dans un état opérationnel.|  
|[SwitchOut, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)|Notifie le CLR que la tâche est représentée par le `ICLRTask` instance n’est plus dans un état opérationnel.|  
|[YieldTask, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-yieldtask-method.md)|Demande que le CLR mette le temps processeur disponible pour les autres tâches. Le CLR ne garantit pas que la tâche sera mises dans un état où elle peut générer des temps de traitement.|  
  
## <a name="remarks"></a>Notes  
 Un `ICLRTask` est la représentation sous forme d’une tâche pour le CLR. À tout moment pendant l’exécution de code, une tâche peut être décrite comme en cours d’exécution ou en attente d’exécution. L’hôte appelle la `ICLRTask::SwitchIn` méthode pour informer le CLR que la tâche qui en cours `ICLRTask` instance représente est maintenant en état de fonctionnement. Après un appel à `ICLRTask::SwitchIn`, l’hôte peut planifier la tâche sur n’importe quel thread de système d’exploitation, sauf dans les cas où le runtime requiert affinité de thread, tel que spécifié par les appels à la [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md) et [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md) méthodes. Quelques instants plus tard, le système d’exploitation peut décider de supprimer la tâche à partir du thread et de placer dans un état non-en cours d’exécution. Par exemple, cela peut se produire chaque fois que la tâche bloque sur les primitives de synchronisation ou attend la fin des opérations d’e/s. L’hôte appelle [SwitchOut](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md) pour notifier le CLR que la tâche est représentée par le `ICLRTask` instance n’est plus dans un état opérationnel.  
  
 Généralement, une tâche se termine à la fin de l’exécution de code. À ce stade, l’hôte appelle `ICLRTask::ExitTask` à détruire associé `ICLRTask`. Toutefois, les tâches peuvent également être recyclées en à l’aide d’un appel à `ICLRTask::Reset`, ce qui permet la `ICLRTask` instance à utiliser à nouveau. Cette approche évite la surcharge de manière répétée la création et la destruction des instances.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [ICLRTask2, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
