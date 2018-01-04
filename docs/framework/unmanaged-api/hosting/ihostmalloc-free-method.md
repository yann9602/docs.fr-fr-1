---
title: "IHostMAlloc::Free, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc.Free
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc::Free
helpviewer_keywords:
- IHostMAlloc::Free method [.NET Framework hosting]
- Free method, IHostMAlloc interface [.NET Framework hosting]
ms.assetid: c89abf5b-1120-4437-8b57-4a99fb3ae7f9
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4775b6ae00f34d7d046515f8700a35470b2f6650
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="7eb98-102">IHostMAlloc::Free, méthode</span><span class="sxs-lookup"><span data-stu-id="7eb98-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="7eb98-103">Libère la mémoire qui a été allouée à l’aide de la [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="7eb98-103">Frees memory that was allocated by using the [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eb98-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7eb98-104">Syntax</span></span>  
  
```  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7eb98-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7eb98-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="7eb98-106">[in] Pointeur vers la mémoire à libérer.</span><span class="sxs-lookup"><span data-stu-id="7eb98-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7eb98-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7eb98-107">Return Value</span></span>  
  
|<span data-ttu-id="7eb98-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7eb98-108">HRESULT</span></span>|<span data-ttu-id="7eb98-109">Description</span><span class="sxs-lookup"><span data-stu-id="7eb98-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7eb98-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7eb98-110">S_OK</span></span>|<span data-ttu-id="7eb98-111">`Free`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="7eb98-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="7eb98-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7eb98-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7eb98-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="7eb98-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7eb98-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7eb98-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7eb98-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="7eb98-115">The call timed out.</span></span>|  
|<span data-ttu-id="7eb98-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7eb98-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7eb98-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="7eb98-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7eb98-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7eb98-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7eb98-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="7eb98-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7eb98-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7eb98-120">E_FAIL</span></span>|<span data-ttu-id="7eb98-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="7eb98-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7eb98-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="7eb98-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7eb98-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7eb98-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7eb98-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="7eb98-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="7eb98-125">Une tentative a été effectuée pour libérer de la mémoire n’est allouée par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="7eb98-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7eb98-126">Notes</span><span class="sxs-lookup"><span data-stu-id="7eb98-126">Remarks</span></span>  
 <span data-ttu-id="7eb98-127">Si le `pMem` paramètre fait référence à une région de mémoire n’est allouée à l’aide d’un appel à `Alloc`, l’hôte doit retourner HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="7eb98-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7eb98-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7eb98-128">Requirements</span></span>  
 <span data-ttu-id="7eb98-129">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7eb98-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7eb98-130">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7eb98-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7eb98-131">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7eb98-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7eb98-132">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7eb98-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eb98-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7eb98-133">See Also</span></span>  
 [<span data-ttu-id="7eb98-134">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="7eb98-134">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="7eb98-135">IHostMalloc, interface</span><span class="sxs-lookup"><span data-stu-id="7eb98-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
