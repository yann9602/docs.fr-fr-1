---
title: ICLRMetaHost, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost
helpviewer_keywords: ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type: apiref
caps.latest.revision: "28"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d271a69847e3bd4dc972ed8e697b8cd15f049fb9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="984e2-102">ICLRMetaHost, interface</span><span class="sxs-lookup"><span data-stu-id="984e2-102">ICLRMetaHost Interface</span></span>
<span data-ttu-id="984e2-103">Fournit des méthodes qui retournent une version spécifique du common language runtime (CLR) en fonction de son numéro de version, répertorient tous les installés, listent tous les runtimes chargés dans un processus spécifique, découvrir la version CLR utilisée pour compiler un assembly, un processus de sortie avec un arrêt de runtime normal et la liaison d’API héritée de requête.</span><span class="sxs-lookup"><span data-stu-id="984e2-103">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="984e2-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="984e2-104">Methods</span></span>  
  
|<span data-ttu-id="984e2-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="984e2-105">Method</span></span>|<span data-ttu-id="984e2-106">Description</span><span class="sxs-lookup"><span data-stu-id="984e2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="984e2-107">EnumerateInstalledRuntimes (méthode)</span><span class="sxs-lookup"><span data-stu-id="984e2-107">EnumerateInstalledRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="984e2-108">Retourne une énumération qui contient un élément valide [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) pointeur d’interface pour chaque version du CLR qui est installée sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="984e2-108">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="984e2-109">EnumerateLoadedRuntimes (méthode)</span><span class="sxs-lookup"><span data-stu-id="984e2-109">EnumerateLoadedRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="984e2-110">Retourne une énumération qui contient un élément valide [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) pointeur d’interface pour chaque CLR qui est chargé dans un processus donné.</span><span class="sxs-lookup"><span data-stu-id="984e2-110">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="984e2-111">Cette méthode remplace [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="984e2-111">This method supersedes [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="984e2-112">ExitProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="984e2-112">ExitProcess Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|<span data-ttu-id="984e2-113">Tente de charger tous les runtimes s’arrête, puis se termine le processus.</span><span class="sxs-lookup"><span data-stu-id="984e2-113">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="984e2-114">Remplace le [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="984e2-114">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="984e2-115">GetRuntime (méthode)</span><span class="sxs-lookup"><span data-stu-id="984e2-115">GetRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|<span data-ttu-id="984e2-116">Obtient le [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface qui correspond à une version particulière du CLR.</span><span class="sxs-lookup"><span data-stu-id="984e2-116">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="984e2-117">Cette méthode remplace la [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) fonction utilisée avec les [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) indicateur.</span><span class="sxs-lookup"><span data-stu-id="984e2-117">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="984e2-118">GetVersionFromFile (méthode)</span><span class="sxs-lookup"><span data-stu-id="984e2-118">GetVersionFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="984e2-119">Obtient d’origine .NET Framework version de compilation l’assembly (stockée dans les métadonnées), étant donnée son chemin d’accès de fichier.</span><span class="sxs-lookup"><span data-stu-id="984e2-119">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="984e2-120">Cette méthode remplace [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span><span class="sxs-lookup"><span data-stu-id="984e2-120">This method supersedes [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="984e2-121">QueryLegacyV2RuntimeBinding (méthode)</span><span class="sxs-lookup"><span data-stu-id="984e2-121">QueryLegacyV2RuntimeBinding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="984e2-122">Retourne une interface qui représente un runtime auquel une stratégie d’activation héritée a été liée, par exemple à l’aide de la `useLegacyV2RuntimeActivationPolicy` de l’attribut le [ \<démarrage > élément](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) entrée de fichier de configuration, en utilisant directement des API d’activation hérité ou en appelant le [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="984e2-122">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="984e2-123">RequestRuntimeLoadedNotification (méthode)</span><span class="sxs-lookup"><span data-stu-id="984e2-123">RequestRuntimeLoadedNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="984e2-124">Garantit un rappel au pointeur fonction spécifié lorsqu’une version CLR est chargée en premier, mais pas encore démarrée.</span><span class="sxs-lookup"><span data-stu-id="984e2-124">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="984e2-125">Cette méthode remplace [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span><span class="sxs-lookup"><span data-stu-id="984e2-125">This method supersedes [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="984e2-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="984e2-126">Remarks</span></span>  
 <span data-ttu-id="984e2-127">La seule façon d’obtenir une instance de cette interface est en appelant le [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) fonctionne comme suit :</span><span class="sxs-lookup"><span data-stu-id="984e2-127">The only way to get an instance of this interface is by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as follows:</span></span>  
  
```  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="984e2-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="984e2-128">Requirements</span></span>  
 <span data-ttu-id="984e2-129">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="984e2-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="984e2-130">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="984e2-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="984e2-131">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="984e2-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="984e2-132">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="984e2-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="984e2-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="984e2-133">See Also</span></span>  
 [<span data-ttu-id="984e2-134">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="984e2-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="984e2-135">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="984e2-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
