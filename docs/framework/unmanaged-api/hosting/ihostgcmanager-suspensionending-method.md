---
title: "IHostGCManager::SuspensionEnding, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostGCManager.SuspensionEnding
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostGCManager::SuspensionEnding
helpviewer_keywords:
- SuspensionEnding method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionEnding method [.NET Framework hosting]
ms.assetid: 8849a1db-17f0-44b7-880a-bd36d431eb91
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9952e62d4979efa0d07b19f183ca71adcc643365
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="eb687-102">IHostGCManager::SuspensionEnding, méthode</span><span class="sxs-lookup"><span data-stu-id="eb687-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="eb687-103">Avertit l’hôte que le common language runtime (CLR) reprend l’exécution de tâches sur les threads qui avaient été interrompus pour un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="eb687-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb687-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb687-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb687-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eb687-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="eb687-106">[in] La génération de garbage collection qui est en train de se terminer, à partir de laquelle le thread se poursuit.</span><span class="sxs-lookup"><span data-stu-id="eb687-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb687-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="eb687-107">Return Value</span></span>  
  
|<span data-ttu-id="eb687-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eb687-108">HRESULT</span></span>|<span data-ttu-id="eb687-109">Description</span><span class="sxs-lookup"><span data-stu-id="eb687-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eb687-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="eb687-110">S_OK</span></span>|<span data-ttu-id="eb687-111">`SuspensionEnding`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="eb687-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="eb687-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eb687-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eb687-113">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="eb687-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eb687-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eb687-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eb687-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="eb687-115">The call timed out.</span></span>|  
|<span data-ttu-id="eb687-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eb687-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eb687-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="eb687-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eb687-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eb687-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eb687-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="eb687-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eb687-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eb687-120">E_FAIL</span></span>|<span data-ttu-id="eb687-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="eb687-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eb687-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="eb687-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eb687-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="eb687-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb687-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="eb687-124">Remarks</span></span>  
 <span data-ttu-id="eb687-125">Le CLR appelle `SuspensionEnding` une fois qu’il effectue un garbage collection, pour informer l’hôte que le thread reprend son exécution.</span><span class="sxs-lookup"><span data-stu-id="eb687-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="eb687-126">Ne replanifiez pas le thread de de que l’appel de méthode a été effectué à partir.</span><span class="sxs-lookup"><span data-stu-id="eb687-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb687-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="eb687-127">Requirements</span></span>  
 <span data-ttu-id="eb687-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb687-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb687-129">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eb687-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eb687-130">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eb687-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb687-131">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb687-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb687-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb687-132">See Also</span></span>  
 [<span data-ttu-id="eb687-133">ICLRTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="eb687-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="eb687-134">ICLRTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="eb687-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="eb687-135">IHostTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="eb687-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="eb687-136">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="eb687-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="eb687-137">IHostGCManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="eb687-137">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
