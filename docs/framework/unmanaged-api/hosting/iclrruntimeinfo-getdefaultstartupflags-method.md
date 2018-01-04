---
title: "ICLRRuntimeInfo::GetDefaultStartupFlags, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.GetDefaultStartupFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b278a791c7e5418322a80bc6478f75791a35af8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="13e0d-102">ICLRRuntimeInfo::GetDefaultStartupFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="13e0d-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="13e0d-103">Obtient les indicateurs de démarrage et le fichier de configuration hôte qui permet de démarrer le runtime.</span><span class="sxs-lookup"><span data-stu-id="13e0d-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13e0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13e0d-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13e0d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="13e0d-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="13e0d-106">[out] Pointeur vers les indicateurs de démarrage hôtes actuellement définis.</span><span class="sxs-lookup"><span data-stu-id="13e0d-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="13e0d-107">[out] Pointeur vers le chemin d’accès du répertoire du fichier de configuration hôte en cours.</span><span class="sxs-lookup"><span data-stu-id="13e0d-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="13e0d-108">[dans, out] Lors de l’entrée, la taille de `pwzHostConfigFile`, pour éviter les dépassements de mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="13e0d-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="13e0d-109">Si `pwzHostConfigFile` est null, la méthode retourne la taille requise de `pwzHostConfigFile` pour préallocation.</span><span class="sxs-lookup"><span data-stu-id="13e0d-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13e0d-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="13e0d-110">Return Value</span></span>  
 <span data-ttu-id="13e0d-111">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l’échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="13e0d-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="13e0d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13e0d-112">HRESULT</span></span>|<span data-ttu-id="13e0d-113">Description</span><span class="sxs-lookup"><span data-stu-id="13e0d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13e0d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="13e0d-114">S_OK</span></span>|<span data-ttu-id="13e0d-115">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="13e0d-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13e0d-116">Notes</span><span class="sxs-lookup"><span data-stu-id="13e0d-116">Remarks</span></span>  
 <span data-ttu-id="13e0d-117">Cette méthode retourne les valeurs d’indicateur par défaut (`STARTUP_CONCURRENT_GC` et `NULL`), ou les valeurs fournies par un appel précédent à la [ICLRRuntimeInfo::SetDefaultStartupFlags, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), ou les valeurs définies par un de la `CorBind*` méthodes qu’ils sont liés à cette exécution.</span><span class="sxs-lookup"><span data-stu-id="13e0d-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13e0d-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="13e0d-118">Requirements</span></span>  
 <span data-ttu-id="13e0d-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13e0d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13e0d-120">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="13e0d-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="13e0d-121">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="13e0d-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13e0d-122">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13e0d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e0d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13e0d-123">See Also</span></span>  
 [<span data-ttu-id="13e0d-124">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="13e0d-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="13e0d-125">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="13e0d-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="13e0d-126">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="13e0d-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
