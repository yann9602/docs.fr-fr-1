---
title: "EMemoryCriticalLevel, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EMemoryCriticalLevel
api_location: mscoree.dll
api_type: COM
f1_keywords: EMemoryCriticalLevel
helpviewer_keywords: EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b15a6786cb99a64d441d7e05fb91cd8ff0f3af92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ememorycriticallevel-enumeration"></a>EMemoryCriticalLevel, énumération
Contient des valeurs qui indiquent l’impact d’un échec lors de l’allocation de mémoire spécifique a été demandée, mais ne peut pas être satisfaite.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`eAppDomainCritical`|Indique que l’allocation est critique pour l’exécution du code managé dans le domaine qui a demandé l’allocation. Si la mémoire ne peut pas être allouée, le CLR ne peut pas garantir que le domaine est toujours utilisable. L’hôte décide quelle action à effectuer lorsque l’allocation ne peut pas être satisfaite. Il peut indiquer au CLR pour abandonner la `AppDomain` automatiquement, ou lui permettre de poursuivre son exécution en appelant des méthodes sur [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).|  
|`eProcessCritical`|Indique que l’allocation est critique pour l’exécution du code managé dans le processus. Cette valeur est utilisée lors du démarrage et lors de l’exécution des finaliseurs. Si la mémoire ne peut pas être allouée, le CLR ne peut pas fonctionner dans le processus. Si l’allocation échoue, le CLR est désactivé. Tous les appels dans le CLR échouent avec HOST_E_CLRNOTAVAILABLE.|  
|`eTaskCritical`|Indique que l’allocation est critique pour l’exécution de la tâche qui a demandé l’allocation. Si la mémoire ne peut pas être allouée, le CLR ne peut pas garantir que la tâche peut être exécutée. En cas de défaillance, le CLR lève une <xref:System.Threading.ThreadAbortException> sur le thread de système d’opération physique.|  
  
## <a name="remarks"></a>Remarques  
 Les méthodes d’allocation de mémoire définies dans le [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) et [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces prennent un paramètre de ce type. En fonction de la gravité d’une défaillance, un hôte peut décider Échec de la demande d’allocation immédiatement ou attendre qu’il peut être satisfaite.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRMemoryNotificationCallback (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
