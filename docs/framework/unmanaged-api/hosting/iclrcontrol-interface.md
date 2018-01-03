---
title: ICLRControl, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRControl
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRControl
helpviewer_keywords: ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b93d87107e1a69b0a047dbf156124fe49cd95d16
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrcontrol-interface"></a>ICLRControl, interface
Fournit des méthodes qui permettent à un hôte obtenir des références à et de configurer les aspects de, le common language runtime (CLR).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetCLRManager, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|Obtient un pointeur d’interface vers une instance d’un des types de manager que l’hôte peut utiliser pour configurer le CLR.|  
|[SetAppDomainManagerType, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|Définit un type dérivé <xref:System.AppDomainManager> comme type pour les gestionnaires de domaine d’application.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRAssemblyIdentityManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [ICLRDebugManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [ICLRGCManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [ICLRHostBindingPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 [ICLRHostProtectionManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [ICLROnEventManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [ICLRPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [IHostControl, interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
