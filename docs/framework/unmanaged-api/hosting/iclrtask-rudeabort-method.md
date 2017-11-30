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
ms.openlocfilehash: df1f688ec3f58ae7317a4fed0dd70cffc1647045
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="74b67-102">ICLRTask::RudeAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="74b67-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="74b67-103">Fait en sorte que le common language runtime (CLR) d’abandonner la tâche représentée par le [ICLRTask (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) immédiatement et sans condition de l’instance.</span><span class="sxs-lookup"><span data-stu-id="74b67-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74b67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74b67-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="74b67-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="74b67-105">Return Value</span></span>  
  
|<span data-ttu-id="74b67-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="74b67-106">HRESULT</span></span>|<span data-ttu-id="74b67-107">Description</span><span class="sxs-lookup"><span data-stu-id="74b67-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="74b67-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="74b67-108">S_OK</span></span>|<span data-ttu-id="74b67-109">`RudeAbort`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="74b67-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="74b67-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="74b67-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="74b67-111">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="74b67-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="74b67-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="74b67-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="74b67-113">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="74b67-113">The call timed out.</span></span>|  
|<span data-ttu-id="74b67-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="74b67-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="74b67-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="74b67-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="74b67-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="74b67-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="74b67-117">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="74b67-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="74b67-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="74b67-118">E_FAIL</span></span>|<span data-ttu-id="74b67-119">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="74b67-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="74b67-120">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="74b67-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="74b67-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="74b67-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74b67-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="74b67-122">Remarks</span></span>  
 <span data-ttu-id="74b67-123">Un hôte appelle `RudeAbort` pour abandonner immédiatement une tâche.</span><span class="sxs-lookup"><span data-stu-id="74b67-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="74b67-124">Les finaliseurs et les routines de gestion des exceptions ne sont pas garantis pour être exécutée.</span><span class="sxs-lookup"><span data-stu-id="74b67-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74b67-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="74b67-125">Requirements</span></span>  
 <span data-ttu-id="74b67-126">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74b67-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74b67-127">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="74b67-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="74b67-128">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="74b67-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74b67-129">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74b67-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74b67-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74b67-130">See Also</span></span>  
 [<span data-ttu-id="74b67-131">ICLRTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="74b67-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="74b67-132">ICLRTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="74b67-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="74b67-133">IHostTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="74b67-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="74b67-134">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="74b67-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
