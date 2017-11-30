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
ms.openlocfilehash: a833be39f93082e8d2c0cb28f435f754143721f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="8ef85-102">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="8ef85-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="8ef85-103">Permet aux hôtes non managés de charger le common language runtime (CLR) dans un processus.</span><span class="sxs-lookup"><span data-stu-id="8ef85-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="8ef85-104">Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8ef85-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ef85-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ef85-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ef85-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8ef85-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="8ef85-107">[in] Une chaîne décrivant la version du CLR que vous souhaitez charger.</span><span class="sxs-lookup"><span data-stu-id="8ef85-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="8ef85-108">Un numéro de version du .NET Framework se compose de quatre parties séparées par des points : *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="8ef85-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="8ef85-109">La chaîne passée en tant que `pwszVersion` doit commencer par le caractère « v », suivi par les trois premières parties du numéro de version (par exemple, « v1.0.1529 »).</span><span class="sxs-lookup"><span data-stu-id="8ef85-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="8ef85-110">Certaines versions du CLR sont installées avec une instruction de stratégie qui spécifie la compatibilité avec les versions précédentes du CLR.</span><span class="sxs-lookup"><span data-stu-id="8ef85-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="8ef85-111">Par défaut, le shim de démarrage évalue `pwszVersion` par rapport aux instructions de stratégie et charge la dernière version du runtime qui est compatible avec la version demandée.</span><span class="sxs-lookup"><span data-stu-id="8ef85-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="8ef85-112">Un hôte peut forcer le shim à ignorer l’évaluation de stratégie et charger la version exacte spécifiée dans `pwszVersion` en passant une valeur de `STARTUP_LOADER_SAFEMODE` pour la `flags` paramètre, comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="8ef85-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="8ef85-113">Si l’appelant spécifie null pour `pwszVersion`, la dernière version du runtime est chargée.</span><span class="sxs-lookup"><span data-stu-id="8ef85-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="8ef85-114">Passage de null ne donne à l’hôte aucun contrôle sur lequel la version du runtime est chargée.</span><span class="sxs-lookup"><span data-stu-id="8ef85-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="8ef85-115">Bien que cette approche peut convenir dans certains scénarios, il est fortement recommandé que l’hôte de fournisse une version spécifique à charger.</span><span class="sxs-lookup"><span data-stu-id="8ef85-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="8ef85-116">[in] Chaîne qui spécifie s’il faut charger le serveur de build ou de la station de travail du CLR.</span><span class="sxs-lookup"><span data-stu-id="8ef85-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="8ef85-117">Les valeurs valides sont `svr` et `wks`.</span><span class="sxs-lookup"><span data-stu-id="8ef85-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="8ef85-118">La build du serveur est optimisée pour tirer parti de plusieurs processeurs pour les garbage collection, et la génération de la station de travail est optimisée pour les applications clientes s’exécutant sur un ordinateur à processeur unique.</span><span class="sxs-lookup"><span data-stu-id="8ef85-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="8ef85-119">Si `pwszBuildFlavor` a la valeur null, la build de la station de travail est chargée.</span><span class="sxs-lookup"><span data-stu-id="8ef85-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="8ef85-120">Lors de l’exécution sur un ordinateur à un seul processeur, la build de la station de travail est toujours chargée, même si `pwszBuildFlavor` a la valeur `svr`.</span><span class="sxs-lookup"><span data-stu-id="8ef85-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="8ef85-121">Toutefois, si `pwszBuildFlavor` a la valeur `svr` et le garbage collection simultané est spécifié (consultez la description de le `flags` paramètre), la build du serveur est chargée.</span><span class="sxs-lookup"><span data-stu-id="8ef85-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="8ef85-122">[in] Le `CLSID` de la coclasse qui implémente le [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou le [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="8ef85-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="8ef85-123">Valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="8ef85-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="8ef85-124">[in] Le `IID` de l’interface demandée à partir de `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="8ef85-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="8ef85-125">Valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="8ef85-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="8ef85-126">[out] Pointeur d’interface retourné à `riid`.</span><span class="sxs-lookup"><span data-stu-id="8ef85-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ef85-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="8ef85-127">Remarks</span></span>  
 <span data-ttu-id="8ef85-128">Si `pwszVersion` spécifie une version du runtime qui n’existe pas, `CorBindToRuntimeEx` retourne une valeur HRESULT de CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="8ef85-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="8ef85-129">Contexte d’exécution et les flux d’identité Windows</span><span class="sxs-lookup"><span data-stu-id="8ef85-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="8ef85-130">Dans la version 1 du CLR, la <xref:System.Security.Principal.WindowsIdentity> objet n’est pas transmis entre des points asynchrones telles que de nouveaux threads, pools de threads ou rappels de la minuterie.</span><span class="sxs-lookup"><span data-stu-id="8ef85-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="8ef85-131">Dans la version 2.0 du CLR, un <xref:System.Threading.ExecutionContext> objet encapsule des informations sur le thread en cours d’exécution et les transmet d’un point asynchrone, mais pas entre les limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="8ef85-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="8ef85-132">De même, le <xref:System.Security.Principal.WindowsIdentity> objet transmis d’un point asynchrone.</span><span class="sxs-lookup"><span data-stu-id="8ef85-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="8ef85-133">Par conséquent, l’emprunt d’identité actuel sur le thread, le cas échéant, est également transmis.</span><span class="sxs-lookup"><span data-stu-id="8ef85-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="8ef85-134">Vous pouvez modifier le flux de deux manières :</span><span class="sxs-lookup"><span data-stu-id="8ef85-134">You can alter the flow in two ways:</span></span>  
  
