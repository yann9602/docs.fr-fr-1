---
title: "IHostTaskManager::ReverseLeaveRuntime, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.ReverseLeaveRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::ReverseLeaveRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseLeaveRuntime method [.NET Framework hosting]
- ReverseLeaveRuntime method [.NET Framework hosting]
ms.assetid: 4837d398-16a1-4e32-902c-022cd1aad3ca
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 634465e2d78dbac41b8791d5be44b2821744f07d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="1710d-102">IHostTaskManager::ReverseLeaveRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="1710d-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="1710d-103">Avertit l’hôte que le contrôle est en laissant le common language runtime (CLR) et une fonction non managée qui a été, à son tour, appelée à partir du code managé.</span><span class="sxs-lookup"><span data-stu-id="1710d-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1710d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1710d-104">Syntax</span></span>  
  
```  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1710d-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1710d-105">Return Value</span></span>  
  
|<span data-ttu-id="1710d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1710d-106">HRESULT</span></span>|<span data-ttu-id="1710d-107">Description</span><span class="sxs-lookup"><span data-stu-id="1710d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1710d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="1710d-108">S_OK</span></span>|<span data-ttu-id="1710d-109">`ReverseLeaveRuntime`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="1710d-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="1710d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1710d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1710d-111">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="1710d-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1710d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1710d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1710d-113">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="1710d-113">The call timed out.</span></span>|  
|<span data-ttu-id="1710d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1710d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1710d-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="1710d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1710d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1710d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1710d-117">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="1710d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1710d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1710d-118">E_FAIL</span></span>|<span data-ttu-id="1710d-119">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="1710d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1710d-120">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="1710d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1710d-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1710d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1710d-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1710d-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="1710d-123">Pas assez de mémoire est disponible pour terminer l’allocation de la ressource demandée.</span><span class="sxs-lookup"><span data-stu-id="1710d-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1710d-124">Notes</span><span class="sxs-lookup"><span data-stu-id="1710d-124">Remarks</span></span>  
 <span data-ttu-id="1710d-125">Le CLR appelle `ReverseLeaveRuntime` pour informer l’hôte que la tâche en cours d’exécution retourne le contrôle à une fonction non managée qui a été, à son tour, appelée à partir du code managé via la plateforme de code non managé.</span><span class="sxs-lookup"><span data-stu-id="1710d-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="1710d-126">Chaque appel à `ReverseLeaveRuntime` correspond à un appel correspondant à [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="1710d-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1710d-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1710d-127">Requirements</span></span>  
 <span data-ttu-id="1710d-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1710d-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1710d-129">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1710d-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1710d-130">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1710d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1710d-131">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1710d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1710d-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1710d-132">See Also</span></span>  
 [<span data-ttu-id="1710d-133">CallNeedsHostHook, méthode</span><span class="sxs-lookup"><span data-stu-id="1710d-133">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)  
 [<span data-ttu-id="1710d-134">EnterRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="1710d-134">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)  
 [<span data-ttu-id="1710d-135">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="1710d-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="1710d-136">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="1710d-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="1710d-137">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="1710d-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="1710d-138">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="1710d-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="1710d-139">LeaveRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="1710d-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)  
 [<span data-ttu-id="1710d-140">L’appel de plateforme plus approfondie</span><span class="sxs-lookup"><span data-stu-id="1710d-140">A Closer Look at Platform Invoke</span></span>](http://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)
