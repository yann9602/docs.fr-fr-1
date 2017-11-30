---
title: "IHostSemaphore::ReleaseSemaphore, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSemaphore.ReleaseSemaphore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSemaphore::ReleaseSemaphore
helpviewer_keywords:
- ReleaseSemaphore method [.NET Framework hosting]
- IHostSemaphore::ReleaseSemaphore method [.NET Framework hosting]
ms.assetid: a343d197-979a-4ac6-ab8c-cb8a05f3120e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 06765d019d5443730656e7f4d6745bd8ad39ee00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="dbfeb-102">IHostSemaphore::ReleaseSemaphore, méthode</span><span class="sxs-lookup"><span data-stu-id="dbfeb-102">IHostSemaphore::ReleaseSemaphore Method</span></span>
<span data-ttu-id="dbfeb-103">Incrémente le nombre d’actuel [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance de la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-103">Increases the count of the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbfeb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbfeb-104">Syntax</span></span>  
  
```  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dbfeb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dbfeb-105">Parameters</span></span>  
 `lReleaseCount`  
 <span data-ttu-id="dbfeb-106">[in] La quantité d’augmentation du nombre d’en cours `IHostSemaphore` instance.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="dbfeb-107">Ce montant doit être supérieur à zéro.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="dbfeb-108">[out] Pointeur vers le compteur antérieur ou null si l’appelant ne nécessite pas le compteur antérieur.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dbfeb-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="dbfeb-109">Return Value</span></span>  
  
|<span data-ttu-id="dbfeb-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dbfeb-110">HRESULT</span></span>|<span data-ttu-id="dbfeb-111">Description</span><span class="sxs-lookup"><span data-stu-id="dbfeb-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dbfeb-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="dbfeb-112">S_OK</span></span>|<span data-ttu-id="dbfeb-113">`ReleaseSemaphore`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="dbfeb-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dbfeb-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dbfeb-115">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dbfeb-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dbfeb-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dbfeb-117">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-117">The call timed out.</span></span>|  
|<span data-ttu-id="dbfeb-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dbfeb-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dbfeb-119">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dbfeb-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dbfeb-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dbfeb-121">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dbfeb-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dbfeb-122">E_FAIL</span></span>|<span data-ttu-id="dbfeb-123">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dbfeb-124">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dbfeb-125">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbfeb-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="dbfeb-126">Remarks</span></span>  
 <span data-ttu-id="dbfeb-127">Le CLR appelle généralement `ReleaseSemaphore` pour notifier l’hôte qu’il a terminé d’utiliser une ressource, en passant une valeur de 1 pour le `lReleaseCount` paramètre.</span><span class="sxs-lookup"><span data-stu-id="dbfeb-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbfeb-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dbfeb-128">Requirements</span></span>  
 <span data-ttu-id="dbfeb-129">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbfeb-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbfeb-130">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dbfeb-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dbfeb-131">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dbfeb-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbfeb-132">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbfeb-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbfeb-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbfeb-133">See Also</span></span>  
 [<span data-ttu-id="dbfeb-134">ICLRSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="dbfeb-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="dbfeb-135">IHostAutoEvent (Interface)</span><span class="sxs-lookup"><span data-stu-id="dbfeb-135">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="dbfeb-136">IHostManualEvent (Interface)</span><span class="sxs-lookup"><span data-stu-id="dbfeb-136">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="dbfeb-137">IHostSemaphore (Interface)</span><span class="sxs-lookup"><span data-stu-id="dbfeb-137">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="dbfeb-138">IHostSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="dbfeb-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
