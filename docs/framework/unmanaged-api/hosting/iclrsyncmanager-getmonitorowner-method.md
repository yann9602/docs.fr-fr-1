---
title: "ICLRSyncManager::GetMonitorOwner, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager.GetMonitorOwner
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager::GetMonitorOwner
helpviewer_keywords:
- ICLRSyncManager::GetMonitorOwner method [.NET Framework hosting]
- GetMonitorOwner method [.NET Framework hosting]
ms.assetid: 840983a4-396d-47b4-86a0-d35f9b437cdb
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 90fbba9a5aead27d79c5355d69bc12481e826b65
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="98a7c-102">ICLRSyncManager::GetMonitorOwner, méthode</span><span class="sxs-lookup"><span data-stu-id="98a7c-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="98a7c-103">Obtient le [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance qui possède l’analyseur identifié par le cookie spécifié.</span><span class="sxs-lookup"><span data-stu-id="98a7c-103">Gets the [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98a7c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98a7c-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="98a7c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="98a7c-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="98a7c-106">[in] Le cookie associé à l’analyse.</span><span class="sxs-lookup"><span data-stu-id="98a7c-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="98a7c-107">[out] Un pointeur vers le `IHostTask` qui possède actuellement l’analyseur, ou null si aucune tâche n’est propriétaire.</span><span class="sxs-lookup"><span data-stu-id="98a7c-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98a7c-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="98a7c-108">Return Value</span></span>  
  
|<span data-ttu-id="98a7c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="98a7c-109">HRESULT</span></span>|<span data-ttu-id="98a7c-110">Description</span><span class="sxs-lookup"><span data-stu-id="98a7c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="98a7c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="98a7c-111">S_OK</span></span>|<span data-ttu-id="98a7c-112">`GetMonitorOwner`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="98a7c-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="98a7c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="98a7c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="98a7c-114">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="98a7c-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="98a7c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="98a7c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="98a7c-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="98a7c-116">The call timed out.</span></span>|  
|<span data-ttu-id="98a7c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="98a7c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="98a7c-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="98a7c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="98a7c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="98a7c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="98a7c-120">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="98a7c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="98a7c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="98a7c-121">E_FAIL</span></span>|<span data-ttu-id="98a7c-122">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="98a7c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="98a7c-123">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="98a7c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="98a7c-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="98a7c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98a7c-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="98a7c-125">Remarks</span></span>  
 <span data-ttu-id="98a7c-126">L’hôte appelle généralement `GetMonitorOwner` dans le cadre d’un mécanisme de détection de blocage.</span><span class="sxs-lookup"><span data-stu-id="98a7c-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="98a7c-127">Le cookie est associé à un analyseur lorsqu’il est créé à l’aide d’un appel à [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="98a7c-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98a7c-128">Un appel pour libérer l’événement sous-jacent de l’analyseur peut se bloquer, mais pas blocage — si un appel à cette méthode est actuellement en vigueur sur le cookie associé à ce moniteur.</span><span class="sxs-lookup"><span data-stu-id="98a7c-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="98a7c-129">Autres tâches peuvent également se bloquer si elles tentent d’acquérir ce moniteur.</span><span class="sxs-lookup"><span data-stu-id="98a7c-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="98a7c-130">`GetMonitorOwner`Retourne toujours immédiatement et peut être appelée à tout moment après un appel à `CreateMonitorEvent`.</span><span class="sxs-lookup"><span data-stu-id="98a7c-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="98a7c-131">L’ordinateur hôte n’a pas besoin d’attendre une tâche est en attente sur l’événement.</span><span class="sxs-lookup"><span data-stu-id="98a7c-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98a7c-132">Spécifications</span><span class="sxs-lookup"><span data-stu-id="98a7c-132">Requirements</span></span>  
 <span data-ttu-id="98a7c-133">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98a7c-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98a7c-134">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="98a7c-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="98a7c-135">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="98a7c-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98a7c-136">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98a7c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98a7c-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98a7c-137">See Also</span></span>  
 [<span data-ttu-id="98a7c-138">ICLRSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="98a7c-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="98a7c-139">IHostSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="98a7c-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
