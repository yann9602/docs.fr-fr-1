---
title: "IHostGCManager::ThreadIsBlockingForSuspension, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostGCManager.ThreadIsBlockingForSuspension
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostGCManager::ThreadIsBlockingForSuspension
helpviewer_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: 2657d45d-26d2-4d0a-8473-32b652e3321d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5ea5f110754b8b607673bcbd4060dee85cd5ca9f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="0cb64-102">IHostGCManager::ThreadIsBlockingForSuspension, méthode</span><span class="sxs-lookup"><span data-stu-id="0cb64-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="0cb64-103">Avertit l’hôte que le thread à partir de laquelle l’appel de méthode a été effectué sur le point de bloquer pour un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0cb64-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cb64-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cb64-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0cb64-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0cb64-105">Return Value</span></span>  
  
|<span data-ttu-id="0cb64-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0cb64-106">HRESULT</span></span>|<span data-ttu-id="0cb64-107">Description</span><span class="sxs-lookup"><span data-stu-id="0cb64-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0cb64-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="0cb64-108">S_OK</span></span>|<span data-ttu-id="0cb64-109">`ThreadIsBlockingForSuspension`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="0cb64-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="0cb64-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0cb64-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0cb64-111">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="0cb64-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0cb64-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0cb64-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0cb64-113">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="0cb64-113">The call timed out.</span></span>|  
|<span data-ttu-id="0cb64-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0cb64-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0cb64-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="0cb64-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0cb64-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0cb64-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0cb64-117">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="0cb64-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0cb64-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0cb64-118">E_FAIL</span></span>|<span data-ttu-id="0cb64-119">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="0cb64-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0cb64-120">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="0cb64-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0cb64-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0cb64-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cb64-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="0cb64-122">Remarks</span></span>  
 <span data-ttu-id="0cb64-123">Le CLR appelle généralement la `ThreadIsBlockForSuspension` méthode en vue d’un garbage collection, pour permettre à l’hôte de replanifier le thread pour les tâches non managées.</span><span class="sxs-lookup"><span data-stu-id="0cb64-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0cb64-124">L’hôte peut replanifier des tâches uniquement après un appel à `ThreadIsBlockingForSuspension`.</span><span class="sxs-lookup"><span data-stu-id="0cb64-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="0cb64-125">Après le runtime appelle [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), l’hôte ne doit pas replanifier une tâche.</span><span class="sxs-lookup"><span data-stu-id="0cb64-125">After the runtime calls [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cb64-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0cb64-126">Requirements</span></span>  
 <span data-ttu-id="0cb64-127">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cb64-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cb64-128">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0cb64-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0cb64-129">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0cb64-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0cb64-130">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cb64-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cb64-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0cb64-131">See Also</span></span>  
 [<span data-ttu-id="0cb64-132">ICLRTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="0cb64-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="0cb64-133">ICLRTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="0cb64-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="0cb64-134">IHostTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="0cb64-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="0cb64-135">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="0cb64-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="0cb64-136">IHostGCManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="0cb64-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
