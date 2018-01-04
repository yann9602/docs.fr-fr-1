---
title: "IHostIoCompletionManager::GetAvailableThreads, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.GetAvailableThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 66f2471e07ae5827d2edb553b4226784b42278c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="9acbf-102">IHostIoCompletionManager::GetAvailableThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="9acbf-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="9acbf-103">Obtient le nombre de threads de terminaison d’e/s, le nombre total de threads gérés par l’hôte, qui ne sont pas traiter actuellement des demandes.</span><span class="sxs-lookup"><span data-stu-id="9acbf-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9acbf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9acbf-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9acbf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9acbf-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="9acbf-106">[out] Pointeur vers le nombre de threads de terminaison d’e/s gérés par l’hôte qui sont actuellement disponibles pour traiter les demandes.</span><span class="sxs-lookup"><span data-stu-id="9acbf-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9acbf-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9acbf-107">Return Value</span></span>  
  
|<span data-ttu-id="9acbf-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9acbf-108">HRESULT</span></span>|<span data-ttu-id="9acbf-109">Description</span><span class="sxs-lookup"><span data-stu-id="9acbf-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9acbf-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9acbf-110">S_OK</span></span>|<span data-ttu-id="9acbf-111">`GetAvailableThreads`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="9acbf-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="9acbf-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9acbf-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9acbf-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="9acbf-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9acbf-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9acbf-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9acbf-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="9acbf-115">The call timed out.</span></span>|  
|<span data-ttu-id="9acbf-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9acbf-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9acbf-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="9acbf-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9acbf-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9acbf-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9acbf-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="9acbf-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9acbf-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9acbf-120">E_FAIL</span></span>|<span data-ttu-id="9acbf-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="9acbf-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9acbf-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9acbf-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9acbf-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9acbf-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9acbf-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="9acbf-124">E_NOTIMPL</span></span>|<span data-ttu-id="9acbf-125">L’hôte ne fournit pas une implémentation de `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="9acbf-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9acbf-126">Notes</span><span class="sxs-lookup"><span data-stu-id="9acbf-126">Remarks</span></span>  
 <span data-ttu-id="9acbf-127">Un hôte peut souhaiter le contrôle exclusif sur la taille du pool de threads d’achèvement d’e/s, pour des raisons telles que l’implémentation, les performances ou l’évolutivité.</span><span class="sxs-lookup"><span data-stu-id="9acbf-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="9acbf-128">Par conséquent, l’hôte n’est pas requis pour implémenter `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="9acbf-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="9acbf-129">Dans ce cas, l’hôte doit retourner E_NOTIMPL à partir de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="9acbf-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9acbf-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9acbf-130">Requirements</span></span>  
 <span data-ttu-id="9acbf-131">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9acbf-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9acbf-132">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9acbf-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9acbf-133">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9acbf-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9acbf-134">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9acbf-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9acbf-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9acbf-135">See Also</span></span>  
 [<span data-ttu-id="9acbf-136">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="9acbf-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="9acbf-137">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="9acbf-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
