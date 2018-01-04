---
title: "ICLRTask::SwitchIn, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.SwitchIn
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::SwitchIn
helpviewer_keywords:
- ICLRTask::SwitchIn method [.NET Framework hosting]
- SwitchIn method [.NET Framework hosting]
ms.assetid: 3d37ce20-aa65-4043-8f13-7c728b5d8a52
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e99fc43dea70d456bbaab9bba63e5a018e9e9201
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="7ddf0-102">ICLRTask::SwitchIn, méthode</span><span class="sxs-lookup"><span data-stu-id="7ddf0-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="7ddf0-103">Notifie le common language runtime (CLR) que la tâche qui en cours [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance représente est maintenant en état de fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="7ddf0-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ddf0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ddf0-104">Syntax</span></span>  
  
```  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ddf0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7ddf0-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="7ddf0-106">[in] Un handle du thread physique sur lequel la tâche est représentée par le `ICLRTask` instance est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="7ddf0-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ddf0-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7ddf0-107">Return Value</span></span>  
  
|<span data-ttu-id="7ddf0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7ddf0-108">HRESULT</span></span>|<span data-ttu-id="7ddf0-109">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7ddf0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7ddf0-110">S_OK</span></span>|<span data-ttu-id="7ddf0-111">`SwitchIn`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="7ddf0-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="7ddf0-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7ddf0-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7ddf0-113">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="7ddf0-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7ddf0-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7ddf0-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7ddf0-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="7ddf0-115">The call timed out.</span></span>|  
|<span data-ttu-id="7ddf0-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7ddf0-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7ddf0-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="7ddf0-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7ddf0-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7ddf0-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7ddf0-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="7ddf0-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7ddf0-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7ddf0-120">E_FAIL</span></span>|<span data-ttu-id="7ddf0-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="7ddf0-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7ddf0-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="7ddf0-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7ddf0-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7ddf0-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7ddf0-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="7ddf0-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="7ddf0-125">`SwitchIn`a été appelé sans un appel précédent à [SwitchOut, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span><span class="sxs-lookup"><span data-stu-id="7ddf0-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ddf0-126">Notes</span><span class="sxs-lookup"><span data-stu-id="7ddf0-126">Remarks</span></span>  
 <span data-ttu-id="7ddf0-127">Le `threadHandle` paramètre représente un handle vers le thread de système d’exploitation sur lequel la tâche est représentée par le `ICLRTask` instance a été planifiée.</span><span class="sxs-lookup"><span data-stu-id="7ddf0-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="7ddf0-128">Si l’emprunt d’identité s’est produite sur ce thread, vous devez appeler [IHostSecurityManager::RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) avant de basculer dans la tâche.</span><span class="sxs-lookup"><span data-stu-id="7ddf0-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ddf0-129">Un appel à `SwitchIn` sans un appel précédent à `SwitchOut` échoue avec une valeur HRESULT de HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="7ddf0-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ddf0-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7ddf0-130">Requirements</span></span>  
 <span data-ttu-id="7ddf0-131">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ddf0-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ddf0-132">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7ddf0-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7ddf0-133">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7ddf0-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ddf0-134">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ddf0-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ddf0-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ddf0-135">See Also</span></span>  
 [<span data-ttu-id="7ddf0-136">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="7ddf0-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="7ddf0-137">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="7ddf0-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="7ddf0-138">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="7ddf0-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="7ddf0-139">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="7ddf0-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
