---
title: "ICLRPolicyManager::SetActionOnFailure, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetActionOnFailure
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5dc8e27ed1a5701886c3583a7515e4212f490208
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a>ICLRPolicyManager::SetActionOnFailure, méthode
Spécifie l’action de stratégie que le common language runtime (CLR) doit prendre en cas d’échec spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `failure`  
 [in] Parmi les [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) valeurs indiquant le type d’échec pour lequel effectuer l’action.  
  
 `action`  
 [in] Parmi les [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valeurs, indiquant l’action à entreprendre lorsqu’une défaillance se produit. Pour obtenir la liste de valeurs prises en charge, consultez la section Notes.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetActionOnFailure`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.|  
|E_FAIL|Une défaillance grave et inconnue s’est produite. Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|Impossible de définir une action de la stratégie pour l’opération spécifiée, ou une action de stratégie non valide a été spécifiée pour l’opération.|  
  
## <a name="remarks"></a>Remarques  
 Par défaut, le CLR lève une exception lorsqu’il ne peut pas allouer une ressource, telles que la mémoire. `SetActionOnFailure`permet à l’hôte de substituer ce comportement en spécifiant l’action de stratégie à appliquer en cas d’échec. Le tableau suivant montre les combinaisons de [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) et [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valeurs prises en charge. (Le préfixe FAIL_ est omis de [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) valeurs.)  
  
||NonCriticalResource|CriticalResource|FatalRuntime|OrphanedLock|Dépassement de capacité|AccessViolation|CodeContract|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|X|X||||N/A||  
|eThrowException|X|X||||N/A||  
|`eAbortThread`|X|X||||N/A|X|  
|`eRudeAbortThread`|X|X||||N/A|X|  
|`eUnloadAppDomain`|X|X||X||N/A|X|  
|`eRudeUnloadAppDomain`|X|X||X|X|N/A|X|  
|`eExitProcess`|X|X||X|X|N/A|X|  
|eFastExitProcess|X|X||X|X|N/A||  
|`eRudeExitProcess`|X|X|X|X|X|N/A||  
|`eDisableRuntime`|X|X|X|X|X|N/A||  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [EClrFailure (énumération)](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [EPolicyAction (énumération)](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [ICLRControl (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [ICLRPolicyManager (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
