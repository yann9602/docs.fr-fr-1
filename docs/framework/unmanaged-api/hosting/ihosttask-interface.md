---
title: IHostTask, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask
helpviewer_keywords: IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbffe2a171c112d4e9650b2c1b2a9ce1f010f382
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttask-interface"></a>IHostTask, interface
Fournit des méthodes qui permettent le common language runtime (CLR) pour communiquer avec l’hôte pour gérer les tâches.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Alert, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|Demande que l’hôte réactive la tâche représentée par le `IHostTask` de l’instance, donc la tâche peut être annulée.|  
|[GetPriority, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|Obtient le niveau de priorité de thread de la tâche représentée par le `IHostTask` instance.|  
|[Join, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|Bloque la tâche appelante jusqu'à ce que la tâche représentée par le `IHostTask` fin de l’instance, l’intervalle de temps spécifié est dépassé, ou [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) est appelée.|  
|[SetCLRTask, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|Associe un [ICLRTask (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance avec actuel `IHostTask` instance.|  
|[SetPriority, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|Le niveau de demande que l’hôte ajuste la priorité de thread de la tâche représentée par le `IHostTask` instance.|  
|[Start, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|Demande que l’hôte déplace la tâche représentée par le `IHostTask` instance à partir d’un état suspendu à un état actif, dans lequel le code peut être exécuté.|  
  
## <a name="remarks"></a>Notes  
 Le CLR appelle les méthodes définies par `IHostTask` pour démarrer une tâche, définir sa priorité de thread niveau, et ainsi de suite.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRTask, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
