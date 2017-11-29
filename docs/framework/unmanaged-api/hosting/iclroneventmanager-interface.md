---
title: ICLROnEventManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLROnEventManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLROnEventManager
helpviewer_keywords: ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d3f792af3e01d476768961928272cb6166a144f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclroneventmanager-interface"></a>ICLROnEventManager, interface
Fournit des méthodes qui permettent à l’hôte inscrire et désinscrire des rappels pour les événements du common language runtime (CLR).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[RegisterActionOnEvent (méthode)](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|Enregistre un pointeur de rappel pour l’événement spécifié.|  
|[UnregisterActionOnEvent (méthode)](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|Annule l’inscription d’un pointeur de rappel précédemment enregistré pour l’événement spécifié.|  
  
## <a name="remarks"></a>Remarques  
 Pour enregistrer et annuler l’inscription du rappel d’événement, l’hôte obtient une référence à `ICLROnEventManager` en appelant le [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) (méthode).  
  
> [!NOTE]
>  Les événements décrits par [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) peuvent être déclenchés plusieurs fois et à partir de threads différents pour signaler le déchargement ou la désactivation du CLR.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [EClrEvent (énumération)](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [IActionOnCLREvent (Interface)](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [ICLRControl (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
