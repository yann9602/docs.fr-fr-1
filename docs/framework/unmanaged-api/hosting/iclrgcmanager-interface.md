---
title: ICLRGCManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager
helpviewer_keywords: ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6cc6c84d57e4114a28a8b363b99b98f3c4d21410
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrgcmanager-interface"></a>ICLRGCManager, interface
Fournit des méthodes qui permettent à un hôte d’interagir avec le système de garbage collection du common language runtime.  
  
> [!NOTE]
>  En commençant par le [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], vous pouvez utiliser la [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) pour définir la taille d’un segment de garbage collection et la taille maximale de la génération du système de garbage collection 0 pour les valeurs supérieure (méthode) à la `DWORD` limite imposée par le [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) (méthode).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Collect, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|Force une garbage collection pour la génération spécifiée.|  
|[GetStats, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|Obtient un jeu de statistiques actuelles concernant le système de garbage collection.|  
|[SetGCStartupLimits, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|Définit la taille d’un segment de garbage collection et la taille maximale de la génération du système de garbage collection 0.|  
  
## <a name="remarks"></a>Notes  
 Le common language runtime (CLR) implémente son mécanisme de garbage collection avec managé <xref:System.GC> type. Pour plus d’informations sur le système de garbage collection, consultez [le Garbage Collection](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion automatique de la mémoire](../../../../docs/standard/automatic-memory-management.md)  
 [COR_GC_STATS, structure](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [ICLRControl, interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [Interfaces d’hébergement CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hébergement d’applications WPF](../../../../docs/framework/unmanaged-api/hosting/index.md)
