---
title: IHostTaskManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager
helpviewer_keywords: IHostTaskManager interface [.NET Framework hosting]
ms.assetid: 4a0b05b9-3ef1-4607-b7c8-bd4dd43647a0
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9573891a2c27a2a92eccd0522f84175effa8037a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanager-interface"></a>IHostTaskManager, interface
Fournit des méthodes qui permettent le common language runtime (CLR) pour travailler avec les tâches via l’hôte au lieu d’utiliser les fonctions de threading ou fiber de système d’exploitation standard.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[BeginDelayAbort, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|Avertit l’hôte que le code managé entre dans une période dans laquelle la tâche en cours ne doit pas être abandonnée.|  
|[BeginThreadAffinity, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|Avertit l’hôte que le code managé entre dans une période dans laquelle la tâche en cours ne doit pas être déplacée vers un autre thread de système d’exploitation.|  
|[CallNeedsHostHook, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|Permet à l’hôte de spécifier si le common language runtime peut inline l’appel spécifié à une fonction non managée.|  
|[CreateTask, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|Demande que l’hôte crée une nouvelle tâche.|  
|[EndDelayAbort, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|Avertit l’hôte que le code managé sort de la période dans laquelle la tâche en cours ne doit pas être abandonnée, à la suite d’un appel précédent à `BeginDelayAbort`.|  
|[EndThreadAffinity, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|Avertit l’hôte que le code managé sort de la période dans laquelle la tâche en cours ne doit pas être déplacée vers un autre thread de système d’exploitation, à la suite d’un appel précédent à `BeginThreadAffinity`.|  
|[EnterRuntime, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|Avertit l’hôte qu’un appel à une méthode non managée, comme un appel de méthode, retourne le contrôle d’exécution au CLR.|  
|[GetCurrentTask, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|Obtient un pointeur d’interface à la tâche en cours d’exécution sur le thread de système d’exploitation à partir de laquelle cet appel est effectué.|  
|[GetStackGuarantee, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|Obtient la quantité d’espace de pile est assuré d’être disponible après qu’une opération de pile se termine, mais avant la fermeture d’un processus.|  
|[LeaveRuntime, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|Avertit l’hôte que le code managé est sur le point d’effectuer un appel à une fonction non managée.|  
|[ReverseEnterRuntime, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|Avertit l’hôte qu’un appel est effectué dans le common language runtime (CLR) à partir de code non managé.|  
|[ReverseLeaveRuntime, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|Avertit l’hôte que le contrôle est en laissant le CLR et une fonction non managée qui a été, à son tour, appelée à partir du code managé.|  
|[SetCLRTaskManager, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|Fournit à l’hôte avec un pointeur d’interface vers un [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implémentée par le CLR.|  
|[SetLocale, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|Avertit l’hôte que le CLR a modifié les paramètres régionaux sur la tâche en cours.|  
|[SetStackGuarantee, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|Réservé à un usage interne uniquement.|  
|[SetUILocale, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|Avertit l’hôte que les paramètres régionaux d’une interface utilisateur a été modifié sur la tâche en cours.|  
|[Sleep, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|Avertit l’hôte que la tâche actuelle est mise en veille.|  
|[SwitchToTask, méthode](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|Avertit l’hôte qu’il doit éliminer la tâche actuelle.|  
  
## <a name="remarks"></a>Notes  
 `IHostTaskManager`permet au CLR créer et gérer des tâches, pour fournir des connexions à l’hôte une action quand le contrôle est transféré du code managé au code non managé et vice versa et de spécifier certaines actions que l’hôte peut et ne peut pas effectuer pendant l’exécution de code.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRTask, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
