---
title: "ICLRTask::Reset, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.Reset
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c50dc4770665e2b049f41a105b58231221b8e9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskreset-method"></a>ICLRTask::Reset, méthode
Informe le common language runtime (CLR) que l’hôte a terminé une tâche et permet au Runtime de réutiliser l’actuel [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance pour représenter une autre tâche.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `fFull`  
 [in] `true`, si le runtime doit réinitialiser toutes les valeurs statiques liées au thread en plus de la sécurité et les paramètres régionaux relatives à actuel `ICLRTask` instance ; sinon, `false`.  
  
 Si la valeur est `true`, le runtime réinitialise les données stockées à l’aide de <xref:System.Threading.Thread.AllocateDataSlot%2A> ou <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`Reset`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel. avec succès|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.|  
|E_FAIL|Une défaillance grave et inconnue s’est produite. Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  
 Le CLR peut recycler précédemment créé `ICLRTask` instances afin d’éviter la surcharge de la création de nouvelles instances à plusieurs reprises chaque fois qu’il a besoin d’une nouvelle tâche. L’hôte active cette fonction en appelant `ICLRTask::Reset` au lieu de [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) lorsqu’il a terminé une tâche. La liste suivante résume le cycle de vie normal d’une `ICLRTask` instance :  
  
1.  Le runtime crée un nouveau `ICLRTask` instance.  
  
2.  Le runtime appelle [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) pour obtenir une référence à la tâche hôte actuelle.  
  
3.  Le runtime appelle [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) à associer la nouvelle instance de la tâche de l’hôte.  
  
4.  La tâche s’exécute et se termine.  
  
5.  L’hôte détruit la tâche en appelant `ICLRTask::ExitTask`.  
  
 `Reset`modifie ce scénario de deux façons. À l’étape 5 ci-dessus, l’hôte appelle `Reset` pour réinitialiser la tâche à un état propre, puis découple le `ICLRTask` instance à partir de son associé [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance. Si vous le souhaitez, l’hôte peut également mettre en cache le `IHostTask` instance pour une réutilisation. Dans l’étape 1 ci-dessus, le runtime extrait un recyclage `ICLRTask` à partir du cache au lieu de créer une nouvelle instance.  
  
 Cette approche fonctionne bien lorsque l’hôte dispose également d’un pool de tâches de travail réutilisables. Lorsque l’hôte détruit l’une de ses `IHostTask` instances, elle détruit correspondant `ICLRTask` en appelant `ExitTask`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRTask (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
