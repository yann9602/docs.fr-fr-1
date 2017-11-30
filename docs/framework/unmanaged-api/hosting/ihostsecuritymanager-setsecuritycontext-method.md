---
title: "IHostSecurityManager::SetSecurityContext, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.SetSecurityContext
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::SetSecurityContext
helpviewer_keywords:
- SetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::SetSecurityContext method [.NET Framework hosting]
ms.assetid: e4372384-ee69-48d7-97e0-8fab7866597a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c25b8bb0effb4e5e1e61447c74c9729989d04702
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="cf4aa-102">IHostSecurityManager::SetSecurityContext, méthode</span><span class="sxs-lookup"><span data-stu-id="cf4aa-102">IHostSecurityManager::SetSecurityContext Method</span></span>
<span data-ttu-id="cf4aa-103">Définit le contexte de sécurité du thread en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="cf4aa-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf4aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf4aa-104">Syntax</span></span>  
  
```  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf4aa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cf4aa-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="cf4aa-106">[in] Parmi les [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) valeurs, indiquant le type de contexte que le common language runtime (CLR) place sur l’hôte.</span><span class="sxs-lookup"><span data-stu-id="cf4aa-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="cf4aa-107">[out] Un pointeur vers l’adresse d’un nouveau [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) objet.</span><span class="sxs-lookup"><span data-stu-id="cf4aa-107">[out] A pointer to the address of a new [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf4aa-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="cf4aa-108">Return Value</span></span>  
  
|<span data-ttu-id="cf4aa-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cf4aa-109">HRESULT</span></span>|<span data-ttu-id="cf4aa-110">Description</span><span class="sxs-lookup"><span data-stu-id="cf4aa-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cf4aa-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="cf4aa-111">S_OK</span></span>|<span data-ttu-id="cf4aa-112">`SetSecurityContext`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="cf4aa-112">`SetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="cf4aa-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cf4aa-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cf4aa-114">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="cf4aa-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cf4aa-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cf4aa-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cf4aa-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="cf4aa-116">The call timed out.</span></span>|  
|<span data-ttu-id="cf4aa-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cf4aa-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cf4aa-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="cf4aa-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cf4aa-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cf4aa-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cf4aa-120">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="cf4aa-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cf4aa-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cf4aa-121">E_FAIL</span></span>|<span data-ttu-id="cf4aa-122">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="cf4aa-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cf4aa-123">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="cf4aa-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cf4aa-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cf4aa-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf4aa-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="cf4aa-125">Remarks</span></span>  
 <span data-ttu-id="cf4aa-126">Le CLR appelle `SetSecurityContext` dans plusieurs scénarios.</span><span class="sxs-lookup"><span data-stu-id="cf4aa-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="cf4aa-127">Avant d’exécuter les constructeurs de module et les finaliseurs de classes et, le CLR appelle `SetSecurityContext` pour protéger l’ordinateur hôte à partir des erreurs d’exécution.</span><span class="sxs-lookup"><span data-stu-id="cf4aa-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="cf4aa-128">Il réinitialise ensuite le contexte de sécurité à son état d’origine après l’exécution du constructeur ou finaliseur, à l’aide d’un autre appel à `SetSecurityContext`.</span><span class="sxs-lookup"><span data-stu-id="cf4aa-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="cf4aa-129">Un modèle semblable se produit avec la saisie semi-automatique des e/s.</span><span class="sxs-lookup"><span data-stu-id="cf4aa-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="cf4aa-130">Si l’hôte implémente [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), le CLR appelle `SetSecurityContext` après l’hôte appelle [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="cf4aa-130">If the host implements [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="cf4aa-131">Aux points asynchrones dans les threads de travail, le CLR appelle `SetSecurityContext` dans <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> ou dans [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), selon que l’ordinateur hôte ou le CLR implémente le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="cf4aa-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf4aa-132">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cf4aa-132">Requirements</span></span>  
 <span data-ttu-id="cf4aa-133">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf4aa-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf4aa-134">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cf4aa-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf4aa-135">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf4aa-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf4aa-136">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf4aa-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf4aa-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf4aa-137">See Also</span></span>  
 <xref:System.Threading.ThreadPool?displayProperty=nameWithType>  
 [<span data-ttu-id="cf4aa-138">EContextType (énumération)</span><span class="sxs-lookup"><span data-stu-id="cf4aa-138">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)  
 [<span data-ttu-id="cf4aa-139">ICLRIoCompletionManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="cf4aa-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="cf4aa-140">IHostIoCompletionManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="cf4aa-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="cf4aa-141">IHostSecurityContext (Interface)</span><span class="sxs-lookup"><span data-stu-id="cf4aa-141">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="cf4aa-142">IHostSecurityManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="cf4aa-142">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="cf4aa-143">IHostThreadPoolManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="cf4aa-143">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
