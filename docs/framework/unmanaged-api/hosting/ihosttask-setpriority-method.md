---
title: "IHostTask::SetPriority, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.SetPriority
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2f9a57442b1671ef0286536215d10768636e3aa8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="d2163-102">IHostTask::SetPriority, méthode</span><span class="sxs-lookup"><span data-stu-id="d2163-102">IHostTask::SetPriority Method</span></span>
<span data-ttu-id="d2163-103">Le niveau de demande que l’hôte ajuste la priorité de thread de la tâche représentée par le [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="d2163-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2163-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2163-104">Syntax</span></span>  
  
```  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2163-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d2163-105">Parameters</span></span>  
 `newPriority`  
 <span data-ttu-id="d2163-106">[in] Entier qui représente la valeur de priorité de thread demandée pour la tâche représentée par le `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="d2163-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2163-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d2163-107">Return Value</span></span>  
  
|<span data-ttu-id="d2163-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d2163-108">HRESULT</span></span>|<span data-ttu-id="d2163-109">Description</span><span class="sxs-lookup"><span data-stu-id="d2163-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d2163-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d2163-110">S_OK</span></span>|<span data-ttu-id="d2163-111">`SetPriority`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="d2163-111">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="d2163-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d2163-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d2163-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="d2163-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d2163-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d2163-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d2163-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="d2163-115">The call timed out.</span></span>|  
|<span data-ttu-id="d2163-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d2163-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d2163-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="d2163-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d2163-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d2163-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d2163-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="d2163-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d2163-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d2163-120">E_FAIL</span></span>|<span data-ttu-id="d2163-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="d2163-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d2163-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="d2163-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d2163-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d2163-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2163-124">Notes</span><span class="sxs-lookup"><span data-stu-id="d2163-124">Remarks</span></span>  
 <span data-ttu-id="d2163-125">Threads de traitement sont accordé moment à l’aide d’un système de tourniquet qui est basé en partie sur le niveau de priorité d’un thread.</span><span class="sxs-lookup"><span data-stu-id="d2163-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="d2163-126">`SetPriority`permet au CLR de définir ce niveau de priorité de thread pour la tâche actuelle.</span><span class="sxs-lookup"><span data-stu-id="d2163-126">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="d2163-127">Les éléments suivants `newPriority` valeurs sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="d2163-127">The following `newPriority` values are supported.</span></span>  
  
-   <span data-ttu-id="d2163-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="d2163-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
-   <span data-ttu-id="d2163-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="d2163-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
-   <span data-ttu-id="d2163-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="d2163-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
-   <span data-ttu-id="d2163-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="d2163-131">THREAD_PRIORITY_IDLE</span></span>  
  
-   <span data-ttu-id="d2163-132">NIVEAU DE PRIORITÉ</span><span class="sxs-lookup"><span data-stu-id="d2163-132">THREAD_PRIORITY_LOWEST</span></span>  
  
-   <span data-ttu-id="d2163-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="d2163-133">THREAD_PRIORITY_NORMAL</span></span>  
  
-   <span data-ttu-id="d2163-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="d2163-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="d2163-135">Le CLR appelle `SetPriority` lorsque la valeur de la <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> est modifiée par le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d2163-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="d2163-136">Un hôte peut définir ses propres algorithmes pour l’attribution de priorité de thread et est libre d’ignorer cette demande.</span><span class="sxs-lookup"><span data-stu-id="d2163-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2163-137">`SetPriority`ne signale pas si le niveau de priorité de thread a été modifié.</span><span class="sxs-lookup"><span data-stu-id="d2163-137">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="d2163-138">Appelez [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) pour déterminer la valeur de niveau de priorité de thread de la tâche.</span><span class="sxs-lookup"><span data-stu-id="d2163-138">Call [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="d2163-139">Les valeurs de niveau de priorité de thread sont définies par Win32 `SetThreadPriority` (fonction).</span><span class="sxs-lookup"><span data-stu-id="d2163-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="d2163-140">Pour plus d’informations sur la priorité de thread, consultez la documentation de la plateforme Windows.</span><span class="sxs-lookup"><span data-stu-id="d2163-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2163-141">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d2163-141">Requirements</span></span>  
 <span data-ttu-id="d2163-142">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2163-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2163-143">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d2163-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d2163-144">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d2163-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2163-145">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2163-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2163-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2163-146">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="d2163-147">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="d2163-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="d2163-148">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="d2163-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="d2163-149">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="d2163-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="d2163-150">GetPriority, méthode</span><span class="sxs-lookup"><span data-stu-id="d2163-150">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)  
 [<span data-ttu-id="d2163-151">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="d2163-151">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
