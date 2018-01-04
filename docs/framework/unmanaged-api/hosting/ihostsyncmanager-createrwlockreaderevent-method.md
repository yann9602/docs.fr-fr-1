---
title: "IHostSyncManager::CreateRWLockReaderEvent, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateRWLockReaderEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b583e7b5dd1a83ecb891591c25802ae257ad7c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="e777a-102">IHostSyncManager::CreateRWLockReaderEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="e777a-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="e777a-103">Crée un objet d’événement de réinitialisation manuelle pour l’implémentation d’un verrou de lecteur.</span><span class="sxs-lookup"><span data-stu-id="e777a-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e777a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e777a-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e777a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e777a-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="e777a-106">[in] `true`si `ppEvent` doit être signalé ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="e777a-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="e777a-107">[in] Cookie à associer avec le verrou de lecteur.</span><span class="sxs-lookup"><span data-stu-id="e777a-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="e777a-108">[out] Un pointeur vers l’adresse d’un [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) de l’instance, ou null si l’objet d’événement n’a pas pu être créé.</span><span class="sxs-lookup"><span data-stu-id="e777a-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e777a-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e777a-109">Return Value</span></span>  
  
|<span data-ttu-id="e777a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e777a-110">HRESULT</span></span>|<span data-ttu-id="e777a-111">Description</span><span class="sxs-lookup"><span data-stu-id="e777a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e777a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e777a-112">S_OK</span></span>|<span data-ttu-id="e777a-113">`CreateRWLockReaderEvent`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="e777a-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="e777a-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e777a-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e777a-115">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="e777a-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e777a-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e777a-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e777a-117">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="e777a-117">The call timed out.</span></span>|  
|<span data-ttu-id="e777a-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e777a-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e777a-119">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="e777a-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e777a-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e777a-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e777a-121">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="e777a-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e777a-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e777a-122">E_FAIL</span></span>|<span data-ttu-id="e777a-123">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e777a-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e777a-124">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e777a-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e777a-125">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e777a-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e777a-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e777a-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e777a-127">Pas assez de mémoire n’était disponible pour créer l’objet de l’événement demandé.</span><span class="sxs-lookup"><span data-stu-id="e777a-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e777a-128">Notes</span><span class="sxs-lookup"><span data-stu-id="e777a-128">Remarks</span></span>  
 <span data-ttu-id="e777a-129">Le CLR appelle `CreateRWLockReaderEvent` pour obtenir une référence à un `IHostManualEvent` instance à utiliser dans son implémentation d’un verrou de lecteur.</span><span class="sxs-lookup"><span data-stu-id="e777a-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="e777a-130">L’hôte peut utiliser le cookie pour déterminer quelles tâches attendent le verrou de lecteur en interrogeant le [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="e777a-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e777a-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e777a-131">Requirements</span></span>  
 <span data-ttu-id="e777a-132">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e777a-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e777a-133">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e777a-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e777a-134">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e777a-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e777a-135">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e777a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e777a-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e777a-136">See Also</span></span>  
 [<span data-ttu-id="e777a-137">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="e777a-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="e777a-138">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="e777a-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="e777a-139">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="e777a-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="e777a-140">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="e777a-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
