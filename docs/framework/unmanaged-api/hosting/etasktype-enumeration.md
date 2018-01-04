---
title: "ETaskType, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ETaskType
api_location: mscoree.dll
api_type: COM
f1_keywords: ETaskType
helpviewer_keywords: ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7973b8cbd49858daaf6f08d55c7d9f60f687a72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="etasktype-enumeration"></a>ETaskType, énumération
Contient des valeurs qui indiquent le type de tâche est représentée par une [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) ou [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum ETaskType {  
    TT_DEBUGGERHELPER           = 0x1,  
    TT_GC                       = 0x2,  
    TT_FINALIZER                = 0x4,  
    TT_THREADPOOL_TIMER         = 0x8,  
    TT_THREADPOOL_GATE          = 0x10,  
    TT_THREADPOOL_WORKER        = 0x20,  
    TT_THREADPOOL_IOCOMPLETION  = 0x40,  
    TT_ADUNLOAD                 = 0x80,  
    TT_USER                     = 0x100,  
    TT_THREADPOOL_WAIT          = 0x200,  
    TT_UNKNOWN                  = 0x80000000  
} ETaskType;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`TT_ADUNLOAD`|L’interface représente une tâche de déchargement du domaine application.|  
|`TT_DEBUGGERHELPER`|L’interface représente une tâche d’assistance du débogueur.|  
|`TT_FINALIZER`|L’interface représente une tâche du finaliseur.|  
|`TT_GC`|L’interface représente une tâche de garbage collection.|  
|`TT_THREADPOOL_GATE`|L’interface représente une tâche du thread de grille.|  
|`TT_THREADPOOL_IOCOMPLETION`|L’interface représente une tâche du thread d’e/s ou une tâche de thread de port de fin.|  
|`TT_THREADPOOL_TIMER`|L’interface représente une tâche du thread du minuteur.|  
|`TT_THREADPOOL_WAIT`|L’interface représente une tâche de thread d’attente.|  
|`TT_THREADPOOL_WORKER`|L’interface représente une tâche du thread de travail.|  
|`TT_UNKNOWN`|La tâche est inconnue.|  
|`TT_USER`|L’interface représente une tâche utilisateur.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
