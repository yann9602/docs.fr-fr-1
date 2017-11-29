---
title: "ICLRTask::LocksHeld, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.LocksHeld
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::LocksHeld
helpviewer_keywords:
- LocksHeld method [.NET Framework hosting]
- ICLRTask::LocksHeld method [.NET Framework hosting]
ms.assetid: e88a4dc3-02cc-4703-a474-292b71c40657
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2d51fded9f2e475759f2912aea659d272ce08855
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="2603e-102">ICLRTask::LocksHeld, méthode</span><span class="sxs-lookup"><span data-stu-id="2603e-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="2603e-103">Obtient le nombre de verrous actuellement maintenus sur la tâche.</span><span class="sxs-lookup"><span data-stu-id="2603e-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2603e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2603e-104">Syntax</span></span>  
  
```  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2603e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2603e-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="2603e-106">[out] Le nombre de verrous maintenus sur la tâche au moment de l’appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="2603e-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2603e-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2603e-107">Return Value</span></span>  
  
|<span data-ttu-id="2603e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2603e-108">HRESULT</span></span>|<span data-ttu-id="2603e-109">Description</span><span class="sxs-lookup"><span data-stu-id="2603e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2603e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2603e-110">S_OK</span></span>|<span data-ttu-id="2603e-111">`LocksHeld`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="2603e-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="2603e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2603e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2603e-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="2603e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2603e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2603e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2603e-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="2603e-115">The call timed out.</span></span>|  
|<span data-ttu-id="2603e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2603e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2603e-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="2603e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2603e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2603e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2603e-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="2603e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2603e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2603e-120">E_FAIL</span></span>|<span data-ttu-id="2603e-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="2603e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2603e-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="2603e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2603e-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2603e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2603e-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2603e-124">Requirements</span></span>  
 <span data-ttu-id="2603e-125">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2603e-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2603e-126">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2603e-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2603e-127">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2603e-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2603e-128">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2603e-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2603e-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2603e-129">See Also</span></span>  
 [<span data-ttu-id="2603e-130">ICLRTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="2603e-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="2603e-131">ICLRTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="2603e-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="2603e-132">IHostTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="2603e-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="2603e-133">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="2603e-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
