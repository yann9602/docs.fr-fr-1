---
title: "ICLRSyncManager::CreateRWLockOwnerIterator, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager.CreateRWLockOwnerIterator
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f153550544a8e7622ea3cec0273ff9a97a99f91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="21b85-102">ICLRSyncManager::CreateRWLockOwnerIterator, méthode</span><span class="sxs-lookup"><span data-stu-id="21b85-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="21b85-103">Demande que le common language runtime (CLR) crée un itérateur pour l’hôte à utiliser pour déterminer l’ensemble de tâches attendant un verrou de lecteur-writer.</span><span class="sxs-lookup"><span data-stu-id="21b85-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21b85-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21b85-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21b85-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="21b85-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="21b85-106">[in] Le cookie associé au verrou de lecteur-writer voulu.</span><span class="sxs-lookup"><span data-stu-id="21b85-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="21b85-107">[out] Un pointeur vers un itérateur qui peut être passé à la [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) et [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) méthodes.</span><span class="sxs-lookup"><span data-stu-id="21b85-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21b85-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="21b85-108">Return Value</span></span>  
  
|<span data-ttu-id="21b85-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21b85-109">HRESULT</span></span>|<span data-ttu-id="21b85-110">Description</span><span class="sxs-lookup"><span data-stu-id="21b85-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21b85-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="21b85-111">S_OK</span></span>|<span data-ttu-id="21b85-112">`CreateRWLockOwnerIterator`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="21b85-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="21b85-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="21b85-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="21b85-114">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="21b85-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="21b85-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="21b85-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="21b85-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="21b85-116">The call timed out.</span></span>|  
|<span data-ttu-id="21b85-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="21b85-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="21b85-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="21b85-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="21b85-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="21b85-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="21b85-120">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="21b85-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="21b85-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="21b85-121">E_FAIL</span></span>|<span data-ttu-id="21b85-122">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="21b85-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="21b85-123">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="21b85-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="21b85-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="21b85-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="21b85-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="21b85-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="21b85-126">`CreateRWLockOwnerIterator`a été appelé sur un thread en cours d’exécution du code managé.</span><span class="sxs-lookup"><span data-stu-id="21b85-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21b85-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="21b85-127">Remarks</span></span>  
 <span data-ttu-id="21b85-128">Les hôtes appellent généralement la `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, et `GetRWLockOwnerNext` méthodes lors de la détection de blocage.</span><span class="sxs-lookup"><span data-stu-id="21b85-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="21b85-129">L’hôte est chargé de s’assurer que le verrou de lecteur-writer est toujours valide, car le CLR n’effectue aucune tentative afin de maintenir le verrou de lecteur-writer.</span><span class="sxs-lookup"><span data-stu-id="21b85-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="21b85-130">Plusieurs stratégies sont disponibles pour l’ordinateur hôte garantir la validité du verrou :</span><span class="sxs-lookup"><span data-stu-id="21b85-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
-   <span data-ttu-id="21b85-131">L’hôte peut bloquer des appels de libération sur le verrou de lecteur-writer (par exemple, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) tout en garantissant que ce bloc ne provoque pas d’interblocage.</span><span class="sxs-lookup"><span data-stu-id="21b85-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
-   <span data-ttu-id="21b85-132">L’hôte peut empêcher la sortie d’attendre l’objet d’événement associé au verrou de lecteur-writer, à nouveau vous être assuré que ce bloc ne provoque pas d’interblocage.</span><span class="sxs-lookup"><span data-stu-id="21b85-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21b85-133">`CreateRWLockOwnerIterator`doit être appelé uniquement sur des threads qui exécutent du code non managé.</span><span class="sxs-lookup"><span data-stu-id="21b85-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21b85-134">Spécifications</span><span class="sxs-lookup"><span data-stu-id="21b85-134">Requirements</span></span>  
 <span data-ttu-id="21b85-135">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21b85-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21b85-136">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="21b85-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21b85-137">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="21b85-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21b85-138">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21b85-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21b85-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21b85-139">See Also</span></span>  
 [<span data-ttu-id="21b85-140">ICLRSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="21b85-140">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="21b85-141">IHostSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="21b85-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
