---
title: "IHostMAlloc::Alloc, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc.Alloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc::Alloc
helpviewer_keywords:
- Alloc method, IHostMAlloc interface [.NET Framework hosting]
- IHostMAlloc::Alloc method [.NET Framework hosting]
ms.assetid: a3007f5e-d75d-4b37-842b-704e9edced5e
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d999425be2bc5963aaa9f15b82bd951f6f564af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="7782e-102">IHostMAlloc::Alloc, méthode</span><span class="sxs-lookup"><span data-stu-id="7782e-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="7782e-103">Demande que l’hôte alloue la quantité de mémoire spécifiée à partir du tas.</span><span class="sxs-lookup"><span data-stu-id="7782e-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7782e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7782e-104">Syntax</span></span>  
  
```  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,   
    [in] EMemoryCriticalLevel dwCriticalLevel,   
    [out] void** ppMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7782e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7782e-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="7782e-106">[in] La taille, en octets, de la demande d’allocation de mémoire actuelle.</span><span class="sxs-lookup"><span data-stu-id="7782e-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="7782e-107">[in] Parmi les [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) valeurs, indiquant l’impact d’un échec d’allocation.</span><span class="sxs-lookup"><span data-stu-id="7782e-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="7782e-108">[out] Pointeur vers la mémoire allouée, ou null si la demande n’a pas pu être effectuée.</span><span class="sxs-lookup"><span data-stu-id="7782e-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7782e-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7782e-109">Return Value</span></span>  
  
|<span data-ttu-id="7782e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7782e-110">HRESULT</span></span>|<span data-ttu-id="7782e-111">Description</span><span class="sxs-lookup"><span data-stu-id="7782e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7782e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="7782e-112">S_OK</span></span>|<span data-ttu-id="7782e-113">`Alloc`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="7782e-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="7782e-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7782e-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7782e-115">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="7782e-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7782e-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7782e-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7782e-117">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="7782e-117">The call timed out.</span></span>|  
|<span data-ttu-id="7782e-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7782e-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7782e-119">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="7782e-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7782e-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7782e-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7782e-121">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="7782e-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7782e-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7782e-122">E_FAIL</span></span>|<span data-ttu-id="7782e-123">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="7782e-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7782e-124">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="7782e-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7782e-125">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7782e-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7782e-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7782e-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7782e-127">Mémoire était insuffisante pour terminer la demande d’allocation.</span><span class="sxs-lookup"><span data-stu-id="7782e-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7782e-128">Notes</span><span class="sxs-lookup"><span data-stu-id="7782e-128">Remarks</span></span>  
 <span data-ttu-id="7782e-129">Le CLR obtient un pointeur d’interface vers un `IHostMalloc` instance en appelant le [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="7782e-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7782e-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7782e-130">Requirements</span></span>  
 <span data-ttu-id="7782e-131">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7782e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7782e-132">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7782e-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7782e-133">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7782e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7782e-134">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7782e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7782e-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7782e-135">See Also</span></span>  
 [<span data-ttu-id="7782e-136">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="7782e-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="7782e-137">IHostMalloc, interface</span><span class="sxs-lookup"><span data-stu-id="7782e-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
