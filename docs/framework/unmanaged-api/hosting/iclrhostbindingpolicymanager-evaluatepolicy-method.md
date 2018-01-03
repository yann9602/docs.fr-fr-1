---
title: "ICLRHostBindingPolicyManager::EvaluatePolicy, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostBindingPolicyManager.EvaluatePolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostBindingPolicyManager::EvaluatePolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy method [.NET Framework hosting]
- EvaluatePolicy method [.NET Framework hosting]
ms.assetid: 3a3a9446-7a4e-4836-9b27-5c536c15993d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 14f4db56529fbbb08f8f3d9adde0d4dc7a8ce045
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a>ICLRHostBindingPolicyManager::EvaluatePolicy, méthode
Évalue la stratégie de liaison pour le compte de l’ordinateur hôte.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pwzReferenceIdentity`  
 [in] Une référence à l’assembly avant l’évaluation de stratégie.  
  
 `pbApplicationPolicy`  
 [in] Pointeur vers une mémoire tampon qui contient les données de stratégie.  
  
 `cbAppPolicySize`  
 [in] La taille de la `pbApplicationPolicy` mémoire tampon.  
  
 `pwzPostPolicyReferenceIdentity`  
 [out] Une référence à l’assembly après l’évaluation des nouvelles données de stratégie.  
  
 `pcchPostPolicyReferenceIdentity`  
 [dans, out] Pointeur vers la taille de la mémoire tampon de référence assembly identité après l’évaluation des nouvelles données de stratégie.  
  
 `pdwPoliciesApplied`  
 [out] Un pointeur vers une combinaison OR logique de [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) valeurs indiquant quelles stratégies ont été appliquées.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|L’évaluation s’est terminée correctement.|  
|E_INVALIDARG|Soit `pwzReferenceIdentity` ou `pbApplicationPolicy` est une référence null.|  
|ERROR_INSUFFICIENT_BUFFER|`cbAppPolicySize`est trop petite.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.|  
|E_FAIL|Une défaillance grave et inconnue s’est produite. Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes  
 Le `EvaluatePolicy` méthode permet à l’hôte pour influencer la stratégie de liaison pour mettre à jour d’assembly spécifique à l’hôte les exigences de contrôle de version. Le moteur de stratégie reste à l’intérieur du CLR.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRHostBindingPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
