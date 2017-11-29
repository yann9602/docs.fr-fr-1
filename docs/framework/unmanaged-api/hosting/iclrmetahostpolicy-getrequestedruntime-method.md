---
title: "ICLRMetaHostPolicy::GetRequestedRuntime, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHostPolicy.GetRequestedRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHostPolicy::GetRequestedRuntime
helpviewer_keywords:
- GetRequestedRuntime method [.NET Framework hosting]
- ICLRMetaHostPolicy::GetRequestedRuntime method [.NET Framework hosting]
ms.assetid: 59ec1832-9cc1-4b5c-983d-03407e51de56
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 57e5efc604568aea0a6edef5cc57f83fb99eb561
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a>ICLRMetaHostPolicy::GetRequestedRuntime, méthode
Fournit une interface pour une version préférée du Common Language Runtime (CLR) basée sur une stratégie d'hébergement, un assembly managé, une chaîne de version et un flux de configuration. Cette méthode ne charge pas réellement ou n’active le CLR, mais retourne simplement le [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface qui représente le résultat de la stratégie. Cette méthode remplace la [GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md), et [GetCORRequiredVersion](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md) méthodes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRequestedRuntime(  
    [in]  METAHOST_POLICY_FLAGS dwPolicyFlags,  
    [in]  LPCWSTR pwzBinary,  
    [in]  IStream *pCfgStream,  
    [in, out, size_is(*pcchVersion)] LPWSTR pwzVersion,  
    [in, out]  DWORD *pcchVersion,  
    [out, size_is(*pcchImageVersion)] LPWSTR pwzImageVersion,  
    [in, out]  DWORD *pcchImageVersion,  
    [out] DWORD *pdwConfigFlags,  
    [in]  REFIID  riid  
    [out, iid_is(riid), retval] LPVOID *ppRuntime);  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Nom|Description|  
|----------|-----------------|  
|`dwPolicyFlags`|[in] Obligatoire. Spécifie un membre de la [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) énumération, représentant une stratégie de liaison et un nombre quelconque de modificateurs. La seule stratégie actuellement disponible est [METAHOST_POLICY_HIGHCOMPAT](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).<br /><br /> Incluent des modificateurs [METAHOST_POLICY_EMULATE_EXE_LAUNCH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), et [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).|  
|`pwzBinary`|[in] Facultatif. Spécifie le chemin d’accès de fichier d’assembly.|  
|`pCfgStream`|[in] Facultatif. Spécifie le fichier de configuration en tant que <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.|  
|`pwzVersion`|[in, out] Facultatif. Spécifie ou retourne la version du CLR par défaut à charger.|  
|`pcchVersion`|[in, out] Obligatoire. Spécifie la taille attendue de `pwzVersion` comme entrée, pour éviter les dépassements de mémoire tampon. Si `pwzVersion` a la valeur null, `pcchVersion` contient la taille attendue de `pwzVersion` quand `GetRequestedRuntime` retourne, pour autoriser la préallocation ; sinon, `pcchVersion` contient le nombre de caractères écrits dans `pwzVersion`.|  
|`pwzImageVersion`|[out] Facultatif. Lorsque `GetRequestedRuntime` est retournée, contient la version CLR correspondant à la [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface qui est retournée.|  
|`pcchImageVersion`|[in, out] Facultatif. Spécifie la taille de `pwzImageVersion` comme entrée pour éviter les dépassements de mémoire tampon. Si `pwzImageVersion` a la valeur null, `pcchImageVersion` contient la taille requise de `pwzImageVersion` quand `GetRequestedRuntime` retourne, pour autoriser la préallocation.|  
|`pdwConfigFlags`|[out] Facultatif. Si `GetRequestedRuntime` utilise un fichier de configuration pendant le processus de liaison, quand elle retourne, `pdwConfigFlags` contient un [METAHOST_CONFIG_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) valeur qui indique si le [ \<démarrage >](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) élément a le `useLegacyV2RuntimeActivationPolicy` attribut ensemble et la valeur de l’attribut. Appliquer le [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) au masque `pdwConfigFlags` pour obtenir les valeurs pertinentes à `useLegacyV2RuntimeActivationPolicy`.|  
|`riid`|[in] Spécifie l’identificateur d’interface IID_ICLRRuntimeInfo pour demandé [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.|  
|`ppRuntime`|[out] Lorsque `GetRequestedRuntime` est retournée, contient un pointeur correspondant [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.|  
  
## <a name="remarks"></a>Remarques  
 Quand cette méthode réussit, elle a comme effet secondaire de combiner des indicateurs supplémentaires avec les indicateurs de démarrage par défaut actuels de l'interface d'exécution retournée, si et seulement si un ou plusieurs des éléments suivants existent dans le flux de configuration dans la section `<configuration><runtime>` :  
  
-   `<gcServer enabled="true"/>` provoque la définition de `STARTUP_SERVER_GC`.  
  
-   `<etwEnable enabled="true"/>` provoque la définition de `STARTUP_ETW`.  
  
-   `<appDomainResourceMonitoring enabled="true"/>` provoque la définition de `STARTUP_ARM`.  
  
 La valeur par défaut `STARTUP_FLAGS` résultante est la combinaison OR au niveau du bit des valeurs qui sont définies à partir de la liste précédente avec les indicateurs de démarrage par défaut.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_POINTER|`pwzVersion` n'est pas null et `pcchVersion` est null.<br /><br /> ou<br /><br /> `pwzImageVersion` n'est pas null et `pcchImageVersion` est null.|  
|E_INVALIDARG|`dwPolicyFlags` ne spécifie pas `METAHOST_POLICY_HIGHCOMPAT`.|  
|ERROR_INSUFFICIENT_BUFFER|La mémoire allouée à `pwzVerison` est insuffisante.<br /><br /> ou<br /><br /> La mémoire allouée à `pwzImageVerison` est insuffisante.|  
|CLR_E_SHIM_RUNTIMELOAD|`dwPolicyFlags` comprend METAHOST_POLICY_APPLY_UPGRADE_POLICY et `pwzVersion` et `pcchVersion` sont tous deux null.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRMetaHostPolicy, Interface](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 [Interfaces d’hébergement CLR est ajouté dans le .NET Framework 4 et 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hébergement d’applications WPF](../../../../docs/framework/unmanaged-api/hosting/index.md)
