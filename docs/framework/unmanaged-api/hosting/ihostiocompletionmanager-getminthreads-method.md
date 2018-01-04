---
title: "IHostIoCompletionManager::GetMinThreads, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.GetMinThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::GetMinThreads
helpviewer_keywords:
- GetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetMinThreads method [.NET Framework hosting]
ms.assetid: d7a7f733-677d-481c-b3d5-444fcc502b8e
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f90a3f416520cc3f635f19d7ae34d5f9f304e9c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="236b9-102">IHostIoCompletionManager::GetMinThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="236b9-102">IHostIoCompletionManager::GetMinThreads Method</span></span>
<span data-ttu-id="236b9-103">Obtient le nombre minimal de threads que l’hôte fournit pour traiter les demandes d’e/s.</span><span class="sxs-lookup"><span data-stu-id="236b9-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="236b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="236b9-104">Syntax</span></span>  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="236b9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="236b9-105">Parameters</span></span>  
 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="236b9-106">[out] Pointeur vers le nombre minimal de threads que l’hôte fournit aux demandes du processus d’e/s.</span><span class="sxs-lookup"><span data-stu-id="236b9-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="236b9-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="236b9-107">Return Value</span></span>  
  
|<span data-ttu-id="236b9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="236b9-108">HRESULT</span></span>|<span data-ttu-id="236b9-109">Description</span><span class="sxs-lookup"><span data-stu-id="236b9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="236b9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="236b9-110">S_OK</span></span>|<span data-ttu-id="236b9-111">`GetMinThreads`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="236b9-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="236b9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="236b9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="236b9-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="236b9-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="236b9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="236b9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="236b9-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="236b9-115">The call timed out.</span></span>|  
|<span data-ttu-id="236b9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="236b9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="236b9-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="236b9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="236b9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="236b9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="236b9-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="236b9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="236b9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="236b9-120">E_FAIL</span></span>|<span data-ttu-id="236b9-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="236b9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="236b9-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="236b9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="236b9-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="236b9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="236b9-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="236b9-124">E_NOTIMPL</span></span>|<span data-ttu-id="236b9-125">L’hôte ne fournit pas une implémentation de `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="236b9-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="236b9-126">Notes</span><span class="sxs-lookup"><span data-stu-id="236b9-126">Remarks</span></span>  
 <span data-ttu-id="236b9-127">Un hôte peut souhaiter le contrôle exclusif sur le nombre de threads alloués pour traiter les demandes d’e/s, pour des raisons telles que l’implémentation, les performances ou l’évolutivité.</span><span class="sxs-lookup"><span data-stu-id="236b9-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="236b9-128">Pour cette raison, l’hôte n’est pas tenu d’implémenter `GetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="236b9-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="236b9-129">Dans ce cas, l’hôte doit retourner E_NOTIMPL à partir de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="236b9-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="236b9-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="236b9-130">Requirements</span></span>  
 <span data-ttu-id="236b9-131">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="236b9-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="236b9-132">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="236b9-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="236b9-133">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="236b9-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="236b9-134">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="236b9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="236b9-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="236b9-135">See Also</span></span>  
 [<span data-ttu-id="236b9-136">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="236b9-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="236b9-137">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="236b9-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
