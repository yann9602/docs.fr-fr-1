---
title: "ICLRDebugManager::BeginConnection, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.BeginConnection
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::BeginConnection
helpviewer_keywords:
- ICLRDebugManager::BeginConnection method [.NET Framework hosting]
- BeginConnection method [.NET Framework hosting]
ms.assetid: bdd98146-ff4d-4150-a264-a4c1a32d31f3
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 302b2abfdde7bbccbef51de21233948d042420be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="3a1f0-102">ICLRDebugManager::BeginConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="3a1f0-102">ICLRDebugManager::BeginConnection Method</span></span>
<span data-ttu-id="3a1f0-103">Établit une connexion entre l’hôte et le débogueur pour associer une liste de tâches à un identificateur et un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-103">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a1f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a1f0-104">Syntax</span></span>  
  
```  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a1f0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3a1f0-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="3a1f0-106">[in] Identificateur à associer à la liste des tâches de courantes language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="3a1f0-106">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="3a1f0-107">[in] Un nom convivial à associer à la liste des tâches du CLR.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-107">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a1f0-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3a1f0-108">Return Value</span></span>  
  
|<span data-ttu-id="3a1f0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3a1f0-109">HRESULT</span></span>|<span data-ttu-id="3a1f0-110">Description</span><span class="sxs-lookup"><span data-stu-id="3a1f0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a1f0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3a1f0-111">S_OK</span></span>|<span data-ttu-id="3a1f0-112">`BeginConnection`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-112">`BeginConnection` returned successfully.</span></span>|  
|<span data-ttu-id="3a1f0-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3a1f0-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3a1f0-114">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3a1f0-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3a1f0-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3a1f0-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-116">The call timed out.</span></span>|  
|<span data-ttu-id="3a1f0-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3a1f0-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3a1f0-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3a1f0-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3a1f0-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3a1f0-120">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3a1f0-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3a1f0-121">E_FAIL</span></span>|<span data-ttu-id="3a1f0-122">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3a1f0-123">Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3a1f0-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3a1f0-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3a1f0-125">E_INVALIDARG</span></span>|<span data-ttu-id="3a1f0-126">`dwConnectionId`est égal à zéro, ou `BeginConnection` a déjà été appelée à l’aide de ce `dwConnectionId` valeur, ou `szConnectionName` était null.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-126">`dwConnectionId` was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="3a1f0-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3a1f0-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="3a1f0-128">Pas assez de mémoire peut être allouée pour contenir la liste des tâches associées à cette connexion.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-128">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a1f0-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="3a1f0-129">Remarks</span></span>  
 <span data-ttu-id="3a1f0-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) fournit trois méthodes, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), et [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), permettant d’associer des listes de tâches à des identificateurs et noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3a1f0-131">Ces trois méthodes doivent être appelées dans un ordre spécifique pour chaque ensemble de tâches.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-131">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="3a1f0-132">`BeginConnection`est appelée en premier pour établir une nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-132">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="3a1f0-133">`SetConnectionTasks`est ensuite appelée pour fournir l’ensemble des tâches à associer à cette connexion.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-133">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="3a1f0-134">`EndConnection`est appelée en dernier pour supprimer l’association entre la liste des tâches et l’identificateur et le nom convivial. Toutefois, les appels pour des connexions différentes peuvent être imbriqués.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-134">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a1f0-135">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3a1f0-135">Requirements</span></span>  
 <span data-ttu-id="3a1f0-136">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a1f0-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a1f0-137">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3a1f0-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a1f0-138">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3a1f0-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a1f0-139">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a1f0-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a1f0-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a1f0-140">See Also</span></span>  
 [<span data-ttu-id="3a1f0-141">ICLRControl (Interface)</span><span class="sxs-lookup"><span data-stu-id="3a1f0-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="3a1f0-142">ICLRDebugManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="3a1f0-142">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="3a1f0-143">EndConnection (méthode)</span><span class="sxs-lookup"><span data-stu-id="3a1f0-143">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)  
 [<span data-ttu-id="3a1f0-144">SetConnectionTasks (méthode)</span><span class="sxs-lookup"><span data-stu-id="3a1f0-144">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)  
 [<span data-ttu-id="3a1f0-145">IHostControl (Interface)</span><span class="sxs-lookup"><span data-stu-id="3a1f0-145">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
