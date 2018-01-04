---
title: "ICLRTask::SetTaskIdentifier, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.SetTaskIdentifier
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::SetTaskIdentifier
helpviewer_keywords:
- SetTaskIdentifier method [.NET Framework hosting]
- ICLRTask::SetTaskIdentifier method [.NET Framework hosting]
ms.assetid: bdb7f047-1e90-40fc-9e3b-d44a16509073
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9ace5b7b0153e9e019b56ebc2b7f5df0c5ed91d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtasksettaskidentifier-method"></a><span data-ttu-id="2d72a-102">ICLRTask::SetTaskIdentifier, méthode</span><span class="sxs-lookup"><span data-stu-id="2d72a-102">ICLRTask::SetTaskIdentifier Method</span></span>
<span data-ttu-id="2d72a-103">Fait en sorte que le common language runtime (CLR) pour associer la valeur de l’identificateur spécifié à la tâche représentée par le [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="2d72a-103">Instructs the common language runtime (CLR) to associate the specified identifier value with the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d72a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d72a-104">Syntax</span></span>  
  
```  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d72a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2d72a-105">Parameters</span></span>  
 `Asked`  
 <span data-ttu-id="2d72a-106">[in] L’identificateur unique pour le common language runtime à associer à la tâche représentée par le `ICLRTask` instance.</span><span class="sxs-lookup"><span data-stu-id="2d72a-106">[in] The unique identifier for the common language runtime to associate with the task represented by the current `ICLRTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d72a-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2d72a-107">Return Value</span></span>  
  
|<span data-ttu-id="2d72a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d72a-108">HRESULT</span></span>|<span data-ttu-id="2d72a-109">Description</span><span class="sxs-lookup"><span data-stu-id="2d72a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d72a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d72a-110">S_OK</span></span>|<span data-ttu-id="2d72a-111">`SetTaskIdentifier`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="2d72a-111">`SetTaskIdentifier` returned successfully.</span></span>|  
|<span data-ttu-id="2d72a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2d72a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2d72a-113">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="2d72a-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2d72a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2d72a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2d72a-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="2d72a-115">The call timed out.</span></span>|  
|<span data-ttu-id="2d72a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2d72a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2d72a-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="2d72a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2d72a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2d72a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2d72a-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="2d72a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2d72a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2d72a-120">E_FAIL</span></span>|<span data-ttu-id="2d72a-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="2d72a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2d72a-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="2d72a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2d72a-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2d72a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d72a-124">Notes</span><span class="sxs-lookup"><span data-stu-id="2d72a-124">Remarks</span></span>  
 <span data-ttu-id="2d72a-125">L’hôte peut associer un identificateur à une tâche pour faciliter l’intégration du CLR et l’ordinateur hôte dans un environnement de débogage.</span><span class="sxs-lookup"><span data-stu-id="2d72a-125">The host can associate an identifier with a task to help integrate the CLR and the host in a debugging environment.</span></span> <span data-ttu-id="2d72a-126">L’identificateur n’a aucune signification pour le CLR.</span><span class="sxs-lookup"><span data-stu-id="2d72a-126">The identifier has no meaning for the CLR.</span></span> <span data-ttu-id="2d72a-127">Le CLR passe à une application de débogage.</span><span class="sxs-lookup"><span data-stu-id="2d72a-127">The CLR passes it along to a debugger application.</span></span> <span data-ttu-id="2d72a-128">Le débogueur peut utiliser cet identificateur pour associer une pile des appels CLR avec une pile d’appels hôte et activer leurs informations de traçage respectives unification lorsqu’ils sont affichés dans l’interface utilisateur du débogueur.</span><span class="sxs-lookup"><span data-stu-id="2d72a-128">The debugger can use this identifier to associate a CLR call stack with a host call stack, and enable their respective trace information to be unified when viewed in the debugger's user interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d72a-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2d72a-129">Requirements</span></span>  
 <span data-ttu-id="2d72a-130">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d72a-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d72a-131">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2d72a-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d72a-132">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2d72a-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d72a-133">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d72a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d72a-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d72a-134">See Also</span></span>  
 [<span data-ttu-id="2d72a-135">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="2d72a-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="2d72a-136">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="2d72a-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="2d72a-137">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="2d72a-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="2d72a-138">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="2d72a-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