1.  <span data-ttu-id="8ef85-135">En modifiant le <xref:System.Threading.ExecutionContext> paramètres afin de supprimer le flux sur une base par thread (consultez la <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, et <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> méthodes).</span><span class="sxs-lookup"><span data-stu-id="8ef85-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2.  <span data-ttu-id="8ef85-136">En modifiant le mode par défaut de processus pour le mode de compatibilité de la version 1, où le <xref:System.Security.Principal.WindowsIdentity> objet ne transmet pas d’un point asynchrone, quel que soit le <xref:System.Threading.ExecutionContext> paramètres sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="8ef85-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="8ef85-137">Comment vous modifiez le mode par défaut varie selon que vous utilisez un fichier exécutable managé ou une interface d’hébergement non managée pour charger le CLR :</span><span class="sxs-lookup"><span data-stu-id="8ef85-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1.  <span data-ttu-id="8ef85-138">Pour les fichiers exécutables managés, vous devez définir le `enabled` attribut de la [ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) élément `true`.</span><span class="sxs-lookup"><span data-stu-id="8ef85-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2.  <span data-ttu-id="8ef85-139">Pour les interfaces d’hébergement non managées, configurer le `STARTUP_LEGACY_IMPERSONATION` indicateur dans le `flags` paramètre lors de l’appel du `CorBindToRuntimeEx` (fonction).</span><span class="sxs-lookup"><span data-stu-id="8ef85-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="8ef85-140">Le mode de compatibilité de la version 1 s’applique à l’ensemble du processus et tous les domaines d’application dans le processus.</span><span class="sxs-lookup"><span data-stu-id="8ef85-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ef85-141">Remarques</span><span class="sxs-lookup"><span data-stu-id="8ef85-141">Remarks</span></span>  
 <span data-ttu-id="8ef85-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) et `CorBindToRuntime` exécutent la même opération, mais la `CorBindToRuntimeEx` fonction vous permet de définir des indicateurs pour spécifier le comportement du CLR.</span><span class="sxs-lookup"><span data-stu-id="8ef85-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ef85-143">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8ef85-143">Requirements</span></span>  
 <span data-ttu-id="8ef85-144">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ef85-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ef85-145">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8ef85-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ef85-146">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8ef85-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ef85-147">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ef85-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef85-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ef85-148">See Also</span></span>  
 [<span data-ttu-id="8ef85-149">CorBindToCurrentRuntime (fonction)</span><span class="sxs-lookup"><span data-stu-id="8ef85-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="8ef85-150">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="8ef85-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="8ef85-151">CorBindToRuntimeEx (fonction)</span><span class="sxs-lookup"><span data-stu-id="8ef85-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="8ef85-152">CorBindToRuntimeHost (fonction)</span><span class="sxs-lookup"><span data-stu-id="8ef85-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="8ef85-153">ICorRuntimeHost (Interface)</span><span class="sxs-lookup"><span data-stu-id="8ef85-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="8ef85-154">Fonctions d’hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="8ef85-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
