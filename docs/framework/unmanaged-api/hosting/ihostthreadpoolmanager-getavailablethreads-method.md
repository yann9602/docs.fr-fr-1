---
title: "IHostThreadPoolManager::GetAvailableThreads, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.GetAvailableThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: 61d26dfd-7f24-4e7d-a63e-b30a463f08e1
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5151b26bad08ef8e1e3c53d649f57f79eb18d03c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="6f988-102">IHostThreadPoolManager::GetAvailableThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="6f988-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="6f988-103">Obtient le nombre de threads du pool de threads qui ne traitent pas actuellement des éléments de travail.</span><span class="sxs-lookup"><span data-stu-id="6f988-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f988-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f988-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f988-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6f988-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="6f988-106">[out] Pointeur vers le nombre de threads dans le pool de threads qui ne traitent pas actuellement des éléments de travail.</span><span class="sxs-lookup"><span data-stu-id="6f988-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f988-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6f988-107">Return Value</span></span>  
  
|<span data-ttu-id="6f988-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f988-108">HRESULT</span></span>|<span data-ttu-id="6f988-109">Description</span><span class="sxs-lookup"><span data-stu-id="6f988-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f988-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f988-110">S_OK</span></span>|<span data-ttu-id="6f988-111">`GetAvailableThreads`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="6f988-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="6f988-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6f988-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6f988-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="6f988-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6f988-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6f988-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6f988-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="6f988-115">The call timed out.</span></span>|  
|<span data-ttu-id="6f988-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6f988-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6f988-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="6f988-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6f988-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6f988-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6f988-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="6f988-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6f988-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6f988-120">E_FAIL</span></span>|<span data-ttu-id="6f988-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="6f988-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6f988-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="6f988-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6f988-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6f988-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6f988-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="6f988-124">E_NOTIMPL</span></span>|<span data-ttu-id="6f988-125">L’hôte ne fournit pas une implémentation de `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="6f988-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f988-126">Notes</span><span class="sxs-lookup"><span data-stu-id="6f988-126">Remarks</span></span>  
 <span data-ttu-id="6f988-127">Si l’hôte ne fournit pas une implémentation de `GetAvailableThreads`, elle doit retourner une valeur HRESULT d’E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="6f988-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f988-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6f988-128">Requirements</span></span>  
 <span data-ttu-id="6f988-129">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f988-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f988-130">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6f988-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f988-131">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6f988-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f988-132">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f988-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f988-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f988-133">See Also</span></span>  
 <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="6f988-134">IHostThreadPoolManager, interface</span><span class="sxs-lookup"><span data-stu-id="6f988-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
