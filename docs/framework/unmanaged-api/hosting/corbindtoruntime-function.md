---
title: CorBindToRuntime, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CorBindToRuntime
helpviewer_keywords: CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e6ce976961eedaa58ad265a133c15b2f27a8985
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corbindtoruntime-function"></a>CorBindToRuntime, fonction
Permet aux hôtes non managés de charger le common language runtime (CLR) dans un processus.  
  
 Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pwszVersion`  
 [in] Une chaîne décrivant la version du CLR que vous souhaitez charger.  
  
 Un numéro de version du .NET Framework se compose de quatre parties séparées par des points : *major.minor.build.revision*. La chaîne passée en tant que `pwszVersion` doit commencer par le caractère « v », suivi par les trois premières parties du numéro de version (par exemple, « v1.0.1529 »).  
  
 Certaines versions du CLR sont installées avec une instruction de stratégie qui spécifie la compatibilité avec les versions précédentes du CLR. Par défaut, le shim de démarrage évalue `pwszVersion` par rapport aux instructions de stratégie et charge la dernière version du runtime qui est compatible avec la version demandée. Un hôte peut forcer le shim à ignorer l’évaluation de stratégie et charger la version exacte spécifiée dans `pwszVersion` en passant une valeur de `STARTUP_LOADER_SAFEMODE` pour la `flags` paramètre, comme décrit ci-dessous.  
  
 Si l’appelant spécifie null pour `pwszVersion`, la dernière version du runtime est chargée. Passage de null ne donne à l’hôte aucun contrôle sur lequel la version du runtime est chargée. Bien que cette approche peut convenir dans certains scénarios, il est fortement recommandé que l’hôte de fournisse une version spécifique à charger.  
  
 `pwszBuildFlavor`  
 [in] Chaîne qui spécifie s’il faut charger le serveur de build ou de la station de travail du CLR. Les valeurs valides sont `svr` et `wks`. La build du serveur est optimisée pour tirer parti de plusieurs processeurs pour les garbage collection, et la génération de la station de travail est optimisée pour les applications clientes s’exécutant sur un ordinateur à processeur unique.  
  
 Si `pwszBuildFlavor` a la valeur null, la build de la station de travail est chargée. Lors de l’exécution sur un ordinateur à un seul processeur, la build de la station de travail est toujours chargée, même si `pwszBuildFlavor` a la valeur `svr`. Toutefois, si `pwszBuildFlavor` a la valeur `svr` et le garbage collection simultané est spécifié (consultez la description de le `flags` paramètre), la build du serveur est chargée.  
  
 `rclsid`  
 [in] Le `CLSID` de la coclasse qui implémente le [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou le [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface. Valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.  
  
 `riid`  
 [in] Le `IID` de l’interface demandée à partir de `rclsid`. Valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Pointeur d’interface retourné à `riid`.  
  
## <a name="remarks"></a>Notes  
 Si `pwszVersion` spécifie une version du runtime qui n’existe pas, `CorBindToRuntimeEx` retourne une valeur HRESULT de CLR_E_SHIM_RUNTIMELOAD.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Contexte d’exécution et les flux d’identité Windows  
 Dans la version 1 du CLR, la <xref:System.Security.Principal.WindowsIdentity> objet n’est pas transmis entre des points asynchrones telles que de nouveaux threads, pools de threads ou rappels de la minuterie. Dans la version 2.0 du CLR, un <xref:System.Threading.ExecutionContext> objet encapsule des informations sur le thread en cours d’exécution et les transmet d’un point asynchrone, mais pas entre les limites du domaine d’application. De même, le <xref:System.Security.Principal.WindowsIdentity> objet transmis d’un point asynchrone. Par conséquent, l’emprunt d’identité actuel sur le thread, le cas échéant, est également transmis.  
  
 Vous pouvez modifier le flux de deux manières :  
  
1.  En modifiant le <xref:System.Threading.ExecutionContext> paramètres afin de supprimer le flux sur une base par thread (consultez la <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, et <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> méthodes).  
  
2.  En modifiant le mode par défaut de processus pour le mode de compatibilité de la version 1, où le <xref:System.Security.Principal.WindowsIdentity> objet ne transmet pas d’un point asynchrone, quel que soit le <xref:System.Threading.ExecutionContext> paramètres sur le thread actuel. Comment vous modifiez le mode par défaut varie selon que vous utilisez un fichier exécutable managé ou une interface d’hébergement non managée pour charger le CLR :  
  
    1.  Pour les fichiers exécutables managés, vous devez définir le `enabled` attribut de la [ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) élément `true`.  
  
    2.  Pour les interfaces d’hébergement non managées, configurer le `STARTUP_LEGACY_IMPERSONATION` indicateur dans le `flags` paramètre lors de l’appel du `CorBindToRuntimeEx` (fonction).  
  
     Le mode de compatibilité de la version 1 s’applique à l’ensemble du processus et tous les domaines d’application dans le processus.  
  
## <a name="remarks"></a>Notes  
 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) et `CorBindToRuntime` exécutent la même opération, mais la `CorBindToRuntimeEx` fonction vous permet de définir des indicateurs pour spécifier le comportement du CLR.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [CorBindToCurrentRuntime, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [CorBindToRuntimeByCfg, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [CorBindToRuntimeEx, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [CorBindToRuntimeHost, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [ICorRuntimeHost, interface](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
