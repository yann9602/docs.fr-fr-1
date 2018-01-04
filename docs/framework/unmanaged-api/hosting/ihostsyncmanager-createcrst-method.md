---
title: "IHostSyncManager::CreateCrst, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateCrst
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f932c91892292c787feecf1768c33fb429334bae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="eed7b-102">IHostSyncManager::CreateCrst, méthode</span><span class="sxs-lookup"><span data-stu-id="eed7b-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="eed7b-103">Crée un objet de section critique pour la synchronisation.</span><span class="sxs-lookup"><span data-stu-id="eed7b-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eed7b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eed7b-104">Syntax</span></span>  
  
```  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eed7b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eed7b-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="eed7b-106">[out] Un pointeur vers l’adresse d’un [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implémenté par l’hôte, ou null si la section critique n’a pas pu être créée.</span><span class="sxs-lookup"><span data-stu-id="eed7b-106">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eed7b-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="eed7b-107">Return Value</span></span>  
  
|<span data-ttu-id="eed7b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eed7b-108">HRESULT</span></span>|<span data-ttu-id="eed7b-109">Description</span><span class="sxs-lookup"><span data-stu-id="eed7b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eed7b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="eed7b-110">S_OK</span></span>|<span data-ttu-id="eed7b-111">`CreateCrst`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="eed7b-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="eed7b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eed7b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eed7b-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="eed7b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eed7b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eed7b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eed7b-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="eed7b-115">The call timed out.</span></span>|  
|<span data-ttu-id="eed7b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eed7b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eed7b-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="eed7b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eed7b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eed7b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eed7b-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="eed7b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eed7b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eed7b-120">E_FAIL</span></span>|<span data-ttu-id="eed7b-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="eed7b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eed7b-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="eed7b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eed7b-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="eed7b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="eed7b-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="eed7b-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="eed7b-125">Pas assez de mémoire n’était disponible pour créer la section critique demandée.</span><span class="sxs-lookup"><span data-stu-id="eed7b-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eed7b-126">Notes</span><span class="sxs-lookup"><span data-stu-id="eed7b-126">Remarks</span></span>  
 <span data-ttu-id="eed7b-127">Objets de section critique fournissent une synchronisation similaire à celle fournie par un objet mutex, à ceci près que les sections critiques peuvent être utilisées uniquement par les threads d’un processus unique.</span><span class="sxs-lookup"><span data-stu-id="eed7b-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="eed7b-128">`CreateCrst`reflète Win32 `InitializeCriticalSection` (fonction).</span><span class="sxs-lookup"><span data-stu-id="eed7b-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eed7b-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="eed7b-129">Requirements</span></span>  
 <span data-ttu-id="eed7b-130">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eed7b-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eed7b-131">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eed7b-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eed7b-132">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eed7b-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eed7b-133">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eed7b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eed7b-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eed7b-134">See Also</span></span>  
 [<span data-ttu-id="eed7b-135">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="eed7b-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="eed7b-136">IHostCrst, interface</span><span class="sxs-lookup"><span data-stu-id="eed7b-136">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="eed7b-137">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="eed7b-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="eed7b-138">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="eed7b-138">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="eed7b-139">Mutex</span><span class="sxs-lookup"><span data-stu-id="eed7b-139">Mutexes</span></span>](../../../../docs/standard/threading/mutexes.md)  
 [<span data-ttu-id="eed7b-140">Semaphore et SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="eed7b-140">Semaphore and SemaphoreSlim</span></span>](../../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
