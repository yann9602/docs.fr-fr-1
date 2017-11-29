---
title: "IHostIoCompletionManager::SetMinThreads, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.SetMinThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: dea34b81-8d2b-4cc3-8696-0ad4291d8a92
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a8903aa2f2119ad3c4dceebfaba9ede26200e899
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="1f9ef-102">IHostIoCompletionManager::SetMinThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="1f9ef-102">IHostIoCompletionManager::SetMinThreads Method</span></span>
<span data-ttu-id="1f9ef-103">Définit le nombre minimal de threads que l’hôte doit allouer pour l’achèvement d’e/s.</span><span class="sxs-lookup"><span data-stu-id="1f9ef-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f9ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f9ef-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f9ef-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1f9ef-105">Parameters</span></span>  
 `dwMinIoCompletionThreads`  
 <span data-ttu-id="1f9ef-106">[in] Le nombre minimal de threads de terminaison d’e/s que l’hôte doit créer.</span><span class="sxs-lookup"><span data-stu-id="1f9ef-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f9ef-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1f9ef-107">Return Value</span></span>  
  
|<span data-ttu-id="1f9ef-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f9ef-108">HRESULT</span></span>|<span data-ttu-id="1f9ef-109">Description</span><span class="sxs-lookup"><span data-stu-id="1f9ef-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f9ef-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1f9ef-110">S_OK</span></span>|<span data-ttu-id="1f9ef-111">`SetMinThreads`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="1f9ef-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="1f9ef-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1f9ef-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1f9ef-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="1f9ef-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1f9ef-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1f9ef-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1f9ef-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="1f9ef-115">The call timed out.</span></span>|  
|<span data-ttu-id="1f9ef-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1f9ef-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1f9ef-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="1f9ef-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1f9ef-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1f9ef-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1f9ef-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="1f9ef-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1f9ef-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1f9ef-120">E_FAIL</span></span>|<span data-ttu-id="1f9ef-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="1f9ef-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1f9ef-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="1f9ef-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1f9ef-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1f9ef-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1f9ef-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="1f9ef-124">E_NOTIMPL</span></span>|<span data-ttu-id="1f9ef-125">L’hôte ne fournit pas une implémentation de `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="1f9ef-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f9ef-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="1f9ef-126">Remarks</span></span>  
 <span data-ttu-id="1f9ef-127">Un hôte peut souhaiter le contrôle exclusif sur le nombre de threads qui peuvent être alloués pour traiter les demandes d’e/s, pour des raisons telles que l’implémentation, les performances ou l’évolutivité.</span><span class="sxs-lookup"><span data-stu-id="1f9ef-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="1f9ef-128">Pour cette raison, l’hôte n’est pas tenu d’implémenter `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="1f9ef-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="1f9ef-129">Dans ce cas, l’hôte doit retourner E_NOTIMPL à partir de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="1f9ef-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f9ef-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1f9ef-130">Requirements</span></span>  
 <span data-ttu-id="1f9ef-131">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f9ef-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f9ef-132">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1f9ef-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f9ef-133">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1f9ef-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f9ef-134">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f9ef-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f9ef-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f9ef-135">See Also</span></span>  
 [<span data-ttu-id="1f9ef-136">ICLRIoCompletionManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="1f9ef-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="1f9ef-137">SetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="1f9ef-137">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="1f9ef-138">IHostIoCompletionManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="1f9ef-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
