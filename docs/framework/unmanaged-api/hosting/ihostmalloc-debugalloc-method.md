---
title: "IHostMAlloc::DebugAlloc, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc.DebugAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 18759aa319bf39c49418e3b9388d96829ed52f7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="3fff8-102">IHostMAlloc::DebugAlloc, méthode</span><span class="sxs-lookup"><span data-stu-id="3fff8-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="3fff8-103">Demande que l’hôte alloue la quantité de mémoire spécifiée à partir du tas et enregistre également où la mémoire a été allouée.</span><span class="sxs-lookup"><span data-stu-id="3fff8-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fff8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fff8-104">Syntax</span></span>  
  
```  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,   
    [in]  EMemoryCriticalLevel dwCriticalLevel,   
    [in]  char*   pszFileName,   
    [in]  int     iLineNo,   
    [out] void**  ppMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3fff8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3fff8-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="3fff8-106">[in] La taille, en octets, de la demande d’allocation de mémoire actuelle.</span><span class="sxs-lookup"><span data-stu-id="3fff8-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="3fff8-107">[in] Parmi les [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) valeurs, indiquant l’impact d’un échec d’allocation.</span><span class="sxs-lookup"><span data-stu-id="3fff8-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="3fff8-108">[in] Le fichier de code de l’exécutable en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="3fff8-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="3fff8-109">[in] Le numéro de ligne dans `pszFileName` où l’allocation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="3fff8-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="3fff8-110">[out] Pointeur vers la mémoire allouée, ou null si la demande n’a pas pu être effectuée.</span><span class="sxs-lookup"><span data-stu-id="3fff8-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3fff8-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3fff8-111">Return Value</span></span>  
  
|<span data-ttu-id="3fff8-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3fff8-112">HRESULT</span></span>|<span data-ttu-id="3fff8-113">Description</span><span class="sxs-lookup"><span data-stu-id="3fff8-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3fff8-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="3fff8-114">S_OK</span></span>|<span data-ttu-id="3fff8-115">`DebugAlloc`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="3fff8-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="3fff8-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3fff8-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3fff8-117">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="3fff8-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3fff8-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3fff8-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3fff8-119">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="3fff8-119">The call timed out.</span></span>|  
|<span data-ttu-id="3fff8-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3fff8-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3fff8-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="3fff8-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3fff8-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3fff8-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3fff8-123">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="3fff8-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3fff8-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3fff8-124">E_FAIL</span></span>|<span data-ttu-id="3fff8-125">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="3fff8-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3fff8-126">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="3fff8-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3fff8-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3fff8-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3fff8-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3fff8-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="3fff8-129">Mémoire était insuffisante pour terminer la demande d’allocation.</span><span class="sxs-lookup"><span data-stu-id="3fff8-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fff8-130">Remarques</span><span class="sxs-lookup"><span data-stu-id="3fff8-130">Remarks</span></span>  
 <span data-ttu-id="3fff8-131">Le CLR obtient un pointeur d’interface vers un [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance en appelant le [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="3fff8-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="3fff8-132">`DebugAlloc`permet l’exécution pour obtenir des informations sur les fichiers de code pour une utilisation pendant le débogage.</span><span class="sxs-lookup"><span data-stu-id="3fff8-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fff8-133">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3fff8-133">Requirements</span></span>  
 <span data-ttu-id="3fff8-134">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fff8-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fff8-135">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3fff8-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3fff8-136">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3fff8-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3fff8-137">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fff8-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fff8-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fff8-138">See Also</span></span>  
 [<span data-ttu-id="3fff8-139">IHostMemoryManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="3fff8-139">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="3fff8-140">IHostMalloc (Interface)</span><span class="sxs-lookup"><span data-stu-id="3fff8-140">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
