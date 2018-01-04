---
title: "IHostTaskManager::BeginDelayAbort, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.BeginDelayAbort
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a6b37c87f26013dab95f7607e03463437b9797a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="5ded2-102">IHostTaskManager::BeginDelayAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="5ded2-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="5ded2-103">Avertit l’hôte que le code managé entre dans une période dans laquelle la tâche en cours ne doit pas être abandonnée.</span><span class="sxs-lookup"><span data-stu-id="5ded2-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ded2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ded2-104">Syntax</span></span>  
  
```  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5ded2-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5ded2-105">Return Value</span></span>  
  
|<span data-ttu-id="5ded2-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5ded2-106">HRESULT</span></span>|<span data-ttu-id="5ded2-107">Description</span><span class="sxs-lookup"><span data-stu-id="5ded2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ded2-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="5ded2-108">S_OK</span></span>|<span data-ttu-id="5ded2-109">`BeginDelayAbort`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="5ded2-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="5ded2-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5ded2-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5ded2-111">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="5ded2-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5ded2-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5ded2-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5ded2-113">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="5ded2-113">The call timed out.</span></span>|  
|<span data-ttu-id="5ded2-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5ded2-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5ded2-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="5ded2-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5ded2-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5ded2-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5ded2-117">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="5ded2-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5ded2-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5ded2-118">E_FAIL</span></span>|<span data-ttu-id="5ded2-119">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="5ded2-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5ded2-120">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="5ded2-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5ded2-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5ded2-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5ded2-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="5ded2-122">E_UNEXPECTED</span></span>|<span data-ttu-id="5ded2-123">`BeginDelayAbort`a déjà été appelé, mais l’appel correspondant à [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) n’a pas encore été reçus.</span><span class="sxs-lookup"><span data-stu-id="5ded2-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ded2-124">Notes</span><span class="sxs-lookup"><span data-stu-id="5ded2-124">Remarks</span></span>  
 <span data-ttu-id="5ded2-125">L’hôte ne doit pas abandonner la tâche en cours jusqu'à ce que `EndDelayAbort` est appelée.</span><span class="sxs-lookup"><span data-stu-id="5ded2-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="5ded2-126">Si un autre appel à `BeginDelayAbort` est établie sans appel intermédiaire à `EndDelayAbort`, l’hôte doit retourner E_UNEXPECTED à partir de `BeginDelayAbort`et ne doit effectuer aucune action.</span><span class="sxs-lookup"><span data-stu-id="5ded2-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ded2-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5ded2-127">Requirements</span></span>  
 <span data-ttu-id="5ded2-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ded2-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ded2-129">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5ded2-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5ded2-130">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5ded2-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ded2-131">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ded2-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ded2-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ded2-132">See Also</span></span>  
 [<span data-ttu-id="5ded2-133">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="5ded2-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="5ded2-134">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="5ded2-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="5ded2-135">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="5ded2-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="5ded2-136">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="5ded2-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
