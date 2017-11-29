---
title: CorBindToRuntimeHost, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntimeHost
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CorBindToRuntimeHost
helpviewer_keywords: CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type: apiref
caps.latest.revision: "28"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eff6fdf0294e3b1cc9830e58bc8103a64102d5b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="24005-102">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="24005-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="24005-103">Permet aux hôtes de charger une version spécifiée du common language runtime (CLR) dans un processus.</span><span class="sxs-lookup"><span data-stu-id="24005-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="24005-104">Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="24005-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24005-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24005-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,   
    [in] LPCWSTR       pwszBuildFlavor,   
    [in] LPCWSTR       pwszHostConfigFile,   
    [in] VOID*         pReserved,   
    [in] DWORD         startupFlags,   
    [in] REFCLSID      rclsid,   
    [in] REFIID        riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24005-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="24005-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="24005-107">[in] Chaîne qui décrit la version du CLR à charger.</span><span class="sxs-lookup"><span data-stu-id="24005-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="24005-108">Un numéro de version du .NET Framework se compose de quatre parties séparées par des points : *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="24005-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="24005-109">La chaîne passée en tant que `pwszVersion` doit commencer par le caractère « v », suivi par les trois premières parties du numéro de version (par exemple, « v1.0.1529 »).</span><span class="sxs-lookup"><span data-stu-id="24005-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="24005-110">Certaines versions du CLR sont installées avec une instruction de stratégie qui spécifie la compatibilité avec les versions précédentes du CLR.</span><span class="sxs-lookup"><span data-stu-id="24005-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="24005-111">Par défaut, le shim de démarrage évalue `pwszVersion` par rapport aux instructions de stratégie et charge la dernière version du runtime qui est compatible avec la version demandée.</span><span class="sxs-lookup"><span data-stu-id="24005-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="24005-112">Un hôte peut forcer le shim à ignorer l’évaluation de stratégie et charger la version exacte spécifiée dans `pwszVersion` en passant une valeur de STARTUP_LOADER_SAFEMODE pour le `startupFlags` paramètre.</span><span class="sxs-lookup"><span data-stu-id="24005-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="24005-113">Si `pwszVersion` est `null,` la méthode ne charge pas de n’importe quelle version du CLR.</span><span class="sxs-lookup"><span data-stu-id="24005-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="24005-114">Au lieu de cela, il retourne CLR_E_SHIM_RUNTIMELOAD, qui indique l’échec de chargement du runtime.</span><span class="sxs-lookup"><span data-stu-id="24005-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="24005-115">[in] Chaîne qui spécifie s’il faut charger le serveur de build ou de la station de travail du CLR.</span><span class="sxs-lookup"><span data-stu-id="24005-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="24005-116">Les valeurs valides sont `svr` et `wks`.</span><span class="sxs-lookup"><span data-stu-id="24005-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="24005-117">La build du serveur est optimisée pour tirer parti de plusieurs processeurs pour les garbage collection, et la génération de la station de travail est optimisée pour les applications clientes s’exécutant sur un ordinateur à processeur unique.</span><span class="sxs-lookup"><span data-stu-id="24005-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="24005-118">Si `pwszBuildFlavor` a la valeur null, la build de la station de travail est chargée.</span><span class="sxs-lookup"><span data-stu-id="24005-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="24005-119">Lors de l’exécution sur un ordinateur à un seul processeur, la build de la station de travail est toujours chargée, même si `pwszBuildFlavor` a la valeur `svr`.</span><span class="sxs-lookup"><span data-stu-id="24005-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="24005-120">Toutefois, si `pwszBuildFlavor` a la valeur `svr` et le garbage collection simultané est spécifié (consultez la description de le `startupFlags` paramètre), la build du serveur est chargée.</span><span class="sxs-lookup"><span data-stu-id="24005-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24005-121">Le garbage collection simultané n’est pas pris en charge dans les applications en cours d’exécution WOW64 x86 émulateur sur les systèmes 64 bits qui implémentent l’architecture Intel Itanium (anciennement appelée IA-64).</span><span class="sxs-lookup"><span data-stu-id="24005-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="24005-122">Pour plus d’informations sur l’utilisation de WOW64 sur les systèmes 64 bits de Windows, consultez [Applications en cours d’exécution de 32 bits](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span><span class="sxs-lookup"><span data-stu-id="24005-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="24005-123">[in] Le nom de fichier de configuration hôte qui spécifie la version du CLR à charger.</span><span class="sxs-lookup"><span data-stu-id="24005-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="24005-124">Si le nom de fichier n’inclut pas un chemin d’accès complet, le fichier est supposé être dans le même répertoire que l’exécutable qui effectue l’appel.</span><span class="sxs-lookup"><span data-stu-id="24005-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="24005-125">[in] Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="24005-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="24005-126">[in] Un ensemble d’indicateurs qui contrôle le garbage collection simultané, code indépendant du domaine et le comportement de le `pwszVersion` paramètre.</span><span class="sxs-lookup"><span data-stu-id="24005-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="24005-127">La valeur par défaut est le domaine unique si aucun indicateur n’est défini.</span><span class="sxs-lookup"><span data-stu-id="24005-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="24005-128">Pour obtenir la liste de valeurs prises en charge, consultez la [énumération STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="24005-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="24005-129">[in] Le `CLSID` de la coclasse qui implémente le [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou le [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="24005-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="24005-130">Valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="24005-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="24005-131">[in] Le `IID` de l’interface demandée.</span><span class="sxs-lookup"><span data-stu-id="24005-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="24005-132">Valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="24005-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="24005-133">[out] Un pointeur d’interface vers la version du runtime qui a été chargé.</span><span class="sxs-lookup"><span data-stu-id="24005-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24005-134">Spécifications</span><span class="sxs-lookup"><span data-stu-id="24005-134">Requirements</span></span>  
 <span data-ttu-id="24005-135">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24005-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24005-136">**En-tête :** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="24005-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="24005-137">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="24005-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="24005-138">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24005-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24005-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24005-139">See Also</span></span>  
 [<span data-ttu-id="24005-140">CorBindToCurrentRuntime (fonction)</span><span class="sxs-lookup"><span data-stu-id="24005-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="24005-141">CorBindToRuntime (fonction)</span><span class="sxs-lookup"><span data-stu-id="24005-141">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="24005-142">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="24005-142">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="24005-143">CorBindToRuntimeEx (fonction)</span><span class="sxs-lookup"><span data-stu-id="24005-143">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="24005-144">ICorRuntimeHost (Interface)</span><span class="sxs-lookup"><span data-stu-id="24005-144">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="24005-145">Fonctions d’hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="24005-145">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
