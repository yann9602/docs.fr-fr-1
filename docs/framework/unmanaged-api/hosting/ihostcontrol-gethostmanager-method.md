---
title: "IHostControl::GetHostManager, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostControl.GetHostManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostControl::GetHostManager
helpviewer_keywords:
- GetHostManager method [.NET Framework hosting]
- IHostControl::GetHostManager method [.NET Framework hosting]
ms.assetid: 0fa34bca-ed18-4626-9e78-d33684d18edb
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6701350fa9bdb51843b117b0191b677e739807a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="db8c3-102">IHostControl::GetHostManager, méthode</span><span class="sxs-lookup"><span data-stu-id="db8c3-102">IHostControl::GetHostManager Method</span></span>
<span data-ttu-id="db8c3-103">Obtient un pointeur d’interface à l’implémentation de l’hôte de l’interface avec l’objet `IID`.</span><span class="sxs-lookup"><span data-stu-id="db8c3-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db8c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db8c3-104">Syntax</span></span>  
  
```  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db8c3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="db8c3-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="db8c3-106">[in] Le `IID` de l’interface que le common language runtime (CLR) effectue une requête.</span><span class="sxs-lookup"><span data-stu-id="db8c3-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="db8c3-107">[out] Pointeur vers l’interface implémentée par l’hôte, ou null si l’hôte ne prend pas en charge cette interface.</span><span class="sxs-lookup"><span data-stu-id="db8c3-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db8c3-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="db8c3-108">Return Value</span></span>  
  
|<span data-ttu-id="db8c3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db8c3-109">HRESULT</span></span>|<span data-ttu-id="db8c3-110">Description</span><span class="sxs-lookup"><span data-stu-id="db8c3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db8c3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="db8c3-111">S_OK</span></span>|<span data-ttu-id="db8c3-112">`GetHostManager`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="db8c3-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="db8c3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="db8c3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="db8c3-114">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="db8c3-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="db8c3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="db8c3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="db8c3-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="db8c3-116">The call timed out.</span></span>|  
|<span data-ttu-id="db8c3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="db8c3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="db8c3-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="db8c3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="db8c3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="db8c3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="db8c3-120">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="db8c3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="db8c3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="db8c3-121">E_FAIL</span></span>|<span data-ttu-id="db8c3-122">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="db8c3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="db8c3-123">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="db8c3-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="db8c3-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="db8c3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="db8c3-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="db8c3-125">E_INVALIDARG</span></span>|<span data-ttu-id="db8c3-126">Demandé `IID` n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="db8c3-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="db8c3-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="db8c3-127">E_NOINTERFACE</span></span>|<span data-ttu-id="db8c3-128">L’interface demandée n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="db8c3-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db8c3-129">Notes</span><span class="sxs-lookup"><span data-stu-id="db8c3-129">Remarks</span></span>  
 <span data-ttu-id="db8c3-130">Le CLR interroge l’hôte pour déterminer si elle prend en charge un ou plusieurs des interfaces suivantes :</span><span class="sxs-lookup"><span data-stu-id="db8c3-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
-   [<span data-ttu-id="db8c3-131">IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="db8c3-131">IHostMemoryManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
  
-   [<span data-ttu-id="db8c3-132">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="db8c3-132">IHostTaskManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
  
-   [<span data-ttu-id="db8c3-133">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="db8c3-133">IHostThreadPoolManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
  
-   [<span data-ttu-id="db8c3-134">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="db8c3-134">IHostIoCompletionManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
  
-   [<span data-ttu-id="db8c3-135">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="db8c3-135">IHostSyncManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
  
-   [<span data-ttu-id="db8c3-136">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="db8c3-136">IHostAssemblyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
  
-   [<span data-ttu-id="db8c3-137">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="db8c3-137">IHostGCManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
  
-   [<span data-ttu-id="db8c3-138">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="db8c3-138">IHostPolicyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
  
-   [<span data-ttu-id="db8c3-139">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="db8c3-139">IHostSecurityManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="db8c3-140">Si l’hôte prend en charge l’interface spécifiée, il définit `ppObject` à son implémentation de cette interface.</span><span class="sxs-lookup"><span data-stu-id="db8c3-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="db8c3-141">Dans le cas contraire, il définit `ppObject` avec la valeur null.</span><span class="sxs-lookup"><span data-stu-id="db8c3-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="db8c3-142">Le CLR n’appelle pas `Release` sur les gestionnaires d’hôte, même lorsque vous l’avez arrêté.</span><span class="sxs-lookup"><span data-stu-id="db8c3-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db8c3-143">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="db8c3-143">Requirements</span></span>  
 <span data-ttu-id="db8c3-144">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db8c3-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db8c3-145">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="db8c3-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db8c3-146">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="db8c3-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db8c3-147">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db8c3-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db8c3-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db8c3-148">See Also</span></span>  
 [<span data-ttu-id="db8c3-149">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="db8c3-149">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
