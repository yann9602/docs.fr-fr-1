---
title: "IHostIoCompletionManager::SetMaxThreads, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.SetMaxThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::SetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: ebad4f40-d9f1-4dc6-9b27-a89c9eb3926f
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3d2d8436d85f7be40c89693628794b007e0c6a88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="90b55-102">IHostIoCompletionManager::SetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="90b55-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>
<span data-ttu-id="90b55-103">Définit le nombre maximal de threads plus travail alloue de l’ordinateur hôte pour traiter les demandes d’e/s.</span><span class="sxs-lookup"><span data-stu-id="90b55-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90b55-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90b55-104">Syntax</span></span>  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90b55-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="90b55-105">Parameters</span></span>  
 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="90b55-106">[in] Le nombre maximal de threads à allouer pour les demandes d’e/s.</span><span class="sxs-lookup"><span data-stu-id="90b55-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90b55-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="90b55-107">Return Value</span></span>  
  
|<span data-ttu-id="90b55-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="90b55-108">HRESULT</span></span>|<span data-ttu-id="90b55-109">Description</span><span class="sxs-lookup"><span data-stu-id="90b55-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="90b55-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="90b55-110">S_OK</span></span>|<span data-ttu-id="90b55-111">`SetMaxThreads`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="90b55-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="90b55-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="90b55-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="90b55-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="90b55-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="90b55-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="90b55-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="90b55-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="90b55-115">The call timed out.</span></span>|  
|<span data-ttu-id="90b55-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="90b55-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="90b55-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="90b55-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="90b55-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="90b55-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="90b55-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="90b55-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="90b55-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="90b55-120">E_FAIL</span></span>|<span data-ttu-id="90b55-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="90b55-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="90b55-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="90b55-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="90b55-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="90b55-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="90b55-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="90b55-124">E_NOTIMPL</span></span>|<span data-ttu-id="90b55-125">L’hôte ne fournit pas une implémentation de `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="90b55-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90b55-126">Notes</span><span class="sxs-lookup"><span data-stu-id="90b55-126">Remarks</span></span>  
 <span data-ttu-id="90b55-127">`SetMaxThreads`fournit au CLR avec possibilité de définir le nombre maximal de threads qui sont disponibles pour traiter les demandes sur les ports d’e/s.</span><span class="sxs-lookup"><span data-stu-id="90b55-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="90b55-128">Un hôte peut souhaiter le contrôle exclusif sur la taille du pool de threads, pour des raisons telles que l’implémentation, les performances ou l’évolutivité.</span><span class="sxs-lookup"><span data-stu-id="90b55-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="90b55-129">Pour cette raison, l’hôte n’est pas tenu d’implémenter `SetMaxThreads`.</span><span class="sxs-lookup"><span data-stu-id="90b55-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="90b55-130">Dans ce cas, un hôte doit retourner E_NOTIMPL à partir de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="90b55-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90b55-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="90b55-131">Requirements</span></span>  
 <span data-ttu-id="90b55-132">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90b55-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90b55-133">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="90b55-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="90b55-134">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="90b55-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90b55-135">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90b55-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90b55-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90b55-136">See Also</span></span>  
 [<span data-ttu-id="90b55-137">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="90b55-137">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="90b55-138">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="90b55-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
