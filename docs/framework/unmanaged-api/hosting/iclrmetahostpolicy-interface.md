---
title: ICLRMetaHostPolicy, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHostPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHostPolicy
helpviewer_keywords: ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type: apiref
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cd9b8d6aef2289833a0bd192b838e6f70ea8c0ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahostpolicy-interface"></a>ICLRMetaHostPolicy, interface
Fournit la [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) méthode, qui retourne un pointeur vers une interface du common language runtime (CLR) selon un critère de stratégie, managé fichier de configuration, de la version et de l’assembly.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetRequestedRuntime, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|Fournit une interface CLR par défaut selon un critère de stratégie, géré de fichier d’assembly, version et la configuration.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez obtenir une référence à cette interface en appelant le [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) fonctionne comme indiqué dans le code suivant :  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  Cette interface ne prend pas réellement charger et activer le CLR, mais retourne simplement la version CLR par défaut selon les versions disponibles qui sont installées ou chargées.  
  
 Le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] API d’hébergement consolide les stratégies de sorte que les hôtes avec des besoins spécifiques puissent utiliser les fonctionnalités de base sans encourir des pénalités imprévues. Par exemple, la plupart des exportations MSCorEE.dll liera à un CLR spécifique, bien qu’une méthode peut logiquement impose pas. Le [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) énumération fournit des stratégies de liaison qui sont communes à la majorité des ordinateurs hôtes.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces d’hébergement CLR ajoutées dans .NET Framework 4 et 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hébergement d’applications WPF](../../../../docs/framework/unmanaged-api/hosting/index.md)
