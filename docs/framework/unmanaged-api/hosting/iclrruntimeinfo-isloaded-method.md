---
title: "ICLRRuntimeInfo::IsLoaded, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.IsLoaded
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f1a83db3a5fc7b5f8b4ad763208fa31ab8f840e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="0685f-102">ICLRRuntimeInfo::IsLoaded, méthode</span><span class="sxs-lookup"><span data-stu-id="0685f-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="0685f-103">Indique si le common language runtime (CLR) associées à la [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface est chargé dans un processus.</span><span class="sxs-lookup"><span data-stu-id="0685f-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="0685f-104">Un runtime peut être chargé sans également en cours de démarrage.</span><span class="sxs-lookup"><span data-stu-id="0685f-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0685f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0685f-105">Syntax</span></span>  
  
```  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0685f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0685f-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="0685f-107">[in] Handle vers le processus.</span><span class="sxs-lookup"><span data-stu-id="0685f-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="0685f-108">[out] `true` si le CLR est chargé dans le processus ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="0685f-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0685f-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0685f-109">Return Value</span></span>  
 <span data-ttu-id="0685f-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="0685f-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0685f-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0685f-111">HRESULT</span></span>|<span data-ttu-id="0685f-112">Description</span><span class="sxs-lookup"><span data-stu-id="0685f-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0685f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="0685f-113">S_OK</span></span>|<span data-ttu-id="0685f-114">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="0685f-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="0685f-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="0685f-115">E_POINTER</span></span>|<span data-ttu-id="0685f-116">`pbLoaded` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="0685f-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0685f-117">Notes</span><span class="sxs-lookup"><span data-stu-id="0685f-117">Remarks</span></span>  
 <span data-ttu-id="0685f-118">Cette méthode est à compatibilité descendante avec les fonctions et les interfaces suivantes :</span><span class="sxs-lookup"><span data-stu-id="0685f-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
-   <span data-ttu-id="0685f-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface (dans l’API d’hébergement .NET Framework version 1).</span><span class="sxs-lookup"><span data-stu-id="0685f-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
-   <span data-ttu-id="0685f-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface (dans l’API d’hébergement .NET Framework 2.0).</span><span class="sxs-lookup"><span data-stu-id="0685f-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
-   <span data-ttu-id="0685f-121">Deprecated `CorBindTo*` fonctions (consultez [déconseillée des fonctions d’hébergement CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) dans l’API d’hébergement .NET Framework 2.0).</span><span class="sxs-lookup"><span data-stu-id="0685f-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="0685f-122">Un hôte peut appeler une des déconseillées `CorBindTo*` fonctions, telles que la [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) fonction, pour instancier une version spécifique du CLR.</span><span class="sxs-lookup"><span data-stu-id="0685f-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="0685f-123">L’hôte peut ensuite appeler la [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) (méthode) et spécifiez le numéro de version pour obtenir un [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="0685f-123">The host could then call the [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="0685f-124">Si l’hôte appelle ensuite la `IsLoaded` méthode sur le [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, `pbLoaded` retourne `true`; sinon, elle retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="0685f-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0685f-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0685f-125">Requirements</span></span>  
 <span data-ttu-id="0685f-126">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0685f-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0685f-127">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0685f-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0685f-128">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0685f-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0685f-129">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0685f-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0685f-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0685f-130">See Also</span></span>  
 [<span data-ttu-id="0685f-131">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="0685f-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="0685f-132">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="0685f-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="0685f-133">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="0685f-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
