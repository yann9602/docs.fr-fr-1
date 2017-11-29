---
title: "IHostMemoryManager::CreateMAlloc, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.CreateMAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::CreateMAlloc
helpviewer_keywords:
- CreateAlloc method [.NET Framework hosting]
- IHostMemoryManager::CreateMAlloc method [.NET Framework hosting]
ms.assetid: 9ee6e052-bef7-4350-9e4f-edfffd99ad6f
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25b4f8a23d03b3d839aeab5d2f571cb4f98f1ec5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="3e130-102">IHostMemoryManager::CreateMAlloc, méthode</span><span class="sxs-lookup"><span data-stu-id="3e130-102">IHostMemoryManager::CreateMAlloc Method</span></span>
<span data-ttu-id="3e130-103">Obtient un pointeur d’interface vers un [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance qui est utilisé pour effectuer des demandes d’allocation à partir d’un tas créé par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="3e130-103">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e130-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e130-104">Syntax</span></span>  
  
```  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3e130-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3e130-105">Parameters</span></span>  
 `dwMallocType`  
 <span data-ttu-id="3e130-106">[in] Une combinaison de [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) indicateurs qui spécifie les caractéristiques de la mémoire est allouée.</span><span class="sxs-lookup"><span data-stu-id="3e130-106">[in] A combination of [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="3e130-107">[out] Un pointeur vers l’adresse d’un `IHostMAlloc` fournie par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="3e130-107">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e130-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3e130-108">Return Value</span></span>  
  
|<span data-ttu-id="3e130-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3e130-109">HRESULT</span></span>|<span data-ttu-id="3e130-110">Description</span><span class="sxs-lookup"><span data-stu-id="3e130-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3e130-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3e130-111">S_OK</span></span>|<span data-ttu-id="3e130-112">`CreateMAlloc`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="3e130-112">`CreateMAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="3e130-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3e130-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3e130-114">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="3e130-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3e130-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3e130-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3e130-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="3e130-116">The call timed out.</span></span>|  
|<span data-ttu-id="3e130-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3e130-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3e130-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="3e130-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3e130-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3e130-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3e130-120">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="3e130-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3e130-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3e130-121">E_FAIL</span></span>|<span data-ttu-id="3e130-122">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="3e130-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3e130-123">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="3e130-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3e130-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3e130-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3e130-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3e130-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="3e130-126">Pas assez de mémoire physique a été permet d’effectuer la demande d’allocation.</span><span class="sxs-lookup"><span data-stu-id="3e130-126">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e130-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="3e130-127">Remarks</span></span>  
 <span data-ttu-id="3e130-128">`CreateMAlloc`Retourne un objet qui permet au CLR effectuer des demandes d’allocation via l’hôte au lieu d’utiliser les fonctions Win32 standard.</span><span class="sxs-lookup"><span data-stu-id="3e130-128">`CreateMAlloc` returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e130-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3e130-129">Requirements</span></span>  
 <span data-ttu-id="3e130-130">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e130-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e130-131">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3e130-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e130-132">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3e130-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e130-133">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e130-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e130-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e130-134">See Also</span></span>  
 [<span data-ttu-id="3e130-135">IHostMalloc (Interface)</span><span class="sxs-lookup"><span data-stu-id="3e130-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [<span data-ttu-id="3e130-136">IHostMemoryManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="3e130-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
