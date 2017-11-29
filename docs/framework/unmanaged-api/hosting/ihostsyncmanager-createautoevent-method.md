---
title: "IHostSyncManager::CreateAutoEvent, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateAutoEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e6a792ca9075e48a8092d92e1adf870174dd1af6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="cf595-102">IHostSyncManager::CreateAutoEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="cf595-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="cf595-103">Crée un objet d’événement de réinitialisation automatique.</span><span class="sxs-lookup"><span data-stu-id="cf595-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf595-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf595-104">Syntax</span></span>  
  
```  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf595-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cf595-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="cf595-106">[out] Un pointeur vers l’adresse d’un [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implémentée par l’hôte, ou null si l’objet d’événement n’a pas pu être créé.</span><span class="sxs-lookup"><span data-stu-id="cf595-106">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf595-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="cf595-107">Return Value</span></span>  
  
|<span data-ttu-id="cf595-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cf595-108">HRESULT</span></span>|<span data-ttu-id="cf595-109">Description</span><span class="sxs-lookup"><span data-stu-id="cf595-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cf595-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cf595-110">S_OK</span></span>|<span data-ttu-id="cf595-111">`CreateAutoEvent`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="cf595-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="cf595-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cf595-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cf595-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="cf595-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cf595-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cf595-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cf595-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="cf595-115">The call timed out.</span></span>|  
|<span data-ttu-id="cf595-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cf595-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cf595-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="cf595-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cf595-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cf595-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cf595-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="cf595-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cf595-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cf595-120">E_FAIL</span></span>|<span data-ttu-id="cf595-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="cf595-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cf595-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="cf595-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cf595-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cf595-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cf595-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="cf595-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="cf595-125">Pas assez de mémoire n’était disponible pour créer l’objet de l’événement demandé.</span><span class="sxs-lookup"><span data-stu-id="cf595-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf595-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="cf595-126">Remarks</span></span>  
 <span data-ttu-id="cf595-127">`CreateAutoEvent`Crée un objet événement automatique dont l’état est modifié automatiquement en non signalé une fois que le thread en attente a été publié.</span><span class="sxs-lookup"><span data-stu-id="cf595-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="cf595-128">Cette méthode reflète Win32 `CreateEvent` fonction avec la valeur `false` spécifié pour le `bManualReset` paramètre</span><span class="sxs-lookup"><span data-stu-id="cf595-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf595-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cf595-129">Requirements</span></span>  
 <span data-ttu-id="cf595-130">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf595-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf595-131">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cf595-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf595-132">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf595-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf595-133">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf595-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf595-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf595-134">See Also</span></span>  
 [<span data-ttu-id="cf595-135">ICLRSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="cf595-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="cf595-136">IHostAutoEvent (Interface)</span><span class="sxs-lookup"><span data-stu-id="cf595-136">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="cf595-137">IHostControl (Interface)</span><span class="sxs-lookup"><span data-stu-id="cf595-137">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="cf595-138">IHostSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="cf595-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
