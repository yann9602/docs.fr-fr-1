---
title: "IHostSyncManager::CreateMonitorEvent, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateMonitorEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae12db71f4eae0f7d887fda26e05401f4f23ee5c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="4c31d-102">IHostSyncManager::CreateMonitorEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="4c31d-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="4c31d-103">Crée un objet d’événement de réinitialisation automatique surveillé.</span><span class="sxs-lookup"><span data-stu-id="4c31d-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c31d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c31d-104">Syntax</span></span>  
  
```  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c31d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4c31d-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="4c31d-106">[in] Cookie à associer à l’objet d’événement.</span><span class="sxs-lookup"><span data-stu-id="4c31d-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="4c31d-107">[out] Un pointeur vers l’adresse d’un [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) de l’instance, ou null si l’objet d’événement n’a pas pu être créé.</span><span class="sxs-lookup"><span data-stu-id="4c31d-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c31d-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4c31d-108">Return Value</span></span>  
  
|<span data-ttu-id="4c31d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4c31d-109">HRESULT</span></span>|<span data-ttu-id="4c31d-110">Description</span><span class="sxs-lookup"><span data-stu-id="4c31d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4c31d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4c31d-111">S_OK</span></span>|<span data-ttu-id="4c31d-112">`CreateMonitorEvent`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="4c31d-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="4c31d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4c31d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4c31d-114">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="4c31d-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4c31d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4c31d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4c31d-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="4c31d-116">The call timed out.</span></span>|  
|<span data-ttu-id="4c31d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4c31d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4c31d-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="4c31d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4c31d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4c31d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4c31d-120">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="4c31d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4c31d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4c31d-121">E_FAIL</span></span>|<span data-ttu-id="4c31d-122">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="4c31d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4c31d-123">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="4c31d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4c31d-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4c31d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4c31d-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4c31d-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="4c31d-126">Pas assez de mémoire n’était disponible pour créer l’objet de l’événement demandé.</span><span class="sxs-lookup"><span data-stu-id="4c31d-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c31d-127">Notes</span><span class="sxs-lookup"><span data-stu-id="4c31d-127">Remarks</span></span>  
 <span data-ttu-id="4c31d-128">`CreateMonitorEvent`Retourne un `IHostAutoEvent` que le CLR utilise dans son implémentation de managé <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span><span class="sxs-lookup"><span data-stu-id="4c31d-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="4c31d-129">Cette méthode reflète Win32 `CreateEvent` fonction, avec la valeur `false` spécifié pour le `bManualReset` paramètre.</span><span class="sxs-lookup"><span data-stu-id="4c31d-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="4c31d-130">L’hôte peut utiliser le cookie pour déterminer quelle tâche attend sur l’écran en appelant le [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="4c31d-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c31d-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4c31d-131">Requirements</span></span>  
 <span data-ttu-id="4c31d-132">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c31d-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c31d-133">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4c31d-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c31d-134">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4c31d-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c31d-135">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c31d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c31d-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c31d-136">See Also</span></span>  
 [<span data-ttu-id="4c31d-137">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="4c31d-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="4c31d-138">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="4c31d-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="4c31d-139">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="4c31d-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="4c31d-140">Moniteurs</span><span class="sxs-lookup"><span data-stu-id="4c31d-140">Monitors</span></span>](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)
