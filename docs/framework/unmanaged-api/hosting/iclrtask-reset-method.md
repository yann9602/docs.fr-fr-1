---
title: "ICLRTask::Reset, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.Reset
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c50dc4770665e2b049f41a105b58231221b8e9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="97599-102">ICLRTask::Reset, méthode</span><span class="sxs-lookup"><span data-stu-id="97599-102">ICLRTask::Reset Method</span></span>
<span data-ttu-id="97599-103">Informe le common language runtime (CLR) que l’hôte a terminé une tâche et permet au Runtime de réutiliser l’actuel [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance pour représenter une autre tâche.</span><span class="sxs-lookup"><span data-stu-id="97599-103">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97599-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97599-104">Syntax</span></span>  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97599-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="97599-105">Parameters</span></span>  
 `fFull`  
 <span data-ttu-id="97599-106">[in] `true`, si le runtime doit réinitialiser toutes les valeurs statiques liées au thread en plus de la sécurité et les paramètres régionaux relatives à actuel `ICLRTask` instance ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="97599-106">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="97599-107">Si la valeur est `true`, le runtime réinitialise les données stockées à l’aide de <xref:System.Threading.Thread.AllocateDataSlot%2A> ou <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span><span class="sxs-lookup"><span data-stu-id="97599-107">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97599-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="97599-108">Return Value</span></span>  
  
|<span data-ttu-id="97599-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="97599-109">HRESULT</span></span>|<span data-ttu-id="97599-110">Description</span><span class="sxs-lookup"><span data-stu-id="97599-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="97599-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="97599-111">S_OK</span></span>|<span data-ttu-id="97599-112">`Reset`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="97599-112">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="97599-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="97599-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="97599-114">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel.</span><span class="sxs-lookup"><span data-stu-id="97599-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="97599-115">avec succès</span><span class="sxs-lookup"><span data-stu-id="97599-115">successfully</span></span>|  
|<span data-ttu-id="97599-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="97599-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="97599-117">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="97599-117">The call timed out.</span></span>|  
|<span data-ttu-id="97599-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="97599-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="97599-119">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="97599-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="97599-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="97599-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="97599-121">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="97599-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="97599-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="97599-122">E_FAIL</span></span>|<span data-ttu-id="97599-123">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="97599-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="97599-124">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="97599-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="97599-125">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="97599-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97599-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="97599-126">Remarks</span></span>  
 <span data-ttu-id="97599-127">Le CLR peut recycler précédemment créé `ICLRTask` instances afin d’éviter la surcharge de la création de nouvelles instances à plusieurs reprises chaque fois qu’il a besoin d’une nouvelle tâche.</span><span class="sxs-lookup"><span data-stu-id="97599-127">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="97599-128">L’hôte active cette fonction en appelant `ICLRTask::Reset` au lieu de [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) lorsqu’il a terminé une tâche.</span><span class="sxs-lookup"><span data-stu-id="97599-128">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="97599-129">La liste suivante résume le cycle de vie normal d’une `ICLRTask` instance :</span><span class="sxs-lookup"><span data-stu-id="97599-129">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1.  <span data-ttu-id="97599-130">Le runtime crée un nouveau `ICLRTask` instance.</span><span class="sxs-lookup"><span data-stu-id="97599-130">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2.  <span data-ttu-id="97599-131">Le runtime appelle [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) pour obtenir une référence à la tâche hôte actuelle.</span><span class="sxs-lookup"><span data-stu-id="97599-131">The runtime calls [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3.  <span data-ttu-id="97599-132">Le runtime appelle [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) à associer la nouvelle instance de la tâche de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="97599-132">The runtime calls [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4.  <span data-ttu-id="97599-133">La tâche s’exécute et se termine.</span><span class="sxs-lookup"><span data-stu-id="97599-133">The task executes and completes.</span></span>  
  
5.  <span data-ttu-id="97599-134">L’hôte détruit la tâche en appelant `ICLRTask::ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="97599-134">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="97599-135">`Reset`modifie ce scénario de deux façons.</span><span class="sxs-lookup"><span data-stu-id="97599-135">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="97599-136">À l’étape 5 ci-dessus, l’hôte appelle `Reset` pour réinitialiser la tâche à un état propre, puis découple le `ICLRTask` instance à partir de son associé [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="97599-136">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span> <span data-ttu-id="97599-137">Si vous le souhaitez, l’hôte peut également mettre en cache le `IHostTask` instance pour une réutilisation.</span><span class="sxs-lookup"><span data-stu-id="97599-137">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="97599-138">Dans l’étape 1 ci-dessus, le runtime extrait un recyclage `ICLRTask` à partir du cache au lieu de créer une nouvelle instance.</span><span class="sxs-lookup"><span data-stu-id="97599-138">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="97599-139">Cette approche fonctionne bien lorsque l’hôte dispose également d’un pool de tâches de travail réutilisables.</span><span class="sxs-lookup"><span data-stu-id="97599-139">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="97599-140">Lorsque l’hôte détruit l’une de ses `IHostTask` instances, elle détruit correspondant `ICLRTask` en appelant `ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="97599-140">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97599-141">Spécifications</span><span class="sxs-lookup"><span data-stu-id="97599-141">Requirements</span></span>  
 <span data-ttu-id="97599-142">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97599-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97599-143">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="97599-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97599-144">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="97599-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97599-145">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97599-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97599-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97599-146">See Also</span></span>  
 [<span data-ttu-id="97599-147">ICLRTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="97599-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="97599-148">ICLRTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="97599-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="97599-149">IHostTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="97599-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="97599-150">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="97599-150">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
