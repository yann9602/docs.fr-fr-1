---
title: IGCHost, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCHost
helpviewer_keywords: IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5c0f398c09569a855291a1565ce63b513161a803
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="igchost-interface"></a>IGCHost, interface
Fournit des méthodes pour obtenir des informations sur le système de garbage collection et contrôler certains aspects du garbage collection.  
  
> [!NOTE]
>  En commençant par le [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], vous pouvez utiliser la [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) pour définir la taille d’un segment de garbage collection et la taille maximale de la génération du système de garbage collection 0 pour les valeurs supérieure à la `DWORD` limite imposée par le [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) (méthode).  
  
> [!NOTE]
>  Cette interface est uniquement à l’usage expert. Il peut affecter les performances d’une application pour une utilisation incorrecte.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Collect (méthode)](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|Force une collection pour la génération donnée, quel que soit l’état du garbage collection en cours.|  
|[GetStats (méthode)](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|Obtient les statistiques de l’état actuel du système de garbage collection.|  
|[GetThreadStats (méthode)](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|Obtient les statistiques par thread pour le garbage collection.|  
|[SetGCStartupLimits (méthode)](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|Définit la taille du segment et la taille maximale pour la génération 0.|  
|[SetVirtualMemLimit (méthode)](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|Définit la taille maximale de mémoire virtuelle du runtime.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** GCHost.idl, GCHost.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Corruntimehost, coclasse](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
