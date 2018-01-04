---
title: "IHostManualEvent::Wait, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostManualEvent.Wait
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostManualEvent::Wait
helpviewer_keywords:
- IHostManualEvent::Wait method [.NET Framework hosting]
- Wait method, IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 1fbb7d8b-8a23-4c2b-8376-1a70cd2d6030
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2dd456a3901f91fc8598a707a5699637ec450dbd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmanualeventwait-method"></a><span data-ttu-id="6890e-102">IHostManualEvent::Wait, méthode</span><span class="sxs-lookup"><span data-stu-id="6890e-102">IHostManualEvent::Wait Method</span></span>
<span data-ttu-id="6890e-103">Fait en [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance attendre qu’il appartient, ou un certain laps de temps.</span><span class="sxs-lookup"><span data-stu-id="6890e-103">Causes the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to wait until it is owned, or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6890e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6890e-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6890e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6890e-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="6890e-106">[in] Le nombre de millisecondes à attendre avant de retourner, si actuel `IHostManualEvent` instance n’est pas détenue.</span><span class="sxs-lookup"><span data-stu-id="6890e-106">[in] The number of milliseconds to wait before returning, if the current `IHostManualEvent` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="6890e-107">[in] Un de le [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valeurs, indiquant l’action de l’hôte doit effectuer si cette opération bloque.</span><span class="sxs-lookup"><span data-stu-id="6890e-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6890e-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6890e-108">Return Value</span></span>  
  
|<span data-ttu-id="6890e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6890e-109">HRESULT</span></span>|<span data-ttu-id="6890e-110">Description</span><span class="sxs-lookup"><span data-stu-id="6890e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6890e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6890e-111">S_OK</span></span>|<span data-ttu-id="6890e-112">`Wait`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="6890e-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="6890e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6890e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6890e-114">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="6890e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6890e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6890e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6890e-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="6890e-116">The call timed out.</span></span>|  
|<span data-ttu-id="6890e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6890e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6890e-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="6890e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6890e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6890e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6890e-120">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="6890e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6890e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6890e-121">E_FAIL</span></span>|<span data-ttu-id="6890e-122">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="6890e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6890e-123">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="6890e-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6890e-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6890e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6890e-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="6890e-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="6890e-126">L’hôte a détecté un interblocage pendant l’intervalle d’attente et choisissez actuel `IHostManualEvent` instance comme victime du blocage.</span><span class="sxs-lookup"><span data-stu-id="6890e-126">The host detected a deadlock during the wait interval, and chose the current `IHostManualEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6890e-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6890e-127">Requirements</span></span>  
 <span data-ttu-id="6890e-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6890e-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6890e-129">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6890e-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6890e-130">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6890e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6890e-131">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6890e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6890e-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6890e-132">See Also</span></span>  
 [<span data-ttu-id="6890e-133">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="6890e-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="6890e-134">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="6890e-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="6890e-135">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="6890e-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="6890e-136">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="6890e-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="6890e-137">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="6890e-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
