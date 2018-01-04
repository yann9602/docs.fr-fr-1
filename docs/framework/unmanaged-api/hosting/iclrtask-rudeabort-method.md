---
title: "ICLRTask::RudeAbort, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.RudeAbort
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f48de1fb44d978b1d9c8960c3e44c360b0801e27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="7bb93-102">ICLRTask::RudeAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="7bb93-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="7bb93-103">Fait en sorte que le common language runtime (CLR) d’abandonner la tâche représentée par le [ICLRTask (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) immédiatement et sans condition de l’instance.</span><span class="sxs-lookup"><span data-stu-id="7bb93-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bb93-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7bb93-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="7bb93-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7bb93-105">Return Value</span></span>  
  
|<span data-ttu-id="7bb93-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7bb93-106">HRESULT</span></span>|<span data-ttu-id="7bb93-107">Description</span><span class="sxs-lookup"><span data-stu-id="7bb93-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7bb93-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="7bb93-108">S_OK</span></span>|<span data-ttu-id="7bb93-109">`RudeAbort`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="7bb93-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="7bb93-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7bb93-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7bb93-111">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="7bb93-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7bb93-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7bb93-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7bb93-113">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="7bb93-113">The call timed out.</span></span>|  
|<span data-ttu-id="7bb93-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7bb93-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7bb93-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="7bb93-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7bb93-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7bb93-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7bb93-117">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="7bb93-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7bb93-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7bb93-118">E_FAIL</span></span>|<span data-ttu-id="7bb93-119">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="7bb93-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7bb93-120">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="7bb93-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7bb93-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7bb93-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bb93-122">Notes</span><span class="sxs-lookup"><span data-stu-id="7bb93-122">Remarks</span></span>  
 <span data-ttu-id="7bb93-123">Un hôte appelle `RudeAbort` pour abandonner immédiatement une tâche.</span><span class="sxs-lookup"><span data-stu-id="7bb93-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="7bb93-124">Les finaliseurs et les routines de gestion des exceptions ne sont pas garantis pour être exécutée.</span><span class="sxs-lookup"><span data-stu-id="7bb93-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bb93-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7bb93-125">Requirements</span></span>  
 <span data-ttu-id="7bb93-126">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bb93-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bb93-127">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7bb93-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7bb93-128">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7bb93-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7bb93-129">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bb93-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb93-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7bb93-130">See Also</span></span>  
 [<span data-ttu-id="7bb93-131">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="7bb93-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="7bb93-132">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="7bb93-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="7bb93-133">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="7bb93-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="7bb93-134">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="7bb93-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
