---
title: "IHostSyncManager::CreateRWLockWriterEvent, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateRWLockWriterEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb38cd76a051b1a4459dff4f8164a6405f5fb32d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="9b5b0-102">IHostSyncManager::CreateRWLockWriterEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="9b5b0-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>
<span data-ttu-id="9b5b0-103">Crée un objet d’événement de réinitialisation automatique pour l’implémentation d’un verrou de writer.</span><span class="sxs-lookup"><span data-stu-id="9b5b0-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b5b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b5b0-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b5b0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9b5b0-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="9b5b0-106">[in] Cookie à associer à l’événement de réinitialisation automatique.</span><span class="sxs-lookup"><span data-stu-id="9b5b0-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="9b5b0-107">[out] Un pointeur vers l’adresse d’un [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) de l’instance, ou null si l’objet d’événement n’a pas pu être créé.</span><span class="sxs-lookup"><span data-stu-id="9b5b0-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b5b0-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9b5b0-108">Return Value</span></span>  
  
|<span data-ttu-id="9b5b0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9b5b0-109">HRESULT</span></span>|<span data-ttu-id="9b5b0-110">Description</span><span class="sxs-lookup"><span data-stu-id="9b5b0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9b5b0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9b5b0-111">S_OK</span></span>|<span data-ttu-id="9b5b0-112">`CreateRWLockWriterEvent`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="9b5b0-112">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="9b5b0-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9b5b0-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9b5b0-114">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="9b5b0-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9b5b0-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9b5b0-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9b5b0-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="9b5b0-116">The call timed out.</span></span>|  
|<span data-ttu-id="9b5b0-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9b5b0-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9b5b0-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="9b5b0-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9b5b0-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9b5b0-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9b5b0-120">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="9b5b0-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9b5b0-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9b5b0-121">E_FAIL</span></span>|<span data-ttu-id="9b5b0-122">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="9b5b0-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9b5b0-123">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9b5b0-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9b5b0-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9b5b0-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9b5b0-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9b5b0-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="9b5b0-126">Pas assez de mémoire n’était disponible pour créer l’objet de l’événement demandé.</span><span class="sxs-lookup"><span data-stu-id="9b5b0-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b5b0-127">Notes</span><span class="sxs-lookup"><span data-stu-id="9b5b0-127">Remarks</span></span>  
 <span data-ttu-id="9b5b0-128">Le CLR appelle la `CreateRWLockWriterEvent` méthode pour obtenir une référence à un `IHostAutoEvent` instance à utiliser dans son implémentation d’un verrou de writer.</span><span class="sxs-lookup"><span data-stu-id="9b5b0-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="9b5b0-129">L’hôte peut utiliser le cookie pour déterminer quelles tâches attendent le verrou en appelant les méthodes d’itération de la [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="9b5b0-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b5b0-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9b5b0-130">Requirements</span></span>  
 <span data-ttu-id="9b5b0-131">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b5b0-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b5b0-132">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9b5b0-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9b5b0-133">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9b5b0-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b5b0-134">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b5b0-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b5b0-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b5b0-135">See Also</span></span>  
 [<span data-ttu-id="9b5b0-136">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="9b5b0-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="9b5b0-137">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="9b5b0-137">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="9b5b0-138">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="9b5b0-138">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="9b5b0-139">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="9b5b0-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
