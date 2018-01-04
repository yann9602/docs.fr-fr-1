---
title: "IHostIoCompletionManager::SetCLRIoCompletionManager, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.SetCLRIoCompletionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fde1045fd0f15e7255a163c1f1b041800e85921
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="d8d72-102">IHostIoCompletionManager::SetCLRIoCompletionManager, méthode</span><span class="sxs-lookup"><span data-stu-id="d8d72-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="d8d72-103">Fournit à l’hôte avec un pointeur d’interface vers le [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implémentée par le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="d8d72-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8d72-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8d72-104">Syntax</span></span>  
  
```  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8d72-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d8d72-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="d8d72-106">[in] Pointeur d’interface vers un `ICLRIoCompletionManager` fournie par le CLR.</span><span class="sxs-lookup"><span data-stu-id="d8d72-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8d72-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d8d72-107">Return Value</span></span>  
  
|<span data-ttu-id="d8d72-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d8d72-108">HRESULT</span></span>|<span data-ttu-id="d8d72-109">Description</span><span class="sxs-lookup"><span data-stu-id="d8d72-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d8d72-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d8d72-110">S_OK</span></span>|<span data-ttu-id="d8d72-111">`SetCLRIoCompletionManager`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="d8d72-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="d8d72-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d8d72-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d8d72-113">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="d8d72-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d8d72-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d8d72-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d8d72-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="d8d72-115">The call timed out.</span></span>|  
|<span data-ttu-id="d8d72-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d8d72-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d8d72-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="d8d72-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d8d72-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d8d72-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d8d72-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="d8d72-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d8d72-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d8d72-120">E_FAIL</span></span>|<span data-ttu-id="d8d72-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="d8d72-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d8d72-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="d8d72-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d8d72-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d8d72-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8d72-124">Notes</span><span class="sxs-lookup"><span data-stu-id="d8d72-124">Remarks</span></span>  
 <span data-ttu-id="d8d72-125">Une fois que le CLR a appelé `SetCLRIoCompletionManager`, l’hôte doit appeler [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) pour informer le CLR lorsqu’une demande d’e/s a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="d8d72-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8d72-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d8d72-126">Requirements</span></span>  
 <span data-ttu-id="d8d72-127">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8d72-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8d72-128">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d8d72-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d8d72-129">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d8d72-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8d72-130">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8d72-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8d72-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8d72-131">See Also</span></span>  
 [<span data-ttu-id="d8d72-132">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="d8d72-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="d8d72-133">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="d8d72-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
