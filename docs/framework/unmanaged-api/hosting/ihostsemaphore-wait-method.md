---
title: "IHostSemaphore::Wait, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSemaphore.Wait
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSemaphore::Wait
helpviewer_keywords:
- IHostSemaphore::Wait method [.NET Framework hosting]
- Wait method, IHostSemaphore interface [.NET Framework hosting]
ms.assetid: 0da962a3-ce55-44dd-ab7a-14ad7105af4a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d30a946cadc312e683d256ce6f08528cffa95481
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="8aeb9-102">IHostSemaphore::Wait, méthode</span><span class="sxs-lookup"><span data-stu-id="8aeb9-102">IHostSemaphore::Wait Method</span></span>
<span data-ttu-id="8aeb9-103">Fait en [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance attendre qu’elle appartient ou la quantité de temps spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8aeb9-103">Causes the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aeb9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8aeb9-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8aeb9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8aeb9-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="8aeb9-106">[in] Le nombre de millisecondes à attendre avant de retourner, si actuel `IHostSemaphore` instance n’est pas détenue.</span><span class="sxs-lookup"><span data-stu-id="8aeb9-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="8aeb9-107">[in] Parmi les [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valeurs, en spécifiant l’action l’hôte doit effectuer si cette opération bloque.</span><span class="sxs-lookup"><span data-stu-id="8aeb9-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8aeb9-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8aeb9-108">Return Value</span></span>  
  
|<span data-ttu-id="8aeb9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8aeb9-109">HRESULT</span></span>|<span data-ttu-id="8aeb9-110">Description</span><span class="sxs-lookup"><span data-stu-id="8aeb9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8aeb9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8aeb9-111">S_OK</span></span>|<span data-ttu-id="8aeb9-112">`Wait`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="8aeb9-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="8aeb9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8aeb9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8aeb9-114">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="8aeb9-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8aeb9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8aeb9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8aeb9-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="8aeb9-116">The call timed out.</span></span>|  
|<span data-ttu-id="8aeb9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8aeb9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8aeb9-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="8aeb9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8aeb9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8aeb9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8aeb9-120">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="8aeb9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8aeb9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8aeb9-121">E_FAIL</span></span>|<span data-ttu-id="8aeb9-122">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="8aeb9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8aeb9-123">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="8aeb9-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8aeb9-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8aeb9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8aeb9-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="8aeb9-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="8aeb9-126">L’hôte a détecté un interblocage pendant l’intervalle d’attente et choisissez actuel `IHostSemaphore` instance comme victime du blocage.</span><span class="sxs-lookup"><span data-stu-id="8aeb9-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8aeb9-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8aeb9-127">Requirements</span></span>  
 <span data-ttu-id="8aeb9-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8aeb9-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aeb9-129">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8aeb9-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8aeb9-130">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8aeb9-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8aeb9-131">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aeb9-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aeb9-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8aeb9-132">See Also</span></span>  
 [<span data-ttu-id="8aeb9-133">ICLRSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="8aeb9-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="8aeb9-134">IHostAutoEvent (Interface)</span><span class="sxs-lookup"><span data-stu-id="8aeb9-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="8aeb9-135">IHostManualEvent (Interface)</span><span class="sxs-lookup"><span data-stu-id="8aeb9-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="8aeb9-136">IHostSemaphore (Interface)</span><span class="sxs-lookup"><span data-stu-id="8aeb9-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="8aeb9-137">IHostSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="8aeb9-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
