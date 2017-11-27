---
title: "IHostTask::Join, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.Join
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::Join
helpviewer_keywords:
- IHostTask::Join method [.NET Framework hosting]
- Join method, IHostTask interface [.NET Framework hosting]
ms.assetid: 2cffcc52-19e0-4ced-a440-fc7375078ac9
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b5dbfcfc87a520925f36e09d4f2d21dbffadfe1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="cfaee-102">IHostTask::Join, méthode</span><span class="sxs-lookup"><span data-stu-id="cfaee-102">IHostTask::Join Method</span></span>
<span data-ttu-id="cfaee-103">Bloque la tâche appelante jusqu'à ce que la tâche représentée par le [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) fin de l’instance, l’intervalle de temps spécifié est dépassé, ou [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) est appelée.</span><span class="sxs-lookup"><span data-stu-id="cfaee-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfaee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cfaee-104">Syntax</span></span>  
  
```  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cfaee-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cfaee-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="cfaee-106">[in] L’intervalle de temps, en millisecondes, pour attendre la fin de la tâche.</span><span class="sxs-lookup"><span data-stu-id="cfaee-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="cfaee-107">Si cet intervalle est écoulé avant que la tâche se termine, la tâche appelante se débloque.</span><span class="sxs-lookup"><span data-stu-id="cfaee-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="cfaee-108">[in] Parmi les [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valeurs.</span><span class="sxs-lookup"><span data-stu-id="cfaee-108">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values.</span></span> <span data-ttu-id="cfaee-109">Une valeur WAIT_ALERTABLE indique l’ordinateur hôte pour réactiver la tâche si `Alert` est appelée avant que `milliseconds` s’écoule.</span><span class="sxs-lookup"><span data-stu-id="cfaee-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cfaee-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="cfaee-110">Return Value</span></span>  
  
|<span data-ttu-id="cfaee-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cfaee-111">HRESULT</span></span>|<span data-ttu-id="cfaee-112">Description</span><span class="sxs-lookup"><span data-stu-id="cfaee-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cfaee-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="cfaee-113">S_OK</span></span>|<span data-ttu-id="cfaee-114">`Join`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="cfaee-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="cfaee-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cfaee-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cfaee-116">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="cfaee-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cfaee-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cfaee-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cfaee-118">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="cfaee-118">The call timed out.</span></span>|  
|<span data-ttu-id="cfaee-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cfaee-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cfaee-120">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="cfaee-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cfaee-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cfaee-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cfaee-122">Un événement a été annulé alors qu’un thread bloqué ou une fibre attendait, ou en cours `IHostTask` instance n’est pas associée à une tâche.</span><span class="sxs-lookup"><span data-stu-id="cfaee-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="cfaee-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cfaee-123">E_FAIL</span></span>|<span data-ttu-id="cfaee-124">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="cfaee-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cfaee-125">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="cfaee-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cfaee-126">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cfaee-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cfaee-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cfaee-127">Requirements</span></span>  
 <span data-ttu-id="cfaee-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfaee-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfaee-129">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cfaee-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cfaee-130">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cfaee-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cfaee-131">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfaee-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfaee-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cfaee-132">See Also</span></span>  
 [<span data-ttu-id="cfaee-133">ICLRTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="cfaee-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="cfaee-134">ICLRTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="cfaee-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="cfaee-135">IHostTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="cfaee-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="cfaee-136">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="cfaee-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="cfaee-137">WAIT_OPTION (énumération)</span><span class="sxs-lookup"><span data-stu-id="cfaee-137">WAIT_OPTION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)
