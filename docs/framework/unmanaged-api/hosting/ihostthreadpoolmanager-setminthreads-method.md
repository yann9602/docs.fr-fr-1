---
title: "IHostThreadPoolManager::SetMinThreads, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.SetMinThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fccfeb616b7a1c6d797ad9d91f47e696c4f3599
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="067c7-102">IHostThreadPoolManager::SetMinThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="067c7-102">IHostThreadPoolManager::SetMinThreads Method</span></span>
<span data-ttu-id="067c7-103">Définit le nombre minimal de threads inactifs que l’hôte doit gérer en anticipation des demandes.</span><span class="sxs-lookup"><span data-stu-id="067c7-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="067c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="067c7-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="067c7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="067c7-105">Parameters</span></span>  
 `MinThreads`  
 <span data-ttu-id="067c7-106">[in] Le nouveau nombre minimal de threads que l’hôte doit gérer.</span><span class="sxs-lookup"><span data-stu-id="067c7-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="067c7-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="067c7-107">Return Value</span></span>  
  
|<span data-ttu-id="067c7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="067c7-108">HRESULT</span></span>|<span data-ttu-id="067c7-109">Description</span><span class="sxs-lookup"><span data-stu-id="067c7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="067c7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="067c7-110">S_OK</span></span>|<span data-ttu-id="067c7-111">`SetMinThreads`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="067c7-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="067c7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="067c7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="067c7-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="067c7-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="067c7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="067c7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="067c7-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="067c7-115">The call timed out.</span></span>|  
|<span data-ttu-id="067c7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="067c7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="067c7-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="067c7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="067c7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="067c7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="067c7-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="067c7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="067c7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="067c7-120">E_FAIL</span></span>|<span data-ttu-id="067c7-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="067c7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="067c7-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="067c7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="067c7-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="067c7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="067c7-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="067c7-124">E_NOTIMPL</span></span>|<span data-ttu-id="067c7-125">L’hôte ne fournit pas une implémentation de `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="067c7-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="067c7-126">Notes</span><span class="sxs-lookup"><span data-stu-id="067c7-126">Remarks</span></span>  
 <span data-ttu-id="067c7-127">Un hôte n’est pas obligé de fournir une implémentation de `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="067c7-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="067c7-128">Dans ce cas, elle doit retourner une valeur HRESULT d’E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="067c7-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="067c7-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="067c7-129">Requirements</span></span>  
 <span data-ttu-id="067c7-130">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="067c7-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="067c7-131">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="067c7-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="067c7-132">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="067c7-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="067c7-133">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="067c7-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="067c7-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="067c7-134">See Also</span></span>  
 <xref:System.Threading.ThreadPool.SetMinThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="067c7-135">GetMinThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="067c7-135">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)  
 [<span data-ttu-id="067c7-136">SetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="067c7-136">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="067c7-137">IHostThreadPoolManager, interface</span><span class="sxs-lookup"><span data-stu-id="067c7-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
