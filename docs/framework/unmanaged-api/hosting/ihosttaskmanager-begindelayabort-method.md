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
ms.openlocfilehash: 17af69c533c62b6a25d498fb245dfefe162690ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="e76a5-102">IHostTaskManager::BeginDelayAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="e76a5-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="e76a5-103">Avertit l’hôte que le code managé entre dans une période dans laquelle la tâche en cours ne doit pas être abandonnée.</span><span class="sxs-lookup"><span data-stu-id="e76a5-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e76a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e76a5-104">Syntax</span></span>  
  
```  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e76a5-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e76a5-105">Return Value</span></span>  
  
|<span data-ttu-id="e76a5-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e76a5-106">HRESULT</span></span>|<span data-ttu-id="e76a5-107">Description</span><span class="sxs-lookup"><span data-stu-id="e76a5-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e76a5-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e76a5-108">S_OK</span></span>|<span data-ttu-id="e76a5-109">`BeginDelayAbort`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="e76a5-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="e76a5-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e76a5-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e76a5-111">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="e76a5-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e76a5-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e76a5-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e76a5-113">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="e76a5-113">The call timed out.</span></span>|  
|<span data-ttu-id="e76a5-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e76a5-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e76a5-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="e76a5-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e76a5-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e76a5-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e76a5-117">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="e76a5-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e76a5-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e76a5-118">E_FAIL</span></span>|<span data-ttu-id="e76a5-119">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e76a5-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e76a5-120">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e76a5-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e76a5-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e76a5-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e76a5-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="e76a5-122">E_UNEXPECTED</span></span>|<span data-ttu-id="e76a5-123">`BeginDelayAbort`a déjà été appelé, mais l’appel correspondant à [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) n’a pas encore été reçus.</span><span class="sxs-lookup"><span data-stu-id="e76a5-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e76a5-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="e76a5-124">Remarks</span></span>  
 <span data-ttu-id="e76a5-125">L’hôte ne doit pas abandonner la tâche en cours jusqu'à ce que `EndDelayAbort` est appelée.</span><span class="sxs-lookup"><span data-stu-id="e76a5-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="e76a5-126">Si un autre appel à `BeginDelayAbort` est établie sans appel intermédiaire à `EndDelayAbort`, l’hôte doit retourner E_UNEXPECTED à partir de `BeginDelayAbort`et ne doit effectuer aucune action.</span><span class="sxs-lookup"><span data-stu-id="e76a5-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e76a5-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e76a5-127">Requirements</span></span>  
 <span data-ttu-id="e76a5-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e76a5-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e76a5-129">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e76a5-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e76a5-130">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e76a5-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e76a5-131">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e76a5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e76a5-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e76a5-132">See Also</span></span>  
 [<span data-ttu-id="e76a5-133">ICLRTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="e76a5-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="e76a5-134">ICLRTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="e76a5-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="e76a5-135">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="e76a5-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="e76a5-136">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="e76a5-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
