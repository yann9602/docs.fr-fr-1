---
title: IHostMemoryManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager
helpviewer_keywords: IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 415539be0dbed8e0cf3f9d6e5c79bf4cfac09fe2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager, interface
Fournit des méthodes qui permettent le common language runtime (CLR) pour effectuer des demandes de mémoire virtuelle via l’hôte, au lieu d’utiliser les fonctions de mémoire virtuelle Win32 standard.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[AcquiredVirtualAddressSpace (méthode)](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|Avertit l’hôte que le common language runtime (CLR) a acquis la mémoire spécifiée à partir du système d’exploitation.|  
|[CreateMAlloc, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|Obtient un pointeur d’interface vers un [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance qui est utilisé pour demander des allocations de mémoire à partir d’un tas créé par l’hôte.|  
|[GetMemoryLoad (méthode)](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|Obtient la quantité de mémoire physique qui est actuellement utilisé, comme indiqué par l’hôte.|  
|[NeedsVirtualAddressSpace (méthode)](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|Avertit l’hôte que le CLR va tenter d’utiliser la mémoire spécifiée.|  
|[RegisterMemoryNotificationCallback (méthode)](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|Enregistre un pointeur vers une fonction de rappel que l’hôte appelle pour notifier le CLR de la charge actuelle de la mémoire sur l’ordinateur.|  
|[ReleasedVirtualAddressSpace (méthode)](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|Avertit l’hôte que le CLR a terminé d’utiliser la mémoire spécifiée.|  
|[VirtualAlloc, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|Sert de wrapper logique pour la fonction Win32 correspondante, qui se réserve ou valide une région de pages dans l’espace d’adressage virtuel du processus appelant.|  
|[VirtualFree, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|Sert de wrapper logique pour la fonction Win32 correspondante, qui libère, annule sa validation ou libère et invalider une région de pages au sein de l’espace d’adressage virtuel du processus appelant.|  
|[VirtualProtect (méthode)](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|Sert de wrapper logique pour la fonction Win32 correspondante, qui modifie la protection sur une région de pages validées dans l’espace d’adressage virtuel du processus appelant.|  
|[VirtualQuery (méthode)](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|Sert de wrapper logique pour la fonction Win32 correspondante, qui Récupère des informations sur une plage de pages dans l’espace d’adressage virtuel du processus appelant.|  
  
## <a name="remarks"></a>Remarques  
 `IHostMemoryManager`fournit également des méthodes pour le CLR obtenir un pointeur par l’intermédiaire duquel pour effectuer des demandes de mémoire sur le tas et obtenir le niveau de sollicitation de la mémoire dans le processus, comme indiqué par l’hôte.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IHostMalloc (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
