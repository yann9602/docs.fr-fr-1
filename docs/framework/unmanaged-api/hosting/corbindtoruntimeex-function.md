---
title: CorBindToRuntimeEx, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntimeEx
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CorBindToRuntimeEx
helpviewer_keywords: CorBindToRuntimeEx function [.NET Framework hosting]
ms.assetid: aae9fb17-5d01-41da-9773-1b5b5b642d81
topic_type: apiref
caps.latest.revision: "41"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c0080e5a01c8e856c2862182ba06096fdc9385c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="2b1ea-102">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="2b1ea-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="2b1ea-103">Permet aux hôtes non managés de charger le common language runtime (CLR) dans un processus.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="2b1ea-104">Le [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) et `CorBindToRuntimeEx` fonctions effectuent la même opération, mais la `CorBindToRuntimeEx` fonction vous permet de définir des indicateurs pour spécifier le comportement du CLR.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-104">The [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="2b1ea-105">Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2b1ea-105">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
 <span data-ttu-id="2b1ea-106">Cette fonction prend un ensemble de paramètres qui permettent à un hôte effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="2b1ea-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
-   <span data-ttu-id="2b1ea-107">Spécifiez la version du runtime qui vont être chargée.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-107">Specify the version of the runtime that will be loaded.</span></span>  
  
-   <span data-ttu-id="2b1ea-108">Indiquer si la build du serveur ou station de travail doit être chargée.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
-   <span data-ttu-id="2b1ea-109">Contrôle si le garbage collection simultané ou le garbage collection non simultané est effectué.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b1ea-110">Le garbage collection simultané n’est pas pris en charge dans les applications en cours d’exécution WOW64 x86 émulateur sur les systèmes 64 bits qui implémentent l’architecture Intel Itanium (anciennement appelée IA-64).</span><span class="sxs-lookup"><span data-stu-id="2b1ea-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="2b1ea-111">Pour plus d’informations sur l’utilisation de WOW64 sur les systèmes 64 bits de Windows, consultez [Applications en cours d’exécution de 32 bits](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span><span class="sxs-lookup"><span data-stu-id="2b1ea-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span></span>  
  
-   <span data-ttu-id="2b1ea-112">Contrôler si les assemblys sont chargés comme indépendants du domaine.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
-   <span data-ttu-id="2b1ea-113">Obtenir un pointeur d’interface vers un [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) qui peut être utilisé pour définir des options supplémentaires pour configurer une instance du CLR avant son démarrage.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-113">Obtain an interface pointer to an [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b1ea-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b1ea-114">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,   
    [in]  LPCWSTR      pwszBuildFlavor,   
    [in]  DWORD        startupFlags,   
    [in]  REFCLSID     rclsid,   
    [in]  REFIID       riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b1ea-115">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2b1ea-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="2b1ea-116">[in] Une chaîne décrivant la version du CLR que vous souhaitez charger.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="2b1ea-117">Un numéro de version du .NET Framework se compose de quatre parties séparées par des points : *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="2b1ea-118">La chaîne passée en tant que `pwszVersion` doit commencer par le caractère « v », suivi par les trois premières parties du numéro de version (par exemple, « v1.0.1529 »).</span><span class="sxs-lookup"><span data-stu-id="2b1ea-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="2b1ea-119">Certaines versions du CLR sont installées avec une instruction de stratégie qui spécifie la compatibilité avec les versions précédentes du CLR.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="2b1ea-120">Par défaut, le shim de démarrage évalue `pwszVersion` par rapport aux instructions de stratégie et charge la dernière version du runtime qui est compatible avec la version demandée.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="2b1ea-121">Un hôte peut forcer le shim à ignorer l’évaluation de stratégie et charger la version exacte spécifiée dans `pwszVersion` en passant une valeur de `STARTUP_LOADER_SAFEMODE` pour la `startupFlags` paramètre, comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="2b1ea-122">Si l’appelant spécifie null pour `pwszVersion`, `CorBindToRuntimeEx` identifie le jeu de runtime installés dont les numéros de version sont inférieurs à l’exécution de .NET Framework 4 et chargement la dernière version du runtime à partir de cet ensemble.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="2b1ea-123">Il ne charge pas le .NET Framework 4 ou version ultérieure et qu’il échoue si aucune version antérieure n’est installée.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="2b1ea-124">Notez que passage de null ne donne à l’hôte aucun contrôle sur lequel la version du runtime est chargée.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="2b1ea-125">Bien que cette approche peut convenir dans certains scénarios, il est fortement recommandé que l’hôte de fournisse une version spécifique à charger.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="2b1ea-126">[in] Chaîne qui spécifie s’il faut charger le serveur de build ou de la station de travail du CLR.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="2b1ea-127">Les valeurs valides sont `svr` et `wks`.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="2b1ea-128">La build du serveur est optimisée pour tirer parti de plusieurs processeurs pour les garbage collection, et la génération de la station de travail est optimisée pour les applications clientes s’exécutant sur un ordinateur à processeur unique.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="2b1ea-129">Si `pwszBuildFlavor` a la valeur null, la build de la station de travail est chargée.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="2b1ea-130">Lors de l’exécution sur un ordinateur à un seul processeur, la build de la station de travail est toujours chargée, même si `pwszBuildFlavor` a la valeur `svr`.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="2b1ea-131">Toutefois, si `pwszBuildFlavor` a la valeur `svr` et le garbage collection simultané est spécifié (consultez la description de le `startupFlags` paramètre), la build du serveur est chargée.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="2b1ea-132">[in] Une combinaison de valeurs de la [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-132">[in] A combination of values of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="2b1ea-133">Ces indicateurs contrôlent le garbage collection simultané, code indépendant du domaine et le comportement de le `pwszVersion` paramètre.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="2b1ea-134">La valeur par défaut est le domaine unique si aucun indicateur n’est défini.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="2b1ea-135">Les valeurs suivantes sont valides :</span><span class="sxs-lookup"><span data-stu-id="2b1ea-135">The following values are valid:</span></span>  
  
-   `STARTUP_CONCURRENT_GC`  
  
-   `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
-   `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
-   `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
-   `STARTUP_LOADER_SAFEMODE`  
  
-   `STARTUP_LEGACY_IMPERSONATION`  
  
-   `STARTUP_LOADER_SETPREFERENCE`  
  
-   `STARTUP_SERVER_GC`  
  
-   `STARTUP_HOARD_GC_VM`  
  
-   `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
-   `STARTUP_LEGACY_IMPERSONATION`  
  
-   `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
-   `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 <span data-ttu-id="2b1ea-136">Pour obtenir une description de ces indicateurs, consultez la [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-136">For descriptions of these flags, see the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="2b1ea-137">[in] Le `CLSID` de la coclasse qui implémente le [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou le [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="2b1ea-138">Valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="2b1ea-139">[in] Le `IID` de l’interface demandée à partir de `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="2b1ea-140">Valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="2b1ea-141">[out] Pointeur d’interface retourné à `riid`.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b1ea-142">Notes</span><span class="sxs-lookup"><span data-stu-id="2b1ea-142">Remarks</span></span>  
 <span data-ttu-id="2b1ea-143">Si `pwszVersion` spécifie une version du runtime qui n’existe pas, `CorBindToRuntimeEx` retourne une valeur HRESULT de CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="2b1ea-144">Contexte d’exécution et les flux d’identité Windows</span><span class="sxs-lookup"><span data-stu-id="2b1ea-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="2b1ea-145">Dans la version 1 du CLR, la <xref:System.Security.Principal.WindowsIdentity> objet n’est pas transmis entre des points asynchrones telles que de nouveaux threads, pools de threads ou rappels de la minuterie.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="2b1ea-146">Dans la version 2.0 du CLR, un <xref:System.Threading.ExecutionContext> objet encapsule des informations sur le thread en cours d’exécution et les transmet d’un point asynchrone, mais pas entre les limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="2b1ea-147">De même, le <xref:System.Security.Principal.WindowsIdentity> objet transmis d’un point asynchrone.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="2b1ea-148">Par conséquent, l’emprunt d’identité actuel sur le thread, le cas échéant, est également transmis.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="2b1ea-149">Vous pouvez modifier le flux de deux manières :</span><span class="sxs-lookup"><span data-stu-id="2b1ea-149">You can alter the flow in two ways:</span></span>  
  
1.  <span data-ttu-id="2b1ea-150">En modifiant le <xref:System.Threading.ExecutionContext> paramètres afin de supprimer le flux sur une base par thread (consultez la <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, et <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> méthodes).</span><span class="sxs-lookup"><span data-stu-id="2b1ea-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2.  <span data-ttu-id="2b1ea-151">En modifiant le mode par défaut de processus pour le mode de compatibilité de la version 1, où le <xref:System.Security.Principal.WindowsIdentity> objet ne transmet pas d’un point asynchrone, quel que soit le <xref:System.Threading.ExecutionContext> paramètres sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="2b1ea-152">Comment vous modifiez le mode par défaut varie selon que vous utilisez un fichier exécutable managé ou une interface d’hébergement non managée pour charger le CLR :</span><span class="sxs-lookup"><span data-stu-id="2b1ea-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1.  <span data-ttu-id="2b1ea-153">Pour les fichiers exécutables managés, vous devez définir le `enabled` attribut de la [ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) élément `true`.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2.  <span data-ttu-id="2b1ea-154">Pour les interfaces d’hébergement non managées, configurer le `STARTUP_LEGACY_IMPERSONATION` indicateur dans le `startupFlags` paramètre lors de l’appel du `CorBindToRuntimeEx` (fonction).</span><span class="sxs-lookup"><span data-stu-id="2b1ea-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="2b1ea-155">Le mode de compatibilité de la version 1 s’applique à l’ensemble du processus et tous les domaines d’application dans le processus.</span><span class="sxs-lookup"><span data-stu-id="2b1ea-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b1ea-156">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2b1ea-156">Requirements</span></span>  
 <span data-ttu-id="2b1ea-157">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b1ea-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b1ea-158">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2b1ea-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2b1ea-159">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2b1ea-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b1ea-160">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b1ea-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b1ea-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b1ea-161">See Also</span></span>  
 [<span data-ttu-id="2b1ea-162">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="2b1ea-162">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="2b1ea-163">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="2b1ea-163">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="2b1ea-164">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="2b1ea-164">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="2b1ea-165">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="2b1ea-165">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="2b1ea-166">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="2b1ea-166">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="2b1ea-167">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="2b1ea-167">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
